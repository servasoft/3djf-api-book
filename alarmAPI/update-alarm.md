# 更新告警

<font face="Droid Sans Mono,monospace" size="5">
<font color="#00b2ed"><b>PUT</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/alarm/[<font color="#005977">id</font>]
</font>

### Path parameters
name | type | description
:-----:|:------:|:------------:
id   |string|推送方的告警的唯一标识

### Body
>要更新的告警属性，通常在确认告警或修改告警状态时，通过更新方法

Accept: application/json

```
{
    deviceId : string，required，发生告警的设备,
    alarmType: string，required，对应告警类型中的编号，参考告警类型模块,
    level: string，required，对应告警级别中的编号，参考告警级别模块,
    description: string，告警描述,
    time: date，告警发生时间,
    ack_time: date，告警确认时间,
    ack_notice: string，确认告警时备注,
    devIp: string，发生告警的IP,
    client: {} Object，扩展的字段
}
```

### Returns
异步操作，返回结果仅表示推送到3D机房系统后端

Content-Type: application/json

```
{value:"success", error:''}
```

### Demo
>以增加告警章节demo中添加的编号为123的告警为例

```
var data = {
    "ackTime": "2016-12-30",
    "ackNotice": "已转交其他同事处理",
    "client": {
        "确认时间": "2016-12-30 9",
        "告警确认人": "admin",
        "确认内容": "已转交其他同事处理"
    },
    "status": "ack"
}
$.ajax({
    url: '/api/monitor/alarm/123',
    type: 'PUT',
    data: data,
    success: function(result) {
      // Do something with the result
    }
});
```