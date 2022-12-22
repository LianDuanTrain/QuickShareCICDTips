<!--# **👨‍⚕️ How to Add Health Check API to Microservice? | Spring Boot Actuator** -->   
# **👨‍⚕️ How to Add Health Check API to Spring Boot Microservice?** 
## **📑 Add Actuator Dependency in Spring Boot Project**
```
Maven
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
	</dependency>
```
Or 
```  
Gradle 
    dependencies {
        compile("org.springframework.boot:spring-boot-starter-actuator")
}
```     
<br>
<br>
<br>
<br>
<br>
<br>   
<br>
<br>
<br>      
📌 

## **✍🏼 Add Actuator Configuration Items in application.properties of Spring Boot Project**
```
management.endpoints.web.exposure.include=prometheus,health
management.endpoint.health.show-details=always
management.health.redis.enabled=false
```
📘[Spring Boot Production-ready Features](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html)      
📘[Auto-configured HealthIndicators](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html#actuator.endpoints.health)   

<br>
<br>
<br>
<br>
<br>
<br>   
<br>
<br>
<br>
<br>
<br>
<br>     
<br>
<br>
<br>   
📌 

## **👊 Hands-on Demo**   

- **<h3>How to Get Spring Boot based Microservice Demo Code?</h3>**   
         
   - Git Clone https://gitlab.com/lian.duan.training/dockerspringbootdemo.git
     - feature-add-sprintboot-healthcheck
- **<h3>Start Spring Boot based Microservice </h3>** 


- **<h3>Run Postman Collection to Test Health Check API</h3>** 


     - https://gitlab.com/lian.duan.training/dockerspringbootdemo/-/blob/feature-add-sprintboot-healthcheck/src/test/resource/SpringBootDemo%20APIs.postman_collection.json 


<br>
<br>
<br>
<br>
<br>
<br>   
<br>
<br>
<br>      
📌 