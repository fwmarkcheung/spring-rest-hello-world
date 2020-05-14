# Spring REST Hello World Example

Article link : https://www.mkyong.com/spring-boot/spring-rest-hello-world-example/

## 1. How to start
```
$ mvn spring-boot:run

$ curl -v localhost:8080/books

Promethemus link is configured at

localhost:8080/metrics for OCP to scrape


To create prometheus server in docker:

1. docker pull prom/prometheus
2. docker run -d -p 9090:9090 -v /Users/markcheung/JBossGigs/videotron/spring-rest-hello-world/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

To remove the prometheus container:

1. docker ps to get the container id
2. docker stop <container id>

To create the app in openshift:

1. oc new-project springboot-prometheus
2. oc new-app redhat-openjdk18-openshift:1.5~https://github.com/fwmarkcheung/spring-rest-hello-world.git --name=springboot-prometheus
3. oc expose svc/springboot-prometheus
4. The available promemtheus metrics will be available through http://<route url>/metrics

To enable app monitoring in OCP (Need admin access)

1. Enable the techPreviewUserWorkload and make sure the prometheus-user-workload pods were created as described in

https://docs.openshift.com/container-platform/4.4/monitoring/monitoring-your-own-services.html

2. Create the service monitor

oc apply -f springboot-service-monitor.yml 

3. To check metric, enter the expression in the OCP Web Console.  See the graph.  Metric expression is available from http://<route>/metrics

4. Optionally create an alert rule

 oc apply -f springboot-app-alerting-rule.yam




--------------------------------
Default actuator link is disable.  
--------------------------------

Check application.properties

Default links:

localhost:8080/actuator

Health link:

http://localhost:8080/api/actuator/health

http://localhost:8080/api/actuator/prometheus

https://www.javadevjournal.com/spring-boot/spring-boot-actuator-with-prometheus/

Needed to add the management properties to the application.properties to enable prometheus
