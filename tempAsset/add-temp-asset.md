# 增加临时资产


<font face="Droid Sans Mono,monospace" size="5">
<font color="#003bed"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/tempAsset
</font>


### Body
>一个或多个需要同步到系统中的资产实例

Accept: application/json

```
{
	data: [
        {
            id: string，required，编号,
            name : string，required，名称,
            description: string，描述,
            location: int, 给设备使用，描述设备所在的U位,
            parentId: string，父对象，给设备使用,
            height: int，给设备使用，表示设备所占的U数，
            extend: {}，扩展的字段，这些扩展字段最终将存到对应的Category的扩展表中
        }
    ]
}
```

### Returns

Content-Type: application/json

添加成功

```
{
	value: 添加的资产对象(JSON格式),
	error: null
}
```
添加失败

```
{
	value: "fail", 
	error: "原因",
	item: 错误的资产对象，但是不一定会有，只有在添加资产做验证不通过时有值
}
```

### Demo

```
var data = {
	module: "PEMS", 
	data: [
        {
            id: 'b8r201c04r23e01',
            name: 'b8r201c04r23e01',
            extend: {
            		ipAddr: '192.168.1.11',
            		brand: '华为'
            }
        }
    ]
};
$.post('/api/monitor/tempAsset', data, function(data, textStatus, xhr) {
    /*optional stuff to do after success */
});
```