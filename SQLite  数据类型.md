SQLite 数据类型是一个用来指定任何对象的数据类型的属性。SQLite 中的每一列，每个变量和表达式都有相关的数据类型。

您可以在创建表的同时使用这些数据类型。SQLite 使用一个更普遍的动态类型系统。在 SQLite 中，值的数据类型与值本身是相关的，而不是与它的容器相关。

SQLite 存储类
每个存储在 SQLite 数据库中的值都具有以下存储类之一：

|<font color="#31b0d5">存储类</font>|	<font color="#31b0d5">描述</font>|
|:----|:----|
|	<font color="#449d44">NULL</font>|<font color="#ec971f">值是一个 |NULL 值。</font>|
|	<font color="#449d44">INTEGER&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font>|<font color="#ec971f">值是一个带符号的整数，根据值的大小存储在 1、2、3、4、6 或 8 字节中。</font>|
|	<font color="#449d44">	REAL</font>|<font color="#ec971f">值是一个浮点值，存储为 8 字节的 IEEE 浮点数字。</font>|
|	<font color="#449d44">	TEXT</font>|<font color="#ec971f">值是一个文本字符串，使用数据库编码（UTF-8、UTF-16BE 或 UTF-16LE）存储。</font>
|<font color="#449d44">	BLOB</font>|<font color="#ec971f">值是一个 blob 数据，完全根据它的输入存储。</font>|
SQLite 的存储类稍微比数据类型更普遍。INTEGER 存储类，例如，包含 6 种不同的不同长度的整数数据类型。

SQLite Affinity 类型
SQLite 支持列上的类型 affinity 概念。任何列仍然可以存储任何类型的数据，但列的首选存储类是它的 affinity。在 SQLite3 数据库中，每个表的列分配为以下类型的 affinity 之一：

|<font color="#31b0d5">Affinity</font>|	<font color="#31b0d5">描述</font>|
|:----|:----|
|	<font color="#449d44">	TEXT</font>|<font color="#ec971f">该列使用存储类 NULL、TEXT 或 BLOB 存储所有数据。</span>|
|	<font color="#449d44">NUMERIC&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font>|<font color="#ec971f">该列可以包含使用所有五个存储类的值。</font>|
|	<font color="#449d44">INTEGER</font>|<font color="#ec971f">与带有 NUMERIC affinity 的列相同，在 CAST 表达式中带有异常。</font>|
|	<font color="#449d44">REAL</font>|<font color="#ec971f">与带有 NUMERIC affinity 的列相似，不同的是，它会强制把整数值转换为浮点表示。</font>|
|	<font color="#449d44">NONE</font>|<font color="#ec971f">带有 affinity NONE</span>| 的列，不会优先使用哪个存储类，也不会尝试把数据从一个存储类强制转换为另一个存储类。
SQLite Affinity 及类型名称
下表列出了当创建 SQLite3 表时可使用的各种数据类型名称，同时也显示了相应的应用 Affinity：

|<font color="#31b0d5">数据类型</font>|	<font color="#31b0d5">Affinity</font>|
|:----|:----|
|<font color="#449d44">•&nbsp;INT<br />•&nbsp;INTEGER<br />•&nbsp;TINYINT<br />•&nbsp;SMALLINT<br />• MEDIUMINT<br />•&nbsp;BIGINT<br />•&nbsp;UNSIGNED BIG INT<br />•&nbsp;INT2<br />•&nbsp;INT8&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</font>|<font color="#ec971f">INTEGER&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font>|
|<font color="#449d44">•&nbsp;CHARACTER(20)<br />•&nbsp;VARCHAR(255)<br />•&nbsp;VARYING CHARACTER(255)<br />•&nbsp;NCHAR(55)<br />•&nbsp;NATIVE CHARACTER(70)<br />•&nbsp;NVARCHAR(100)<br />•&nbsp;TEXT<br />•&nbsp;CLOB</font>|<font color="#ec971f">TEXT </font>|
|<font color="#449d44">•&nbsp;BLOB<br />•&nbsp;no datatype specified</font>|<font color="#ec971f">NONE</font>|
|<font color="#449d44">REAL<br />•&nbsp;DOUBLE<br />•&nbsp;DOUBLE PRECISION<br />•&nbsp;FLOAT</font>|<font color="#ec971f">REAL</font>|
|<font color="#449d44">•&nbsp;NUMERIC<br />•&nbsp;DECIMAL(10,5)<br />•&nbsp;BOOLEAN<br />•&nbsp;DATE<br />•&nbsp;DATETIME</font>|<font color="#ec971f">NUMERIC</font>|

Boolean 数据类型
SQLite 没有单独的 Boolean 存储类。相反，布尔值被存储为整数 0（false）和 1（true）。

Date 与 Time 数据类型
SQLite 没有一个单独的用于存储日期和/或时间的存储类，但 SQLite 能够把日期和时间存储为 TEXT、REAL 或 INTEGER 值。

|<font color="#31b0d5">存储类&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</font>|	<font color="#31b0d5">日期格式</font>|
|:----|:----|
|	<font color="#449d44">TEXT</font>|	<font color="#ec971f">格式为 "YYYY-MM-DD HH:MM:SS.SSS" 的日期。</font>|
|	<font color="#449d44">REAL</font>|	<font color="#ec971f">从公元前 4714 年 11 月 24 日格林尼治时间的正午开始算起的天数。</font>|
|	<font color="#449d44">INTEGER	</font>|<font color="#ec971f">从 1970-01-01 00:00:00 UTC 算起的秒数。您可以以任何上述格式来存储日期和时间，<br/>并且可以使用内置的日期和时间函数来自由转换不同格式。</font>|