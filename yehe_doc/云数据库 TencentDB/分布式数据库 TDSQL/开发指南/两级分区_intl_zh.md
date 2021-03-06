
如您需要阅读或下载全量开发文档，请参见 [TDSQL 开发指南](https://intl.cloud.tencent.com/document/product/1042/33352)。

TDSQL 只用 HASH 方式进行数据拆分，不利于删除特定条件的数据，如流水类型，删除旧的数据，为解决这个问题，可以使用两级分区。
TDSQL 支持 range 和 list 格式的两级分区，具体建表语法和 MySQL 分区语法类似。

>分区使用的是小于`<`符号，因此如果要存储当年的数据的话（2017），需要创建` <2018 `的分区，用户只需创建到当前的时间分区，TDSQL 会自动增加后续分区，默认往后创建3个分区，以 YEAR 为例，TDSQL 会自动创建2018，2019，2020的分区，后续也会自动增减。

**range 支持类型**
- DATE，DATETIME，TIMESTAMP
支持 year，month，day 函数，函数为空和 day 函数一样。
- TINYINT, SMALLINT, MEDIUMINT, INT (INTEGER), and BIGINT
支持 year，month，day 函数，此时传入的值转换为年月日，然后和分表信息对比。

函数为空则直接使用该 int 值和分表信息对比。

示例：
如果 hired 是 date 类型，则查询插入对应的值格式为 '20160101 10:20:20' ,20160101
```
	CREATE TABLE employees_int (
	    id INT key NOT NULL,
	    fname VARCHAR(30),
	    lname VARCHAR(30),
	    hired date,
	    separated DATE NOT NULL DEFAULT '9999-12-31',
	    job_code INT,
	    store_id INT
	)
	shardkey=id
	PARTITION BY RANGE ( month(hired) ) (
	    PARTITION p0 VALUES LESS THAN (199102),
	    PARTITION p1 VALUES LESS THAN (199603),
	    PARTITION p2 VALUES LESS THAN (200101)
	);

```
如果 hired 是 int 类型，则查询插入对应的值格式为 1474961034，proxy 首先会转换成对应的 date 格式，20160927，然后和分表信息对比。
```
	CREATE TABLE employees_int (
	    id INT key NOT NULL,
	    fname VARCHAR(30),
	    lname VARCHAR(30),
	    hired int,
	    separated DATE NOT NULL DEFAULT '9999-12-31',
	    job_code INT,
	    store_id INT
	)
	shardkey=id
	PARTITION BY RANGE ( month(hired) ) (
	    PARTITION p0 VALUES LESS THAN (199102),
	    PARTITION p1 VALUES LESS THAN (199603),
	    PARTITION p2 VALUES LESS THAN (200101)
	);

```

**list 支持类型**
DATE，DATETIME，TIMESTAMP ，支持年月日函数;
TINYINT, SMALLINT, MEDIUMINT, INT (INTEGER), and BIGINT;
CHAR, VARCHAR, BINARY, and VARBINARY;
```
	CREATE TABLE customers_1 (
	    first_name VARCHAR(25),
	    last_name VARCHAR(25),
	    street_1 VARCHAR(30),
	    street_2 VARCHAR(30),
	    city VARCHAR(15),
	    renewal DATE
	) shardkey=first_name
	PARTITION BY LIST (city) (
	    PARTITION pRegion_1 VALUES IN('1', '2', '3'),
	    PARTITION pRegion_2 VALUES IN('4', '5', '6'),
	    PARTITION pRegion_3 VALUES IN('7', '8', '9'),
	    PARTITION pRegion_4 VALUES IN('10', '11', '12')
	);

```
