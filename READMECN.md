Docker发布新的跨容器的分布式应用编排服务
2014-12-06 Container技术日报

在刚刚结束的欧洲DockerCon，Docker发布了跨容器的分布式应用编排服务，编排服务可以帮助开发者和运维人员创建并管理新一代的可移植的分布式应用程序，新一代的分布式应用程序是由独立且互通的Docker容器快速组合而成，他们有动态的生命周期，并且可以在任何地方以可扩展的方式运行，不管是在开发者的笔记本上，还是在云端。

“一开始用户在几台主机上运行少量的Docker容器，但是现在他们已经在集群和不同的基础设施中运行了大量的Docker容器，我们需要满足用户的需求，这非常重要”。Docker的创始人兼CTO Solomon Hykes说道。“编排服务开放了原生的接口，可以保证应用的可移植性，并通过一个通用的UI整合了生态圈中的18000个工具和60000个容器化的应用。”

Docker编排服务已经得到了很多合作伙伴的支持，包括Cisco、Digital Ocean、HP、IBM、Mesosphere、Microsoft和VMware。

Docker平台加强了跨容器的分布式应用能力

Docker编排功能在开放平台的基础上构建，开放平台能够创建企业级标准的Docker容器：将分散的应用服务打包到可交互、可迭代、可随处运行的容器中。Docker编排服务可以满足企业从整体式的应用转移到容器化的分布式应用的需求，因为编排这些分布式应用需要多个容器、多个主机以及可以在这些设施中运行的工具和通用UI。

编排服务为应用的开发和运维提供了一种新的方式

Docker的编排功能由3个新的平台服务组成，它们覆盖了分布式应用的所有动态生命周期，当新的代码或者新的容器化服务改变时，应用可以在几分钟内部署到生产环境，而不是像之前一样需要几个月。Docker的编排服务是目前市场上功能最全面的服务，它们独特的模块化结构决定了其可以被不同的人员使用，包括开发者、运维人员以及其它合作伙伴。比如它其中就有一项服务可以帮助开发人员方便地创建分布式的应用程序栈，而另外一个服务可以重点处理集群以及运维团队的问题。

这三个新的编排服务分别是：

Docker Machine：这项服务进一步扩展了分布式应用的可移植能力，它为用户提供了灵活的功能，用户可以在任何主机上运行Docker容器，不管是笔记本、数据中心VM还是云端。这大幅度减少了开发者在手动设置、自定义脚本的时间，可以加快迭代和研发周期。

具体来说，Docker Machine是一个简化Docker安装的命令行工具，通过一个简单的命令行即可在相应的平台上安装Docker，比如VirtualBox、 Digital Ocean、Microsoft Azure。Docker官方是这样介绍Machine的初衷的。

Machine做事也很聪明，很符合Docker公司的做事风格，他们号称自己架构很好，方便第三方集成。所以Machine现在只支持有限的几个平台（VirtualBox、 Digital Ocean、Microsoft Azure），其它平台的兼容留给那些爱Docker的第三方厂商以及开发者去做吧。所以接下来一定会有很多的厂商跟进，比如国内阿里云之类的，他们根据官方的接口开发个Driver即可加入Machine的能力。

需要注意的是Machine是完全独立于Docker项目的，目前的主要维护者是也是一位叫Ben的人，当然还是使用Go语言。GitHub地址：https://github.com/docker/machine

Docker Swarm：Docker Swarm是一个支持Docker容器（由Docker Machine提供）的原生的集群服务，它在分布式的应用运行的主机提供了一个资源池。相比于手动管理资源的低效率以及易出错的问题，Docker Swarm可以自动平衡容器工作负载和分配资源，它更加高效。在行业中，Docker Swarm是独一无二的，它是专门为从开发到运维的一个持续的生命周期而设计的。开发者可以在生产环境的几台机器上测试集群服务，同时运维团队可以使用相同的工具在不同的架构中的上百台主机上扩展相同的应用程序。Docker Swarm API支持插件化的集群实现，以便客户选择其它的高可扩展的解决方案，比如Mesosphere需要管理上千个节点的容器。

Docker Swarm是一个Docker集群的控制工具，而对外部来说它就像一个虚拟的单主机。Swarm使用了标准的Docker API，所以Docker生态中的任何工具，比如Docker client、dokku、fig、krane、flynn、deis、docker-ui、shipyard、drone.io、Jenkins等，都能和Swarm对话。GitHub地址：https://github.com/docker/swarm/

Docker Compose：这项服务为开发者提供了应用组合的能力，这些应用基于独立于任何底层基础设施的分散的、可交互的Docker容器之上构建，以便于分布式的应用栈可以随时随地部署并迁移。Docker Compose通过一个简单的YAML配置文件来定义分布式的应用程序栈以及依赖，这样一个复杂的过程通过几次键盘输入就可以完成。这个强大的功能也就意味着一个新的集群应用可以在几分钟之内构建完成，而这在之前是不可思议的。GitHub上的说明：https://github.com/docker/docker/issues/9459

原文链接：http://dockerone.com/article/26
http://dockerone.com/article/27
