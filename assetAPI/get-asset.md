# 获取资产


<font face="Droid Sans Mono,monospace" size="5">
<font color="#61C000"><b>GET</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/asset
</font>


### Query parameters
name | type | description
:-----:|:------:|:------------:
id   |string|资产的唯一标识
name   |string|名称
description   |string| 描述
parentId   |string|父对象，例如设备的的父对象为机柜
dataTypeId   |string|资产模型编号
categoryId   |string|分类编号

### Body
无内容

### Returns
Content-Type: application/json

```
{value:{count:'查询结果条目数',rows:array}, error: null或原因}
```

array为数组，数组元素包含资产的所有字段，以及资产的所有扩展字段，由于扩展字段由资产分类来决定，所以资产的扩展字段不尽相同

### Demo

```

$.ajax({
    url: '/api/monitor/asset',
    data: {categoryId:'airConditioning',parentId:'r101'},
    type: 'GET',
    success: function(result) {
        console.log(result);
    }
});
```
