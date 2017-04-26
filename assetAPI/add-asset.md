# 增加资产

<font face="Droid Sans Mono,monospace" size="5">
<font color="#003bed"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/asset
</font>


### Body
>一个或多个资产实例

Accept: application/json

```
{
	data: [
        {
            id: string，required，编号,
            name : string，required，名称,
            description: string，描述,
            position: string，物理坐标，值是{x:0,y:0,z:0}的JSON字符串，参考附录一：location、position、空间规划,
            position2d: string，2D中的物理坐标,
            rotation: string，表示资产对象的旋转值，{x:0,y:0,z:0}，x、y、z分别表示三个方向上的旋转角度,
            location: string，逻辑坐标，值是{x:0,y:0,z:0}的JSON字符串，，参考附录一：location、position、空间规划,
            parentId: string，required，父对象，例如设备的的父对象为机柜,
            dataTypeId: string，required，资产模型编号,
            weight: int，资产重量，
            customField: {}，资产的扩展字段，扩展字段是存在根据资产分类创建的扩展表中。customField中内容为扩展表中的字段
        }
    ]
}
```

### Returns

Content-Type: application/json

```
{value: 添加的资产对象(JSON格式), error:''}
```

### Demo

```
var data = {
	module: "PEMS", 
	data: [
        {
            id: 'b8r201c04r23e01',
            name: 'b8r201c04r23e01',
            location: {"y":28,"z":"pos_pos"},
            parentId: 'b8r201c04r23',
            dataTypeId: 'equipment2',
            customField: {
            		ipAddr: '192.168.1.11',
            		brand: '华为'
            }
        }
    ]
};
$.post('/api/monitor/asset', data, function(data, textStatus, xhr) {
    /*optional stuff to do after success */
});
```