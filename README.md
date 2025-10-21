---
Firstly Launch an instance.
In instance install docker and k8s minikube.
##   1: Create a Simple Python Application

Let’s build a small Flask web app.

**📁 Folder Structure**

```
python-docker-k8s/
├── app.py
├── requirements.txt
└── Dockerfile
```
### 🔹 requirements.txt

```
Flask==3.0.3
```

---

## 2: Create Dockerfile
## 3: Build and Run Docker Container

### Build Docker image

```bash
docker build -t python-docker-k8s:latest .
```

### Run Docker container

```bash
docker run -d -p 5000:5000 python-docker-k8s
```

### Test

 `http://localhost:5000`
You should see:

```
Hello from Python App running on Docker & Kubernetes!
```

---

## 4: Create Kubernetes Manifests

Create a folder named `k8s/`

```
python-docker-k8s/
├── app.py
├── requirements.txt
├── Dockerfile
└── k8s/
    ├── deployment.yaml
    └── service.yaml
```

### 🔹 deployment.yaml
---

### 🔹 service.yaml
---

## 5: Deploy to Kubernetes (Minikube Example)

### Start Minikube

```bash
minikube start 
```

### Apply Deployment & Service

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### Check Pods

```bash
kubectl get pods
```

### Check Services

```bash
kubectl get svc
```

### Get Access URL

```bash
minikube service python-app-service
```

It will open our app in the browser! 

---

```bash
docker tag python-docker-k8s <your_dockerhub_username>/python-docker-k8s:v1
docker push <your_dockerhub_username>/python-docker-k8s:v1
```

Then update the image name in `deployment.yaml`:

```yaml
image: <your_dockerhub_username>/python-docker-k8s:v1
imagePullPolicy: Always
```

---

##  RESULT

We have:

* Built a Python Flask app
* Containerized it using Docker
* Deployed it to Kubernetes
* Accessed it via a NodePort service

---
