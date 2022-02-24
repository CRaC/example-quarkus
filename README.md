# example-quarkus project

## Building

### Quarkus

1. Build, install locally: https://github.com/CRaC/quarkus, branch `main-crac` (Quarkus development branch + CRaC changes)

2. Use maven to build
```
mvn package
```

## Running

Please refer to [README](https://github.com/CRaC/docs#users-flow) for details.

### Preparing the image
1. Run the [JDK](https://github.com/CRaC/openjdk-builds/releases/) (at least `17-crac+2`) in the checkpoint mode:

```
$JAVA_HOME/bin/java -XX:CRaCCheckpointTo=cr -jar target/quarkus-app/quarkus-run.jar
```
2. Warm-up the instance
```
siege -c 1 -r 100000 -b http://localhost:8080/hello
```
3. Request checkpoint
```
jcmd target/quarkus-app/quarkus-run.jar JDK.checkpoint
```

### Restoring

```
$JAVA_HOME/bin/java -XX:CRaCRestoreFrom=cr
```
