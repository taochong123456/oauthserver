<p align="center">
<a href="http://www.oracle.com/technetwork/java/javase/overview/index.html"><img src="https://img.shields.io/badge/language-java%208.0-orange.svg"></a>
<a href="https://www.jetbrains.com/idea/"><img src="https://img.shields.io/badge/platform-jetbrains-green.svg"></a>
<a href="http://projects.spring.io/spring-boot/"><img src="https://img.shields.io/badge/SpringBoot-1.5.21-990066.svg"></a>
<img src="https://img.shields.io/badge/Database-MySQL%7COracle%7CPostgreSQL-brightgreen.svg">
<img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg">
<img src="https://img.shields.io/badge/release-1.3.0-brightgreen.svg">

</p>

# oauthserver

国内用户可访问[gitee](https://gitee.com/jeesun/oauthserver)，代码和[github](https://github.com/jeesun/oauthserver)同步。

## 简介
oauthserver是一个基于Spring Boot Oauth2的完整的独立的Oauth2 Server微服务。项目的目的是，仅仅需要创建相关数据表，修改数据库的连接信息，你就可以得到一个Oauth2 Server微服务。  
为了开发方便，项目拆分成三个模块，api、web和common：
1. api运行在8181端口，api模块是提供api服务的，主要是oauth token等其他业务接口；
2. web运行在8182端口，是一个简单的管理后台；
3. common是公共工具模块。

支持的关系型数据库：
- MySQL
- Oracle
- PostgreSQL

## 功能概览
### api
1. Oauth token服务，支持3种登录方式：手机号+验证码、手机号+密码、邮箱+密码（使用流程参考[oauth接口调用示例](tutorial/api.md)，如果你需要使用短信验证码服务，请前往阿里大于和云之讯短信服务购买短信验证码服务，并在application.properties中配置相关参数）；
2. 短信验证码服务，支持三种：阿里大于、腾讯云短信服务、云之讯短信服务；
3. 微信、支付宝支付；
4. 七牛云存储；
5. 代码生成器。
### common
公共工具类模块
### web
1. 主页
   1. 了解OauthServer
   2. 新闻管理
   3. 订单管理
2. 系统管理
   1. 定时任务
   2. 菜单管理
   3. 用户管理
   4. 权限管理
   5. 数据字典
3. 系统工具
   1. 代码生成
   2. swagger
   3. druid
   4. 日志管理

## 更新日志
### 2.0.20190521-alpha
1. 更新角色管理页面；
2. 解决角色已拥有页面权限，页面依然不显示的bug，需要重新保存一次权限。

### 2.0.20190517-alpha
1. 修复quartz定时任务bug；
2. 移除api模块的代码生成器，统一使用web模块的生成器，代码生成器位置允许选择common模块；
3. 省市区信息添加缓存；
4. 重写home页面；
5. 使用java8时间类型代替Date类型，并解决序列化问题；
6. 合并model、service、serviceImpl、repository、mapper到common模块；
7. 增加登录失败原因提示；
8. Spring Boot 1.5.20->1.5.21；
9. 动态计算iframe高度；
10. 其他bug修复。

### 2.0.20190506-alpha
1. 新增了很多功能；
2. 修复了很多bug；
3. 管理端页面重构，使用Vue + Element UI代替JQuery + EasyUI。

**更多历史更新日志查看[CHANGE_LOG.md](tutorial/CHANGE_LOG.md)**

## 使用流程
### 准备
IntelliJ IDEA或Eclipse请先安装lombok插件。
- IntelliJ IDEA安装请参考[https://projectlombok.org/setup/intellij](https://projectlombok.org/setup/intellij)；
- Eclipse安装请参考[https://projectlombok.org/setup/eclipse](https://projectlombok.org/setup/eclipse)。
### 1. 安装jar
有部分自建jar在中央仓库是没有的，需要使用`mvn install`安装到本地。执行“需要安装的jars”文件夹下的`install.bat`安装。
### 2. 建表
- MySQL  
请执行`schema-mysql.sql`，完成数据表的创建和测试数据的导入。之后，请执行SQL增量更新目录下的增量更新SQL。
- Oracle  
请执行`schema-oracle.sql`，完成数据表的创建和测试数据的导入。之后，请执行SQL增量更新目录下的增量更新SQL。
- PostgreSQL  
请执行`schema-postgresql.sql`，完成数据表的创建和测试数据的导入。之后，请执行SQL增量更新目录下的增量更新SQL。
### 3. 修改数据库连接信息
- MySQL  
连接信息在`application-mysql.yml`里。修改完数据库连接信息后，还需要设置`application-common.yml`的`spring.profiles.active=mysql`。    
- Oracle  
连接信息在`application-oracle.yml`里。修改完数据库连接信息后，还需要设置`application-common.yml`的`spring.profiles.active=oracle`。  
- PostgreSQL  
连接信息在`application-pg.yml`里。修改完数据库连接信息后，还需要设置`application-common.yml`的`spring.profiles.active=pg`。  
### 4. 运行
现在，一切已准备就绪。运行项目，当程序成功启动时，即表明你已配置成功。

## api测试
[oauth接口调用示例](tutorial/api.md)

## 管理端页面
测试账号：手机号18800000000，密码1234567890c
![登录页](tutorial/screenshots/login.png)

![管理端主页](tutorial/screenshots/index.png)

## 分享交流
在使用过程中有任何疑问或者问题，可以微信扫码询问。  
![author](tutorial/screenshots/author.jpg)