# 增加告警

<font face="Droid Sans Mono,monospace" size="5">
<font color="#003bed"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/alarms
</font>


### Body
>一个或多个告警实例

Accept: application/json

```
{
	module: string,模块名，保留字段，缺省值“PEMS”, 
	data: [
        {
            alarmId: string，required，告警的唯一标识,
            deviceId : string，required，发生告警的设备,
            alarmType: string，required，对应告警类型中的编号，参考告警类型模块,
            level: string，required，对应告警级别中的编号，参考告警级别模块,
            description: string，告警描述,
            time: date，告警发生时间,
            ackTime: date，告警确认时间,
            ackNotice: string，确认告警时备注,
            devIp: string，发生告警的IP,
            client: {} Object，扩展的字段
        }
    ]
}
```

### Returns
异步操作，返回结果仅表示推送到3D机房系统后端

Content-Type: application/json

验证成功

```
{
	value:"success",
	error: null
}
```
某种原因验证失败

```
{
	value: "fail", 
	error: "原因",
	items: [{}],数组元素为，错误的告警对象，但是不一定会有，只有在添加告警做验证不通过时有值
}
```
多种原因验证失败

```
{
	value: "fail", 
	error: "verification failed",
	items: [{
		reason:'',
		items: [{}],数组元素为，错误的告警对象，但是不一定会有，只有在添加告警做验证不通过时有值
	}]
}

```

### Demo

```
var data = {
	module: "PEMS", 
	data: [
        {
            alarmId: '123',
            deviceId : 'rack84_E01',
            alarmType: '温度告警',
            level: 'critical',
            description: '湿度过高',
            time: new Date(),
            devIp:'127.0.0.1',
            client: {'告警值':70}
        },
        {
            alarmId: '234',
            deviceId : 'rack84_E01',
            alarmType: '网络告警',
            level: 'critical',
            description: '网络端口',
            time: new Date(),
            devIp:'127.0.0.1',
            client: {告警值:'disconnect'}
        },
    ]
};
$.post('/api/monitor/alarms', data, function(data, textStatus, xhr) {
    /*optional stuff to do after success */
});
```