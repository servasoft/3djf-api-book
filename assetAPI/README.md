# 资产API

对于资产的管理，大部分的资产数据在初始化的系统的时候，会将资产数据整理导入系统。对于系统上线后，对于少量的资产操作可以使用资产API，通过资产API对资产进行操作可以实时同步到前端浏览器


###资产字段列表
<style>
table th:nth-child(3) {
    min-width: 30px;
}
</style>

| 字段 | 类型 | 必需 | 描述 |
|:-----|:------:|:-----:|:------------|
|id   |string| 是 |编号|
|name |string| 是 |名称|
|description   |string|  |描述|
|position   |string|  |参考附录一：location、position、空间规划|
|position2d   |string|  |2D中的物理坐标|
|rotation   |string|  |表示资产对象的旋转值，{x:0,y:0,z:0}，x、y、z分别表示三个方向上的旋转角度|
|location   |string|  |参考附录一：location、position、空间规划|
|parentId   |string| 是 |父对象，例如设备的的父对象为机柜|
|dataTypeId   |string| 是 |资产模型编号|
|weight   |int|  |资产重量|
