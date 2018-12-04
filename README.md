# 简介

在讨论docker与k8s之前，先了解一下CNCF

#### CNCF\(Cloud Native Computing Foundation\):

背景：

* 早在 2006 年 8 月 9 日，google公司董事长埃里克·施密特（EricSchmidt）在搜索引擎大会上首次提出了“云计算”（Cloud Computing）的概念。一转眼十年过去了，它的发展势如破竹，不断渗透当代的 IT 市场。

* 云计算被视为继 80 年代大型计算机到客户端-服务器的大转变之后的又一次革命，为我们带来了工作方式和商业模式的根本性变，进而成为推动企业创新的引擎。2013年，Pivotal 的 MattStine 提出了云原生（Cloud Native）的概念，凭借其优良的可伸缩性，云原生应用和服务也越来越受到青睐。

* 为了统一云计算接口和相关标准，2015 年 7 月隶属于 Linux 基金会的云原生计算基金会（CNCF）应运而生。谈到 CNCF，首先它是一个非营利组织，致力于通过技术优势和用户价值创造一套新的通用容器技术，推动本土云计算和服务的发展。CNCF 关注于容器如何管理而不是如何创建，因为如果没有一个成熟的平台去管理容器，那么大型企业无法真正放心接受并使用容器。

                 ![](/assets/CNCF.jpg)

CNCF 已经吸收了一系列终端用户与支持者企业:

![](/assets/Members-CNCF.jpg)

* 其中不仅包括 Google、IBM、Intel、Docker 和 Red Hat 等知名公司，也包括 DaoCloud 等后起之秀。CNCF 的成员代表了容器、云计算技术、IT 服务和终端用户，共同营造全球云原生生态系统，维护和集成开源技术，支持容器化编排的微服务架构应用，携手推动现代化企业架构的进程。

### docker

[Docker](http://www.docker.com/) 是个划时代的开源项目，它彻底释放了计算虚拟化的威力，极大提高了应用的维护效率，降低了云计算应用开发的成本！使用 Docker，可以让应用的部署、测试和分发都变得前所未有的高效和轻松！

无论是应用开发者、运维人员、还是其他信息技术从业人员，都有必要认识和掌握 Docker，节约有限的生命。

本书既适用于具备基础 Linux 知识的 Docker 初学者，也希望可供理解原理和实现的高级用户参考。同时，书中给出的实践案例，可供在进行实际部署时借鉴。供用户理解 Docker 的基本概念和操作、数据管理、网络等高级操作、容器生态中的几个核心项目；最后，还展示了使用容器技术的典型的应用场景和实践案例。

### kubernetes \(k8s\)

[Kubernetes](https://kubernetes.io/) 是容器集群管理系统，是一个开源的平台，可以实现容器集群的自动化部署、自动扩缩容、维护等功能。

Kubernetes是Google 2014年创建管理的，是Google 10多年大规模容器管理技术Borg的开源版本。

我们的目标是促进完善组件和工具的生态系统，以减轻应用程序在公有云或私有云中运行的负担。

通过Kubernetes你可以：

* 快速部署应用
* 快速扩展应用
* 无缝对接新的应用功能
* 节省资源，优化硬件资源的使用

Kubernetes 特点

* **可移植：**
  支持公有云，私有云，混合云，多重云（multi-cloud）
* **可扩展：**
  模块化, 插件化, 可挂载, 可组合
* **自动化：** 
  自动部署，自动重启，自动复制，自动伸缩/扩展



