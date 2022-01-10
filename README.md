# Java-Web项目: 在线考试管理系统
## 前瞻: 
本系统使用了Servlet, JSP, JDBC, JavaScript --> 从服务端向浏览器过渡<br>
这个系统使用的Http服务器是Tomcat, 使用的数据库服务器是MySQL<br>
###  开发流程
1. 首先根据互联网通信特征，画出流程图
2. 根据流程图分析开发功能，然后进行开发与测试
## 1. 项目主要功能
系统大体由【学员信息管理】，【试题信息管理】，【在线考试管理】三个模块组成
## 2. 项目特色介绍
1. 使用监听器模拟了数据库连接池功能，节省Connection创建与销毁时间，提高执行速度，增加QPS(服务器在单位时间内接受的访问量) <br>
2. 使用过滤器，防止用户恶意登录行为，提高系统安全性

## 3. 项目结构具体介绍
1. DAO层: 使用JDBC对数据库的直接操作,包含增删改查
2. Controller层: 存放所有Servlet, 用于前后端交互
3. Util类: 存放JDBC实体类，用于初始化
4. Entity类: 包含两个实体类: 学生与问题
5. Web框架下文件: 包含HTML与jsp文件。HTML文件用于前端界面渲染, javascipt动态界面; jsp用于前后端交互以及动态运行java文件

## 4. 页面分析

### 1. 登陆页面
![image](https://user-images.githubusercontent.com/66471809/148714074-2491415f-dd62-4b84-ade2-5d22919757a0.png)
```HTML
<form action="/myWeb/login" method="post">
                  <table border="2">
                      <tr>
                          <td>登录名</td>
                          <td><input type="text" name="userName"/></td>
                      </tr>
                      <tr>
                          <td>密码</td>
                          <td><input type="password" name="password"/></td>
                      </tr>
                      <tr>
                          <td><input type="submit" value="登录"/></td>
                          <td><input type="reset" /></td>
                      </tr>
                  </table>

              </form>
```
特征1: **action="/myWeb/login"** 意味着用户点击提交按钮后会出发LoginServlet, 与后端交互 <br/>
特征2: **method="post"** 访问方式为post,更加安全，防止用户账户信息暴露在地址栏以及被浏览器缓存<br/>

### 2. 主页面index.html
![image](https://user-images.githubusercontent.com/66471809/148714395-7733b6cc-a9ed-43f5-a447-320052d30a1c.png)
```HTML
<frameset rows="15%,85%">
    <frame name="top" src="/myWeb/top.html"/>
    <frameset cols="15%,85%">
        <frame name="left" src="/myWeb/left.html"/>
        <frame name="right">
    </frameset>
</frameset>
</html>
```
主页面由两部分组成，left.html && top.html <br/>


### 3. 左侧功能栏

左侧功能栏集合了本项目用到的所有主要功能, 是项目的核心所在, 共有3大功能, 用户信息管理, 试题信息管理, 考试管理

```HTML
<body>
    <ul>
        <li>用户信息管理
             <ol>
                 <li><a href="/myWeb/user_Add.html" target="right">用户信息注册</a></li>
                 <li><a href="/myWeb/user/find" target="right">用户信息查询</a></li>
             </ol>
        </li>
        <li>试题信息管理
            <ol>
                <li><a href="/myWeb/question_Add.html" target="right">试题信息注册</a></li>
                <li><a href="/myWeb/question/find" target="right">试题信息查询</a></li>
            </ol>
        </li>
        <li>考试管理
            <ol>
                <li><a href="/myWeb/question/rand" target="right">参加考试</a></li>
                <li><a href="/myWeb/question/find" target="right">试题信息查询</a></li>
            </ol>
        </li>
    </ul>
</body>
```
[用户信息注册] (https://github.com/E0253740/Java-Web-Project/blob/main/用户信息注册.md)

