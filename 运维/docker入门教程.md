# 什么是Docker? #

Docker是一个开源的引擎，可以轻松的为任何应用创建一个轻量级的、可移植的、自给自足的容器。开发者在笔记本上编译测试通过的容器可以批量地在生产环境中部署，包括VMs（虚拟机）、 bare metal、OpenStack 集群和其他的基础应用平台。 

Docker通常用于如下场景：
web应用的自动化打包和发布；
自动化测试和持续集成、发布；
在服务型环境中部署和调整数据库或其他的后台应用；
从头编译或者扩展现有的OpenShift或Cloud Foundry平台来搭建自己的PaaS环境。

# 关于docker入门教程 #
docker入门教程翻译自docker官方网站的Docker getting started 教程，官方网站： https://docs.docker.com/linux/started/

官方网站是一个交互的教程，在左侧是相应的说明，右侧是一个交互的终端，输入预期的目录，可以跳到下一步，大家可以参考我们的翻译，在官网上面运行相应的命令，以验证效果。


译者按：之前的交互教程在新版本的docker官网上已无法找到，但核心的概念流程没有变，仍然可以参考。(2015/9/16)

# 准备开始 #
Docker系统有两个程序：docker服务端和docker客户端。其中docker服务端是一个服务进程，管理着所有的容器。docker客户端则扮演着docker服务端的远程控制器，可以用来控制docker的服务端进程。大部分情况下，docker服务端和客户端运行在一台机器上。

目标：
检查docker的版本，这样可以用来确认docker服务在运行并可通过客户端链接。

提示：
可以通过在终端输入docker命令来查看所有的参数。

官网的在线模拟器只提供了有限的命令，无法保证所有的命令可以正确执行。

正确的命令：
$ docker version 

