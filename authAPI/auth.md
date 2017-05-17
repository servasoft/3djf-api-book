# 认证

<font face="Droid Sans Mono,monospace" size="5">
<font color="#003bed"><b>POST</b></font> <font color="#888">http://{serverhost:serverport}</font>/api/monitor/auth
</font>

### Body
>用户名和密码

Accept: application/json

```
{"username":"","password":""}
```

### Returns

Content-Type: application/json

```
//成功
{"access_token":""}

//失败
{error:"失败原因"}
```