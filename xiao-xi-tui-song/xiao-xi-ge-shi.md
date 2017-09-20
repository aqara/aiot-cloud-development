### 资源消息

```
{
    msgType: "resource", 
    data: [
        {
            time: "1503556533", 
            attr: "load_power", 
            value: "3.93", 
            did: "lumi.158d00011c1cee"
        }
    ]
}
```

| 参数 | 说明 |
| :--- | :--- |
| msgType | 消息类型，资源消息固定为resource |
| did | 设备ID |
| attr | 资源别名，所有资源别名见网页“应用管理-&gt;资源授权” |
| value | 资源的最新值 |
| time | 时间戳，单位：秒 |

### 设备消息

```
{
    msgType: "device", 
    data: {
        openId: "GoeFrrL7mN9SsGRi8WJn4x4YnQpXTS", 
        name: "02凝胶净化室", 
        model: "lumi.acpartner.aq1", 
        time: 1503560767, 
        event: "DEV_INFO_CHANGED", 
        did: "lumi.158d00010b4090", 
        parentId: ""
    }
}
```

| 参数 | 说明 |
| :--- | :--- |
| msgType | 消息类型，资源消息固定为resource |
| openId | 用户ID |
| did | 设备ID |
| name | 设备名称 |
| model | 设备类型 |
| parentId | 父设备（网关）ID，如果是网关，该字段为空 |
| event | 事件类型，见下表 |
| time | 时间戳，单位：秒 |

| 事件类型 | 描述 |
| :--- | :--- |
| GW\_BIND | 网关入网 |
| GW\_UN\_BIND | 网关解绑 |
| GW\_ONLINE | 网关在线 |
| GW\_OFFLINE | 网关离线 |
| SUB\_DEV\_BIND | 子设备入网 |
| SUB\_DEV\_UN\_BIND | 子设备解绑 |
| SUB\_DEV\_ONLINE | 子设备在线 |
| SUB\_DEV\_OFFLINE | 子设备离线 |
| DEV\_INFO\_CHANGED | 设备信息改变 |



