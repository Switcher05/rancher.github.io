---
title: Adding Other Hosts
layout: rancher-default-v1.6-zh
version: v1.6
lang: zh
---

## 添加其他云提供商的主机
---

Rancher 支持使用 `docker machine` 来管理其他云提供商的主机服务。通过提供一个通用的界面，输入必要的参数键值对，然后作为 `docker-machine`运行的参数。

查阅 Docker Machine 的默认值文档来确保默认值符合预期想法。

### 添加云提供商的驱动

通过 [Admin（系统管理）]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/configuration/accounts/#管理员)的 [machine drivers（主机驱动）]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/configuration/machine-drivers/) 页面来添加。

### 启动云提供商的主机

选择 **Add Host（添加主机）** 页内的 **Other（其他）**：

1. 拖动滑条来选择需要启动的主机数目；
2. 输入 **Name（名称）**，需要详细备注的时候就填写 **Description（描述）**；
3. 选择要被使用的 **Driver（驱动）**；
4. 根据选择的 **Driver（驱动）**，输入对应的 **Driver Options（驱动选项）**。这些选项参数将会直接被 `docker machine`调用；
5. 必要时，添加 **[labels（标签）]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/hosts/#labels)** 来辅助管理主机以及 [调度服务或负载均衡]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/cattle/scheduling/)，也可以 [通过DNS-IP映射来管理不在 Rancher 内启动的服务]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/cattle/external-dns-service/#为外部dns使用特定的ip)；
6. 必要时，通过 **Advanced Options（高级选项）**，定制化 [Docker engine options（Docker引擎选项）](https://docs.docker.com/machine/reference/create/#specifying-configuration-options-for-the-created-docker-engine) 来控制 `docker-machine create` 时用到的选项指令；
7. 一切准备就绪后, 点击 **Create（创建）**。

点击创建后，Rancher 将创建选择对应 **Driver（驱动）** 的（虚拟）主机，接着在主机上启动一个 _rancher-agent_的容器。几分钟之后，就可以通过 [services（服务）]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/cattle/adding-services/) 页面看到一个 Rancher 的主机被启动了。
