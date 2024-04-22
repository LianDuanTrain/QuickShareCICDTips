<br>

📌

<br> 


# **☸️ Install Minikube on Mac** 
## **👨‍🏫 Hands-on Demo Goals**
- **<h3>🐳 Install Docker Desktop 24.0.7</h3>**
- **<h3>🍺 Install Homebrew Version: 4.2.15</h3>**
- **<h3>❄ Install Minikube Version: 1.32.0</h3>**
  - **🛤 Install Kubectl Version: 1.29.3**
- **<h3>🍎 MAC OS Version: 14.3.1</h3>**
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
<br>
<br>    
📌 


## **🐳 Install Docker Desktop on Mac**
- **<h3>⚙️ Check CPU Type</h3>**
  - **Apple silicon(M1/M2/M3...)**
  - **Intel chip**
- **<h3>🛂 At least 4 GB of RAM</h3>**
- **<h3>📥 Download Link: https://docs.docker.com/desktop/install/mac-install/.</h3>** 

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
<br>
<br>    
📌 



## **🍺 Install Homebrew**
- **<h3>🔧 Commands</h3>**
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew config
```
- **<h3>📚 Document:  https://docs.brew.sh/Installation</h3>**


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
<br>
<br>    
📌 


## **☸️ Install Minikube**
- **<h3>🔧 Commands</h3>**
```
brew install minikube
minikube start  
minikube status
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
<br>
<br>  
<br>
<br>    
📌 


## **Install Kubectl**
- **<h3>🔧 Commands</h3>**
```
brew install kubectl
kubectl version 
minikube kubectl -- get po -A 
```
- **<h3>Document: https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/#install-with-homebrew-on-macos</h3>**

