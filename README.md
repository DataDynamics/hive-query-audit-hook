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

```xml
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

### Cloudera Manager

"Cloudera > Hive On Tez > Configuration > Hive Service Advanced Configuration Snippet (Safety Valve) for hive-site.xml"에 다음을 추가합니다.

* Pre Hooks
  * Name : `hive.exec.pre.hooks`
  * Value : `io.datadynamics.hive.hook.QueryAuditHook`
* Post Hooks
  * Name : `hive.exec.post.hooks`
  * Value : `io.datadynamics.hive.hook.QueryAuditHook`
* Failure Hooks
  * Name : `hive.exec.failure.hooks`
  * Value : `io.datadynamics.hive.hook.QueryAuditHook`
* Enable
  * Name : `QueryAuditHook.enabled`
  * Value : `true`
* Target URL
  * Name : `QueryAuditHook.target.url` 
  * Value : `http://10.10.10.10/api/hive/audit`
