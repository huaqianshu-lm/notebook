# HTTP

## HTTP 请求信息和响应信息的格式

请求

![](E:\personal\notebook\HTTP_learn\images\请求报文格式.png)

- 请求行

  > GET /test.php HTTP/1.1 

  - GET --- 请求方法
  - /test.php --- 请求路径
  - HTTP/1.1  --- 所用的协议

- 请求头信息

  - 头信息结束后有一个空行，不管有没有主体信息，这个空行是必须要有的
  - content-length：主体信息的长度

- 请求主体信息（可以没有）

  

响应

![](E:\personal\notebook\HTTP_learn\images\响应信息.jpg)

- 响应行
  - 协议版本
  - 状态码
  - 状态文字
- 响应头信息
  - key:value
  - content-lenght:23 : 响应主体的长度
- 响应正文（主体信息）





请求方法

GET  POST PUT DELETE 等



状态码

200 

404

304

...

























