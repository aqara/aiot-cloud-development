# 设备信息推送

当设备信息发生更改时，比如固件版本发生更改时，AIOT会及时将设备信息推送至第三方应用，需要第三方应用后台提供接口，这里定义推送的数据格式。

| msgType | device_info |
| --: | :-- |
| **描述** | 设备信息推送 |
| **header** | {"**Appid**":"xxx","**Appkey**":"xxx"} |
| **payload** | {"**msgType**":"device_info","**data**":[{"**did**":"xxx","mac": "xxx", "name": "xxx", "firmwareVersion": "xxx", "state":"xxx", "model":"xxx", "chipVersion":"xxx"}]} |

> - did: 设备id
> - msgType: 消息类型
> - state: 设备在线/离线状态，0-在线，1-离线
> - Appid: 第三方应用的appId
> - Appkey: 第三方应用的appKey

##消息回复格式

回复消息中需包含code字段，用于表示是否接收成功。

| code | 错误码 |
| --: | :-- |
| **0** | SUCCESS (成功) |
| **100** | ERROR_TIMEOUT (超时) |
| **301** | ERROR_REQUEST_PATH (请求路径错误) |
| **302** | ERROR_REQUEST_PARAMS (请求参数错误) |
| **801** | ERROR_APPID_OR_APPKEY_ILLEGAL (appId或appKey有误) |
| **500** | ERROR_INTERNAL_SERVER (服务器出错) |

