# orientDB

## 初始化

连接控制台

下载二进制包 
运行：bin/console.sh

```
orientdb> connect remote:192.168.50.80/test root root;
```

创建数据库cmdb

```
CREATE DATABASE remote:192.168.50.80/cmdb root root ;
```

展示数据库列表

```
list databases;
```

删除数据库tong

```
drop database remote:192.168.50.80/tong root root;
```

初始的一些class

```
orientdb {db=cmdb}> list classes                               


CLASSES
+----+-------------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------+-----+
|#   |NAME               |SUPER-CLASSES|CLUSTERS                                                                                                                           |COUNT|
+----+-------------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------+-----+
|0   |E                  |             |e(26),e_1(27),e_2(28),e_3(29),e_4(30),e_5(31),e_6(32),e_7(33),e_8(34),e_9(35),e_10(36),e_11(37),e_12(38),e_13(39),e_14(40),e_15(41)|    0|
|1   |OFunction          |             |ofunction(7)                                                                                                                       |    0|
|2   |OGeometryCollection|[OShape]     |-                                                                                                                                  |    0|
|3   |OIdentity          |             |-                                                                                                                                  |    0|
|4   |OLineString        |[OShape]     |-                                                                                                                                  |    0|
|5   |OMultiLineString   |[OShape]     |-                                                                                                                                  |    0|
|6   |OMultiPoint        |[OShape]     |-                                                                                                                                  |    0|
|7   |OMultiPolygon      |[OShape]     |-                                                                                                                                  |    0|
|8   |OPoint             |[OShape]     |-                                                                                                                                  |    0|
|9   |OPolygon           |[OShape]     |-                                                                                                                                  |    0|
|10  |ORectangle         |[OShape]     |-                                                                                                                                  |    0|
|11  |ORestricted        |             |-                                                                                                                                  |    0|
|12  |ORole              |[OIdentity]  |orole(5)                                                                                                                           |    3|
|13  |OSchedule          |             |oschedule(9)                                                                                                                       |    0|
|14  |OSecurityPolicy    |             |osecuritypolicy(4)                                                                                                                 |    4|
|15  |OSequence          |             |osequence(8)                                                                                                                       |    0|
|16  |OShape             |             |-                                                                                                                                  |    0|
|17  |OTriggered         |             |-                                                                                                                                  |    0|
|18  |OUser              |[OIdentity]  |ouser(6)                                                                                                                           |    3|
|19  |V                  |             |v(10),v_1(11),v_2(12),v_3(13),v_4(14),v_5(15),v_6(16),v_7(17),v_8(18),v_9(19),v_10(20),v_11(21),v_12(22),v_13(23),v_14(24),v_15(25)|    0|
+----+-------------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------+-----+
|    |TOTAL              |             |                                                                                                                                   |   10|
+----+-------------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------+-----+

```

其中 V，E 分别是点(vertrix),边(edge)的抽象父类



创建公共点类型ConfigureItem：

```
 CREATE CLASS ConfigureItem extends V
```

声明点属性：

```
CREATE PROPERTY ConfigureItem.name STRING (MANDATORY TRUE,MIN 1,MAX 128);
CREATE PROPERTY ConfigureItem.createdAt DATETIME (MANDATORY TRUE);
```



创建物理服务器类PhysicalServer，继承ConfigureItem类:

```
CREATE CLASS PhysicalServer extends ConfigureItem
```

声明点属性：

```
CREATE PROPERTY PhysicalServer.temperature STRING (MANDATORY TRUE);
```



插入数据...



创建处理器模型，暂时继承ConfigureItem

```
CREATE CLASS Processor extends ConfigureItem
```

声明点属性：

```
CREATE PROPERTY Processor.brand STRING (MANDATORY TRUE); 
```



插入数据...



创建公共边类型 Relation

```
CREATE CLASS Relation extends E
```

声明边属性

```
CREATE PROPERTY Relation.name STRING (MANDATORY TRUE,MIN 1,MAX 128);
CREATE PROPERTY Relation.createdAt DATETIME (MANDATORY TRUE);
```



创建Connect 继承Relation

```
CREATE CLASS Connect extends Relation
```



创建边

```
CREATE EDGE Connect FROM #74:0 TO #90:0 SET createdAt = '2021-2-3 13:00:00'
```



Supported Data Types 

OrientDB supports several data types natively. Below is the complete table.

