# Mysql

##  解压版安装

1. 配置环境变量，在管理员权限下打开命令行，输入 mysql

    提示`Can't connect to MySQL server on 'localhost'`则证明添加成功；

2. 创建配置文件 my.ini

    [mysql] 
default-character-set=utf8 
    

[mysqld] 
    character-set-server=utf8 
default-storage-engine=INNODB
    
3. 初始化mysql（注意，不要在安装文件下新建data文件夹，系统将自动生成）

    mysqld --initialize-insecure

4. 注册mysql服务

    mysqld -install

5. 启动服务

    net start mysql

6. 设置默认账户（管理员账户）

    mysqladmin -u root password 1234

7. 登入

    mysql -uroot p1234

    

##  SQL语句
1. 注释

    - // 单行
    - /* 多行  */
2. 分类

    - DDL 操作数据库和表
    - DML 增删改表中数据
    - DQL 查询表中数据
    - DCL 管理用户，授权

###   DDL

1. 数据库DDL

    - Create 创建数据库
        1. create database 数据库名； 创建数据库
        2. create database if not exists 数据库名；创建数据库先判断是否存在
        3. create database 数据库名 character set 字符集； 创建数据库并指定字符集
    - Retrieve 查询数据库
        1. show databases；查询所有数据库的名称
        2. show create database； 数据库名，查看数据库的创建语句
    - Update 修改
        1. alter database 数据库名 character set 字符集；修改字符集

    - Delete 删除
        1. drop database 数据库名; 删除数据库
        2. drop database if exists 数据库名; 删除数据库

    - 使用数据库

        1. select database(); 查询当前数据库名称
        2. use 数据库名; 使用数据库

2. 表DDL

    - Create 创建表

        1. create table 表名(

            ​		列名1 数据类型1，

            ​		列名2 数据类型2,

            ​		....,

            ​		列名n 数据类型n		//最后一列不加逗号

            );

        ```sql
        create table student(
        	id int,
            name varchar(20),
            age  int,
            score double(4,1),
            birthday date,
            insert_time timestamp
        );
        ```
        
        2. 复制表
            create table 表名 like 被复制的表名

    - Retrieve 查询表

        1. show tables；查询数据库中所有表
        2. desc 表名； 查询表结构
        3. show create table 表名； 查询表结构

    - Update 修改

        1. alter table 表名 character set 字符集；修改表的字符集
        2. alter table 表名 add 列名 数据类型；加列
        3. alter table 表名 change 列名  新列名 新数据类型；修改列
        4. alter table 表名 modify 列名 新数据类型；修改列
        5. alter table 表名 drop 列名 新数据类型；删除列

    - Delete 删除

        1. drop table 表名;   删除表
        2. drop table  if exists 表名;   删除表，先判断表是否存在

    - 数据类型

        1. 整数类型：int
        2. 小数类型：double（5,2）5位小数，小数点后保留2位
        3. 日期类型：date，只包含年月日，yyyy-MM-dd
        4. 时间类型：datetime，包含年月日时分秒, yyyy-MM-dd HH:mm:ss
        5. 时间戳：timestamp，包含年月日时分秒, yyyy-MM-dd HH:mm:ss，不需要赋值，由系统直接指定
        6. 字符串类型：varchar(20)， 指定最长20个字符
        7. BLOB：存储大型数据，如电影
        8. CLOB：存储大型数据，如电影

3. SQLyog图形化的数据库工具

###   DML

1. 添加数据

    - insert into 表名 （列名1，列名2） values（值1，值2);

        - 列名与值要一一对应

        - 如不指定列名，默认给所有列添加值

            insert into 表名  values（值1，值2);

        - 除了数字类型，其他类型需要加引号（单双皆可），比如日期类型"1999-11-11"

2. 删除数据

    - delete from  表名 where 条件;

        - 如果不加条件，默认删除所有

        - truncate table 表名;  删除表，然后再创建一个一模一样的空表（注意与drop的区别）

            推荐使用，效率更高

3. 修改数据
    - update 表名 set 列名=值,列名=值  where 条件;
        - 如果不加条件，默认修改所有

###   DQL

