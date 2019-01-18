---
title: "如何使用kubectl."
date: 2019-01-04T15:04:10.000Z
description: 如何使用kubectl
image: /img/manager_screenshot@2x.png
---

```
kubectl controls the Kubernetes cluster manager.

Find more information at: https://kubernetes.io/docs/reference/kubectl/overview/

Basic Commands (Beginner):
  create         Create a resource from a file or from stdin.
  expose         Take a replication controller, service, deployment or pod and expose it as a new Kubernetes Service
  run            Run a particular image on the cluster
  set            Set specific features on objects
  run-container  Run a particular image on the cluster. This command is deprecated, use "run" instead

Basic Commands (Intermediate):
  get            Display one or many resources
  explain        Documentation of resources
  edit           Edit a resource on the server
  delete         Delete resources by filenames, stdin, resources and names, or by resources and label selector

Deploy Commands:
  rollout        Manage the rollout of a resource
  rolling-update Perform a rolling update of the given ReplicationController
  scale          Set a new size for a Deployment, ReplicaSet, Replication Controller, or Job
  autoscale      Auto-scale a Deployment, ReplicaSet, or ReplicationController

Cluster Management Commands:
  certificate    Modify certificate resources.
  cluster-info   Display cluster info
  top            Display Resource (CPU/Memory/Storage) usage.
  cordon         Mark node as unschedulable
  uncordon       Mark node as schedulable
  drain          Drain node in preparation for maintenance
  taint          Update the taints on one or more nodes

Troubleshooting and Debugging Commands:
  describe       Show details of a specific resource or group of resources
  logs           Print the logs for a container in a pod
  attach         Attach to a running container
  exec           Execute a command in a container
  port-forward   Forward one or more local ports to a pod
  proxy          Run a proxy to the Kubernetes API server
  cp             Copy files and directories to and from containers.
  auth           Inspect authorization

Advanced Commands:
  apply          Apply a configuration to a resource by filename or stdin
  patch          Update field(s) of a resource using strategic merge patch
  replace        Replace a resource by filename or stdin
  convert        Convert config files between different API versions

Settings Commands:
  label          Update the labels on a resource
  annotate       Update the annotations on a resource
  completion     Output shell completion code for the specified shell (bash or zsh)

Other Commands:
  api-versions   Print the supported API versions on the server, in the form of "group/version"
  config         Modify kubeconfig files
  help           Help about any command
  plugin         Runs a command-line plugin
  version        Print the client and server version information

Usage:
  kubectl [flags] [options]

Use "kubectl <command> --help" for more information about a given command.
Use "kubectl options" for a list of global command-line options (applies to all commands).



kubectl控制Kubernetes集群管理器。

有关更多信息，请访问：https：//kubernetes.io/docs/reference/kubectl/overview/

基本命令（初级）：
  create          从文件或stdin创建资源。
  公开            获取复制控制器，服务，部署或pod，并将其作为新的Kubernetes服务公开
  运行            在群集上运行特定映像
  set               在对象上设置特定功能
  run-container       在集群上运行特定映像。不推荐使用此命令，而是使用“run”

基本命令（中级）：
  获取              显示一个或多个资源
  解释                资源的文档
  编辑                编辑服务器上的资源
  delete              按文件名，标准输入，资源和名称或资源和标签选择器删除资源

部署命令：
  rollout             管理资源的部署
  rolling-update          执行给定ReplicationController的滚动更新
  scale               为Deployment，ReplicaSet，Replication Controller或Job设置新大小
  autoscale             自动扩展Deployment，ReplicaSet或ReplicationController

群集管理命令：
  证书                修改证书资源。
  cluster-info        显示集群信息
  top               显示资源（CPU /内存/存储）使用情况。
  警戒线            标记为不可调度
  uncordon        标记节点为可调度
  排水            节点准备维护
  污染            更新一个或多个节点上的污点

故障排除和调试命令：
  describe        显示特定资源或资源组的详细信息
  logs            打印容器中容器的日志
  附加            附加到正在运行的容器
  exec            在容器中执行命令
  port-forward      将一个或多个本地端口转发到pod
  代理      运行代理到Kubernetes API服务器
  cp        将文件和目录复制到容器和从容器复制。
  auth      检查授权

高级命令：
  apply       通过filename或stdin将配置应用于资源
  patch       使用策略合并补丁更新资源的字段
  replace     用filename或stdin替换资源
  转换        在不同的API版本之间转换配置文件

设置命令：
  label       更新资源上的标签
  annotate    更新资源上的注释
  完成        指定shell的外壳完成代码（bash或zsh）

其他命令：
  api-versions  以“组/版本”的形式在服务器上打印支持的API版本
  config        修改kubeconfig文件
  帮助          任何命令的帮助
  插件          运行命令行插件
  version       打印客户端和服务器版本信息

用法：
  kubectl [flags] [选项]

有关给定命令的更多信息，请使用“kubectl <command> --help”。
使用“kubectl options”获取全局命令行选项列表（适用于所有命令）。

```



Gcloud 

```
命令名称参数。

gcloud的可用命令：

  AI和机器学习
      ml              使用Google Cloud机器学习功能。
      ml-engine       管理Cloud ML Engine作业和模型。

  API平台和生态系统
      endpoints             创建，启用和管理API服务。
      service-management    创建，启用和管理API服务。
      services              列出，启用和禁用API和服务。

  计算
      app                   管理您的App Engine部署。
      container(容器)             部署和管理要运行的计算机集群容器。
      functions(功能)       管理Google云功能。

  数据分析
      composer          创建和管理Cloud Composer环境。
      dataflow          管理Google Cloud Dataflow作业。
      dataproc          创建和管理Google Cloud Dataproc集群和工作。
      pubsub          管理Cloud Pub / Sub主题和订阅。

  数据库
      datastore(数据)            存储管理您的Cloud Datastore索引。
      spanner                   用于Cloud Spanner的命令组。
      sql                     创建和管理Google Cloud SQL数据库。

  身份和安全
      auth                管理Google Cloud的oauth2凭据SDK。
      iam               管理IAM服务帐户和密钥。
      kms               管理云中的加密密钥。

  物联网
      iot             管理云物联网资源。

  管理工具
      builds(构建)          为Google Cloud Build创建和管理构建。
      debug             用于与Cloud Debugger交互的命令。

 
      deployment-manager          管理云资源的部署。
      logging管               理堆栈驱动程序日志记录。
      organizations(组织)       创建和管理Google Cloud Platform组织。
      projects(项目)            创建和管理项目访问策略。

  移动
      firebase                使用Google Firebase。

  联网
      dns                 管理您的云DNS管理区域和记录集。
      domains(域)           管理您的Google Cloud项目的域。

  SDK工具
      components(组件)        列出，安装，更新或删除Google Cloud SDK 组件。
      config                  查看和编辑Cloud SDK属性。
      feedback(反馈)          向Google Cloud SDK小组提供反馈。
      help(帮助)              搜索gcloud帮助文本。
      info                  显示有关当前gcloud的信息环境。
      init                    初始化或重新初始化gcloud。
      meta                    Cloud meta内省命令。
      source(源)              Cloud git存储库命令。
      topic(主题)               gcloud补充帮助。
      version                 Cloud SDK的打印版本信息组件。

```