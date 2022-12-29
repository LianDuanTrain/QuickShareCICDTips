# **🐳 How (and Why) to Add a Docker Container Health Check？**    

## **📣What we will cover:**      

- **<h3>❓Why does Docker Container Need HealthCheck?</h3>** 
     
- **<h3>📑How to Add a Health Check to Docker Container?</h3>** 
      
- **<h3>🖐️Hands-on Demo: Container Build in Health Check</h3>**     

- **<h3>🖐️Hands-on Demo: Docker Run Command Overwrite Container Build in Health Check</h3>**

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

## **🔎Why does Docker Container Need HealthCheck?**

- **<h3>Checking Resource Health </h3>**
  
- **<h3>Mounting Operation Tool</h3>**
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
<br>  
<br>
<br>    
📌 

## **🏃How to Add a Health Check to Docker Container?**

- **<h3>Docker uses the command’s exit code to determine the container’s healthiness</h3>**   
  
     - Healthy  0 
     - Unhealthy 1
     - Reserved by Docker 2

- **<h3>Health Check Options Available</h3>**    
  
  - interval  (default: 30s)
  - start-period  (default: 0s)
  - retries  (default: 3)
  - timeout  (default: 30s)  

- **<h3>Add Health Check to Docker Container</h3>**  
  - HEALTHCHECK in Dickerfile 
  - Docker Run Command 



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

## **🖐️ Hands-on Demo - Container Build in Health Check**  
- **<h3>Pre-request</h3>**
  - ```RUN apt-get install -y curl ``` in Doeckerfile
  - APP has Health Check Endpoint 
  - Docker ENV 

```
Example:
HEALTHCHECK --interval=30s --timeout=3s \
CMD curl -f http://localhost:9999/actuator/health || exit 1
```
 📚[healthcheck](https://docs.docker.com/engine/reference/builder/#healthcheck) 
```
  - docker run --name=healthCheckTest -d  lianduantraining/springbootdemo:V11
  - docker ps
  - docker inspect healthCheckTest | jq '.[0].State.Health'
  - docker rm -f  healthCheckTest
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
<br>   
<br>
<br>
<br>  
<br>
<br>
<br>     
📌 

## **🖐️ Hands-on Demo- Docker Run Command Overwrite Container Build in Health Check**  
- **<h3>Pre-request</h3>**
  - ```RUN apt-get install -y curl ``` in Doeckerfile
  - APP has Health Check Endpoint 
  - Docker ENV  
- **<h3>Docker Run Command Health Check Types</h3>** 
  - **<h3>Create Health Check</h3>**
  - **<h3>Overwrite Container Build in Health Check</h3>**  
      
    
📚[docker run --health-cmd,--health-interval,--health-retries,--health-start-period,--health-timeout](https://docs.docker.com/engine/reference/commandline/run/)  

```
Build in Health Check:
HEALTHCHECK --interval=30s --timeout=3s \
CMD curl -f http://localhost:9999/actuator/health || exit 1
```
CMD-SHELL, curl -f http://localhost:9999/actuator/health/ping || exit 1
```
  - docker run --name=healthCheckTest -d  --health-cmd='curl -f http://localhost:9999/actuator/health/ping || exit 1'  --health-interval=2s  lianduantraining/springbootdemo:V11
  - docker ps
  - docker inspect healthCheckTest | jq '.[0].State.Health'
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
<br>   
<br>
<br>
<br>  
<br>
<br>
<br>     
📌 