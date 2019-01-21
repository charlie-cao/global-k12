---
title: "如何使用 Weave Scope."
date: 2019-01-04T15:04:10.000Z
description: 如何使用 Weave Scope
image: /img/manager_screenshot@2x.png
---
Weave Scope 是容器发现和洞察工具.
功能为发现容器关系
监控容器状态
进入容器.

非常有用,如果用来管理docker 容器,类似于mac 下的kitematic
..


(Optional) Launch Weave Scope or Weave Cloud
Weave Scope (local instance)

sudo curl -L git.io/scope -o /usr/local/bin/scope
sudo chmod a+x /usr/local/bin/scope
scope launch
Weave Cloud (hosted platform). Get a token by registering here.

sudo curl -L git.io/scope -o /usr/local/bin/scope
sudo chmod a+x /usr/local/bin/scope
scope launch --service-token=<token>



https://microservices-demo.github.io/deployment/docker-compose-weave.html


启动k8sDashboard at mac docker local

kubectl config use-context docker-for-desktop


kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml


kubectl proxy

UI
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/.

获得登录令牌.
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/

访问站点使用 http://localhost:30001/



linkerd install --linkerd-namespace sock-shop | kubectl apply -f -


Linkerd weavescope 到底是干什么的. 服务网格.

Haproxy 和 k8s的结合意义何在
如果没有Haproxy 那么不用K8s就不行了.但是用了K8s还是可以用Haproxy的.虽然Google不建议用这样的负载均衡器.
https://www.weave.works/blog/kubernetes-best-practices

微服务的容器的版本管理很重要,

问题：当Prod与版本控制不匹配时，您会怎么做？
除了将所有内容保存在Git中之外，我们还运行一个过程来检查prod群集中运行的内容与检入版本控制中的内容之间的差异。当它检测到差异时，会向我们的松弛通道发送警报。

我们使用名为Kube-Diff的开源工具检查差异。

挑战2.自动化持续交付
自动化CI / CD管道并避免手动部署Kubernetes。由于我们每天要多次部署，因此这种方法可以节省团队宝贵的时间，因为它可以消除手动容易出错的步骤。在Weaveworks，开发人员只需执行Git推送，Weave Cloud负责其余工作：

标记代码通过CircleCI测试运行并构建新的容器映像并将新映像推送到注册表。
Weave Cloud'Deploy Automator'通知图像，从存储库中提取新图像，然后在配置仓库中更新其YAML。  
部署同步器检测到群集已过期，它从配置存储库中提取已更改的清单，并将新映像部署到群集。


# 所有下游依赖项都不可靠
您的应用程序中应包含逻辑和错误消息，以说明您无法控制的任何依赖项。为了帮助您进行下游管理，Sandeep建议您可以使用像Istio或Linkerd这样的服务网格。

# 使用Weave Cloud
集群很难可视化和管理，因此使用Weave Cloud可以帮助您了解内部发生的情况并跟踪依赖性。

不要使用type：LoadBalancer
每当您将负载均衡器添加到其中一个公共云提供商的部署文件中时，它就会旋转一个。这对于高可用性和速度非常有用，但它需要花钱。

提示：使用Ingress代替，它允许您通过单个端点对多个服务进行负载平衡。这不仅更简单，而且更便宜。



http://docs.stackpoint.io/en/latest/userguide/ingress/haproxy.html

Haproxy K8s
https://github.com/jcmoraisjr/haproxy-ingress
https://github.com/appscode/voyager


前端还是REACT CSS框架支持SCSS 

服务端使用Go Nodejs

部署使用Jenkins

基础设施使用K8s Docker

开发 Scrum + DEVPOS. GitOps

代码使用Git.

测试 + TDD.

接口标准使用

队列RbitMQ.

负载均衡器 HAproxy

服务发现. xxxx

存储使用S3之类的.

前端就是静态的.

后端才需要上头那些.




