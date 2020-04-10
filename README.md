# mysql-final-test

2019-2020 mysql final test

姓名：徐鑫

学号：17061527

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:00:32 |
+---------------------+
1 row in set (0.00 sec)

```
2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```sql
mysql> select CONCAT('徐鑫','+','17061527');
+-------------------------------+
| CONCAT('徐鑫','+','17061527') |
+-------------------------------+
| 徐鑫+17061527                 |
+-------------------------------+
1 row in set (0.01 sec)
```

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```sql
create table t_dept1(
deptno INT PRIMARY KEY,
dname VARCHAR(20),
loc VARCHAR(40)
);

INSERT INTO t_dept1(deptno, dname,loc)
values (10, "ACCOUNTING", "NEW YORK"),
	(20, "RESEARCH", "DALLAS"),
	(30, "SALES", "CHICAGO"),
	(40, "OPERATIONS", "BOSTON");
select * from t_dept1;


+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)

```

表2：其中empno字段为主键
```sql
create table t_dept2(
empno INT PRIMARY KEY,
ename VARCHAR(20),
job VARCHAR(20),
MGR INT,
Hiredate Date,
sal float,
comm float,
deptno INT
);
INSERT INTO t_dept2(empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno)
    values  (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
	
mysql> select * from t_dept2;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.00 sec)

```

3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
```sql
INSERT INTO t_dept2
 	values (17061527,'xuxin','STUDENT',7782,'1998-12-28',NULL,NULL,10);
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```
```sql
mysql> select * from t_dept2;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061527 | xuxin  | STUDENT   | 7782 | 1998-12-28 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)
```

3.2 表中入职时间（Hiredate字段）最短的人。
```sql
mysql> SELECT * FROM t_dept2 WHERE Hiredate = (SELECT MAX(Hiredate) FROM t_dept2);
+----------+-------+---------+------+------------+------+------+--------+
| empno    | ename | job     | MGR  | Hiredate   | sal  | comm | deptno |
+----------+-------+---------+------+------------+------+------+--------+
| 17061527 | xuxin | STUDENT | 7782 | 1998-12-28 | NULL | NULL |     10 |
+----------+-------+---------+------+------------+------+------+--------+
1 row in set (0.00 sec)
```
3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```sql
mysql> select distinct job
    -> from t_dept2;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
| STUDENT   |
+-----------+
6 rows in set (0.00 sec)
```
共有5种职位，本操作是选择运算

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```sql
mysql> select ename from t_dept2 WHERE sal > (
    -> select sal+100 from t_dept2 WHERE ename='MILLER');
+--------+
| ename  |
+--------+
| ALLEN  |
| JONES  |
| BLAKE  |
| SCOTT  |
| KING   |
| TURNER |
| FORD   |
+--------+
7 rows in set (0.01 sec)

mysql> select * from t_dept2 WHERE sal > (
    -> select sal+100 from t_dept2 WHERE ename='MILLER');
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+
7 rows in set (0.00 sec)
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```sql
mysql> select ename,sal+comm,count(ename) counts,AVG(sal+comm) average_sal_comm from t_dept2;
+-------+----------+--------+------------------+
| ename | sal+comm | counts | average_sal_comm |
+-------+----------+--------+------------------+
| SMITH |     NULL |     14 |             1950 |
+-------+----------+--------+------------------+
1 row in set (0.01 sec)

3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```sql
mysql> select t1.ename My_b_b_name,t2.ename My_b_name ,t3.ename My_name
    -> from (t_dept2 t1 inner join t_dept2 t2 on t1. empno= t2. mgr)  inner join t_dept2 t3
    -> on t2.empno = t3.mgr;
+-------------+-----------+---------+
| My_b_b_name | My_b_name | My_name |
+-------------+-----------+---------+
| JONES       | FORD      | SMITH   |
| KING        | BLAKE     | ALLEN   |
| KING        | BLAKE     | WARD    |
| KING        | BLAKE     | MARTIN  |
| KING        | JONES     | SCOTT   |
| JONES       | SCOTT     | ADAMS   |
| KING        | BLAKE     | JAMES   |
| KING        | JONES     | FORD    |
+-------------+-----------+---------+
8 rows in set (0.01 sec)
```
关系代数：交

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```sql
mysql> select * from t_dept1 t1 inner join t_dept2 t2 on t1.deptno=t2.deptno;
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
| deptno | dname      | loc      | empno    | ename     | job       | MGR  | Hiredate   | sal  | comm | deptno |
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
|     20 | RESEARCH   | DALLAS   |     7369 | SMITH     | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7499 | ALLEN     | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     30 | SALES      | CHICAGO  |     7521 | WARD      | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     20 | RESEARCH   | DALLAS   |     7566 | JONES     | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7654 | MARTIN    | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     10 | ACCOUNTING | NEW YORK |     7698 | BLAKE     | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     20 | RESEARCH   | DALLAS   |     7788 | SCOTT     | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7839 | KING      | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     30 | SALES      | CHICAGO  |     7844 | TURNER    | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     20 | RESEARCH   | DALLAS   |     7878 | ADAMS     | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7900 | JAMES     | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     20 | RESEARCH   | DALLAS   |     7902 | FORD      | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7934 | MILLER    | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
|     10 | ACCOUNTING | NEW YORK | 17061521 | QIUFUKANG | CLERK     | 7782 | 2000-03-12 | NULL | NULL |     10 |
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
14 rows in set (0.01 sec)

mysql> create view view_t_dept1_t_dept2
    -> as
    -> select empno,ename,job,loc from t_dept1 t1 inner join t_dept2 t2 on t1.deptno=t2.deptno;
