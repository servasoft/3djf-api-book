# 更新资产

<font face="Droid Sans Mono,monospace" size="5">
<font color="#00b2ed"><b>PUT</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/asset/[<font color="#005977">id</font>]
</font>

### Path parameters
name | type | description
:-----:|:------:|:------------:
id   |string|资产的唯一标识

### Body
>要更新的告警属性，通常在确认告警或修改告警状态时，通过更新方法

Accept: application/json

```
{
    name : string，required，名称,
    description: string，描述,
    position: string，参考附录一：location、position、空间规划,
    position2d: string，2D中的物理坐标,
    rotation: string，表示资产对象的旋转值，{x:0,y:0,z:0}，x、y、z分别表示三个方向上的旋转角度,
    location: string，参考附录一：location、position、空间规划,
    parentId: string，required，父对象，例如设备的的父对象为机柜,
    dataTypeId: string，required，资产模型编号,
    weight: int，资产重量
}
```

### Returns

Content-Type: application/json

```
{value:"success", error:''}
```

### Demo
>以增加资产章节demo中添加的编号为b8r201c04r23e01的资产为例

```
var data = {
    name: 'b8r201c04r23e01-update',
    description: 'b8r201c04r23e01-update',
    location: {"y":10,"z":"pos_pos"},
    parentId: 'b8r201c04r23',
    dataTypeId: 'equipment2'
}
$.ajax({
    url: '/api/monitor/asset/b8r201c04r23e01',
    type: 'PUT',
    data: data,
    success: function(result) {
      // Do something with the result
    }
});
```
