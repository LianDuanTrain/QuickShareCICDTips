
FROM carsharing/alpine-oraclejdk8-bash
# log-generator-0.0.2.jar is from https://github.com/Febbweiss/log-generator. 
ADD log-generator-0.0.2.jar /log-generator-0.0.2.jar
# Copy JMX
# jmx_prometheus_javaagent is from https://github.com/prometheus/jmx_exporter/releases
ADD jmx_prometheus_javaagent-0.16.1.jar /jmx_prometheus_javaagent-0.16.1.jar
ADD config.yaml /config.yaml
WORKDIR /var/log/java
ENTRYPOINT exec java $JAVA_OPTS -jar /log-generator-0.0.2.jar -n 15 -r 1000