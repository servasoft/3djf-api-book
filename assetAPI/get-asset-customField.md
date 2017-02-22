## 获取资产及扩展字段

<font face="Droid Sans Mono,monospace" size="5">
<font color="#61C000"><b>GET</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/asset/customField
</font>


### Query parameters
<table>
    <tr>
        <th><b>名称</b></th>
        <th><b>类型</b></th>
        <th><b>描述</b></th>
    </tr>
    <tr align="center">
        <td>category</td>
        <td>string</td>
        <td>资产的分类，资产的扩展字段是根据资产分类来设置的，相同分类的资产的扩展字段相同。</td>
    </tr>
    <tr align="center">
        <td>assetProps</td>
        <td>JSON string</td>
        <td>资产的查询条件，包含：id、name、description、parent_id、data_type_id、business_type_id</td>
    </tr>
    <tr align="center">
        <td>customProps</td>
        <td>JSON string</td>
        <td>扩展字段的查询条件，能包含的查询条件为具体的扩展字段，例如扩展字段有ip字段，就可以将ip作为查询条件</td>
    </tr>
</table>

### Body
无内容

### Returns
Content-Type: application/json

```
{value: array, error:''}
```

array为数组，数组元素包含资产的所有字段，以及资产的所有扩展字段，由于扩展字段由资产分类来决定，所以资产的扩展字段不尽相同

### Demo
>以增加资产章节demo中添加的编号为b8r201c04r23e01的资产为例

```

$.ajax({
    url: '/api/monitor/asset/customField',
    data: {assetProps:JSON.stringify({id:'b8r201c04r23e01'})},
    type: 'GET',
    success: function(result) {
        console.log(result);
    }
});
```
