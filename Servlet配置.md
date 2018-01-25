### 此参数可以被多个Servlet公用。
有时候需要给Servlet预置一些参数，如每页显示条目数（size）。
可以自己写配置文件（properties/xml），自己写工具读取。
也可以使用ServletConfig和ServletContext，他们都能够自动获取web,xml中预置的参数，传给Servlet。
#### 在tomcat启动时，它会自动创建ServletContext对象，并且调用该对象的方法自动读取参数

    <context-param>
    <param-name></param-name>
    <param-value><param-value>
    </context-param>
