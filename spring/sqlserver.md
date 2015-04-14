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

connectionPropertiesは、こんなかんじ
```xml
<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
    	<property name="driverClassName" value=""/>
        <property name="url" value=""/>
        <property name="username" value=""/>
        <property name="password" value=""/>
        <property name="maxActive" value=""/>
        <property name="maxWait" value=""/>
        <property name="maxIdle" value=""/>
        <property name="minIdle" value=""/>
        <property name="initialSize" value=""/>
        <property name="validationQuery" value=""/>
        <property name="testOnBorrow" value=""/>
        <property name="testOnReturn" value=""/>        
        <property name="testWhileIdle" value=""/>        
        <property name="timeBetweenEvictionRunsMillis" value=""/>        
        <property name="numTestsPerEvictionRun" value=""/>        
        <property name="connectionProperties">
        	<props>
        		<prop key="SnapshotSerializable">true</prop>
        	</props>
        </property>
    </bean>
```
