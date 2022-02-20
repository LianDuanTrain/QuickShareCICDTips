# How to Add JAVA_OPTS in Docker?

##  The video Topics are 
- How to Add JAVA_OPTS in Docker?
- Quick Demo
- Verify

# How to Add JAVA_OPTS in Docker?
## Add JAVA_OPTS to ENTRYPOINT in Dockerfile
```
ENTRYPOINT exec java $JAVA_OPTS
```
## Add -e in docker run
```
-e JAVA_OPTS='-javaagent:/jmx_prometheus_javaagent-0.16.1.jar=9999:/config.yaml'
```
# Quick Demo
## Purpose 
Use JAVA_OPTS to load Jmx Prometheus Javaagent in Java App
## Jars 
- jmx_prometheus_javaagent-0.16.1.jar
- log-generator-0.0.2.jar
## Dockerfile
```
FROM carsharing/alpine-oraclejdk8-bash
# log-generator-0.0.2.jar is from https://github.com/Febbweiss/log-generator. 
ADD log-generator-0.0.2.jar /log-generator-0.0.2.jar
# Copy JMX
ADD jmx_prometheus_javaagent-0.16.1.jar /jmx_prometheus_javaagent-0.16.1.jar
ADD config.yaml /config.yaml
WORKDIR /var/log/java
ENTRYPOINT exec java $JAVA_OPTS -jar /log-generator-0.0.2.jar -n 15 -r 1000
```
## Build Docker Image  
- docker build -t lianduantraining/log-generator-jmx-exporter:v1 .
## Run Docker
- docker run -e JAVA_OPTS='-javaagent:/jmx_prometheus_javaagent-0.16.1.jar=9999:/config.yaml'  --rm -d -p 9999:9999  lianduantraining/log-generator-jmx-exporter:v1

# Verify
- curl localhost:9999 

ICO is form https://www.pngegg.com/en/png-iwwhd
