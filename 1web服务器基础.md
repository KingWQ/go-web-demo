### 一：go语言中的web server
1. net/http包，通过http包可以搭建起来一个可以运行的web服务
2. 同时使用这个包很便利对web路由、静态文件、模版、cookie等数据进行操作

### 二：web server几个重要概念
1. Request 用户请求的信息，用来解析用户的请求信息，包括post,get,cookie,url等信息
2. Response 服务器需要返回给客户端的信息
3. Conn 用户的每次请求链接
4. Handler 处理请求和生成返回信息的处理逻辑

### 三：web server执行流程
1. 创建listen socket, 监听指定的端口，等待客户端请求到来
2. 监听并接收客户端的请求，接下来通过client socket与客户端通信
3. 处理客户端的请求，首先从client socket读取http请求的协议头，如果是post方法，还可能要读取客户端提交的数据
4. 然后交给相应的handler处理请求，handler处理完毕准备好客户端需要的数据，通过client socket写给客户端

### 四：go语言实现web server的关键点
1. 通过http.ListenAndServe(":800",nil) 监听请求
2. 通过http.HandlerFunc("/", home) 处理请求
3. 通过http.ResponseWriter() 输出响应结果