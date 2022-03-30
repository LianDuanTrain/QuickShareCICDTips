# How to Enable Authentication on Prometheus API and UI?

## Video Topics  
- How to Securely Deploy Prometheus?    
- How to Enable Authentication on Prometheus API and UI? 
- Verify Basic Authentication  

## How to Securely Deploy Prometheus?    

- [Transport Layer Security (TLS)](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#tls_config)
- Authentication
  - Basic authentication
  - <img src="oauth-logo-square.png" width="20">   [Oauth2](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#oauth2)
  - <img src="nginx-icon.png" width="20">   Nginx Reverse Proxy



## How to Enable Basic Authentication on Prometheus API and UI?
Demo YAML files are from   [How to Add Dashboard into Grafana | Import Dashboard into Grafana](https://youtu.be/mfCsMuehHy4)

- Changing Components 
  - <img src="prometheus.png" width="20"> Prometheus
  - <img src="prometheus.png" width="20"> Alertmanager
  - <img src="Grafana.png" width="20"> Change Grafana's DS



### Enable Basic Authentication 

- Get Encrypt Password. 
  - WEB: https://bcrypt-generator.com/
  - CMD: htpasswd -nBC 12 "" | tr -d ':\n'

- Create web.yaml file

```  
basic_auth_users:
    admin: $2a$12$Bpf2s5qEN8GlPbdOG0u8s.nTvwMHKEVXK22fsL.anHvaXTAmpL0za

```  

- Add web.yaml into Docker Command in alertmanager service  and prometheus service  of  docker-compose.yml
- Add basic_auth of alertmanagers in prometheus.yml  
```
alerting:
  alertmanagers:
  - scheme: http
    static_configs:
    - targets:
      - "alertmanager:9093"
    basic_auth:
      username: admin
      password: lian 
```
- Securely Deploy Prometheus   
      -  `docker-compose up -d` 
- Change Datastore in Grafana

## Verify Prometheus Basic Authentication
- Prometheus API
  - http://localhost:9090/api/v1/status/config
- Prometheus UI
  - http://localhost:9090
- Alertmanagers UI  
  - http://localhost:9093
- Grafana Dashboard:
  - http://localhost:3000




