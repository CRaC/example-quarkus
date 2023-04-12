# example-quarkus project

## Building

```
mvn package
```

## Running

Please refer to [README](https://github.com/CRaC/docs#users-flow) for details.

### Preparing the image
1. Run the [JDK](README.md#JDK) in the checkpoint mode
```
$JAVA_HOME/bin/java -XX:CRaCCheckpointTo=cr -jar target/quarkus-app/quarkus-run.jar
```
2. Warm-up the instance
```
siege -c 1 -r 100000 -b http://localhost:8080/hello
```
3. Request checkpoint
```
jcmd quarkus-app/quarkus-run.jar JDK.checkpoint
```

### Restoring

```
$JAVA_HOME/bin/java -XX:CRaCRestoreFrom=cr
```
