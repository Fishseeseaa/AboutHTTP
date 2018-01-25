# Servlet的生命周期
## 什么是Servlet的生命周期
容器如何去创建Servlet对象，如何对其进行初始化处理，
如何调用其方法来处理请求，以及如何销毁该对象的整个过程。
## 分成那几段？
### 实例化
a什么是实例化？
容器调用Servlet的构造器，创建相应的对象
b什么时候实例化？
1情况:容器收到请求之后
2情况:容器启动之后，立即创建。

    <load-on-startup>1</load-on-startup>
参数值要求是一个大于等于0的整数，
参数越小，优先级越高（优先创建）
注：
容器只会创建一个实例
### 初始化
  a.什么是初始化
  容器调用servlet对象的init方法。该方法只会执行一次。
  b.GenericServlet的init方法是如何实现的
  将容器传递过来的ServletConfig对象保存下来，
  并且提供了一个获得该对象的方法(getServletConfig)
  c.如何实现自己的初始化处理逻辑
  只需要override GenericServlet提供的init()方法。
      ###关于init（）使用
      step1，配置
      <init-param>
        <param-name>company</param-name>
        <param-value>中国软件<param-value>
      </init-param>
      step2,读取
      String ServletConfig.getInitParamerter(String paramName)方法
### 就绪
a.什么是就绪
  容器调用Servlet对象的service方法来处理请求
b.HttpServlet的service方法是如何实现的
依据请求类型（get/post）调用对应的doXXX方法(doGet/doPost)。
 ###注：
 我们可以写一个servlet，继承HttpServlet，然后override doGet和doPost方法，
 或者也可以直接override service方法
 
### 销毁
  a.什么是销毁
    容器在删除servlet对象之前，会先调用该对象的destory方法
  b.该方法只会执行一次  
## 相关的几个接口和类
   1）Servlet接口
    init
    service
    destory
   2）GenericServlet抽象类
   实现了Servlet接口中的部分方法(init,destory)
   3）HttpServlet抽象类
   继承GenericServlet抽象类，实现了service方法
   
   
## 容器如恶化处理请求资源路径
比如，在浏览器地址栏输入

    http://ip：port/web04-3/abc.html
#### step1,容器依据应用名（"/web04-3"）找到应用所在的文件夹
#### step2,容器默认为调用的是一个servlet，去web。xml查找有没有一个和"/abc.html"匹配的servlet
   
