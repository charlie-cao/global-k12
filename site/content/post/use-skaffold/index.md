---
title: "如何使用Skaffold."
date: 2019-01-05T15:04:10.000Z
description: 如何使用Skaffold
image: /img/manager_screenshot@2x.png
---

https://skaffold.dev/docs/getting-started/

## install skaffold

brew install skaffold

## install docker and kubernets

mac: install and start kubernets

Tip: start kubernets UI

kubectl proxy &

dashboard-adminuser.yaml
```
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kube-system
```

kubectl apply -f dashboard-adminuser.yaml

kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

use access tokin login at 

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/pod/default/getting-started?namespace=default


## clone skaffold

git clone https://github.com/GoogleContainerTools/skaffold

cd examples/getting-started

skaffold dev


open other shell and edit some source.

## deploy to g cloud [doing]

gcloud auth configure-docker


### 中间记录

简单理解一下. Skaffold 是google的子项目,用来简化从开发到部署到K8集群的过程.也是CI CD的中间环节.

使用容器话部署以及微服务架构应该有比较好的经验.这个需要找到.

倒是有几个关键部分
 1 文件同步.
 2 版本控制.要是直接就上线,这不把中间测试和发布的环节省去了么.会缺少一些监管.