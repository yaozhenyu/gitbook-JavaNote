# JWT {#jwt}

JWT由三部分组成

* Header
* Payload
* Signature

完整的JWT看起来是这种格式 xxxxx.yyyyy.zzzzz

## Header {#header}

header分两部分：token类型，hash加密算法（HMAC SHA256或RSA） 例如

```js
{ 
  "alg": "HS256",
  "typ": "JWT"
}
```

然后JSON经过Base64Url加密成为JWT的第个部分

## Payload {#payload}

payload包含claims，它有三种claims

* Registered claims: 包括iss \(issuer\), exp \(expiration time\), sub \(subject\), aud \(audience\), and others.
* Public claims:
* Private claims:

claims名字长度为三个字符  
例如

```js
{  
  "sub": "1234567890",
  "name": "John Doe",  
  "admin": true
}
```

payload经过Base64Url加密成为JWT的第二个部分

Header,Payload对所有人都是可见的，因此不要把未加密的敏感信息放到这两部分中。

## Signature {#signature}

要生成签名，必须获得加密后的Header,Payload和一个secret  
如果你想用HMAC SHA256 生成签名，方法如下

```js
HMACSHA256( 
 base64UrlEncode(header) + "." +
 base64UrlEncode(payload),
 secret)
```

JWT最终的形式是三个Base64-URL字符串，通过`.`号连接。

如何使用：  
一般是在请求头里加入`Authorization`并加上Bearer标注

```js
fetch('api/user/1',{
    headers: {
        'Authorization': 'Bearer ' + token
    }
})
```

Java库  
maven: com.auth0 / java-jwt / 3.0.1

