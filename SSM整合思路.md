#  SSM整合思路

##  搭建基本环境

1.  创建数据库和表
2.  创建Maven工程webapp
3.  修改pom文件，引入坐标依赖
4.  完善目录结构
5.  创建基础类domain、dao、service、controller



##  Spring 框架代码的编写

1.  创建配置文件，applicationContext.xml 配置文件

    -   引入约束
    -   开启注解扫描，将dao和service交给spring容器管理，略过controller

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xmlns:context="http://www.springframework.org/schema/context"
           xmlns:aop="http://www.springframework.org/schema/aop"
           xmlns:tx="http://www.springframework.org/schema/tx"
           xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/aop
       http://www.springframework.org/schema/aop/spring-aop.xsd
       http://www.springframework.org/schema/tx
       http://www.springframework.org/schema/tx/spring-tx.xsd">
    
        <!-- 开启注解扫描，处理service和dao，但是不需要处理 controller -->
        <context:component-scan base-package="cn.ideal">
            <!-- 配置哪些注解不扫描 -->
            <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
        </context:component-scan>
    
    </beans>
    ```

2.  添加注解，针对service



##  Spring MVC 框架代码的编写

1.  配置 Web.xml，配置servlet、filter、[listener]

    ```xml
    <!--配置前端控制器-->
    <servlet>
        <servlet-name>dispatcherServlet</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <!--加载springmvc.xml配置文件-->
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:springmvc.xml</param-value>
        </init-param>
        <!--启动服务器，创建该servlet-->
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>dispatcherServlet</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
    
    
    <!--配置过滤器，解决中文乱码-->
    <filter>
        <filter-name>characterEncodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>characterEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    ```

2.  创建 springmvc.xml 文件

    -   开启扫描，注解，还有解析视图的，以及防止 css js 等静态文件被过滤的

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
           xmlns:mvc="http://www.springframework.org/schema/mvc"
           xmlns:context="http://www.springframework.org/schema/context"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!--开启只对controller的扫描-->
        <context:component-scan base-package="cn.ideal">
            <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
        </context:component-scan>
    
        <!--配置视图解析器-->
        <bean id="org" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <!--JSP 目录-->
            <property name="prefix" value="/WEB-INF/pages/"/>
            <!--文件后缀-->
            <property name="suffix" value=".jsp"/>
        </bean>
    
        <!--不过滤静态资源-->
        <mvc:resources mapping="/css/**" location="/css/"/>
        <mvc:resources mapping="/images/**" location="/images/"/>
        <mvc:resources mapping="/js/**" location="/js/"/>
    
        <!--开启注解支持-->
        <mvc:annotation-driven/>
    </beans>
    ```

3.  执行测试

    -   创建控制层，`@Controller` `@RequestMapping`
    -   编写页面

    

    

##  Spring 整合 Spring MVC

1.  配置监听器和文件路径
2.  控制层调用业务层方法



##  MyBatis 框架代码编写

1.   创建 SqlMapConfig.xml，MyBatis 的主配置文件

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE configuration
            PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
            "http://mybatis.org/dtd/mybatis-3-config.dtd">
    
    <configuration>
        <environments default="mysql">
            <environment id="mysql">
                <transactionManager type="JDBC"></transactionManager>
                <dataSource type="POOLED">
                    <property name="driver" value="com.mysql.jdbc.Driver"/>
                    <property name="url" value="jdbc:mysql:///ssm"/>
                    <property name="username" value="root"/>
                    <property name="password" value="root99"/>
                </dataSource>
            </environment>
        </environments>
    
        <!--使用注解-->
        <mappers>
            <package name="cn.ideal"/>
        </mappers>
    </configuration>
    ```

2.  Dao 层代码编写

3.  测试 MyBatis





##  Spring 整合 MyBatis

1.  修改 applicationContext.xml

    -   将 SqlMapConﬁg.xml 配置文件中的内容配置到 applicationContext.xml 配置文件中去，MyBatis 就不再独立了，被整合到了 Spring中去了。
    -   在 resources 文件夹下创建了 config 的文件夹，然后创建了druid.properties文件吗，也就是将数据库例如用户名密码配置到了 properties 中，后期维护等就更加方便了，当然使用前需要像下面一样开始扫描 properties文件

    ```xml
    <!-- applicationContext.xml -->
    <!--扫描Resources中的相关properties文件-->
    <context:property-placeholder location="classpath:config/*.properties" ignore-unresolvable="true"/>
    
    <!--Spring 整合 MyBatis-->
    <!--配置数据库连接池-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <!-- 数据库基本信息配置 -->
        <property name="url" value="${druid.jdbc.url}" />
        <property name="username" value="${druid.jdbc.username}" />
        <property name="password" value="${druid.jdbc.password}" />
        <property name="driverClassName" value="${druid.jdbc.driver}" />
    </bean>
    
    <!--配置SqlSessionFactory工厂-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource"/>
    </bean>
    
    <!--配置AccountDao接口所在包-->
    <bean id="mapperScanner" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="cn.ideal.dao"/>
    </bean>
    
    
    
    
    <!-- druid.properties -->
    druid.jdbc.url=jdbc:mysql://localhost:3306/ssm
    druid.jdbc.driver=com.mysql.jdbc.Driver
    druid.jdbc.username=root
    druid.jdbc.password=root
    ```

2.  执行测试

    -   Dao 中添加 @Repository 注解
    -   在Service 中注入 Dao
    -   在Controller中注入 Service
    -   页面编写

3.  添加事务

    ```xml
    <!-- applicationContext.xml -->
    <!--配置Spring框架声明式事务管理-->
    <!--配置事务管理器-->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource" />
    </bean>
    
    <!--配置事务通知-->
    <tx:advice id="txAdvice" transaction-manager="transactionManager">
        <tx:attributes>
            <tx:method name="find*" read-only="true"/>
            <tx:method name="*" isolation="DEFAULT"/>
        </tx:attributes>
    </tx:advice>
    
    <!--配置AOP增强-->
    <aop:config>
        <aop:advisor advice-ref="txAdvice" pointcut="execution(* cn.ideal.service.impl.*ServiceImpl.*(..))"/>
    </aop:config>
    ```

    