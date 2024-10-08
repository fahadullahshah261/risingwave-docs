---
id: sql-create-sink-into
title: CREATE SINK INTO
description: Create a sink into RisingWave's table.
slug: /sql-create-sink-into
---
<head>
  <link rel="canonical" href="https://docs.risingwave.com/docs/current/sql-create-sink-into/" />
</head>

Use the `CREATE SINK INTO` command to create a sink into RisingWave's table.

## Syntax

```sql
CREATE SINK [ IF NOT EXISTS ] sink_name INTO table_name
[FROM sink_from | AS select_query]
```

:::note

A table without a primary key can only accept the append-only sink.

:::

:::note

Currently, if there are sinks in the table, the table cannot be altered to add or drop columns.

:::

## Examples

You can union data from two different Kafka topics.

```sql
CREATE TABLE orders (
    id int primary key,
    price int,
    item_id int,
    customer_id int
);

CREATE source orders_s0 (
    id int primary key,
    price int,
    item_id int,
    customer_id int
) WITH (
    connector = 'kafka',
    topic = 'topic_0',
    ...
) FORMAT PLAIN ENCODE JSON;

CREATE source orders_s1 (
    id int primary key,
    price int,
    item_id int,
    customer_id int
) WITH (
    connector = 'kafka',
    topic = 'topic_1',
    ...
) FORMAT PLAIN ENCODE JSON;

CREATE SINK orders_sink0 FROM orders_s0 INTO orders;
CREATE SINK orders_sink1 FROM orders_s1 INTO orders;
```

If you don't want one of the topics, you can drop it.

```sql
DROP SINK orders_sink0;
```

## See also

[`CREATE SINK`](sql-create-sink.md) — Create a sink into an external target.

[`DROP SINK`](sql-drop-sink.md) — Remove a sink.

[`SHOW CREATE SINK`](sql-show-create-sink.md) — Show the SQL statement used to create a sink.
