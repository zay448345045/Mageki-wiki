Mageki可以使用移动设备来连接到[ongeki-io](https://github.com/Sanheiii/ongeki-io)，来到这个页面的你一定已经迫不及待了，但是首先你需要一个能够成功运行并使用其它方式控制的游戏本体。如果还没有，请参阅：
### [最新最热的游戏下载与配置说明](https://www.bilibili.com/video/BV1GJ411x7h7/)
当游戏本体配置完备后，才可以进行下面的步骤。
## 开始使用
请前往 __[发布页](https://github.com/Sanheiii/Mageki/releases)__ 下载所需的文件。
### 安装程序
- Android
  1. 下载 __mageki.apk__。
  2. 在Android设备上打开以安装程序。
- iOS
  1. 下载 __mageki.ipa__。
  2. 使用自签工具（如[AltStore](https://altstore.io/)）安装ipa。
- UWP
  - 缺少触屏设备无法调试，如有需求请自行编译，Debug并提交Pull request。
### 配置ongeki-io
1.  __MU3Input.zip__ 的内容解压至 __SDDT\package__ 目录下。
2. 将 __segatools_diff.ini__ 中的内容添加到 __segatools.ini__ 中，并删除原有 __[mu3io]__ 与 __[aime3io]__ 下的内容。
3. 根据以下说明修改 __[mu3io]__ 下 __protocol__ 字段的值：
</br>

- 使用 __无线连接__
```ini
protocol=udp
```
- 使用 __Android__ 设备 __有线连接__
```ini
protocol=tcp
```
- 使用 __iOS__ 设备 __有线连接__
```ini
protocol=usbmux
```

</br>

4. 保存文件。
### 使用Mageki连接到ongeki-io
1. 打开Mageki，此时 __*オンゲキ*__ 图标显示为灰色。
2. 点击 __*オンゲキ*__ 图标 打开设置页面。
3. 在 __连接__ → __协议__ 中选择：

</br>

　　无线连接： __UDP__

</br>

　　有线连接： __TCP__

__无线连接在这里即可完成，但由于某些原因，不是所有人都能够成功无线连接。__

__如需使用有线连接需要额外进行下面步骤：__

- 使用USB线缆连接移动设备与PC。
- 如果你使用iOS设备，需要在PC中安装[iTunes](https://support.apple.com/HT210384)与[iCloud](https://support.apple.com/HT204283)（不要下载Microsoft Store中的版本，自签时应该已经安装过）。
- 如果你使用Android设备，需要打开 __USB调试__ 并使用[ADB](https://developer.android.com/studio/releases/platform-tools)命令进行 __端口转发__ 。
```
./adb forward tcp:4354 tcp:4354
```

为Android设备启用端口转发后，PC端将无法正确检测连接性。

<br/>

__成功连接后， *オンゲキ* 图标将会变为黑色__。

<br/>

## 可能遇到的问题

__解答以下问题的前提是在配置Mageki之前能够正常运行，并且解决方案也不一定有效__
### 解压MU3Input后无法正常游戏
可以尝试解压 __configs.zip__ 中的内容至 __package__ 文件夹
### 进入游戏后摇杆没有反应
在游戏中点击 __*オンゲキ*__ 图标打开设置菜单，点击 __Test键__ ，退出Mageki的设置页面。根据游戏Test页面的提示，进入 __レバー設定__，分别向左右滑动Mageki上方的空白区域移动摇杆，使Test页面中十六进制数不再变化。最后保存并退出Test页面。