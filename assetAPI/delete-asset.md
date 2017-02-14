# 删除资产

<font face="Droid Sans Mono,monospace" size="5">
<font color="#ed3b00"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/asset/[<font color="#571800">id</font>]
</font>


### Path parameters
name | type | description
:-----:|:------:|:------------:
id   |string|资产的唯一标识

### Body
无内容


### Returns
Content-Type: application/json

```
{value:"success", error:''}
```

### Demo
>以增加资产章节demo中添加的编号为b8r201c04r23e01的资产为例

```

$.ajax({
    url: '/api/monitor/asset/b8r201c04r23e01',
    type: 'DELETE',
    success: function(result) {
        
    }
});
```
