---
title: 'Learn once, write anywhere: React Native'
date: 2019-12-07 22:34:18
tags:
- React Native
---

[reactnative getting-started]: https://reactnative.cn/docs/getting-started.html
[Scoop: Switching Ruby and Python Versions]: https://github.com/lukesampson/scoop/wiki/Switching-Ruby-And-Python-Versions
[development-environment-manual: javascript]: https://github.com/FloatingShuYin/development-environment-manual/blob/master/javascript.md#%E5%AE%89%E8%A3%85-node-%E7%89%88%E6%9C%AC%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-nvmnode-version-management
[development-environment-manual: java]: https://github.com/FloatingShuYin/development-environment-manual/blob/master/java.md#%E5%AE%89%E8%A3%85-jdk
[react]: https://github.com/facebook/react
[react-native]: https://github.com/facebook/react-native
[reactnative running-on-device]: https://reactnative.cn/docs/running-on-device/
[yarn]: https://github.com/yarnpkg/yarn
[react-native-cli]: https://www.npmjs.com/package/react-native-cli

## 参考

- [reactnative getting-started][]
- [reactnative running-on-device][]
- [Scoop: Switching Ruby and Python Versions][]
- [development-environment-manual: javascript][]
- [development-environment-manual: java][]

## 资源
- [react][]
- [react-native][]
- [yarn][]
- [react-native-cli][]


## 搭建开发环境

### 前提条件
如果不需要使用模拟器而是物理机开发就不必了

- 打开 Intel Virtualization Technology
- 关闭 Hyper-v

### 步骤
1. 安装 node
- [development-environment-manual: javascript][]
2. 安装 python
- [Scoop: Switching Ruby and Python Versions][]
3. 安装 jdk
- [development-environment-manual: java][]
4. 安装 Android Studio
```powershell
scoop install android-studio
```
5. 安装 Android SDK
- [reactnative getting-started.html#2-安装-android-sdk]: https://reactnative.cn/docs/getting-started.html#2-%E5%AE%89%E8%A3%85-android-sdk
6. 添加环境变量
  按快捷键 `win + x + a` 以管理员权限打开 powershell， 执行以下命令：
  ```powershell
  $env:ANDROID_HOME="$env:LOCALAPPDATA\Android\Sdk"
  $env:PATH="$env:PATH;$env:ANDROID_HOME\platform-tools"
  [Environment]::SetEnvironmentVariable("ANDROID_HOME", "$env:ANDROID_HOME", "Machine")
  [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
  ```
7. 安装 [yarn][] 和 [react-native-cli][]
```powershell
npm install -g yarn react-native-cli
```

## 在物理机上运行
- [reactnative running-on-device][]

## hello world
1. 创建 `react.native.workspace` 工作目录
```powershell
mkdir -p react.native.workspace/day0
cd react.native.workspace/day0
```
2. 使用  [react-native-cli][] 来创建一个名为`helloworld`的新项目
```powershell
react-native init helloworld
```
3. 链接安卓手机
- [reactnative running-on-device][]

4. 运行
usb 链接物理机 然后编译安装软件包
```powershell
cd helloWorld
yarn android
```
如果出现 `Failed to install the following Android SDK packages as some licences have not been accepted` 错误
则执行
```powershell
Invoke-Expression "$env:ANDROID_HOME/tools/bin/sdkmanager --licenses"
```

热重载
```
yarn start
```

## 放弃

- 成熟的工具因为 GFW 用不了， 如 https://expo.io/
- 好吧， 既然成熟的工具用不了， 就用官方出的 react-native-cli 吧
  结果十月份的 [bug](https://github.com/react-native-community/cli/issues/853)， 现在都到十二月了还没修复，
  每次编译还要自己去`node_modules`下改源码
- 改源码就改源码吧， 结果想找个类似  `electron` 的 `open-file-dialog` 组件， 没有！！！
- 没有就没有吧， 添加个[react-native-fs](https://github.com/itinance/react-native-fs) 自己实现吧
  又 TM 要手动改 `node_modules` 下源码
- 告辞， Flutter 走起



