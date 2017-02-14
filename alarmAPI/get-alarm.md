## 获取告警

<font face="Droid Sans Mono,monospace" size="5">
<font color="#61C000"><b>GET</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/alarm/[<font color="#005e2f">id</font>]
</font>

### Path parameters
name | type | description
:-----:|:------:|:------------:
id   |string|推送方的告警的唯一标识

### Query parameters
<table>
    <tr>
        <td><b>名称</b></td>
        <td><b>类型</b></td>
        <td><b>描述</b></td>
    </tr>
    <tr align="center">
        <td colspan="3">无数据</td>
    </tr>
</table>

### Body
无内容

### Returns
异步操作，返回不是真实状态