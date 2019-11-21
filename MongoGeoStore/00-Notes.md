# Notes

[TOC]

## 一、spring boot各层之间的关系

 **spring boot 中分为为 controller层、service层、dao层、entity层。** 

- entity层：entity层和model层一样，存放的是实体类，属性值与数据库中的属性值保持一致。 实现set和get方法。

- dao层：即mapper层，对数据库进行持久化操作，他的方法是针对数据库操作的，基本用到的就是增删改查。它只是个接口，只有方法名字，具体实现在mapper.xml中。

- service层：业务层，存放业务逻辑处理，不直接对数据库进行操作，有接口和接口实现类，提供controller层调用的方法。

- controller层：控制器层，导入service层，调用service方法，controller通过接收前端传过来的参数进行业务操作，在返回一个指定的路径或者数据表。 

- 根目录：src.main.java

  -  工程启动类(Application.java) 
  -  实体类(domain) 
  -  数据访问层(Dao) 
  -  数据服务层(Service) 
  -  数据服务接口的实现(serviceImpl) 
  -  前端控制器(Controller) 
  -  工具类(utils) 
  -  常量接口类(constant) 
  -  配置信息类(config) 

- 资源文件：src.main.resources

  -  页面以及js/css/image等置于static文件夹下的各自文件下 
  -  使用模版相关页面等置于templates文件夹下的各自文件下 

-  一个基本 [sb2-web](https://blog.csdn.net/ubuntu64fan/article/details/80555915) 的目录结构如下： 

  ```
  ├── clean-run.sh
  ├── logs/            日志文件目录
  │   ├── sb2-web_test_2018-06-02_0959.0.log
  │   └── sb2-web_test.log
  |               
  ├── mvnw
  ├── mvnw.cmd
  ├── pom.xml
  ├── pysrc/            python 脚本目录
  ├── README.md
  ├── src/              源文件目录
  │   ├── main
  │   │   ├── java
  │   │   │   └── com
  │   │   │       └── mydomain
  │   │   │           ├── guru/          工具包目录
  │   │   │           │   ├── AccountValidator.java
  │   │   │           │   ├── DateConverter.java
  │   │   │           │   ├── JsonBeanUtil.java
  │   │   │           │   ......
  │   │   │           └── webapi/        web 接口目录
  │   │   │               ├── Application.java
  │   │   │               ├── config/    sb2 app 配置文件目录
  │   │   │               │   ├── CORSFilter.java
  │   │   │               │   ├── JwtAuthenticationEntryPoint.java
  │   │   │               │   ├── JwtAuthenticationFilter.java
  │   │   │               │   ├── WebMvcConfig.java
  │   │   │               │   ├── WebSecurityConfig.java
  │   │   │               │   └── ......
  │   │   │               ├── controller/   控制器目录
  │   │   │               │   ├── AuthenticationController.java
  │   │   │               │   ├── KaptchaController.java
  │   │   │               │   └── UserController.java
  │   │   │               ├── dao/          DAO 目录 (或者称为：repository)
  │   │   │               │   ├── KaptchaTokenDao.java
  │   │   │               │   └── UserDao.java
  │   │   │               ├── model/        Model 目录 （绑定数据表）
  │   │   │               │   ├── AuthToken.java
  │   │   │               │   ├── Constants.java
  │   │   │               │   ├── dto/      DTO 数据传输组件目录
  │   │   │               │   │   ├── KaptchaTokenDto.java
  │   │   │               │   │   └── UserDto.java
  │   │   │               │   ├── KaptchaToken.java
  │   │   │               │   ├── LoginUser.java
  │   │   │               │   ├── Role.java
  │   │   │               │   └── User.java
  │   │   │               └── service/      服务接口目录     
  │   │   │                   ├── impl/     服务接口实现目录
  │   │   │                   │   ├── KaptchaTokenServiceImpl.java
  │   │   │                   │   └── UserServiceImpl.java
  │   │   │                   ├── KaptchaTokenService.java
  │   │   │                   └── UserService.java
  │   │   └── resources/          资源总目录
  │   │       ├── application-dev.properties         开发配置
  │   │       ├── application-prod.properties        产品配置
  │   │       ├── application.properties             当前配置
  │   │       ├── application-test.properties        测试配置
  │   │       ├── kaptcha.properties                 图片验证码配置
  │   │       ├── logback-spring.xml                 日志文件配置
  │   │       ├── mysql-webapi.cresql                数据库创建语句
  │   │       └── templates/                         web 模板目录
  │   │       │   ├── user/
  │   │       │   ├── login.html
  │   │       │   ......
  │   │       ├── static/                            静态资源目录
  │   │              ├── bootstrap-4.1.0/
  │   │              │   ├── css/
  │   │              │   │   ├── bootstrap.css
  │   │              │   │   ├── bootstrap.css.map
  │   │              │   │   ├── bootstrap-grid.css
  │   │              │   │   ├── bootstrap-grid.css.map
  │   │              │   │   ├── bootstrap-grid.min.css
  │   │              │   │   ├── bootstrap-grid.min.css.map
  │   │              │   │   ├── bootstrap.min.css
  │   │              │   │   ├── bootstrap.min.css.map
  │   │              │   │   ├── bootstrap-reboot.css
  │   │              │   │   ├── bootstrap-reboot.css.map
  │   │              │   │   ├── bootstrap-reboot.min.css
  │   │              │   │   └── bootstrap-reboot.min.css.map
  │   │              │   └── js
  │   │              │       ├── bootstrap.bundle.js
  │   │              │       ├── bootstrap.bundle.js.map
  │   │              │       ├── bootstrap.bundle.min.js
  │   │              │       ├── bootstrap.bundle.min.js.map
  │   │              │       ├── bootstrap.js
  │   │              │       ├── bootstrap.js.map
  │   │              │       ├── bootstrap.min.js
  │   │              │       └── bootstrap.min.js.map
  │   │              ├── css
  │   │              │   └── common.css
  │   │              └── js
  │   │                  └── jquery
  │   │                      ├── jquery-1.11.2.min.js
  │   │                      └── jquery.min.map
  │   └── test
  │       └── java
  │           └── com
  │               └── yourdomain
  │                   └── webapi/
  │                       ├── ApplicationTests.java
  │                       └── UserDocumentationTests.java        自动文档生成测试
  └── update-build.sh       源文件自动版本更新脚本
  ————————————————
  版权声明：本文为CSDN博主「车斗」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/ubuntu64fan/article/details/80555915
  ```

  