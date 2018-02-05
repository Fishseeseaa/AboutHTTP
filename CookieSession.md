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
