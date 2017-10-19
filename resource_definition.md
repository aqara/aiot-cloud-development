# 资源定义

绿米智能设备均具备完善的资源定义，便于设备的管理。下面会根据设备类型，分别列出这些设备所具有的资源。

## 网关300

**model: lumi.gateway.v3**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| Alarm | alarm\_status | uint8\_t | 0,1 | -- | -- | 报警状态, 0-没报警，1-报警 |
| Alarm | alarm\_bell\_index | uint32\_t | -- | -- | -- | 播放警报index，当index=10000时播放默认铃声 |
| Alarm | alarm\_bell\_volume | uint8\_t | -- | 0 | 100 | 报警状态，0:没报警 ，1：报警 |
| Alarm | alarm\_time\_length | uint32\_t | -- | -- | -- | 报警时长 |
| Doorbell | doorbell\_status | uint8\_t | 0,1 | -- | -- | 门铃状态 |
| Doorbell | doorbell\_bell\_index | uint32\_t | -- | -- | -- | 播放门铃index，当index=10000时播放默认铃声 |
| Doorbell | doorbell\_bell\_volume | uint8\_t | -- | 0 | 100 | 门铃音音量,0~100 |
| Clock | clock\_status | uint8\_t | 0,1 | -- | -- | 闹钟状态 0: 停止播放 1：开始播放 |
| Clock | clock\_bell\_index | uint32\_t | -- | -- | -- | 播放闹钟index，当index=10000时播放默认铃声 |
| Clock | clock\_volume | uint8\_t | -- | 0 | 100 | 闹钟音量,0~100 |
| arming | arming\_status | uint8\_t | 1,2,3,4 | -- | -- | 布防状态：1:开/0:关/2:启动中/3:toggle /4:消警但不撤防 |
| arming | arming\_last\_alert\_time | uint32\_t | -- | -- | -- | 上次改变布防状态的时间,1970.1.1以后的秒数 |
| arming | arming\_delay\_time | uint32\_t | -- | -- | -- | 布防等待时间，单位秒，PROP\_TIME\_DELAY = 113 |
| corridor\_light | corridor\_light\_status | uint8\_t | 0,1,2 | -- | -- | 夜灯 1：打开 0：/关闭/2：toggle/3：智能夜灯打开（无人能自动灭，照度大能自动灭） |
| corridor\_light | corridor\_light\_argb | uint32\_t | -- | -- | -- | 夜灯ARGB |
| corridor\_light | corridor\_light\_bright | uint32\_t | -- | 0 | 100 | 夜灯亮度，0~100 |
| illumination | illumination\_value | float | -- | 0 | 1000 | 照度 |
| system\_volume | system\_volume | uint8\_t | -- | 0 | 100 | 系统音量 |

## 摄像头

**model:lumi.camera.v1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| camera | vedio\_status | uint8\_t | 0,1 | -- | -- | 改变当前视频开关状态，0：关闭视频，1：打开视频 |
| camera | vedio\_mode | uint8\_t | 0,1,2,3,... | -- | -- | 模式切换，水平模式，VR视角，四分屏，二分屏 |
| camera | vedio\_screen\_shot | uint8\_t | 0,1 | -- | -- | 截图 |
| camera | vedio\_record\_time | uint8\_t | -- | 0 | 255 | 录像时间，单位秒 |

## 空调伴侣

**model:lumi.acpartner.v1,lumi.acpartner.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| acpartner | ac\_state | uint32\_t | 0,1,2,3,... | -- | -- | 空调伴侣，根据uint32\_t的值决定是开关、风速、模式等等 |
| acpartner | ac\_load\_power | uint32\_t | -- | -- | -- | 空调伴侣负载功率，单位是瓦 W |

## 中央空调控制器

**model:lumi.ctrl\_hvac.v1, lumi.ctrl\_hvac.aq1, lumi.ctrl\_hvac.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| hvac | ac\_state | uint32\_t | --- | --- | --- | 根据uint32\_t的值决定是开关、风速、模式等 |

### ac\_state 格式说明

\[0 1 2 3\]\[4 5 6 7\]\[8 9 10 11\]\[12 13 14 15\]\[16 17 18 19 20 21 22 23\]\[24 25 26 27 28 29 30 31\]

| 位置 | 值 | 描述 |
| :--- | :--- | :--- |
| \[0 ~3\] | 0: off; 1: on; 2: toggle; E: circle; F: invalid; else: reserve | 开关 |
| \[4 ~ 7\] | 0: heat; 1: cool; 2: auto; 3: dry; 4: wind; E: circle; F: invalid; else: reserve | 模式 |
| \[8 ~ 11\] | 0: low; 1: middle; 2: high; 3: auto; E: circle; F: invalid; else: reserve | 风速 |
| \[12 ~ 13\] | 0: horizontal; 1: vertical; 2: circle; 3: invalid; | 风向 |
| \[14 ~ 15\] | 0: swing; 1: fix; 2: circle; 3: invalid; | 扫风 |
| \[16 ~ 23\] | 0 ~ 240; 243: up; 244: down; FF: invalid | 温度 |
| \[24\] | 默认为0 | 扩展位 |
| \[25\] | 默认为0 | 是否为压缩码 |
| \[26\] | 默认为0 | LED显示 |
| \[27\] | 0: 开关命令; 1: 非开关命令 | 是否为开关命令 |
| \[28 ~ 31\] | 00: 无状态; 01: 有状态; 02: 协议; 03: 推荐场景; 04: 半状态; 11: 忽略 | 空调类型 |

> 注意，ac\_state传值必须采用10进制数

## 86暗插