select * from 表名;  查询所有

- select语法

    select

    ​			字段列表

    from

    ​			表名列表

    where

    ​			条件列表

    group by

    ​			分组字段

    having

    ​			分组后的条件

    order by

    ​			排序

    limit

    ​			分页限定

    ;

1. 基础查询

    - 多字段查询

        - select 字段1,字段2... from 表名
    - 去除重复，distinct 
        - select distinct 字段名 from 表名
    - 运算
        - select math, english, math+english from student;
            - 计算学生表中数学英语成绩总分
        - select math, english, math+ifnull(english，0) from student;
            - 如果有null参与的运算，结果都为null。
            - ifnull(english，0) ,如果英语成绩为null，指定为0
        - select math, english, math+ifnull(english,0) as total from student;
            - as total 为字段起别名
    
2. 条件查询 
    - where子句后跟条件
    - 运算符
        - ">, <, >=, <=, =, <> "
        - BETWEEN AND
        - IN    字段 IN（值1，值2，值3）;
        - LIKE   字段 LIKE '马%' 
            - _ 匹配一个字符
            - % 匹配任意多个字符
        - IS NULL    判断是否为NULL
        - IS NULL
        - AND &&, OR ||,  NOT !
    
3. 排序

    - order by 
        - order by 排序字段1 排序方式1 ，  排序字段2 排序方式2...
    - 排序方式
        - ASC 升序（默认）
        - DESC 降序
    - 注意：
        - 如果有多个排序条件，则当前边的条件值一样时，才会判断第二条件。

4. 聚合函数：将一列数据作为一个整体，进行纵向的计算。

    1. count，计算个数，

        select count(字段) from tableName；

        或者使用ifnull(字段，0)

    2. max，计算最大值

    3. min：

    4. sum：求和

    5. avg：平均值

        注意：

        - 会排除NULL值，一般选非空列
        - select count(字段) from tableName；
        - 或者使用ifnull(字段，0)

5. 分组: group by

    - 分组之后查询的字段：分组字段、聚合函数

        ```sql
        SELECT sex, AVG(math) FROM student3 GROUP BY sex;
        SELECT sex, AVG(math),COUNT(id) FROM student3 GROUP BY sex;
        ```

    - 限定分组条件

        ```sql
        SELECT sex, AVG(math),COUNT(id) FROM student3 WHERE math > 70 GROUP BY sex;
        SELECT sex, AVG(math),COUNT(id) FROM student3 WHERE math > 70 GROUP BY sex HAVING COUNT(id)>2;
        SELECT sex, AVG(math),COUNT(id) AS 人数 FROM student3 WHERE math > 70 GROUP BY sex HAVING 人数>2;--起别名
        ```

        where 和 having 的区别

        1. where 在分组之前进行限定，如果不满足条件，则不参与分组。having在分组之后进行限定，如果不满足结果，则不会被查询出来
        2. where 后不可以跟聚合函数，having可以进行聚合函数的判断。

6. 分页：limit

    - 语法：limit 开始的索引,每页查询的条数;

    - 公式：开始的索引 = （当前的页码 - 1） * 每页显示的条数 

         -- 每页显示3条记录 

        ```sql
        SELECT * FROM student LIMIT 0,3; -- 第1页
        SELECT * FROM student LIMIT 3,3; -- 第2页
        SELECT * FROM student LIMIT 6,3; -- 第3页
        ```

    - limit 是一个MySQL"方言"
###   约束

- 概念： 对表中的数据进行限定，保证数据的正确性、有效性和完整性。

-  分类：

    1. 主键约束：primary key
    2. 非空约束：not null
    3. 唯一约束：unique
    4. 外键约束：foreign key

- 非空约束：not null

    - 创建表时添加约束

        ```sql
        CREATE TABLE stu(
            id INT,
            NAME VARCHAR(20) NOT NULL -- name为非空
        );
        ```

    - 创建表完后，添加非空约束

        ```sql
        ALTER TABLE stu MODIFY NAME VARCHAR(20) NOT NULL;
        ```

    - 删除name的非空约束

        ```sql
        ALTER TABLE stu MODIFY NAME VARCHAR(20);
        ```

    - 默认值

        ```sql
        address varchar(20) default '广州'--创建表时在字段上指定默认值
        insert into st9 values (1,'李四',default);--插入语句使用默认值，default为最后一个字段时，default可以省略
        ```

        

