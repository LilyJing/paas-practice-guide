# 为什么要写本书

1983年，SUN公司提出了Network is Computing的概念。 2006年3月，亚马逊推出弹性计算云服务EC2。 2006年8月9日，Google首席执行官埃里克施密特在搜索引擎大会首次提出“云计算”（Cloud Computing）的概念。云计算这个热词很快火遍了全球各个商业领域，并极大的改变了IT从业者的生存现状。

从本质上讲，**云计算实现了分工，并通过分工提升了社会效率**。就如同发电的功能从工厂中分离出来独立成为发电厂，从而提高了能源利用效率一样。很多行业从自己拥有IT基础设施变成了“租用”其他企业提供的IT基础设施，这样自己可以专注于自己的商业逻辑，降低IT的投资成本；而提供IT基础设施的企业则可能形成规模优势，从而提供更多质优价廉的服务。

通过云计算提供IT服务的形式，业界主要分为IaaS、PaaS和SaaS三种：

* **IaaS**。Infrastructure as a Service 基础设施即服务。面向**系统管理员**提供计算、存储和网络的基础设施。
* **PaaS**。Planfrom as a Service 平台即服务。面向**应用开发者**提供软件平台。
* **SaaS**。Software as a Service 软件即服务。面向**使用者**提供应用本身。

亚马逊AWS的云服务是IaaS的典型代表，Salesforce之前提供的云服务是SaaS的典型代表，这两者在商业上都被证明是成功的，从他们股价的涨幅上就可以看出来。只有PaaS这个被寄予厚望的商业模式却不愠不火，甚至有很多的论调说PaaS已经事实上被证明不存在商业价值。GAE（Google APP Engine）是最早的PaaS代表作，即使以Google的技术领导力也没有让PaaS模式得到广泛的接受。分析其原因，大概是在于提供的便利性不够、对应用开发者有额外要求等。

在GAE之后，还出现了一个明星的PaaS公司Heroku，他本身将基础设施构建在亚马逊AWS之上，为其他应用开发者提供应用托管的服务。因为他提出了Buildpack的方法，并和Git代码库结合，极大提升了应用开发者的生产率。Herorku公司提出了“12因子”的PaaS应用软件开发指导原则，成为后来Cloud Native的重要参考依据，这个公司后来被Salesforce收购，也算有一个很好的结果。

在私有PaaS方面，必须说一下CloudFoundry，Pivotal公司（当时还是EMC公司的一个部门）受到Herorku的启发，希望开发一个私有云的Herorku版本，2011年开始封闭开发，一年后开源。CloudFoundry中采取了很多先进的架构设计，并参考了Herorku的Buildpack。正式推出以后取得了很大的成功，其开源的模式更是受到业界的喜欢，IBM推出的公有云PaaS服务Bluemix就是采用了CloudFoundry。

即使有那么多优秀的公司在其中，到2014年PaaS没有成为主流的云服务，因为他很难提供开发和运行的一致环境；难以调试；对开发人员的语言和工具有限制；并没有给应用开发者带来足够的便利。这一切直到Docker的出现！

Docker将进程封装在容器中进行交付，实现Build、Ship和run。从此大家的进程不是“裸奔”在操作系统中，而是穿上了容器的外衣，通过这层外衣屏蔽了不同操作系统版本、不同的库文件和外部依赖。Docker的出现解决了传统PaaS的问题，而且减轻了PaaS需要承担的任务。于是从私有云开始，PaaS逐渐成为提高内部IT开发效率的重要形式。通过PaaS可以有效支持微服务、持续集成（CI）和DevOps。

以Docker为核心的公有云PaaS服务也被推出，Google和AWS都尝试提供这类PaaS服务。以Docker为核心的PaaS开源软件也火了起来，CloudFoundry的新版本diego可以支持Docker容器的运行，kubernetes作为Google在容器上最佳实践的被推出，mesos通过marathon提供了对docker容器编排的支持，Docker自己也通过Swarm开始支持一部分PaaS的能力。

如果现在我们开发一个应用的时候，还需要开发人员与操作系统直接打交道，处理不同的编译环境、库文件、外部组件依赖；开发人员提交结果给测试人员的时候交付的是代码和部署说明，需要手工部署和测试；测试人员完成测试后提交给运维人员是代码和部署说明，需要运维人员按照说明进行手工部署并上线的话，那么这个公司的IT工程效率一定不高，大家做了很多低水平的重复劳动。这样的公司难以实现数千个微服务的持续部署，一行代码的修改需要非常长的时间才能反应到生产系统之上。

PaaS极大提高了开发和运维的效率，解放了IT从业者的生产力，使得每个人的贡献变多了，这不但使得公司容易成功，也使得个人更加富有竞争力。因此如何今天您所在的公司还没有自己的PaaS平台的话，可能你需要选择立即去构建或者离开这样的公司。

对于当下的中国来说，云计算有重要的意义。因为互联网巨头垄断的加剧和用工成本的升高，使得创新创业困难重重。云计算正是这样一个手段，通过分工合作来优化效率，让创业公司可以享受媲美大公司的资源和服务，而且是按需付费的模式。

因此我们希望更多的人了解和掌握云计算的技术，能充分利用它来将世界变得更美好，这也是我们写作此书的缘由。

在这本书中，我们介绍了PaaS的相关概念、核心功能、技术框架选型、环境搭建和运营。期望将PaaS的最佳实践带给更多的企业。

# 本书适应哪些读者

本书的读者为企业IT从业人员，包括CTO、IT主管、平台管理人员和应用开发人员。

# 本书的内容结构

**第一部分：PaaS的前世今生**

主要介绍PaaS的由来、PaaS的意义、PaaS的现状、PaaS的功能框架。另外单独介绍Docker对PaaS带来的革命性变化。

**第1章：云计算概述**

人口红利的消失，带宽红利的到来

**第2章：PaaS的历史**

**第3章：Docker对PaaS的意义**

**第4章：PaaS的关键能力分析**

**第二部分：主流开源PaaS技术框架**

分别介绍CloudFoundry、Kubernetes、Mesos+Maranthon、Swarm其他开源PaaS框架的历史和技术特点，并对照PaaS功能框架描述其优缺点。

**第5章：功能最全的PaaS框架—CloudFoundry**

**第6章：从资源管理扩展的PaaS框架—Mesos&Maranthon**

**第7章：Google出品的PaaS框架—Kubernetes**

**第8章：Docker官方的PaaS框架—Swarm**

**第9章：其他开源PaaS框架**

**第三部分：PaaS的能力倍增器**

介绍CI CD 敏捷开发 DevOps与PaaS的关系。讨论微服务架构和PaaS的关系。

**第10章：PaaS与持续集成和持续交付**

**第11章：PaaS与DevOps**

**第12章：PaaS与微服务**

**第四部分：企业级PaaS平台案例**

介绍如果利用开源框架和软件，搭建一个企业级PaaS平台。

**第13章：企业级PaaS平台的业务需求**

**第14章：框架选择和搭建**

**第15章：基础功能的实现**

后端服务、持久化、监控服务、日志服务、运维服务

**第16章：PaaS对应用开发的要求**

12因子

**第17章：效果和收益**

# 感谢

## 

