---
id: sql-data-types
slug: /sql-data-types
title: Data types
---



RisingWave supports the following data types:

|Type|Aliases|Description|
|---|---|-------|
|boolean|bool|Logical Boolean. It follows a three-valued logic system (true, false, and null).|
|smallint| |Two-byte integer|
|integer|int|Four-byte integer|
|bigint| |Eight-byte integer|
|numeric|decimal|Exact numeric. We do not support specifying precision and scale as of now.|
|real| |Single precision floating-point number (4 bytes)|
|double precision|double|Double precision floating-point number (8 bytes)|
|character varying|varchar|Variable-length character string. We do not support specifying the maximum length as of now.|
|date| |Calendar date (year, month, day)|
|time| |Time of day (no time zone)|
|timestamp without time zone|timestamp|Date and time (no time zone)|
|timestamp with time zone | |Timestamp with time zone|
|interval| |Time span|


