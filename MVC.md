# MVC是经典的的设计模式，是代码的分层思想：
### 1.Model：业务层，用来处理业务/
### 2View：视图层，用来显示数据。
### 3.Controller：控制层，负责控制（调度）流程，是M和V的桥梁。其目的是要降低代码之间的耦合度，便于团队开发和维护。

# Bean属性
     //对象的属性
     private String userName;

     //Bean属性就是get/set方法后的字符串。
     //当前案例中bean属性就是name。
     public void setName(String name)
     {
        this.userName=name;
     }
     public String getName()
     {
        return this.userName;
     }

# EL表达式
## EL表达式的作用
### EL表达式作用可分为以下几类:
##### 访问Bean属性
##### 
#####
