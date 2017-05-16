# 删除告警

<font face="Droid Sans Mono,monospace" size="5">
<font color="#ed3b00"><b>DELETE</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/alarm/[<font color="#571800">id</font>]
</font>


### Path parameters
name | type | description
:-----:|:------:|:------------:
id   |string|推送方的告警的唯一标识

### Body
无内容


### Returns
异步操作，返回结果仅表示推送到3D机房系统后端

Content-Type: application/json

```
{value:"success", error:null}
```

### Demo
>以增加告警章节demo中添加的编号为123的告警为例

```

$.ajax({
    url: '/api/monitor/alarm/123',
    type: 'DELETE',
    success: function(result) {
        // Do something with the result
    }
});
```