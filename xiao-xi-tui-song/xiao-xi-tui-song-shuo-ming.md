### 明文模式

将推送的json消息包含在http body中推送出去，第三方应用接到http请求后，从http body中取出消息后，调用AIOT SDK中SecHttpHandler.getNoneSecRequest函数解析到请求参数对象，业务处理后，调用SecHttpHandler.getSecResponse函数构造出返回给AIOT开放平台的消息体。

### 兼容或者安全模式

AIOT开放平台会将推送的json消息加密后，加上签名、时间戳、随机数等组成一个新的json消息体放在http body中推送出去，第三方应用接到http请求后，从http body中取出消息后，调用AIOT SDK中SecHttpHandler.getSecRequest函数解析到安全HTTP请求参数对象，业务处理后，调用SecHttpHandler.getSecResponse函数构造出返回给AIOT开放平台的安全HTTP消息体。

[java sdk 下载](https://cnbj2.fds.api.xiaomi.com/lumiaiot/public/message/aiot_sdk_java.zip)

[php sdk 下载](https://cnbj2.fds.api.xiaomi.com/lumiaiot/public/message/aiot_sdk_php.zip)

