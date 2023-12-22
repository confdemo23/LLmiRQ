# LLmiRQ

## Repository Directory Structure

- BR: bug information file (.xml)
- dataset-ben: bug reports (Dataset$_{Ben}$) in different categories (PE*, PE-, ST*, ST-, NL)
- dataset-pce: bug reports (Dataset$_{Ben}$) in different categories (PE*, PE-, ST*, ST-, NL)
- query-ben: queries for Dataset$_{Ben}$
- query-pco: queries for Dataset$_{Pco}$
- results-ben: results for Dataset$_{Ben}$
- results-pco: results for Dataset$_{Pco}$

## Dataset

### Dataset$_{Ben}$([Bench4BL](https://github.com/exatoa/Bench4BL))

- Apache: [CAMEL](https://github.com/apache/camel), [HBASE](https://github.com/apache/hbase), [HIVE](https://github.com/apache/hive)
- Commons: [CODEC](https://github.com/apache/commons-codec), [COLLECTIONS](https://github.com/apache/commons-collections), [COMPRESS](https://github.com/apache/commons-compress), [CONFIGURATION](https://github.com/apache/commons-configuration), [CRYPTO](https://github.com/apache/commons-crypto), [CSV](https://github.com/apache/commons-csv), [IO](https://github.com/apache/commons-io), [LANG](https://github.com/apache/commons-lang), [MATH](https://github.com/apache/commons-math), [WEAVER](https://github.com/apache/commons-weaver)
- JBoss: [ENTESB](https://github.com/jboss-fuse/fuse), [JBMETA](https://github.com/jboss/metadata), [ELY](https://github.com/wildfly-security/wildfly-elytron), [SWARM](https://github.com/thorntail/thorntail), [WFARQ](https://github.com/wildfly/wildfly-arquillian), [WFCORE](https://github.com/wildfly/wildfly-core.git), [WFLY](https://github.com/wildfly/wildfly.git), [WFMP](https://github.com/wildfly/wildfly-maven-plugin.git)
- Spring: [AMQP](https://github.com/spring-projects/spring-amqp), [ANDROID](https://github.com/spring-projects/spring-android), [BATCH](https://github.com/spring-projects/spring-batch), [BATCHADM](https://github.com/spring-projects/spring-batch-admin), [DATACMNS](https://github.com/spring-projects/spring-data-commons), [DATAGRAPH](https://github.com/spring-projects/spring-data-neo4j), [DATAJPA](https://github.com/spring-projects/spring-data-jpa), [DATAMONGO](https://github.com/spring-projects/spring-data-mongodb), [DATAREDIS](https://github.com/spring-projects/spring-data-redis), [DATAREST](https://github.com/spring-projects/spring-data-rest), [LDAP](https://github.com/spring-projects/spring-ldap), [MOBILE](https://github.com/spring-projects/spring-mobile), [ROO](https://github.com/spring-projects/spring-roo), [SEC](https://github.com/spring-projects/spring-security), [SECOAUTH](https://github.com/spring-projects/spring-security-oauth), [SGF](https://github.com/spring-projects/spring-data-gemfire), [SHDP](https://github.com/spring-projects/spring-hadoop), [SHL](https://github.com/spring-projects/spring-shell), [SOCIAL](https://github.com/spring-projects/spring-social), [SOCIALFB](https://github.com/spring-projects/spring-social-facebook), [SOCIALLI](https://github.com/spring-projects/spring-social-linkedin), [SOCIALTW](https://github.com/spring-projects/spring-social-twitter), [SPR](https://github.com/spring-projects/spring-framework), [SWF](https://github.com/spring-projects/spring-webflow), [SWS](https://github.com/spring-projects/spring-ws)

### Dataset$_{Pco}$

- Apache: [CAMEL](https://github.com/apache/camel), [HBASE](https://github.com/apache/hbase), [HIVE](https://github.com/apache/hive)
- Eclipse: [eclipse.jdt.core](https://github.com/eclipse-jdt/eclipse.jdt.core), [eclipse.jdt.debug](https://github.com/eclipse-jdt/eclipse.jdt.debug), [eclipse.jdt.ui](https://github.com/eclipse-jdt/eclipse.jdt.ui), [eclipse.platform.ui](https://github.com/eclipse-platform/eclipse.platform.ui)
- Tomcat: [Tomcat9](https://tomcat.apache.org/download-90.cgi)

## Query

### Query Construction

Set up open ai key in queryConstr.py

```shell
python queryConstr.py [-options]
```
- options
  - -b Bug reports directory
  - -t The type of the bug report (PE, ST, NL)
  - -o Output directory
  - -p Project name

- Examples

```shell
python queryConstr.py -b /Users/Documents/br/ -t PE -o /Users/Documents/output/ -p AMQP
```

### Query Reformulation

Set up open ai key in queryReform.py

```shell
python queryReform.py [-options]
```
- options
  - -b Bug reports directory
  - -ne Non-Existing Classes directory
  - -nb Non-Buggy Classes directory
  - -o Output directory
  - -p Project name

- Examples

```shell
python queryReform.py -b /Users/Documents/br/ -ne /Users/Documents/ne/ -nb /Users/Documents/nb/ -o /Users/Documents/output/ -p AMQP
```

## Fault Localization

```shell
java -jar BRTracer [-options]
```

- options
  - -q indicates the query directory
  - -b indicates the bug information file (.xml)
  - -s indicates the source code directory
  - -a indicates the alpha value (0.3) for combining vsmScore and simiScore
  - -w indicates the output directory
  - -n indicates the project name

This program will make temp directory : {working name}, and final result file :{working name}_output.txt

- Examples

```shell
java -jar BRTracer -q /Users/Documents/query/AMQP.txt -b /Users/Documents/AMQP.xml -s /Users/Documents/spring-amqp/ -a 0.3 -w /Users/Documents/output/ -n AMQP
```
