## 本文主要为那些react-native新手写的项目教程搭建，希望帮助更多的新手入门和跳出不必跳入的深坑，请大家谅解。代码仅供参考。

## react-native项目 简介

This is based on the react-native implementation of the cnblogs.com's mobile client for both android and ios. if you have any comments or suggestions, welcome feedback.

基于 react-native 实现不用懂原生就可以写app的梦想，兼容android和ios。如果您有任何问题或者建议，欢迎留言反馈，作者会第一时间进行回复，谢谢！

## 创建react-native项目 截图
### 命令行：react-native init project-name

![home page ](https://github.com/togayther/react-native-cnblogs/raw/master/screenshot/1.png)


## download 下载
### android
#### download link: 
http://fir.im/togayther


### ios
#### appstore link:
https://itunes.apple.com/cn/app/bo-ke-yuan-she-qu/id1176047767?l=zh&ls=1&mt=8

## how to run 本地运行
note: if you behind GFW, strongly recommend that you work with vpn.

提示：如果你处于全球最大的局域网，强烈建议你购买一个vpn。

* config your react-native environment: https://facebook.github.io/react-native/docs/getting-started.html
* git clone https://github.com/togayther/react-native-cnblogs.git
* npm install
* react-native link
* connect physical device or turn on the emulator
* react-native run-android/run-ios
* good luck and enjoy

注意：
因为本软件涉及到基于oauth的登录授权，故本地运行还需要向博客园申请 clientId、clientSecret、rsa加密公钥等授权信息。否则运行后无法登录进入首页。

应博客园官方团队要求，该软件开源时未公开已取得的授权信息。非常抱歉。

授权信息申请方式：

对于个人开发者，需要提供以下信息：
真实姓名、手机号码、常用邮箱、相关app介绍。
然后邮件发送至： contact@cnblogs.com

授权信息配置文件：source/config/index.js => authData

## License 授权协议
This project is available under the MIT license.