| #id  | Type          | SQL type     | Description                                                  | Java type                        | Minimum Maximum               | Auto-conversion from/to |
| ---- | ------------- | ------------ | ------------------------------------------------------------ | -------------------------------- | ----------------------------- | ----------------------- |
| 0    | Boolean       | BOOLEAN      | Handles only the values *True* or *False*                    | `java.lang.Boolean` or `boolean` | 0 1                           | String                  |
| 1    | Integer       | INTEGER      | 32-bit signed Integers                                       | `java.lang.Integer` or `int`     | -2,147,483,648 +2,147,483,647 | Any Number, String      |
| 2    | Short         | SHORT        | Small 16-bit signed integers                                 | `java.lang.Short` or `short`     | -32,768 32,767                | Any Number, String      |
| 3    | Long          | LONG         | Big 64-bit signed integers                                   | `java.lang.Long` or `long`       | -263 +263-1                   | Any Number, String      |
| 4    | Float         | FLOAT        | Decimal numbers                                              | `java.lang.Float` or `float`     | 2-149 (2-2-23)*2127           | Any Number, String      |
| 5    | Double        | DOUBLE       | Decimal numbers with high precision                          | `java.lang.Double` or `double`   | 2-1074 (2-2-52)*21023         | Any Number, String      |
| 6    | Datetime      | DATETIME     | Any date with the precision up to milliseconds. To know more about it, look at [Managing Dates](http://orientdb.com/docs/3.1.x/general/Managing-Dates.html) | `java.util.Date`                 | - 1002020303                  | Date, Long, String      |
| 7    | String        | STRING       | Any string as alphanumeric sequence of chars                 | `java.lang.String`               | - -                           | -                       |
| 8    | Binary        | BINARY       | Can contain any value as byte array                          | `byte[]`                         | 0 2,147,483,647               | String                  |
| 9    | Embedded      | EMBEDDED     | The Record is contained inside the owner. The contained Record has no [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id) | `ORecord`                        | - -                           | ORecord                 |
| 10   | Embedded list | EMBEDDEDLIST | The Records are contained inside the owner. The contained records have no [Record ID's](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id) and are reachable only by navigating the owner record | `List`                           | 0 41,000,000 items            | String                  |
| 11   | Embedded set  | EMBEDDEDSET  | The Records are contained inside the owner. The contained Records have no [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id) and are reachable only by navigating the owner record | `Set`                            | 0 41,000,000 items            | String                  |
| 12   | Embedded map  | EMBEDDEDMAP  | The Records are contained inside the owner as values of the entries, while the keys can only be Strings. The contained ords e no [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id)s and are reachable only by navigating the owner Record | `Map`                            | 0 41,000,000 items            | `Collection>`, `String` |
| 13   | Link          | LINK         | Link to another Record. It's a common [one-to-one relationship](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#11-and-1n-referenced-relationships) | `ORID`, ``                       | 1:-1 32767:2^63-1             | String                  |
| 14   | Link list     | LINKLIST     | Links to other Records. It's a common [one-to-many relationship](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#1n-and-nn-embedded-relationships) where only the [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id)s are stored | `List                            | 0 41,000,000 items            | String                  |
| 15   | Link set      | LINKSET      | Links to other Records. It's a common [one-to-many relationship](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#1n-and-nn-embedded-relationships) | `Set`                            | 0 41,000,000 items            | `Collection`, `String`  |
| 16   | Link map      | LINKMAP      | Links to other Records as value of the entries, while keys can only be Strings. It's a common [One-to-Many Relationship](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#1n-and-nn-embedded-relationships). Only the [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id)s are stored | `Map`                            | 0 41,000,000 items            | String                  |
| 17   | Byte          | BYTE         | Single byte. Useful to store small 8-bit signed integers     | `java.lang.Byte` or `byte`       | -128 +127                     | Any Number, String      |
| 18   | Transient     | TRANSIENT    | Any value not stored on database                             |                                  |                               |                         |
| 19   | Date          | DATE         | Any date as year, month and day. To know more about it, look at [Managing Dates](http://orientdb.com/docs/3.1.x/general/Managing-Dates.html) | `java.util.Date`                 | --                            | Date, Long, String      |
| 20   | Custom        | CUSTOM       | used to store a custom type providing the marshall and unmarshall methods | `OSerializableStream`            | 0 X                           | -                       |
| 21   | Decimal       | DECIMAL      | Decimal numbers without rounding                             | `java.math.BigDecimal`           | ? ?                           | Any Number, String      |
| 22   | LinkBag       | LINKBAG      | List of [Record ID](http://orientdb.com/docs/3.1.x/datamodeling/Concepts.html#record-id)s as spec [RidBag](http://orientdb.com/docs/3.1.x/internals/RidBag.html) | `ORidBag`                        | ? ?                           | -                       |
| 23   | Any           | ANY          | Not determinated type, used to specify Collections of mixed type, and null | -                                | -                             | -                       |

## SQL查询

If you are looking for the most efficient way to traverse a graph, we suggest to use the [SQL-Match](http://www.orientdb.org/docs/3.0.x/sql/SQL-Match.html) instead.