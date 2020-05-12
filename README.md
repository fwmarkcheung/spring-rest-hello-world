# Spring REST Hello World Example

Article link : https://www.mkyong.com/spring-boot/spring-rest-hello-world-example/

## 1. How to start
```
$ mvn spring-boot:run

$ curl -v localhost:8080/api/books

Add actuator

localhost:8080/api/actuator

Health link:

http://localhost:8080/api/actuator/health

http://localhost:8080/api/actuator/prometheus

https://www.javadevjournal.com/spring-boot/spring-boot-actuator-with-prometheus/

Needed to add the following to the application.properties to enable prometheus

management.endpoint.metrics.enabled=true
management.endpoints.web.exposure.include=*
management.endpoint.prometheus.enabled=true
management.metrics.export.prometheus.enabled=true

To create prometheus server in docker:

1. docker pull prom/prometheus
2. docker run -d -p 9090:9090 -v /Users/markcheung/JBossGigs/videotron/spring-rest-hello-world/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

To remove the prometheus container:

1. docker ps to get the container id
2. docker stop <container id>
