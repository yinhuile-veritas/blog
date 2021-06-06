---
title: "快速了解 2020 Gopher Meetup 深圳站"
date: 2020-10-18T01:03:25+08:00
toc: true
images:
tags: 
  - meetup
---

昨天（20201017）很有幸的参加了 GoCN 的 2020 Gopher Meetup 深圳站，在台下听各位大佬分享各自的知识和案例。恰好也是我第一次参加这类 Meetup。因此希望也能够让没来的小伙伴对本次分享内容有一定的了解。

按过往对其观察的惯例，一般在下周后官方就会陆续释出 Meetup PPT 和推文，在此引个主线。

![会场外的展板，图来自 GoCN](https://image.eddycjy.com/08910eccd6b1b0c16c0f60571cd7745a.jpeg)

本次 Meetup 主要的方向是云原生，包含四位讲师分享，分享的主题如下：

1. 华为云的 go 语言云原生实践。
2. go 云上微服务模式解构。
3. 服务网格在边缘计算领域的实践与探索。
4. 腾讯大规模 etcd 集群治理与优化实践。

## 华为云的 go 语言云原生实践

讲述华为云在早起使用 Go 语言时，当时 Go 语言的整体生态圈还比较薄弱，因此很多第三方基础/工具库并不全：

![](https://image.eddycjy.com/4adaf1b0b465a3197a9ba9d714dda51d.jpeg)

围绕此整体做一系列的东西，主要从统一框架开始做，提供各种插件，组件，基本涵盖了常用的所有组件。其所带来的的价值/效益：能够直接提高研发效能，让其他业务能够简单使用，不需要太重复造轮子：

![](https://image.eddycjy.com/8c0afff2cb0bb6d2901d1e4d7f8296f2.jpeg)

再往后就介绍了其使用了 Mesh 去做整块的流量标识，金丝雀等流量控制方案。同时还支持了市面上常见的框架和协议。是一个比较完整很常见的整体解决方案，有真实的参考意义。

若在企业内部有建设过这类基础应用可能会感触比较深，且各家多多少少都有类似的东西，需要必需品。社区的小伙伴可以多看看，结合自己的实际情况进行选型或融合。

同时该类基础规范，最难的可能还是如何在企业内部达到大一统，做推广，拿规范，遵守则。

## go 云上微服务模式解构

详细介绍了云原生的定义，主体讲解了 k8s 的基本网络模型，核心在于传统微服务模式和云原生模式下的各类优缺点和对比。

### Edge Proxy

![](https://image.eddycjy.com/0275954e8196ac7c687a1c58e1b4be23.jpeg)

### ServiceMesh

![](https://image.eddycjy.com/794182e59306fec93128765f1854a353.jpeg)

需要听讲者有一定的基础，整体语速相当快，口述内容也比较多，因此这块没有过多详细记述。

演讲内容主体对应云原生下的几种部署模式，线上的话在网上查阅资料学习即可，可能会更高效些。

印象比较深的是，讲师表述目前也没用 ServiceMesh，四年前也预演过，但问题不少，近期打算重新启动。这块我司也多次尝试，多多少少都有些问题，期待 Istio 更稳定成熟的一天。

## 服务网格在边缘计算领域的实践与探索

主体介绍边缘计算相关的 KubeEdge、IEF 等技术体系：

![](https://image.eddycjy.com/ddab54efbf97b478c4ea06c8a602dcef.jpeg)

这块不是我的技术领域内，隔壁的小哥也没听懂，稍微有些乱，因此不过多的介绍。

但发现讲师刚毕业一年多，年轻有为，潜力无限。

## 腾讯大规模 etcd 集群治理与优化实践

腾讯云近期推出了 etcd 的云服务，先前关注了一番。恰好这次的分享者就是相关人士。

分享内容主要分为两个部分：

1. etcd 本身的基本知识

2. etcd 云服务的介绍

### etcd 知识

第一部分是 etcd 的基本知识，以及抽出 kubectl 查询作为案例进行逻辑分析：

![](https://image.eddycjy.com/515c7ea827f0d19b0cedab48897ddc62.jpeg)

再更一步介绍了 etcd 读请求分析，软件分层，以及一些内部逻辑，流转模型等：

![](https://image.eddycjy.com/fe56478c26fcbcf2b7441e27156f125b.jpeg)

若有兴趣的小伙伴可以结合 PPT 再去追一遍源码，会比较的有意思。

因为其讲述的具体的操作模式涉及了 etcd 里的基本理念，大部分情形下都会展开讨论。

### etcd 云服务

第二部分是讲解腾讯云自身在做 etcd 云服务时，遇到的一些 etcd 自身的 BUG，利用了 Chaos 来制造混沌，以此来更好的发现问题。并在后半部分讲述了 etcd 云服务的大体设计和内部模块结构：

![](https://image.eddycjy.com/f864e44559ea61f3a666ce676bf2d5f3.jpeg)

后半部分感觉比较贴近产品介绍，因为每个模块都能单独拿出来再做一次分享，有限的时间能也很难讲深。

印象最深的还是 “为什么 kubernetes 会选型 etcd？”，讲师给出的答案是：Watch 机制、高可用、商业原因。

各位可以细品一下。

## 总结

整体来讲，个人感觉本次 Meetup 以技术的半解决方案和理念介绍居多。

一个技术的实际应用，普遍分三部分来看：

1. 在价值上：为什么要这么做，做了对公司，对团队，对个人的利弊，外部/内部价值是什么。

2. 在技术上：技术攻坚，这个大家接触的多。

3. 在推广上：，如何规范，推广，是行政命令，还是深抓用户痛点，怎么落的地，是非常重要的。

技术类 Meetup 一般以技术角度居多，因此在与会前，建议提前了解一些基本知识才能在会议上更好的听懂、发散以及思考，否则很难碰撞出火花出来。

但问题又来了，如果已经有了基本知识，肯定会做知识拓展，因此直接网上查阅资料和与业界朋友沟通能达到更佳的目的，更高的时间效率比。因此这是一个矛盾和定位。

其实每一次 Meetup 的背后，组织方和分享讲师其实都会付出大量的精力，都不容易。

抛出一个问题，**如果你是讲师，你怎么在 40-60 分钟内把一份 PPT 讲好？把知识/价值传达到位？**