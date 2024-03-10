

# 分布式网络通信RPC框架



<!-- PROJECT SHIELDS -->


<!-- PROJECT LOGO -->
<br />





 
## 目录

- [上手指南](#上手指南)
  - [开发前的配置要求](#开发前的配置要求)
  - [运行步骤](#运行步骤)
- [项目介绍](#项目介绍)
- [作者](#作者)

### 上手指南
通过autobulid.sh一键编译脚本生成静态库，通过引入相应头文件并链接静态库即可使用RPC框架，example文件夹是RPC提供者和使用者示例代码，根据业务自定义protobuf通信协议， 并实现相应接口即可快速使用




###### 开发前的配置要求

1. 下载protobuf
2. 下载zookeeper

###### **运行步骤**

```sh
./autobulid.sh
```

### 项目介绍
这个项目就是实现了一个分布式网络通信框架RPC远程调用，网络方面是用的GitHub上面开源的muduo网络库，
一方面是因为这个网络库的性能比较高效，并且可以很好的解耦网络模块和业务模块，另一方面是因为以前通过
看书然后也看过这个网络库的部分源码，自己写过网络模块方面的代码，就没有重复造轮子了，
序列化和反序列化这方面主要是用protobuf，用protobuf主要是因为它不仅提供了序列化的功能而且还可以提供RPC
服务方法的抽象类，就是提供一个接口，可以很方便的描述RPC方法，这样注册RPC方法和使用RPC方法就很方便，
通过使用zookeeper实现了服务注册中心，解耦了RPC服务提供方和使用方，zookeeper根节点下的node节点名字
就是一个服务类的名字，里面的数据就是这个类所在服务器的ip和端口，然后这个node节点下的子节点保存就是这个
类提供的方法，比如说注册或者登录这样的不同的业务功能，rpc使用方先访问zookeeper拿到提供者的ip,端口就可以
使用远程调用了。

### 作者
wwwp12334
qq:2232852166@qq.com