- 唯一约束：unique，值不能重复

    - 创建表时，添加唯一约束

        ```sql
        CREATE TABLE stu(
            id INT,
        	phone_number VARCHAR(20) UNIQUE -- 添加了唯一约束
        );
        ```

        注意：mysql中，唯一约束限定的列的值可以有多个null

    - 删除唯一约束 DROP INDEX 

        ```sql
        ALTER TABLE stu MODIFY phone_number VARCHAR(20); --不能使用修改列的方式
        ```

        ```sql
        ALTER TABLE stu DROP INDEX phone_number;
        ```

    - 在创建表后，添加唯一约束

        ```sql
        ALTER TABLE stu MODIFY phone_number VARCHAR(20) UNIQUE;
        ```

- 主键约束：primary key

    - 注意：

        1. 含义：非空且唯一
        2. 一张表只能有一个字段为主键
        3. 主键就是表中记录的唯一标识

    - 在创建表时，添加主键约束
    
        ```SQL
        create table stu(
            id int primary key,-- 给id添加主键约束
        	name varchar(20)
        );
        ```
    
    - 删除主键
    
        ```SQL
        -- 错误 alter table stu modify id int ;
        ALTER TABLE stu DROP PRIMARY KEY;
        ```
    
    - 创建完表后，添加主键
    
        ```SQL
        ALTER TABLE stu MODIFY id INT PRIMARY KEY;
        ```
    
- 自动增长：

    - 概念：如果某一列是数值类型的，使用 auto_increment 可以来完成值得自动增长

    - 注意

        - 在使用insert语句时，自动增长列可以为null，系统自动赋值
        - 自动增长列的值与上一条数据有关

    - 在创建表时，添加主键约束，并且完成主键自增长

    - ```SQL
        create table stu(
            id int primary key auto_increment,-- 给id添加主键约束
        	name varchar(20)
        	)auto_increment=1000;--指定自增长的起始值，不指定默认为1
        	
        alter table stu auto_increment=2000;--创建后修改起始值
        ```

    - 删除自动增长

        ```sql
        ALTER TABLE stu MODIFY id INT;--可以使用modify
        ```

    - 添加自动增长

        ```sql
        ALTER TABLE stu MODIFY id INT AUTO_INCREMENT;
        ```

- 外键约束 foreign key

    - 让表与表产生关系，从而保证数据的正确性

        - 例：员工表（从）------（外键：部门ID）-------部门表（主）

        - 外键生效后，不能在部门表中删除或修改与员工表有关联的部门ID，不能在员工表中添加部门表中不存在的部门ID（可以为null）

    - 在创建表时，可以添加外键

        ```sql
        create table 从表名(
        	其他列,
        	外键列
        	constraint 外键名称 foreign key (外键列名称) references 主表名称(主表列名称)
        );
        ```

    - 删除外键

        ```sql
        ALTER TABLE 从表名 DROP FOREIGN KEY 外键名称;
        ```

    - 创建表之后，添加外键

        ```sql
        ALTER TABLE 从表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称);
        ```

- 级联：解决外键关联的两张表同步更新的问题

    - 添加级联操作：先删除外键，再添加外键时设置级联

        ```sql
        ALTER TABLE 表名 ADD CONSTRAINT 外键名称 
        	FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称) 
        	ON UPDATE CASCADE ON DELETE CASCADE;
        ```

    - 分类

        - 级联更新：ON UPDATE CASCADE 
        - 级联删除：ON DELETE CASCADE

    - 设置级联时需谨慎，当多张表间存在级联关系时会存在同时删除、更新的情况
    
        

## 数据库的设计

###  多表之间的关系

- 一对一
    - 人与身份证
    - 实现：在任意一方添加唯一外键指向另一方的主键，并添加外键唯一约束。或者创建成一张表（推荐，省事）。
    
