📌
# **🌱How to Shutdown Spring Boot Application Gracefully in Docker Container?**
## **📣What We Will Cover:**      

- **<h3>🐳What is Docker Container Shutdown Process?</h3>**
  
- **<h3>📑How to Config Spring Boot Application Gracefully Shutdown?</h3>**
  
- **<h3>🖐️Hands-On Demo</h3>**

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

##  **🐳What is Docker Container Shutdown Process?**

- **<h3>⛔docker stop [CONTAINER_ID/NAME]</h3>**

- **<h3>📡SIGTERM signal to the container process </h3>**
  
  - **<h3>kill -15 [PID]</h3>**


  

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

##  **📑How to Config Spring Boot Application Gracefully Shutdown?**

- **<h3>👩‍💻YAML File</h3>**  
    `server:`  
     &nbsp; &nbsp;  `shutdown: graceful`  
    `spring:`   
      &nbsp; &nbsp; `lifecycle: `   
        &nbsp; &nbsp; &nbsp; &nbsp;  `timeout-per-shutdown-phase: "10s" `   
 




- **<h3>📃Properties File</h3>**  

 
    `server.shutdown=graceful`   
    `spring.lifecycle.timeout-per-shutdown-phase=10s` 

- 📚 [Graceful Shutdown](https://docs.spring.io/spring-boot/docs/current/reference/html/web.html#web.graceful-shutdown)  
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

##  **🖐️Hands-On Demo**
- **<h3>👨‍💻Source Code:</h3>** 
  
  - Spring Boot Version: 3.0.2
  - Git:https://gitlab.com/lian.duan.training/dockerspringbootdemo.git
    - branch: feature-1-11-How-to-Shutdown-Spring-Boot-Application-Gracefully-in-Docker-Container
- **<h3>🌌Docker Image: lianduantraining/springbootdemo:V12</h3>** 
  - Docker Based on Image - openjdk:17.0.2-jdk
- **<h3>🏷️Docker Version: 20.10.21</h3>** 
- **<h3>🎬[Kubernetes Security| How to Reduce Docker Image Size?](https://studio.youtube.com/video/AWLOEha30Yk/edit)</h3>**
- **<h3>🎬[Use GitLab CI/CD Variables and Pipeline to Push Docker Images](https://youtu.be/lwDYRSdkTrk)</h3>**
- **<h3>🛠️Commands</h3>**

      docker run --name=GracefullyShutdown -d   --stop-timeout=60  -p 9999:9999 lianduantraining/springbootdemo:V12
      docker ps
      docker logs GracefullyShutdown
      docker stop GracefullyShutdown
      docker logs GracefullyShutdown




- **<h3>✅Check Point</h3>** 
  - <div id="wrapper-div" style="box-shadow: 0px 2px 25px rgba(0, 0, 0, .25);  width:fit-content"  width="400px"><image src='./images/result.jpg'  > </div> 

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