# 推送指标数据

<font face="Droid Sans Mono,monospace" size="5">
<font color="#003bed"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/data
</font>


### Body
>一个或多个业务对象指标数据，deviceId作为一个对象，由其指标属性和值组成键值对

Accept: application/json

```
{
	module: string,模块名，保留字段，缺省值“PEMS”, 
	data: {
        'deviceId1': {
            "property1": value1,
            "property2": value2,
            "property3": value3,
            ... ...
        },
        'deviceId2': {
            "property1": value1,
            "property2": value2,
            "property3": value3,
            ... ...
        }
    }
}
```
* deviceId：指推送的业务对象唯一标识或资产对象唯一标识，确切的来说都称为业务对象唯一标示，只是在特定的情况直接将资产对象看作为业务对象。更多细节参考业务对象模块
	- property：指业务对象的属性，也就是指标属性，
	- value: 指对应的指标属性值

### Returns
异步操作，返回结果仅表示推送到3D机房系统后端

Content-Type: application/json

```
{value:"success", error: null}
```

### Demo

```
var getData = function(){
    return {
        module: "PEMS",
        data: {
            'b8f7th02': {
            	'humidity':Math.floor(Math.random()*10),
            	'temperature':Math.floor(Math.random()*10)
            },
            'b8r701c06hr01': {
            	'humidity':Math.floor(Math.random()*10),
            	'temperature':Math.floor(Math.random()*10),
              	"网络":{
                	"状态":"接通",
                	"速度":"100m/s"
              	}
            }

        }
    };
}
var data = getData();
$.post('api/monitor/data', data, function(data, textStatus, xhr) {
    /*optional stuff to do after success */
});
```