- 一对多（多对一）
    - 部门与员工
    - 实现：在多（员工）的一方建立外键，指向一（部门）的一方的主键
    
- 多对多
    - 学生和课程
    - 实现：多对多关系实现需要借助第三张中间表。中间表至少包含两个字段，这两个字段作为第三张表的外键，分别指向两张表的主键
    
- 案例：

    -- 创建旅游线路分类表 tab_category
    -- cid 旅游线路分类主键，自动增长
    -- cname 旅游线路分类名称非空，唯一，字符串 100

    ```sql
    CREATE TABLE tab_category (
    	cid INT PRIMARY KEY AUTO_INCREMENT,
    	cname VARCHAR(100) NOT NULL UNIQUE
    );
    ```

    -- 创建旅游线路表 tab_route
    	rid 旅游线路主键，自动增长
    	rname 旅游线路名称非空，唯一，字符串 100
    	price 价格
    	rdate 上架时间，日期类型
    	cid 外键，所属分类

    ```sql
    CREATE TABLE tab_route(
    	rid INT PRIMARY KEY AUTO_INCREMENT,
    	rname VARCHAR(100) NOT NULL UNIQUE,
    	price DOUBLE,
    	rdate DATE,
    	cid INT,
    	FOREIGN KEY (cid) REFERENCES tab_category(cid)
    );--省略了外键名称，系统自动分配
    ```

    /*创建用户表 tab_user
    		uid 用户主键，自增长
    		username 用户名长度 100，唯一，非空
    		password 密码长度 30，非空
    		name 真实姓名长度 100
    		birthday 生日
    		sex 性别，定长字符串 1
    		telephone 手机号，字符串 11
    		email 邮箱，字符串长度 100
    		*/

    ```sql
    CREATE TABLE tab_user (
        uid INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(100) UNIQUE NOT NULL,
        PASSWORD VARCHAR(30) NOT NULL,
        NAME VARCHAR(100),
        birthday DATE,
        sex CHAR(1) DEFAULT '男',
        telephone VARCHAR(11),
        email VARCHAR(100)
    );
    ```
    
    ​        /*
    ​		创建收藏表 tab_favorite
    ​		rid 旅游线路 id，外键
    ​		date 收藏时间
    ​		uid 用户 id，外键
    ​		rid 和 uid 不能重复，设置复合主键，同一个用户不能收藏同一个线路两次
    ​		*/
    
    ```sql
    CREATE TABLE tab_favorite (
        rid INT, -- 线路id
        DATE DATETIME,
        uid INT, -- 用户id
        -- 创建复合主键
        PRIMARY KEY(rid,uid), -- 联合主键
        FOREIGN KEY (rid) REFERENCES tab_route(rid),
        FOREIGN KEY(uid) REFERENCES tab_user(uid)
    );
    ```
    
    ​    

###   数据库设计的范式

- 概念：设计数据库时，需要遵循的一些规范。要遵循后边的范式要求，必须先遵循前边的所有范式要求

- 三大范式

    - 1NF  数据库表的每一列都是不可分割的原子数据项，不能是集合、数组等非原子数据项。即表中的某个列有多个值时，必须拆分为不同的列。简而言之，第一范式每一列不可再拆分，称为原子性。

        - 存在的问题：
            1. 数据冗余
            2. 数据添加存在问题
            3. 数据删除存在问题

    - 2NF  在满足第一范式的前提下，表中的每一个字段都完全依赖于主键。所谓完全依赖是指不能存在仅依赖主键一部分的列。简而言之，第二范式就是在第一范式的基础上所有列完全依赖于主键列。（在1NF基础上**消除部分依赖**）

        - 依赖概念：
            1. 函数依赖：A-->B,如果通过A属性(属性组)的值，可以确定唯一B属性的值。则称B依赖于A
            2. 完全函数依赖：A-->B，如果A是一个属性组，则B属性值得确定需要依赖于A属性组中所有的属性值。
            3. 部分函数依赖：A-->B， 如果A是一个属性组，则B属性值得确定只需要依赖于A属性组中某一些值即可。
            4. 传递函数依赖：A-->B, B -- >C . 如果通过A属性(属性组)的值，可以确定唯一B属性的值，在通过B属性（属性组）的值可以确定唯一C属性的值，则称 C 传递函数依赖于A
            5. 码：如果在一张表中，一个属性或属性组，被其他所有属性所完全依赖，则称这个属性(属性组)为该表的码

    - 3NF  在2NF基础上，任何非主属性不依赖于其它非主属性（在2NF基础上**消除传递依赖**）

    - BCNF  巴斯-科德范式

    - 4NF

    - 5NF  完美范式

        

