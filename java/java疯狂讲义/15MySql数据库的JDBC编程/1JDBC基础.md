# 1JDBC基础
JDBC的全称是Java Database Connectivity,即Java数据库连接,是一种可以执行SQL语句的api.程序可以通过JDBC API连接到关系数据库,并使用结构化查询语言来完成对数据库的查询、更新.
## JDBC简介
通过使用JDBC就可以使用同一种API访问不同的数据库系统.JDBC的三个基本功能:
* 与数据库建立连接
* 执行SQL语句
* 获得SQL语句的执行结果
## JDBC驱动程序
数据库驱动程序是JDBC程序和数据库之间的转换层,数据库驱动程序负责将JDBC调用映射成特定的数据库调用.