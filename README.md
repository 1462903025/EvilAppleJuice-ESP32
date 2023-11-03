# EvilAppleJuice ESP32

通过蓝牙对Iphone发送垃圾信息！

|iPhone 15s (最新)|旧版 iPhones|
|-------------------|-------------|
|<video controls width="250" src="https://user-images.githubusercontent.com/6680615/274864225-53ed6d7c-0569-4f22-b55b-bc9973c4bc93.mp4"></video>|<video controls width="250" src="https://user-images.githubusercontent.com/6680615/274864287-c6e871fd-9fdf-4507-ae21-a566beead5cc.mp4"></video>|

基于 [ronaldstoner](https://github.com/ronaldstoner) 的 [AppleJuice repository](https://github.com/ECTO-1A/AppleJuice/blob/e6a61f6a199075f5bb5b1a00768e317571d25bb9/ESP32-Arduino/applejuice.ino).

随机发送，它可以使 iPhone 几乎无用，只需一个 ESP32（关闭旧通知后立即发送新通知）

影响设备:
* iPhone 14 Pro (iOS 16.6.1)
* iPhone 13 Pro (TBD which iOS)
* iPhone 11 (iOS 16.6.1)
* iPhone X (iOS 14.8 (18H17)) - only "AppleTV Keyboard", "TV Color Balance", "AppleTV Setup", "AppleTV Homekit Setup", "AppleTV New User".

无影响设备:
* iPhone 4S (iOS 10.3 (14E277))

其他反馈:
* 如果键盘/相机打开，似乎不会生成通知

### 视频演示

ESP32 vs. iPhone 14 Pro @ iOS 16.6.1

https://github.com/ECTO-1A/AppleJuice/assets/6680615/47466ed6-03c9-43b2-a0d0-aac2e2aaa228

## 区别

此实现进行了以下更改:

* 随机源MAC地址 (包括 `BLE_ADDR_TYPE_RANDOM`)
* 随机选择 BLE 信息类型 ([这可能会更有效](https://github.com/ECTO-1A/AppleJuice/pull/25))
* 随机选择一种可能的设备

它每次运行时都会做出这些随机选择（默认每秒重新通告一次）

给定 29 个设备和 3 种通告类型，总共有 87 个唯一可能的通告（忽略随机源 MAC），其中每秒广播一个

## 用法

克隆存储库，最简单的方法是使用 VS Code 和 PlatformIO 将其上传到您的 ESP32。

该项目已在 [ESP32-C3经典版](https://wiki.luatos.com/chips/esp32c3/board.html)上测试.

## 编译与上传

通过 vscode 点击左侧栏的扩展 -> 搜索platformIO -> 安装第一个插件

https://img-blog.csdnimg.cn/img_convert/43c0aaeb10bda68521f9257acb41e3e2.png#pic_center

插件安装好后会在左侧栏自动生成一个蜜蜂图标，点击进入平台主页(或选择点击左下角的小房子)

https://img-blog.csdnimg.cn/img_convert/a139f7311ee96e66ab412e5098ae8255.png#pic_center

先编译再上传（左下角）

https://img-blog.csdnimg.cn/img_convert/14de97095f80da9d69e1fbc9a78ce307.png#pic_center
