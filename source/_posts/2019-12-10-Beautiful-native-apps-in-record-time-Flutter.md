---
title: 'Beautiful native apps in record time: Flutter'
date: 2019-12-10 04:01:08
tags:
- Flutter
---
[Dart | 什么是Stream]: https://juejin.im/post/5baa4b90e51d450e6d00f12e
[Flutter | 状态管理探索篇——Scoped Model（一）]: https://juejin.im/post/5b97fa0d5188255c5546dcf8
[Flutter | 状态管理探索篇——Redux（二）]: https://juejin.im/post/5ba26c086fb9a05ce57697da
[Flutter | 状态管理探索篇——BLoC(三)]: https://juejin.im/post/5bb6f344f265da0aa664d68a
[Flutter | 状态管理拓展篇——RxDart(四)]: https://juejin.im/post/5bcea438e51d4536c65d2232
[Flutter 中文网]: https://flutterchina.club/get-started/install/
[awesome-flutter]: https://github.com/Solido/awesome-flutter
[OpenFlutter/Flutter-Notebook]: https://github.com/OpenFlutter/Flutter-Notebook
[bloc-pattern]: https://github.com/jacobaraujo7/bloc-pattern/blob/master/README.md
[Flutter SDK]: https://flutter.dev/docs/development/tools/sdk/releases#windows
[Flutter 官网]: https://flutter.dev/
[Dart 官网]: https://dart.dev/
[Learn-once-write-anywhere-React-Native]: https://floatsyi.com/2019/12/07/Learn-once-write-anywhere-React-Native/
[Vscode: Dart-Code.flutter]: https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter
[counter-using-bloc_pattern]: https://github.com/LilySny/counter-using-bloc_pattern
[slidy]: https://github.com/Flutterando/slidy
[RxDart]: https://github.com/ReactiveX/rxdart
## 参考
- [Flutter 官网][]
- [Flutter 中文网][]
- [Dart 官网][]
- [Learn-once-write-anywhere-React-Native][]
- [Flutter | 状态管理探索篇——Scoped Model（一）][]
- [Flutter | 状态管理探索篇——Redux（二）][]
- [Flutter | 状态管理探索篇——BLoC(三)][]
- [Dart | 什么是Stream][]
- [Flutter | 状态管理拓展篇——RxDart(四)][]
- [bloc-pattern][]
- [RxDart][]

## 资源
- [Vscode: Dart-Code.flutter][]
- [Flutter SDK][]
- [awesome-flutter][]
- [OpenFlutter/Flutter-Notebook][]
- [bloc-pattern][]
- [slidy][]
- [RxDart][]
- [counter-using-bloc_pattern][]

<!-- more -->

## 配置 android 开发环境
参考 [Learn-once-write-anywhere-React-Native][]

## vscode 的 flutter 插件(必装)
- [Vscode: Dart-Code.flutter][]

## 安装 Flutter SDK
1. 下载 [Flutter SDK][] Stable channel (Windows)， 并解压到合适的目录
2. 按快捷键 `win + x + a` 打开 powershell， 执行以下命令， 以添加环境变量
  ```powershell
    $flutterPath="X:\Support\Other\flutter\bin" # 改为你的 Flutter 解压路径
    $userPath=[Environment]::GetEnvironmentVariable("Path", "User") + ";$flutterPath"
    [Environment]::SetEnvironmentVariable("PATH", "$userPath", "User")
    $env:PATH="$env:PATH;$flutterPath"
    [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
  ```
3. 继续执行以下命令, 以设置镜像
  ```powershell
    [Environment]::SetEnvironmentVariable('PUB_HOSTED_URL', 'https://pub.flutter-io.cn', 'User')
    [Environment]::SetEnvironmentVariable('FLUTTER_STORAGE_BASE_URL', 'https://storage.flutter-io.cn', 'User')
  ```


### Dart
dart 已经包含在 flutter sdk 中， 因此只要添加环境变量即可
  ```powershell
    $dartPath="X:\Support\Other\flutter\bin\cache\dart-sdk\bin" # 改为你的 Flutter 解压路径
    $env:PATH="$env:PATH;$dartPath"
    [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
  ```

#### dart 包管理 pub
pub 使用请参考 [How to use packages](https://dart.dev/guides/packages#importing-libraries-from-packages)

1. 为将来安装在全局的软件包添加环境变量, 请执行以下命令
  ```powershell
    $pubCachePath="X:\Support\Other\flutter\.pub-cache\bin"
    $env:PATH="$env:PATH;$pubCachePath"
    [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
  ```
2. 按快捷键 `win + x + u + i` 注销登录，并重新登录以刷新环境变量
3. 执行以下命令以验证所有安装
  ```powershell
  flutter --version
  dart --version
  pub --version
  ```
#### dart 语法
dart 语法请参考 [A tour of the Dart language](https://dart.dev/guides/language/language-tour)
[Dart 官网][] 有个 Repl 可以练习.

#### dart 代码样式规范

- [Effective Dart](https://dart.dev/guides/language/effective-dart#the-guides)

## 状态管理 BLoC

推荐使用 [bloc-pattern][] + [Rxdart][]
- [Flutter | 状态管理探索篇——Scoped Model（一）][]
- [Flutter | 状态管理探索篇——Redux（二）][]
- [Flutter | 状态管理探索篇——BLoC(三)][]
- [Dart | 什么是Stream][]
- [Flutter | 状态管理拓展篇——RxDart(四)][]

## flutter 包管理 slidy

- [slidy][]

## DI(Dependency Injection): Bloc Pattern

- [bloc-pattern][]

## Hello World: CountApp

- [counter-using-bloc_pattern][]

## MVC

slidy 构建的一个 mvc 模板， 这是很高规格的应用了， 小应用一般用不了这么复杂
https://github.com/Flutterando/slidy/tree/master/example

## 其他
组件 布局 交互 标准库这些
看官网吧
- [Flutter 官网][]
- [Flutter 中文网][]
- [Dart 官网][]

<!--
  $flutterPath="X:\Support\Other\flutter\bin" # 改为你的 Flutter 解压路径
  $userPath=[Environment]::GetEnvironmentVariable("Path", "User") + ";$flutterPath"
  [Environment]::SetEnvironmentVariable("PATH", "$userPath", "User")
  $env:PATH="$env:PATH;$flutterPath"
  [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
-->
<!--
  $dartPath="X:\Support\Other\flutter\bin\cache\dart-sdk\bin"
  $env:PATH="$env:PATH;$dartPath"
  [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
-->
<!--
  [Environment]::SetEnvironmentVariable('PUB_HOSTED_URL', 'https://pub.flutter-io.cn', 'User')
  [Environment]::SetEnvironmentVariable('FLUTTER_STORAGE_BASE_URL', 'https://storage.flutter-io.cn', 'User')
-->
<!--
  $pubCachePath="X:\Support\Other\flutter\.pub-cache\bin"
  $env:PATH="$env:PATH;$pubCachePath"
  [Environment]::SetEnvironmentVariable("PATH", "$env:PATH", "Machine")
-->

