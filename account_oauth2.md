# OAuth2.0

OAuth2.0 是一个关于授权（authorization）的开放网络标准，关于这个标准的详细内容请见：[RFC 6749](http://www.rfcreader.com/#rfc6749)

AIOT提供OAuth2.0的授权码模式（authorization code），这是功能最完整、流程最严密的授权模式。它的主要流程如下：

1. 用户访问客户端，后者将前者导向认证服务器。
2. 用户选择是否给予客户端授权。
3. 假设用户给予授权，认证服务器将用户导向客户端事先指定的"重定向URI"（redirection URI），同时附上一个授权码。
4. 客户端收到授权码，附上早先的"重定向URI"，向认证服务器申请令牌。这一步是在客户端的后台的服务器上完成的，对用户不可见。
5. 认证服务器核对了授权码和重定向URI，确认无误后，向客户端发送访问令牌（access token）和更新令牌（refresh token）。

一、Authorization URI

| URI | [https://aiot-oauth2.aqara.cn/authorize?client\_id=xxx&response\_type=code&redirect\_uri=xxxx&state=xxx&theme=x](/    https://aiot-oauth2.aqara.cn/authorize?client_id=xxx&response_type=code&redirect_uri=xxxx&state=xxx&theme=x) |
| ---: | :--- |
| **描述** | 用户授权登录界面，获取授权码 |
| **请求方法** | Get |
| **发送的数据结构** | client\_id\(第三方应用的appId\);  response\_type=code; redirect\_uri\(重定向url\); scope\[可选\]; state\[可选\]任意值，认证服务器仍返回这个值; theme\[可选\]页面主题，目前支持0,1,2三套主题，默认为0 |
| **返回值数据结构** | [http://redirect\_uri?code=xxxx&state=xxx](http://redirect_uri?code=xxxx&state=xxx)  认证服务器回调url,其中code为授权码，有效期为10分钟；state如果客户端的请求中包含这个参数，认证服务器的回应也包含同样的参数 |

二、Access Token URI

| URI | [https://aiot-oauth2.aqara.cn/access\_token](https://aiot-oauth2.aqara.cn/access_token) |
| ---: | :--- |
| **描述** | 申请access\_token |
| **请求方法** | Post \(x-www-form-urlencoded\) |
| **发送的数据结构** | client\_id\(第三方应用的 appId\); client\_secret\(第三方应用的 appKey\); grant\_type=authorization\_code; code\(授权码\); redirect\_uri\(重定向url\); |
| **返回值数据结构** | {"state":"xxx","expires\_in":7200\(access\_token的有效期，单位为秒\),"token\_type":"bearer","refresh\_token":"xxxxx","access\_token":"xxxxx","openId":"xxx"\(用户的openId\)} |

三、Refresh Token URI

| URI | [https://aiot-oauth2.aqara.cn/access\_token](https://aiot-oauth2.aqara.cn/access_token) 或 [https://aiot-oauth2.aqara.cn/refresh\_token](https://aiot-oauth2.aqara.cn/refresh_token) |
| ---: | :--- |
| **描述** | 刷新access\_token |
| **请求方法** | Post \(x-www-form-urlencoded\) |
| **发送的数据结构** | client\_id\(第三方应用的 appId\); client\_secret\(第三方应用的 appKey\); grant\_type=refresh\_token; refresh\_token; |
| **返回值数据结构** | {"state":"xxx","expires\_in":7200\(access\_token的有效期，单位为秒\),"token\_type":"bearer","refresh\_token":"xxxxx"\(refresh\_token的有效期是30天\),"access\_token":"xxxxx","openId":"xxx"\(用户的openId\)} |

四、Privacy Policy URL

| URI | [https://aiot-oauth2.aqara.cn/privacy\_policy](https://aiot-oauth2.aqara.cn/privacy_policy) |
| ---: | :--- |
| **描述** | 隐私政策声明 |
| **请求方法** | Get |

五、参考

关于OAuth2.0的服务模式，请参考一下资料：

* [理解OAuth 2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)



