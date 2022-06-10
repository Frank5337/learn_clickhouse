Defining a database and table
Defining a database will look very familiar. Defining a table involves some ClickHouse-specific details.

Show instructions  
You use the CREATE DATABASE command to create a new database. Run the following command in the Play UI to define a new database named gettingstarted:  

CREATE DATABASE gettingstarted  

You should see gettingstarted now in the list of databases:  

SHOW DATABASES  
Creating a table is a bit different in that ClickHouse has its own data types, and every table must specify an Engine property that determines the type of table to be created.  

#### 创建表有点不同，ClickHouse 有自己的数据类型，每个表都必须指定一个 Engine 属性来确定要创建的表的类型。
Run the following command to define a new MergeTree table named clickstream in the gettingstarted database:
```sql
CREATE TABLE gettingstarted.clickstream (  
customer_id String,  
time_stamp Date,  
click_event_type String,  
country_code FixedString(2),  
source_id UInt64  
)  
ENGINE = MergeTree()  
ORDER BY (time_stamp)  
```
The table engine determines how and where the data is stored, which queries are supported, support for concurrency, and other details that you will need to gradually understand as you work with ClickHouse. For now, we will use the MergeTree engine - a good starting point when you are not sure which engine you need.

Verify clickstream was created successfully:

DESCRIBE gettingstarted.clickstream  
Your table should look like the following:  



## 有关各种 ClickHouse 数据类型的更多详细信息，请访问文档，但这里有一些关于新表中数据类型的说明：
Visit the [docs](https://clickhouse.com/docs/en/sql-reference/data-types/) for more details on the various ClickHouse data types, but here are a few notes about the data types in your new table:

The String type replaces VARCHAR, BLOB, CLOB and other string-like data types from other databases  
UInt64 is a 64-bit unsigned integer  
Date is one of several ways to store dates in ClickHouse  
If you know the precise length of all strings in a column, then use the FixedString(n) data type 


## 您可能需要将不同格式的数据插入 ClickHouse。有关所有各种支持的输入格式的详细信息，请查看 ClickHouse 文档中的格式。
You probably have data in different formats that needs to be inserted into ClickHouse. For details on all the various supported input formats, [check out the formats in the ClickHouse documentation](https://clickhouse.com/docs/en/interfaces/formats/).

```sql
SHOW DATABASES
SHOW TABLES IN SCHEM
DESCRIBE TABLE
```



