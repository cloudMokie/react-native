## 本文主要为那些react-native新手写的项目教程搭建，希望帮助更多的新手入门和跳出不必跳入的深坑代。

## react-native项目 简介

This is based on the react-native implementation of the cnblogs.com's mobile client for both android and ios. if you have any comments or suggestions, welcome feedback.

基于 react-native 实现不用懂原生就可以写app的梦想，兼容android和ios。如果您有任何问题或者建议，欢迎留言反馈，作者会第一时间进行回复，谢谢！

##首先就是搭建react-native的环境:
* node包
* javaJDK包
* Genymotion安卓模拟器包
* python包
* android Studio包
****等等包
需要以上包的：
不用再为翻墙而苦恼，
不在需要百度，
不在为下的版本不对导致一堆坑而烦恼，
只需要勾勾你的小拇指，
点上一颗星，带你上直通车，
啥配置问题，各种报错，都是浮云，
#车牌号：164527929@qq.com，
上车我帮你，
不用在烦恼，不用再犹豫，快上直通车。



## 创建react-native项目 截图
#### 命令行：react-native init project-name
只要全局安装react-native-cli脚手架，一般都没什么问题


## 构建android项目包，生成本地开发apk(依赖本地环境apk)
#### 命令行：react-native run-android
##### 常见问题:
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/run_android_error.png)
遇到此图这样的问题，不要慌，其实这并不是构建失败，只是没有找到android模拟器，你只要启动你安装的模拟器就行了，推荐用genymotion模拟器http://www.genymotion.net/
#### 安装好启动模拟器，你重新运行一遍，得到如图所示:
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/run_android_success.png)
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_sreen_success.png)


## 如何打包发布apk(不依赖本地环境apk)
* 首先，我们要配置数字签名才会被允许安装在用户手机上,你可以用keytool命令生成一个私有密钥
* 切到项目根目录后，输入以下命令
#### 命令行：keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
有些人就会疑问这行命令行是什么意思，下面我就详细分解下：
* keytool 命令是javaJDK工具，用于生成android的数字签名,所以很明显在此之前你必须要安装javaJDK。
* -keystore 命令设置数字签名文件名，后面的配置要用到，所以不要玩骚操作，规矩命名。
* -alias 命令设置KEY_ALIAS的名称，后面的配置也要用到，还是不要玩蛇，规矩命名。
* -validity 设置数字签名过期时间，这个你随便骚，尽可能设置长点
* 其他都不需要研究，了解这几个是干啥的就行了

#### 此时你会进入一个一脸懵逼的命令行,不要方，我们有神图，请看下图:
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_key.png)

### 如果你还是不懂，那只能再补一刀，请看下图：
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_now_key.png)

### 如果还有问题，那只能把你的问题发送到我的邮箱，温馨提示：除了在送祖传染色体时，其他时间都可以随便骚扰。

当然，以上操作后，会生成一个数字签名文件，如下图所示：
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_key_file.png)

把数字签名文件my-release-key.keystore放到android/app目录下,接下来就开始搞事情了

### 编辑android目录下的gradle.properties文件,添加如下：
* MYAPP_RELEASE_STORE_FILE=my-release-key.keystore（如果忘记该字段表示什么意思，参考上文不要玩蛇内容）
* MYAPP_RELEASE_KEY_ALIAS=my-key-alias（如果忘记该字段表示什么意思，参考上文不要玩蛇内容）
* MYAPP_RELEASE_STORE_PASSWORD=*** (数字签名的设置的密码)
* MYAPP_RELEASE_KEY_PASSWORD=*** (数字签名的设置的密码)
还有所不明，请参考下图：
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_gradle_set.png)

### 配置好上述文件后，我们再编辑android/app下的build.gradle文件（注意不要弄错了，android目录下也有一个这样的文件）
添加配置如下
* signingConfigs {
    release {
        storeFile file(MYAPP_RELEASE_STORE_FILE)
        storePassword MYAPP_RELEASE_STORE_PASSWORD
        keyAlias MYAPP_RELEASE_KEY_ALIAS
        keyPassword MYAPP_RELEASE_KEY_PASSWORD
    }
}
* signingConfig signingConfigs.release
不知代码放何处，请看下图：
![点击查看](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_build_gradle.png)

## 以上操作完后，差不多就是传说中的九九八十一难的最后一难，打开命令行,切到android目录下，然后发功：
### 命令行输入：./gradlew assembleRelease
此难有一小难：cd android表示进入android目录（如果你已经在android目录中了那就不用输入了）。./gradlew assembleRelease在macOS、Linux或是windows的PowerShell环境中表示执行当前目录下的名为gradlew的脚本文件，且其运行参数为assembleRelease，注意这个./不可省略；而在windows的传统CMD命令行下则需要去掉./。

Gradle的assembleRelease参数会把所有用到的JavaScript代码都打包到一起，然后内置到APK包中。如果你想调整下这个行为（比如js代码以及静态资源打包的默认文件名或是目录结构等），可以看看android/app/build.gradle文件，然后琢磨下应该怎么修改以满足你的需求。

生成的APK文件位于android/app/build/outputs/apk/app-release.apk，它已经可以用来发布了

### 总算大功告成，骚年们可以拿起你们的手机骚动起来了
