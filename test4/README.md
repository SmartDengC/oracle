# 实验四：对象管理

# 表空间
这里数据库已经有了users02的表空间，不在重新创建，以下是查询结果。
```sql
SYSTEM@192.168.44.183:1521/orclpdb>select tablespace_name, status, contents from dba_tablespaces;

TABLESPACE_NAME 	       STATUS	 CONTENTS
------------------------------ --------- ---------------------
SYSTEM			       ONLINE	 PERMANENT
SYSAUX			       ONLINE	 PERMANENT
UNDOTBS1		       ONLINE	 UNDO
TEMP			       ONLINE	 TEMPORARY
USERS			       ONLINE	 PERMANENT
HR			       ONLINE	 PERMANENT
EXAMPLE 		       ONLINE	 PERMANENT
USERS02 		       ONLINE	 PERMANENT
USERS03 		       ONLINE	 PERMANENT

已选择 9 行。
```

# 用户授权
我数据里面已经有了用户jet5devil，这里不在重新创建用户，继续使用这个用户来进行一下实验，授权到该用户
```sql
SYSTEM@192.168.44.183:1521/orclpdb>alter user jet5devil identified by jet5devil default tablespace "USERS" temporary tablespace "TEMP";

用户已更改。

SYSTEM@192.168.44.183:1521/orclpdb>alter user jet5devil quota unlimited on USERS;

用户已更改。

SYSTEM@192.168.44.183:1521/orclpdb>alter user jet5devil quota unlimited on USERS02;

用户已更改。

SYSTEM@192.168.44.183:1521/orclpdb>alter user jet5devil account unlock;

用户已更改。
SYSTEM@192.168.44.183:1521/orclpdb>grant "CONNECT" to jet5devil with admin option;

授权成功。

SYSTEM@192.168.44.183:1521/orclpdb>grant "RESOURCE" to jet5devil with admin option;

授权成功。

SYSTEM@192.168.44.183:1521/orclpdb>alter user jet5devil default role "CONNECT", "RESOURCE";

用户已更改。

SYSTEM@192.168.44.183:1521/orclpdb>grant create  view to jet5devil with admin option;

授权成功。

```

# 删除表和序列并创建相应的表
这里我创建一个叫做 test4.sql 的文件，在数据库中执行，进行对表的操作。