##  数据库的备份和还原

1. 命令行
    - 备份  mysqldump -uroot -proot 数据库名 > 保存的路径;
    - 还原  登入数据库->创建数据库->使用数据库->source 文件路径
2. 图形化工具



##  多表查询

- 查询语法

    ```sql
    select
    		列名列表
    	from
    		表名列表
    	where....
    ```

- 笛卡尔积

    - 多表查询要消除无效的笛卡尔积

- 内连接查询：

    - 隐式内连接：使用where条件消除无用数据

    ```sql
    SELECT * FROM emp,dept WHERE emp.`dept_id` = dept.`id`;
    ```

    ```sql
    SELECT 
        t1.name, -- 员工表的姓名
        t1.gender,-- 员工表的性别
        t2.name -- 部门表的名称
    FROM
        emp t1,
        dept t2
    WHERE 
        t1.`dept_id` = t2.`id`;
    ```

    - 显式内连接：

        - 语法:

            ```sql
            select 字段列表 from 表名1 [inner] join 表名2 on 条件
            SELECT * FROM emp INNER JOIN dept ON emp.`dept_id` = dept.`id`;	
            SELECT * FROM emp JOIN dept ON emp.`dept_id` = dept.`id`;	
            ```

        - 内连接查询：

            1. 从哪些表中查询数据
            2. 条件是什么
            3. 查询哪些字段

- 外链接查询：

    - 左外连接：LEFT JOIN ON, 左表所有数据以及其与右表交集部分

        - 语法

            ```sql
            select 字段列表 from 表1 left [outer] join 表2 on 条件；
            ```

        - 需求：查询所有员工信息，如果员工有部门，则查询部门名称，没有部门，则不显示部门名称

            ```sql
            SELECT 	t1.*,t2.`name` FROM emp t1 LEFT JOIN dept t2 ON t1.`dept_id` = t2.`id`;
            ```

    - 右外连接：RIGHT JOIN ON, 右表所有数据以及其与左表交集部分

- 子查询：

    - 概念：查询中嵌套查询，称嵌套查询为子查询。

        ```sql
        SELECT * FROM emp WHERE emp.`salary` = (SELECT MAX(salary) FROM emp);
        ```

    - 不同情况

        - 子查询的结果是单行单列的：子查询可以作为条件，使用运算符去判断。

            ```sql
            SELECT * FROM emp WHERE emp.salary < (SELECT AVG(salary) FROM emp);
            ```

        -  子查询的结果是多行单列的：子查询可以作为条件，使用运算符in来判断

            ```sql
            SELECT * FROM emp WHERE dept_id IN (SELECT id FROM dept WHERE NAME = '财务部' OR NAME = '市场部');
            ```

        - 子查询的结果是多行多列的：子查询可以作为一张虚拟表参与查询

            ```sql
            SELECT * FROM dept t1 ,(SELECT * FROM emp WHERE emp.`join_date` > '2011-11-11') t2 WHERE t1.id = t2.dept_id;
            SELECT * FROM emp t1,dept t2 WHERE t1.`dept_id` = t2.`id` AND t1.`join_date` >  '2011-11-11';--内连接实现子查询功能
            ```



##  事务

- 基本介绍：
    - 概念：如果一个包含多个步骤的业务操作，被事务管理，那么这些操作要么同时成功，要么同时失败。
    - 操作：
        - 开启事务  start transaction;
        - 回滚  rollback;
        - 提交  commit;
    - MySQL数据库中事务默认自动提交
        - 查看事务的默认提交方式：SELECT @@autocommit; -- 1 代表自动提交  0 代表手动提交
        - 修改默认提交方式： set @@autocommit = 0;
        - Oracle 数据库默认是手动提交事务
    
