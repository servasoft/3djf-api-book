# 删除临时资产


<font face="Droid Sans Mono,monospace" size="5">
<font color="#ed3b00"><b>DELETE</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/tempAsset/[<font color="#571800">id</font>]
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
{value:删除的资产对象(JSON格式), error:null或原因}
```

### Demo
>以增加资产章节demo中添加的编号为b8r201c04r23e01的资产为例

```

$.ajax({
    url: '/api/monitor/tempAsset/b8r201c04r23e01',
    type: 'DELETE',
    success: function(result) {
        
    }
});
```
