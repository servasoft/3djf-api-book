# 告警API
>告警API包含：增加、更新、删除、查询。模拟需求场景，对4种API进行说明。


需求场景：编号为rack84_E01设备，可能产生三种告警：温度告警，网络告警，物理告警

###告警字段列表
<style>
table th:nth-child(3) {
    min-width: 30px;
}
</style>

字段 | 类型 | 必需 | 描述
:-----|:------:|:------------:|:------------
realId   |string| 是 |告警的唯一标识，与接口中alarmID对应
dataId |string| 是 |发生告警的设备编号，与接口中deviceID对应
alarmTypeId   |string| 是 |对应告警类型中的编号，参考告警类型模块，与接口中alarmType对应
level   |string| 是 |对应告警级别中的编号，参考告警级别模块
devIp   |string|  |发生告警的IP
time   |date|  |告警发生时间
ackTime   |date|  |告警确认时间
ackNotice   |string| |确认告警时备注
description   |string|  |描述
client   |Object|  |扩展的字段
