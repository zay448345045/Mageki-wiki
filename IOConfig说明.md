# IOConfig
IOConfig.exe是用于配置[ongeki-io](https://github.com/Sanheiii/ongeki-io)的工具，并随其一同发布。
## 手台
软件上方是一个GUI绘制的手台，用于测试对应的功能是否正常工作
## 作用域
允许用户选择这个控制器需要使用的部分，最终聚合所有控制器的输入并发送给游戏
## 控制器
表示已启用的控制器，你可以添加多个控制器或删除它们。

同时使用UDP,TCP，USBMUX时需要分别指定不同的端口号
### TCP
用于使用数据线连接到Android版Mageki
1. 在IOConfig点击 __添加控制器__ → __Tcp__ → __确定__
2. 下载[ADB](https://www.xda-developers.com/install-adb-windows-macos-linux/)
3. 将Android设备使用USB线连接到PC
4. 安装[OEM USB驱动](https://developer.android.google.cn/studio/run/oem-usb)（可能不需要）
5. 将Mageki设置页面的 __连接__ → __协议__ 的值修改为TCP
6. 将Mageki设置页面的 __连接__ → __端口__ 与IOConfig中 __TCP控制器__ → __端口__ 设置为相同的值
7. [PC上使用命令](https://www.xda-developers.com/install-adb-windows-macos-linux/)进行端口转发```adb forward tcp:4354 tcp:4354```<br/>4354是默认端口，按需要修改为与Mageki，IOConfig中相同的端口
### USBMUX
用于使用数据线连接到iOS版Mageki
1. 在IOConfig点击 __添加控制器__ → __Usbmux__ → __确定__
2. 将iOS设备使用USB线连接到PC
3. 安装[__爱思助手__](https://www.i4.cn/)，在爱思助手中成功连接设备并显示设备信息后，关闭爱思助手
4. 将Mageki设置页面的 __连接__ → __协议__ 的值修改为TCP
5. 将Mageki设置页面的 __连接__ → __端口__ 与IOConfig中 __TCP控制器__ → __端口__ 设置为相同的值
### UDP
用于无线连接到Mageki
1. 在IOConfig点击 __添加控制器__ → __Udp__ → __确定__
2. 控制设备与PC连接到同一局域网
3. 将Mageki设置页面的 __连接__ → __协议__ 的值修改为UDP
4. 将Mageki设置页面的 __连接__ → __端口__ 与IOConfig中 __UDP控制器__ → __端口__ 设置为相同的值
5. 如果Mageki设置页面中 __连接__ → __IP地址__ 为 ```Broadcast``` 时候无法连接，请尝试在其中填入[PC的内网IP地址](https://www.jianshu.com/p/da4bdc73a140)
### Keyboard
使用键盘控制按键（不支持摇杆）
1. 在IOConfig点击 __添加控制器__ → __Keyboard__ → __确定__
2. 点击 __键盘__ → __按键设定__ 来指定键位
### HID
用于连接到手台
1. 在IOConfig点击 __添加控制器__ → __Hid__ → __确定__
2. 插入正在运行[对应固件](https://github.com/Sanheiii/ongeki-io/tree/nageki/mu3controller)的手台