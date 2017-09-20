# 开放接口调用规范

AIOT开放接口均使用HTTPS协议，需要在header中添加校验信息，在body中添加payload信息，返回结果为JSON格式。

* 开放接口统一域名: [https://aiot-rpc-3rd.aqara.cn](https://aiot-rpc-3rd.aqara.cn)
* header部分的校验信息: `{"Appid":"xxx","Appkey":"xxx","Access-Token":"xxx","Openid":"xxx"}`
* payload数据格式：JSON
* 返回结果数据格式：JSON

## 例子

给出一个请求获取设备信息的API接口调用示范，如下：

* 获取设备信息API：/open/device/query
* https请求的URL：[https://aiot-rpc-3rd.aqara.cn/open/device/query](https://aiot-rpc-3rd.aqara.cn/open/device/query)
* header: `{"Appid":"xxx","Appkey":"xxx","Access-Token":"xxx","Openid":"xxx"}`
* payload: `{"openId":"xxx","did":"xxx"}`
* response: `{"code":0(errorcode), "result":{"did":"xxx", "model":"xxx", "name":"xxx", "firmwareVersion": "xxx", "isOnline":"xxx", "chipVersion":"xxx", "longitude":"xxx", "latitude":"xxx", ...}`

其中：

* Appid: 第三方应用appId
* Appkey: 第三方应用appKey
* Access-Token: 用户Token（详见账户对接文档）
* Openid: 用户在AIOT中的账号（详见账户对接文档）
* did: 设备id
* errorcode: 错误码（详见错误码文档）
* model: 设备类型
* firmwareVersion: 设备固件版本
* isOnline: 设备是否在线
* chipVersion: 设备芯片版本
* longitude, latitude: 设备地理位置经纬度



