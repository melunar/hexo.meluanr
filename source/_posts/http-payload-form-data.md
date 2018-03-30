---
title: HTTP POST请求Request Payload和Form Data主体类型的区别
tags: [HTTP]
---

 
**看请求报文伪代码示例: **

```
GET:
Content-Type: application/json;charset=UTF-8
query string parameters: a=1&id=4120f5cb-3133-45f6-861e-91a6fb76d36b
```

```
POST:(非request body类型)
Content-Type:application/x-www-form-urlencoded
Form Data: loginName=hooy&password=MTIzNDU2&name=23&gender=0
```

```
POST:(request body类型)
Content-Type:application/json;charset=UTF-8
Request Payload:
{"id":"4769aa96-28c2-11e8-81c3-f80f41fae84e","abilities":[],"nodeTypes":["camera"]}
```
 

> 如果请求的Content-Type设置为application/x-www-form-urlencoded，那么这个Post请求被认为是HTTP POST表单请求，它的参数就是标准的querystring类型, 以key=value&key2=value2的形式发送和解析. 这也是之前post请求常用的方式, 毕竟表单提交的数据格式就是如此

> 其他情况如使用原生AJAX的POST请求如果不指定请求头Request Header，默认使用的Content-Type是text/plain;charset=UTF-8，参数出现在Request payload块, 参数也会以标准JSON的格式传输和解析。当然不同的框架有不同的默认方式, 具体接口形式可以调用相关headerSet方法来设置请求头.