# Personal Portfolio Website 🚀

### Docker + Nginx + Kubernetes (Minikube)

A minimalist, high-performance personal portfolio website built with HTML, CSS, and JavaScript, containerized using Docker (Nginx Alpine) and deployed on Kubernetes (Minikube) using imperative kubectl commands (no YAML files).

This project is designed to showcase DevOps fundamentals end-to-end: 
Docker → Docker Hub → Kubernetes.

## ✨ Key Highlights

- 🎨 Clean, modern, and responsive UI
  
- 🐳 Dockerized using nginx:alpine for lightweight performance
  
- ☁️ Deployed on Kubernetes (Minikube
  
- ⚙️ Kubernetes deployment without manifest (YAML) files
  
- 💼 DevOps-focused portfolio (AWS, Docker, Kubernetes, Terraform, Git)
  
- ⚡ Fast & lightweight (no frontend frameworks)

## 🧩 Project Architecture
Local Code → Docker Image → Docker Hub → Kubernetes (Minikube)

## Folder Structure
my-portfolio/
│── index.html
│── style.css
│── script.js
│── Dockerfile
│── .gitignore
│── .dockerignore
│──assets/
|    ├── linkedin.svg
│    ├── avtar.jpg
│── icons/
│    ├── c.svg
│    ├── python.svg
│    ├── git.svg
│    ├── github.svg
│    ├── terraform.svg
│    ├── kubernetes.svg
│    ├── docker.svg
│    ├── aws.svg
│    ├── gmail.svg
│    ├── linux.svg
│           

## 🐳 Dockerfile Overview

- Uses nginx:alpine as the base image

- Removes default Nginx HTML files

- Copies static website files to /usr/share/nginx/html

- Exposes port 80

- Runs Nginx in the foreground

## 📦 Docker Image (Prebuilt)

The Docker image is already built and pushed to Docker Hub.

Docker Hub Repository:
```
https://hub.docker.com/r/aakansha113/portfolio
```
Image Used:
```
aakansha113/portfolio:v1.1
```
### Note: Docker build & push steps are skipped here to keep the focus on Kubernetes deployment.

## ☸️ Kubernetes Deployment (Minikube – No YAML)
#### Step 1: Start Minikube
```
minikube start
```
Verify cluster:
```
kubectl get nodes
```
#### Step 2: Create Deployment (Imperative Command)
```
kubectl create deployment portfolio-app --image=aakansha113/portfolio:v1.1
```
Verify:
```
kubectl get deployments
kubectl get pods
```
#### step 3: Expose Deployment via Port Forward

Since you didn’t create a Service yet, you can use port-forwarding to map the pod’s port 80 to a local port (like 8080):

Check the Pod Name:
```
kubectl get pods
```
### You’ll see something like:
```
NAME                                READY   STATUS    RESTARTS   AGE
portfolio-app-5d69bd6bd-8jgbzbz      1/1   Running       0       2m

```
Copy the pod name (portfolio-app-5d69bd6bd-8jgbzbz example).

Port Forward Pod to Localhost 

```
kubectl port-forward pod/portfolio-app-5d69bd6bd-8jgbzbz 8080:80
```
Leave this terminal open while you’re testing.

Connect via cmd :
```
ssh -i your-key.pem -L 8080:localhost:8080 ubuntu@<EC2_PUBLIC_IP>
```
#### Explanation:

8080:80 → maps local port 8080 to pod port 80 (nginx default)

#### Step 4: Verify Website in Browser

Open your browser and go to:
```
http://localhost:8080
```
You should see your portfolio website running!

✅ Optional: You can also use minikube service to expose the service automatically instead of manual port-forward:

```
kubectl expose deployment portfolio-app --type=NodePort --port=80
minikube service portfolio-app
```
This will open the website in your default browser.

kubectl get svc will show the NodePort assigned by Minikube

## 📜 Logs & Debugging:
```
kubectl logs <pod-name>
```

## 🧹 Cleanup Resources:
```
kubectl delete service portfolio-app
kubectl delete deployment portfolio-app
minikube stop
```

##  🛠️ Technologies Used
- HTML5

- CSS3

- JavaScript

- Docker

- Nginx

- Kubernetes (Minikube)

- Git & GitHub

## 🎯 Learning Outcomes

- Docker image creation using Nginx

- Hosting images on Docker Hub

- Kubernetes deployment without YAML files

- Using kubectl imperative commands

- Service exposure using NodePort

### 👤 Author

#### Aakansha Hujare

### ⭐ Support

###### If you like this project, feel free to ⭐ star the repository!
