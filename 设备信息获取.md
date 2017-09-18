# 设备属性获取

AIOT开放API可供第三方应用查询设备属性信息，各种资源定义详见资源定义文档。

| API | 描述 | payload | header | response |
| -- | -- | -- | -- | -- |
| /open/res/query | 查询设备有哪些资源 | {"openId":"xxx","did":"xxx"} | {"Appid":"xxx","Appkey":"xxx","Openid":"xxx","Access-Token":"xxx"} | {"code":0(errorcode), "result":{"did":"xxx","attr":[{"attr1":"xxx","name":"xxx","minValue":"xxx","maxValue":"xxx","enum":[xx,xx,xx]}]}} |
| /open/res/query/option | 查询设备的某些资源当前值 | {"openId":"xxx","did":"xxx","option":["attr1", "attr2",…]} | {"Appid":"xxx","Appkey":"xxx","Openid":"xxx","Access-Token":"xxx"} | {"code":0(errorcode), "result":{"did":"xxx","data":{"attr1":"xxx","attr2",...}}} |
| /open/res/query/history/option | 查询资源历史 |{"openId":"xxx","did":"xxx","startDate":"2016-02-10", "endDate":"2016-03-10", "option":["attr1", "attr2",…],"startCount":xx,"endCount":xx} | {"code":0|errorcode, "result":{"did":"11111","data":[{"attr1":"value","time":xxxxx},{"attr1":"value","time":xxxx},{"attr2":"value","time":xxxxx},{},...]}} |

> - startDate: 查询资源历史的起始日期
> - endDate: 查询资源历史的结束日期
> - startCount: 用于分页的开始数目
> - endCount: 用于分页的结束数目