# AboutHTTP
This project is about HTTP learning
// 1使用request接收请求数据额
//2.使用response发送响应数据
//2.1设置状态行
//该数据由tomcat自动设置
//2.2设置消息头
response.setContentType("text/html");
//2.3设置实体内容
PrintWriter out=res.getWriter();
out,println("<h1>helloworld</h1>");
out.close();
