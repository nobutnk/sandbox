# SQL Server に関するメモ

[JDBCのSQL Serverオプション](http://docs.oracle.com/cd/E13157_01/wlevs/docs30/jdbc_drivers/mssqlserver.html)

上記のconnectionPropertiesで、SnapshotSerializableを使うとできそう。

> To configure Snapshot Isolation for connections, 
> you must have your Microsoft SQL Server 2005 database configured for Snapshot Isolation,
> your application must have the transaction isolation level set to Serializable,
> and this property must be set to true.

```java
@Transactional(isolation=Isolation.SERIALIZABLE)
public void someTransactionalMethod(User user) {

  // Interact with testDAO

}
```
