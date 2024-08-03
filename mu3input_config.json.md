运行 __Test.exe__ 能够在当前目录生成mu3input_config.json，在此基础上可以进行一定程度的修改


支持的 __Type__ 及对应 __Param__ 的内容有
- __UDP__：端口号
- __TCP__：端口号
- __Usbmux__：端口号
- __Hid__：无Param
- __Keyboard__：按键映射，不支持摇杆<br>
一般来说支持定义的按键为：
   - L1
   - L2
   - L3
   - LSide
   - LMenu
   - R1
   - R2
   - R3
   - RSide
   - RMenu
   - Test
   - Service
   - Coin
   - Scan

你也可以参考IO源代码获取更多可映射的按键 [__KeyboardIOConfig__](https://github.com/Sanheiii/ongeki-io/blob/develop/MU3Input/IO/KeyboardIO.cs#L82)

  - 值使用KeyCode或[__System.Windows.Forms.Keys__](https://learn.microsoft.com/zh-cn/dotnet/api/system.windows.forms.keys)中定义的枚举值

- __Part__ 用于指定负责的功能，__使用半角逗号(, )分隔__，一般来说可指定的值为下表<br>
（表中等号前面的是你填写至Part的值，等号后的为此值控制的参数）

  - LKeyBoard = L1 | L2 | L3,
  - RKeyBoard = R1 | R2 | R3,
  - Side = LSide | RSide,
  - Menu = LMenu | RMenu,
  - KeyBoard = LKeyBoard | RKeyBoard,
  - Left = LKeyBoard | LSide | LMenu,
  - Right = RKeyBoard | RSide | RMenu,
  - GameButtons = KeyBoard | Side,
  - Buttons = GameButtons | Menu,
  - GamePlay = GameButtons | Lever,
  - All = GamePlay | Menu | Aime,

当然，你也可以参考源代码的Config来查看还能配置出什么神奇的花样 [__MU3Input.Config.cs__](https://github.com/Sanheiii/ongeki-io/blob/develop/MU3Input/Config.cs#L69)

使用多台设备运行Mageki连接到同一PC时请指定不同的端口！！！
# 使用例
## Mageki正常连接例
### UdpIO
- 用于通过局域网无线连接到Mageki<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Udp",
      "Param": 4354,
      "Part": "All"
    }
  ]
}
```
### TcpIO
- 用于通过USB线连接到Android版Mageki<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Tcp",
      "Param": 4354,
      "Part": "All"
    }
  ]
}
```
### UsbmuxIO
- 用于通过USB线连接到iOS版Mageki<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Usbmux",
      "Param": 4354,
      "Part": "All"
    }
  ]
}
```
## 混合使用例
- 使用iPad控制游戏，支持NFC的手机作为读卡器使用<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Usbmux",
      "Param": 4354,
      "Part": "GamePlay, Menu"
    },
    {
      "Type": "Udp",
      "Param": 4355,
      "Part": "Aime"
    }
  ]
}
```
- 使用键盘控制按钮，Mageki控制摇杆，侧键，菜单，读卡<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Keyboard",
      "Param": {
        "L1":"F6",
        "L2":"F7",
        "L3":"F8",
        "R1":"F9",
        "R2":"F10",
        "R3":"F11"
      },
      "Part": "KeyBoard "
    },
    {
      "Type": "Udp",
      "Param": 4354,
      "Part": "Lever, Side, Menu, Aime"
    }
  ]
}
```
-  使用手台控制游戏，Mageki作为读卡器使用
手台需要固件兼容，请咨询你的卖家<br>
mu3input_config.json:
``` json
{
  "IO": [
    {
      "Type": "Hid",
      "Part": "GamePlay, Menu"
    },
    {
      "Type": "Udp",
      "Param": 4354,
      "Part": "Aime"
    }
  ]
}
```