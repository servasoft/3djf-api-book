# 鉴权
>系统的安全性，数据的安全一直是用户关心的问题。由于3D可视化系统主要负责的是呈现，并多在内网中使用，所以这部分一直没有开放出来。最近有客户提到，就把这块慢慢完善起来。

接口部分使用了JWT(JSON Web Token)认证机制，在访问接口之前，需要先认证获取token（参考认证章节），并在之后的所有的接口访问中带上这个token，为了获得最大的可扩展性，我们允许客户端使用一下3个方法附加我们的token：作为请求链接（query)的参数，作为主体的参数（body），和作为请求头（Header）的参数。前两种参数名为access-token，最后一个，将使用Header x-access-token。

如果没有认证，在访问接口的时候会返回：

```
{"error": "must be authorized"}
```

如果认证过期，在访问接口的时候会返回：

```
{"error": "jwt expired"}
```

服务器并没有做refresh token, 所以当token过期后需要再次认证


接口的鉴权默认并没有启用，但是在后端提供开关，congfig.js中auth属性，如果需要启用，将auth值设为true

###总结使用方法：
1. 在后端config.js中将auth值设为true, 开启鉴权开关
2. 通过认证接口，认证并获取token
3. 访问其他接口并带上token，携带token三种方式，query、body、Header（x-access-token）

