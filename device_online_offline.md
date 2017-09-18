# 设备在线离线


AIOT通过心跳包时刻监听设备的在线离线状态，AIOT将设备的在线离线消息开放给第三方应用，通过推送的方式进行。需要第三方应用后台提供接口，消息推送的格式如下：

| msgType | device_state |
| --: | :-- |
| **描述** | 在线/离线状态推送 |
| **header** | {"**Appid**":"xxx","**Appkey**":"xxx"} |
| **payload** | {"**msgType**":"device_state","**did**":"xxx","**state**":0/1,"**time**":xxx} |

> - did: 设备id
> - msgType: 消息类型
> - time: 时间戳，单位为s
> - state: 设备在线离线的状态，0-在线,1-离线
> - Appid: 第三方应用的appId
> - Appkey: 第三方应用的appKey

同样，第三方应用也可以通过调用设备信息获取的开放API来获取设备的在线离线状态。