**model:lumi.ctrl\_86plug.v1,lumi.ctrl\_86plug.es1,lumi.ctrl\_86plug.aq1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| 86plug | 86plug\_status | uint8\_t | 0,1,2 | -- | -- | 插座打开/关闭,0:关闭，1:打开,2:toggle |
| 86plug | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| 86plug | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |
| 86plug | cost\_energy | float | -- | -- | -- | 消耗的电能 |

## 智能插座

**model:lumi.plug.v1, lumi.plug.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| plug | plug\_status | uint8\_t | 0,1,2 | -- | -- | 插座打开/关闭,0:关闭，1:打开,2:toggle |
| plug | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| plug | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |
| plug | cost\_energy | float | -- | -- | -- | 消耗的电能 |

## 86单键开关

**model:lumi.sensor\_86sw1.v1, lumi.sensor\_86sw1.aq1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| switch | switch\_status | uint8\_t | 0,1,2,3 | -- | -- | 0:释放，1:click,2:double\_click,3:three\_click |

## 智能窗帘

**model:lumi.curtain.v1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| curtain | curtain\_open\_percentage | uint8\_t | -- | 0 | 100 | 窗帘打开百分比 |
| curtain | curtain\_status | uint8\_t | 0,1,2 | -- | -- | 0:关，1:开,2:toggle 开窗帘、关窗帘、停止运动 |

## 86无线开关

**model:lumi.sensor\_86sw2.v1, lumi.sensor\_86sw2.aq1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| 86switch | switch\_ch0\_status | uint8\_t | 0,1,2,3 | -- | --- | 0:释放，1:click,2:double\_click,3:three\_click |
| 86switch | switch\_ch1\_status | uint8\_t | 0,1,2,3 | -- | -- | 0:释放，1:click,2:double\_click,3:three\_click |
| 86switch | switch\_both\_status | uint8\_t | 4 | -- | -- | 4-双键单击 |

## 无线开关

**model:lumi.sensor\_switch.v1,lumi.sensor\_switch.v2,lumi.sensor\_switch.aq2,lumi.sensor\_switch.es2**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| switch | switch\_status | uint8\_t | 0,1,2,3 | -- | --- | 0:释放，1:click,2:double\_click,3:three\_click |

## 门窗传感器

**model:lumi.sensor\_magnet.v1,lumi.sensor\_magnet.v2,lumi.sensor\_magnet.aq2,lumi.sensor\_magnet.es2**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| magnet | magnet\_status | uint8\_t | 0,1 | -- | --- | 0:关，1:开 |
| magnet | no\_close\_time\_length | uint32\_t | -- | -- | --- | 上报的数据是时间，单位为秒 |

## 人体传感器

**model:lumi.sensor\_motion.v1,lumi.sensor\_motion.v2,lumi.sensor\_motion.aq2,lumi.sensor\_motion.es2**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| motion | motion\_status | uint8\_t | 1 | -- | --- | 1:有人 |
| motion | no\_motion\_time\_length | uint32\_t | -- | -- | --- | 上报的数据是时间，单位为秒 |

## 温湿度传感器

**model:lumi.sensor\_ht.v1,lumi.sensor\_ht.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| ht | temperature\_value | int32\_t | -- | -4000 | 12500 | 温度，单位0.01摄氏度，只读 |
| ht | humidity\_value | uint32\_t | -- | 0 | 10000 | 湿度，单位万分之一，只读 |

## 零火线单键墙壁开关

**model:lumi.ctrl\_ln1.v1,lumi.ctrl\_ln1.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| ctrl\_ln1 | ctrl\_ch0\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_ln1 | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| ctrl\_ln1 | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |
| ctrl\_ln1 | cost\_energy | float | -- | -- | -- | 消耗的电能 |

## 零火线双键墙壁开关

**model:lumi.ctrl\_ln2.v1,lumi.ctrl\_ln2.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| ctrl\_ln2 | ctrl\_ch0\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_ln2 | ctrl\_ch1\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_ln2 | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| ctrl\_ln2 | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |
| ctrl\_ln2 | cost\_energy | float | -- | -- | -- | 消耗的电能 |

## 单火线单键开关

**model:lumi.ctrl\_neutral1.v1,lumi.ctrl\_neutral1.aq1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| ctrl\_neutral1 | ctrl\_ch0\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_neutral1 | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| ctrl\_neutral1 | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |

## 单火线双键开关

**model:lumi.ctrl\_neutral2.v1,lumi.ctrl\_neutral2.aq1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| ctrl\_neutral2 | ctrl\_ch0\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_neutral2 | ctrl\_ch1\_status | int8\_t | 0,1,2 | -- | -- | 打开/关闭,0:关闭，1:打开,2:toggle |
| ctrl\_neutral2 | load\_voltage | uint32\_t | -- | -- | -- | 负载电压，单位是毫伏 mV |
| ctrl\_neutral2 | load\_power | uint32\_t | -- | -- | -- | 负载功率，单位是瓦 W |

## 魔方

**model:lumi.sensor\_cube.v1,lumi.sensor\_cube.es1**

| 功能模块 | 资源 | 值类型 | 枚举值 | 最大值 | 最小值 | 描述 |
| --- | --- | --- | --- | --- | --- | --- |
| cube | cube\_statue | string | flip90,flip180,move,tap\_twice,shake\_in\_plane,shake\_air,swing,rotate | -- | -- | 魔方的动作 |
| cube | rotate\_time\_length | int32\_t | -- | -- | -- | 上报的数据是时间长度（ms） |
| cube | rotate\_degree | uint32\_t | -- | -- | -- | 上报的数据是角度（°） |



