![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/9QTd6a2037.jpg)

`jenkins`是一个非常老牌的`ci/cd`工具，它是一款使用`Java`写的开源自动化应用。可以通过界面或`Jenkinsfile`告诉它执行什么任务，何时执行，理论上，可以让它执行任何事，一般用来做`ci/cd`（开发只用关心代码实现，提交代码以后自动测试、打包、自动发布）可以说体量稍微大一点的团队都有自己的持续集成工具。

### 安装

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/fvBX1H2037.png)

我使用的是`docker`安装测试,其中`~/Documents/code/jenkins/`这个目录需要替换成你自己的，因为把目录挂载了出来，所以即使容器销毁也不会导致数据丢失。

```BASH
mkdir jenkins-data
docker run \
  -u root \
  --name jenkins \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  -v ~/Documents/code/jenkins/jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkinsci/blueocean
```

安装方法非常简单，其他安装方法以及安装完怎么配置见[官网文档](https://www.jenkins.io/zh/doc/book/installing/), 因为官方网站速度比较慢，可以先不安装插件后期改完镜像源再安装。

### 更新镜像源

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/uKQIlx2038.png)

进入 `Manage Jenkins > Manage Plugins > Advanced`，在这里可以手动上传插件包，也可以更新其他镜像源，然后<kbd>Submit</kbd>，再点击右下角<kbd>Check now</kbd>

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/wNzslS1537.png)

附：清华大学镜像源
https://mirror.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json

PS：我用了镜像源还是卡慢，网上找遍了也没找到好的办法，最后还是翻出去下的。

### 安装插件

还是在此页面，仅安装`pipeline`插件，这个插件就是构建用的核心插件，`jenkins`会自动解决安装插件时的依赖问题，安装完重启`jenkins`

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/pE1ju91637.png)

### 创建项目

1、 左上角 <kbd>New item</kbd> 按钮
2、 输入项目名，选择流水线，提交

![流水线](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/a8dSU31816.png)

3、直接拉到下面，填入以下内容然后保存

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/IjQn0G1817.png)

```Groovy
pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'hello world!'
            }
        }
    }
}
```

代码解释：

- `jenkins`使用的是`Groovy`这种编程语言，常用的是声明式语法
- 上面代码中`pipeline`实际上是一个函数，只是省略了小括号`pipeline({})`,中间是传入参数，大括号包着的是一个匿名的函数（闭包），这个函数里面的内容就是函数体，又调用了`agent`函数和`stages`函数
- `stages`函数传入的是`stage`函数列表表示不同的构建阶段，此处只有`build`阶段
- `steps`又表示不同的步骤

4、在项目详情页面立即构建

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/5VWFG51820.png)

5、可以点击`#1`查看刚刚的构建

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/fmekqc1821.png)

6、点这里可以看到输出历史

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/X1jnJH1822.png)

### 界面重点功能介绍

![](https://coding3min.oss-accelerate.aliyuncs.com/2020/06/28/5TMjMY2153.png)

### 总结

- [官网文档安装 jenkins](https://www.jenkins.io/zh/doc/book/installing/)
- 安装插件位置 `Manage Jenkins > Manage Plugins`
- 初始安装`pipeline`插件即可
- 整个构建流程：获取源代码(凭据、github 等接入源、用户权限、绑定触发动作)-根据`pipeline`描述步骤开始测试、构建、发布以及构建成功与否的通知

最后尽量还是自己动动手试一下，才能更好的学会这个东西。

### 引用

- 官方文档 [创建您的第一个 Pipeline](https://www.jenkins.io/zh/doc/pipeline/tour/hello-world/)
- [泽阳的 jenkins 实战](http://www.idevops.site/jenkins/)