Query OK, 0 rows affected (0.01 sec)

mysql> select * from view_t_dept1_t_dept2;
+----------+-----------+-----------+----------+
| empno    | ename     | job       | loc      |
+----------+-----------+-----------+----------+
|     7369 | SMITH     | CLERK     | DALLAS   |
|     7499 | ALLEN     | SALESMAN  | CHICAGO  |
|     7521 | WARD      | SALESMAN  | CHICAGO  |
|     7566 | JONES     | MANAGER   | DALLAS   |
|     7654 | MARTIN    | SALESMAN  | CHICAGO  |
|     7698 | BLAKE     | MANAGER   | NEW YORK |
|     7788 | SCOTT     | ANALYST   | DALLAS   |
|     7839 | KING      | PRESIDENT | NEW YORK |
|     7844 | TURNER    | SALESMAN  | CHICAGO  |
|     7878 | ADAMS     | CLERK     | DALLAS   |
|     7900 | JAMES     | CLERK     | CHICAGO  |
|     7902 | FORD      | ANALYST   | DALLAS   |
|     7934 | MILLER    | CLERK     | NEW YORK |
| 17061521 | QIUFUKANG | CLERK     | NEW YORK |
+----------+-----------+-----------+----------+
14 rows in set (0.00 sec)
```
为了提高复杂SQL语句的复用性和表操作的安全性,MySQL数据库管理系统提供了视图特性。所谓视图，本质上是一种虚拟表，其内容与真实的表相似，包含系列带有名称的列和行数据。但是，视图并不在数据库中以存储的数据值形式存在。行和列数据来自定义视图的查询所引用基本表，并且在具体引用视图时动态生成。视图使程序员只关心感兴趣的某些特定数据和他们所负责的特定任务。这样程序员只能看到视图中所定义的数据，而不是视图所引用表中的数据，从而提高了数据库中数据的安全性。
3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```sql
mysql> CREATE INDEX index_ename
    -> ON t_dept2 (ename);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE t_dept2 \G
*************************** 1. row ***************************
       Table: t_dept2
Create Table: CREATE TABLE `t_dept2` (
  `empno` int(11) NOT NULL,
  `ename` varchar(20) DEFAULT NULL,
  `job` varchar(20) DEFAULT NULL,
  `MGR` int(11) DEFAULT NULL,
  `Hiredate` date DEFAULT NULL,
  `salary` float DEFAULT NULL,
  `comm` float DEFAULT NULL,
  `deptno` int(11) DEFAULT NULL,
  PRIMARY KEY (`empno`),
  KEY `index_ename` (`ename`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1
1 row in set (0.00 sec)
```
3.10 将表2的 sal 字段改名为 salary
```sql
mysql> alter table t_dept2
    -> CHANGE sal salary float;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc t_dept2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  |     | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| MGR      | int(11)     | YES  |     | NULL    |       |
| Hiredate | date        | YES  |     | NULL    |       |
| salary   | float       | YES  |     | NULL    |       |
| comm     | float       | YES  |     | NULL    |       |
| deptno   | int(11)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.01 sec)
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```sql
mysql>     DELIMITER $$
mysql>     CREATE FUNCTION func_1 (empno INT)
    ->         RETURNS DOUBLE
    ->     BEGIN
    ->         RETURN (SELECT deptno
    ->             FROM t_dept2
    ->             WHERE t_dept2.empno = empno);
    ->     END$$
Query OK, 0 rows affected (0.02 sec)

mysql>     DELIMITER ;
mysql>   SELECT func_1(7499);
+--------------+
| func_1(7499) |
+--------------+
|           30 |
+--------------+
1 row in set (0.00 sec)
```
不同：函数是用在表达式中，在一个存储过程中可能用到多个的函数 
4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
```sql
mysql> insert into mysql.user(Host,User,Password) values("localhost","xuxin",password("17061527"));
ERROR 1054 (42S22): Unknown column 'Password' in 'field list'
mysql> GRANT USAGE ON *.* TO 'xuxin'@'localhost' IDENTIFIED BY '17061527' WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.01 sec)

mysql> SET PASSWORD FOR xuxin@'localhost' = PASSWORD('17061527');
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.02 sec)
```
4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限

4.3 `with grant option` 是什么意思。

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？
外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录(外模式)，也可以利用数据操纵语言(Data Manipulation Language，DML)对这些数据记录进行操作。外模式反映了数据库系统的用户观。
内模式又称存储模式，对应于物理级。它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义的。内模式反映了数据库系统的存储观。
在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式和定义、描述数据库逻辑结构的模式，也是唯一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是唯一的，也不可能是唯一的。

8 什么是ACID？
  ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。
8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
1、图片，文件，二进制数据：对数据库的读/写的速度永远都赶不上文件系统处理的速度数据库备份变的巨大，越来越耗时间对文件的访问需要穿越你的应用层和数据库层这后两个是真正的杀手。
2、短生命期数据：使用情况统计数据，测量数据，GPS定位数据，session数据，任何只是短时间内对你有用，或经常变化的数据。如果你发现自己正在使用定时任务从某个表里删除有效期只有一小时，一天或数周的数据，那说明你没有找对正确的做事情的方法。使用redis， statsd/graphite， Riak，它们都是干这种事情更合适的工具。这建议也适用于对于收集那些短生命期的数据。
3、日志文件：也许你的日志记录做的很保守，每次web请求只产生一条日志。对于整个网站的每个事件来说，这仍然会产生大量的数据库插入操作，争夺你用户需要的数据库资源。如果你的日志级别设置为verbose或debug，那等着看你的数据库着火吧。
