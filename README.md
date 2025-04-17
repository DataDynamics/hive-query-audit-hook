# Hive Query Audit Hook

## Requirement

* Hive 3.1.3
* JDK 8

## Build

```
# mvn -Dmaven.test.skip=true clean package
```

## Configuration

### `hive-site.xml`

```
<property>
  <name>hive.exec.pre.hooks</name>
  <value>io.datadynamics.hive.hook.QueryAuditHook</value> 
</property>

<property>
  <name>hive.exec.post.hooks</name>
  <value>io.datadynamics.hive.hook.QueryAuditHook</value>
</property>

<property>
  <name>hive.exec.failure.hooks</name>
  <value>io.datadynamics.hive.hook.QueryAuditHook</value>
</property>

<property>
  <name>QueryAuditHook.enabled</name>
  <value>true</value>
</property>

<property>
  <name>QueryAuditHook.target.url</name>
  <value>http://10.10.10.10/api/hive/audit</value>
</property>
```