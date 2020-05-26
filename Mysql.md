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

3. 初始化mysql

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
    - DCL 客户端授权

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
        - select math, english, math+ifnull(english) from student;
            - 如果有null参与的运算，结果都为null。
            - ifnull(english，0) ,如果英语成绩为null，指定为0
        - select math, english, math+ifnull(english) as total from student;
            - as total 为字段起别名
2. 条件查询 
    - where子句后跟条件
    - 运算符
        - ">, <, >=, <=, =, <> "
        - BETWEEN AND
        - IN
        - LIKE
        - IS NULL
        - AND &&, OR ||,  NOT !



