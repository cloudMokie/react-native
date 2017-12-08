## 本文主要为那些react-native新手写的项目教程搭建，希望帮助更多的新手入门和跳出不必跳入的深坑，请大家谅解。代码仅供参考。

## react-native项目 简介

This is based on the react-native implementation of the cnblogs.com's mobile client for both android and ios. if you have any comments or suggestions, welcome feedback.

基于 react-native 实现不用懂原生就可以写app的梦想，兼容android和ios。如果您有任何问题或者建议，欢迎留言反馈，作者会第一时间进行回复，谢谢！

## 创建react-native项目 截图
#### 命令行：react-native init project-name
只要全局安装react-native-cli脚手架，一般都没什么问题


## 构建android项目包，生成开发apk
#### 命令行：react-native run-android
#####常见问题:
https://github.com/18871401911/learn_img/tree/master/react-native/img/run_android_error.png
遇到此图这样的问题，不要慌，其实这并不是构建失败，只是没有找到android模拟器，你只要启动你安装的模拟器就行了，推荐用genymotion模拟器http://www.genymotion.net/
####安装好启动模拟器，你重新运行一遍，得到如图所示:
![home page ](https://github.com/18871401911/learn_img/tree/master/react-native/img/run_android_success.png)
![home page ](https://github.com/18871401911/learn_img/tree/master/react-native/img/android_sreen_success.png)
