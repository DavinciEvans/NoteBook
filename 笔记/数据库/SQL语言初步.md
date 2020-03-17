# SQL 语言初步

SQL 功 能 | 动词
| --- | --- |
数 据 查 询 | SELECT
数 据 定 义 |CREATE，DROP，ALTER
数 据 操 纵 |INSERT，UPDATE，DELETE
数 据 控 制 |GRANT，REVOKE

## 相关概念

### 基本表

- 本身独立存在的表
- SQL中一个关系就对应一个基本表
- 一个（或多个）基本表对应一个存储文件
- 一个表可以带若干索引

### 视图

- 从一个或几个基本表导出的表
- 数据库中只存放视图的定义而不存放视图对应的数据
- 视图是一个虚表
- 用户可以在视图上再定义视图

## 数据定义

操作对象 | 创 建| 删 除| 修 改
|---|---|---|---|
模式 |CREATE SCHEMA |DROP SCHEMA|-
表 |CREATE TABLE| DROP TABLE| ALTER TABLE
视图| CREATE VIEW| DROP VIEW |-
索引| CREATE INDEX| DROP INDEX| ALTER INDEX

### 定义模式

`CREATE SCHEMA <模式名> AUTHORIZATION <用户名>[<表定义子句>|<视图定义子句>|<授权定义子句>]`

定义模式实际上定义了一个命名空间（或者说目录）。

在这个空间中可以定义该模式包含的数据库对象，例如基
本表、视图、索引等。

同时定义模式接受 `CREATE TABLE`、`CREATE VIEW` 和 `GRANT` 子句

🌰：

为用户 ZHANG 创建了一个模式 TEST，并且在其中定义一个表 TAB1

```SQL
CREATE SCHEMA TEST AUTHORIZATION ZHANG
/* 下面为表定义子句 */
CREATE TABLE TAB1 ( COL1 SMALLINT,
COL2 INT,
COL3 CHAR(20),
COL4 NUMERIC(10,3),
COL5 DECIMAL(5,2)
);
```

### 删除模式

`DROP SCHEMA <模式名> <CASCADE|RESTRICT>`

- CASCADE 级联

删除的时候把该模式当中所有的数据库对象全部删除

- RESTRICT 限制

如果该模式下拥有数据库对象，则不能进行删除操作

🌰：

删除模式ZHANG

同时该模式中定义的表TAB1也被删除

`DROP SCHEMA ZHANG CASCADE;`

### 定义基本表

```SQL
CREATE TABLE <表名> 
( <列名> <数据类型>[ <列级完整性约束条件> ] /*组成该表的列*/
[,<列名> <数据类型>[ <列级完整性约束条件>] ]
…
[,<表级完整性约束条件> ] );
```

“域”使用数据类型来体现

定义表的属性时需要定义其数据类型以及长度


🌰：

建立学生表

```SQL
CREATE TABLE Student
(Sno CHAR(9) PRIMARY KEY,
/* 列级完整性约束条件,Sno是主码*/
Sname CHAR(20) UNIQUE, /* Sname取唯一值*/
Ssex CHAR(2),
Sage SMALLINT,
Sdept CHAR(20)
);
```

建立课程表

```SQL
CREATE TABLE Course
(Cno CHAR(4) PRIMARY KEY,
Cname CHAR(40),
Cpno CHAR(4),
Ccredit SMALLINT，
FOREIGN KEY (Cpno) REFERENCES Course(Cno)
/* Cpno 是外码，被参照表是Course，被参照列是Cno */
);
```

建立学生选课表

```SQL
CREATE TABLE SC
(Sno CHAR(9),
Cno CHAR(4),
Grade SMALLINT，
PRIMARY KEY (Sno,Cno),
/* 主码由两个属性构成，必须作为表级完整性进行定义*/
FOREIGN KEY (Sno) REFERENCES Student(Sno),
/* 表级完整性约束条件，Sno是外码，被参照表是Student */
FOREIGN KEY (Cno)REFERENCES Course(Cno)
/* 表级完整性约束条件， Cno是外码，被参照表是Course*/
```

### 模式与表的关系

每一个基本表都属于某个模式

定义基本表所属模式的方式：

- 方法一：在表名中明显地给出模式名

```SQL
Create table"S-T".Student(......); /*模式名为 S-T*/
Create table "S-T".Cource(......);
Create table "S-T".SC(......);
```

- 方法二：在创建模式的同时创建表
- 方法三：设置所属的模式

创建基本表（其他数据库对象也一样）时，若没有指定模式，系统根据搜索路径来确定该对象所属的模式

### 修改基本表

```SQL
ALTER TABLE <表名>
[ADD[COLUMN] <新列名> <数据类型> [ 完整性约束 ] ]
[ADD <表级完整性约束>]
[DROP [ COLUMN ] <列名> [CASCADE| RESTRICT] ]
[DROP CONSTRAINT<完整性约束名>[ RESTRICT | CASCADE ] ]
[ALTER COLUMN <列名><数据类型> ] ;
```

概括：

- ADD 增加
- DROP 删除
- ALTER 修改

🌰：

向 Student 表当中增加“入学时间”列：

`ALTER TABLE Student ADD S_entrance DATE;`

将年龄改为整数

`ALTER TABLE Student ALTER COLUMN Sage INT;`

增加约束条件

`ALTER TABLE Course ADD UNIQUE(Cname);`

### 删除基本表

`DROP TABLE <表名>［RESTRICT| CASCADE］;`

在这里 RESTRICT 的含义为：若含有其他依赖该表的对象，则不能被删除， CASCADE 则可以，相关的依赖对象也将被删除。

删除 Student 表

`DROP TABLE Student CASCADE;`
