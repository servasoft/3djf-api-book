# 添加湿度监控
先描述下3D机房系统的流程，当显示湿度信息的时候，

1. 找到当前场景中资产对象
2. 找到资产对象的传感器，并且传感器的类型为湿度，资产对象跟传感器为父子关系
3. 根据传感器的ID找到其关联关系，将关联关系中需要的业务对象及其属性组织为订阅订单
4. 将订阅订单发送服务器端订阅数据，等待服务器推送
5. 服务器响应后，根据缓存反向查寻，定位传感器，并更新传感器的值

综上所述，分析得知需要添加的数据有：

1.	资产对象

	湿度是房间的属性，创建一个房间的资产对象
	
	```
	{
		id:"f2-r1",
		description:"二楼房间一",	
		parentId:"floor2",
		dataTypeId:"area01"
	}
	```
2.	传感器
	
	添加一个湿度传感器
	
	```
	{
		id:"humidity01",
		description:"湿度传感器",
		parentId:"f2-r1",
		type:"humidity",
		position:{x:3,y:100,z:300}
	}
	```
3.	业务对象及其属性
	
	添加一个湿度传感器的业务对象
	
	```
	{
		id:"hum01",
		description:"湿度传感器",
		type:"SRH"
	}
	```
	
	添加业务对象属性

	```
	{
		type:"SRH",
		property:"humidity",
		valueType:"number",
		unit:"%rh"
	}
	```

4.	关联关系
	
	添加传感器与业务对象之间的关联关系
	
	```
	{
		id:"humidity01",
		relations:"[{"bid":"hum01","property":"humidity"}]"
	}
	```
	
5. 第三方推送的JSON数据格式：
	
	```
	{
		module:"PEMS",
		data:{
			"hum01":{
				"humidity":60
			}
		}
	}
	```
