# 状态管理
### 软件中经常有一些前后连续的业务，如登陆时记录账号，打开主页、查询页时显示此账号。要想记录这样的数据，需要满足以下规则：
#### 这份数据在多个Serlvet之间共用；
#### 这份数据在多个请求之间共用；
#### 每个浏览器都有一份这样的数据，要区分浏览器；
### Cookie和Session就可以满足上述规则来存数据.
## Cookie:数据存在浏览器上，服务器压力小，但容易被篡改。
## Session：数据存到服务器上，服务器压力大，但不会被篡改。 
## Cookie的限制
##### cookie可以被用户禁止
##### cookie会将状态保存在浏览器端，不安全。对于敏感数据，需要加密后使用cookie来保存
##### cookie只能保存少量的数据，大约4kb左右
##### cookie的个数是有限制的
##### cookie只能保存字符串
## Session
    <!-- 用EL从cookie中取值:cookie.key.value
      其中key是变化的，而cookie.adminCode.value固定不变。-->
    <%--<span>${cookie.adminCode.value}</span>--%>
    <!--也可以用EL从session中取值，EL默认的取值范围
        分别是page、request、session、application-->
### 如何使用Session绑定对象
#### 绑定对象
    void Session.setAttribute(String name,Object,object)
#### 获取绑定对象
    Object Session.getAttribute(String name)
#### 移除绑定对象
    void Session .removeAttribute(String name)
#### 注：getAttribute方法的返回值是Object类型，在去除数据时要对其进行数据类型转换，且必须与我们存入的数据类型一致 
### 什么是Session超时
#### Web服务器会将空闲时间过长的Session对象删除掉，以节省服务器内存空间资源
#### web服务器缺省的超时时间限制：一般是30分钟
### 荣国修改tomcat中 conf/web.xml文件的设置
    <session-config>
        <session-timeout>30</session-timeout>
    </session-config>
### 浏览器 禁用Cookie的后果
#### 如果浏览器禁用Cookie,Session还能用吗？
#### 答案:不能，但有其他的解决方案
#### 服务器在默认情况下，会使用Cookie的方式将SessionId发送给浏览器，如果用户禁止Cookie，则SessuibId不会被浏览器保存，此时服务器可以使用如URL重写这样的方式来发送SessionId
### 如何删除Session对象
#### 立即删除Session对象：
    Session.invalidate()
### Session的优缺点
