# DumpHarmony
## 功能
实现以App权限复制HarmonyOS NEXT系统文件夹到电脑，主要用于获取系统`/system/lib64`或者`/system/app`这类目录文件，方便安全研究人员进行逆向分析。

## 环境要求
* DevEco Studio 5.0.3.300SP2或更高版本
* HarmonyOS NEXT Developer Beta1或更高版本
* python 3.x并安装好flask

## 使用方式
**注意：您需要首先成为鸿蒙开发者，否则无法获取调试profile为应用签名。**
1. 使用DevEco Studio打开项目，然后配置正确的调试profile；
2. HarmonyOS NEXT手机进入“设置-设备名称”，点按软件版本7次，打开开发者模式，手机会自动重启，手机重启后进入“设置-系统-开发者模式”，打开USB调试；
3. HarmonyOS NEXT手机和PC运行在同一局域网，修改app.run的参数为你想要的，并且运行web/file_receiver.py，并在Index.ets中修改uploadUrl为相同正确的URL；
4. 使用DevEco Studio运行应用，过滤日志输出“DumpHarmony”查看上传进度，文件保存在uploads下。

## 为什么不使用hdc shell获取
华为对hdc shell的权限限制极为严格，并不能访问系统大部分文件路径的内容，所以无法像Android手机一样通过adb shell来获取文件。如果在Android上有类似的需求可以使用：https://github.com/wrlu/Android-Tools。

## License
MIT License