- 事务的四大特征：
  
    - 原子性：是不可分割的最小操作单位，要么同时成功，要么同时失败。
    - 持久性：当事务提交或回滚后，数据库会持久化的保存数据。
    -  隔离性：多个事务之间。相互独立。
    - 一致性：事务操作前后，数据总量不变
    
- 事务的隔离级别：

    - 概念：多个事务之间隔离的，相互独立的。但是如果多个事务操作同一批数据，则会引发一些问题，设置不同的隔离级别就可以解决这些问题。

    - 存在的问题：

        - 脏读：一个事务，读取到另一个事务中没有提交的数据
        - 不可重复读(虚读)：在同一个事务中，两次读取到的数据不一样。
        - 幻读：一个事务操作(DML)数据表中所有记录，另一个事务添加了一条数据，则第一个事务查询不到自己的修改。

    - 隔离级别：

        1. read uncommitted：读未提交

            - 产生的问题：脏读、不可重复读、幻读

        2. read committed：读已提交 （Oracle）

            - 产生的问题：不可重复读、幻读

        3. repeatable read：可重复读 （MySQL默认）

            - 产生的问题：幻读

        4. serializable：串行化

            - 可以解决所有的问题

            隔离级别从小到大安全性越来越高，但是效率越来越低

    - 数据库查询隔离级别：select @@tx_isolation;

    - 数据库设置隔离级别：set global transaction isolation level 级别字符串；



##  DCL

- 管理用户：mysql数据库，user表

    1. 添加用户：

        ```sql
        语法：CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
        ```

    2. 修改用户密码：authentication_string替换第一个PASSWORD

        ```sql
        UPDATE USER SET PASSWORD = PASSWORD('新密码') WHERE USER = '用户名';
        SET PASSWORD FOR '用户名'@'主机名' = PASSWORD('新密码');
        ```

    3. 删除用户：DROP

        ```sql
        语法：DROP USER '用户名'@'主机名';
        ```

    4. 修改root用户密码：

        - 管理员权限下关闭mysql服务 net stop mysql;   
        - 无验证启动mysql服务 mysqld --skip-grant-tables;
        - 开启新的cmd窗口，直接mysql登入
        - 修改root用户密码
        - 关掉两个cmd窗口
        - 启动任务管理器，关闭mysqld进程
        - 打开新的cmd窗口，启动mysql服务
        - 使用新密码登入

- 授权管理：

    1. 查询权限：

        ```SQL
        SHOW GRANTS FOR '用户名'@'主机名';
        SHOW GRANTS FOR 'lisi'@'%';
        ```

    2. 授予权限：

        ```sql
        grant 权限列表 on 数据库名.表名 to '用户名'@'主机名';
        给张三用户授予所有权限，在任意数据库任意表上
        GRANT ALL ON *.* TO 'zhangsan'@'localhost';
        ```

    3. 撤销权限：

        ```sql
        revoke 权限列表 on 数据库名.表名 from '用户名'@'主机名';
        REVOKE UPDATE ON db3.`account` FROM 'lisi'@'%';
        ```

        

# Mysql高级

##  Linux下安装Mysql（有空补全）





##  索引

- 索引（index）是帮助Mysql进行高效获取数据的一种数据结构，该数据结构通过某种方式指向或引用存储的数据

- 无索引的情况下，Mysql查询数据默认从上往下进行全表扫描（filescan）

- 索引的优劣

    - 优势：
        - 提高数据检索的效率，降低数据库的IO成本
        - 通过索引对数据进行排序，降低数据排序的成本，降低CPU的消耗
    - 劣势：
        - 占用磁盘空间：索引实际上也是一张表，该表保存了主键与索引字段，并指向实体类的记录，
        - 降低更新表的速度：Mysql不仅要保存数据，还要保存索引文件每次的更新

- 索引的结构：

    - BTREE索引：Mysql默认的InnoDB引擎支持的索引

    - HASH索引：

    - R-tree（空间索引）

    - Full-text（全文索引）

        

- BTREE结构

    

    

    

    





​    

​    

​    

​    