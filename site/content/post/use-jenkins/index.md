---
title: "使用Jenkins和docker完成从VSTS中检出代码持续集成并持续部署到GoogleCloud并发送通知到Slack."
date: 2019-01-04T15:04:10.000Z
description: 使用Jenkins和docker完成从VSTS中检出代码持续集成并持续部署到GoogleCloud并发送通知到Slack
image: /img/manager_screenshot@2x.png
---

从这个配置文件开始吧

# 全局变量的使用.
#配置提交google cloud的镜像名称
image = "gcr.io/xxxxx-111111/xxxxx_static"
# 启动的端口 grv 语法都可以用
port_list = [2222,3333]
tag = "tag"

# 管道的写法,还有一种简单的直接把stages 写在根上,就不用写steps了.但是就写不了node了.
pipeline {
    agent any
    stages {
        stage("Pull xxxxx-static"){
            steps{
                # 同slack 结合发送通知 
                slackSend color: "good", message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} start now.”
                # 执行容器内命令 和 如何远程执行 git pull
                sh 'cd /root/work/xxxxx-services/hugo_service/src/xxxxx-static && git pull'
            }
        }
        stage("Checkout xxxxx-services"){
            steps{
                # 从git获取源代码到工作空间跟目录
                git 'https://xxxxx.visualstudio.com/xxxxx-services/_git/xxxxx-services'
                // echo GIT_Revision()
            }
        }
        stage("Hugo Build"){
            steps{
                # 使用系统中运行的容器执行任务
                sh 'docker exec xxxxx-hugo-1313 /bin/hugo --cleanDestinationDir -s /src/xxxxx-static/ -b "https://www.xxxxx.io/" -d /output'
            }
        }
        stage("Rsync Site"){
            steps{
                # 获取输出 以及环境变量的使用
                sh 'rsync -a --delete /root/work/xxxxx-services/hugo_service/output/ '+env.WORKSPACE+'/static-service/html/public'
            }
        }
        stage("Docker Build"){
            steps{
                # 使用docker build
                dir('static-service'){
                    sh "docker build -t ${image} ."
                } 
            }
        }
        stage("Docker Run"){
            steps{
                script{
                    port_list.each {
                        # 循环删除和创建容器. 要说什么滚动升级应该就是在这里做文章. 
                        # 这里还出现了大纰漏 , docker container rm 命令要小心. 可能一下就把所有的容器都清理了.
                        # xargs 命令很有用把前面的输出当成自己的输入.
                        c_name = "xxxxx-static-"+it
                        sh "docker ps -f name=${c_name} -q | xargs --no-run-if-empty docker container stop"
                        sh "docker container ls -a -fname=${c_name} -q | xargs -r docker container rm"
                        sh "docker run -d -p ${it}:80 --name ${c_name} ${image}"
                    }  
                }
            }
        }      
        # 上面是本地部署,下面就是云部署了,应该可以通过参数来区别部署环境. gcloud安装后需要在当前机器登录.
        // stage("K8s"){
        //     sh "gcloud container clusters get-credentials standard-cluster-3 --zone us-east1-d --project xxxxx-111111"
        //     sh "docker push ${image}"
        // }
        # 清理工作空间.
        stage("Clean"){
            steps{
                cleanWs()
            }
        }      
    }
    post {
        always {
            /* Use slackNotifier.groovy from shared library and provide current build result as parameter */   
            // slackNotifier(currentBuild.currentResult)
            // cleanWs()
            script {
                # 必须添加script才能执行 里面的脚本 判断语句使用,以及发送通知的方法.
                if(currentBuild.currentResult == "SUCCESS" ){
                    slackSend color: "good", message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} was successful"
                }
                else if( currentBuild.currentResult == "FAILURE" ) { 
                    slackSend color: "danger", message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} was failed"
                }
                else if( currentBuild.currentResult == "UNSTABLE" ) { 
                    slackSend color: "warning", message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} was unstable"
                }
                else {
                    slackSend color: "danger", message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} its resulat was unclear"    
                }     
            }
        }
    }    
}
# 版本号获取,可以在当前配置中使用.
def GIT_Revision() {
    def matcher2 = readFile('.git/HEAD') =~ '(.+)'
    matcher2 ? matcher2[0][1] : null
}

    
    // stage("Build Base Docker"){
    //     dir('xxxxx_io_service'){
    //         sh 'docker build -t xxxxx-io-jenkins .'
    //     }        
    // }
    // stage("Build App Docker"){
    //     dir('xxxxx_io_app_service'){
    //         sh 'docker build -t xxxxx-io-app-jenkins .'
    //     }        
    // }
    // stage("Push Docker"){      
    //     dir('xxxxx_io_service'){
    //         sh 'docker stop app-xxxxx-io-jenkins'
    //         sh 'docker rm app-xxxxx-io-jenkins'
    //         sh 'docker run --name app-xxxxx-io-jenkins -p 801:80 -v html:/tool/nginx-1.14.0/html xxxxx-jenkins'
    //     }        
    //     // dir('xxxxx_io_service'){
    //         // sh 'docker commit -m "jenkins create" -a "jenkins create" app-xxxxx-io-jenkins'
    //     // }
    //     //push 
    //     //dump remont server.
    // }
    // stage("Init code"){
    //     dir('xxxxx_io_service'){
    //         sh 'docker exec app-xxxxx-io-jenkins /bin/bash -c "[/tool/nginx-1.14.0/html/init-prod.sh]"'
    //     }         
    // }
    //    docker exec app-xxxxx-io-80 /tool/nginx-1.14.0/html/init-prod.sh
    