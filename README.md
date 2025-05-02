# 🐳 Flask App in Kubernetes (flask-k8s-demo)

This is a minimal Flask app deployed in Kubernetes using raw YAML files. I built this to practise container orchestration using Kubernetes concepts like **Pods**, **Services**, and **Deployments** — all run locally using Minikube.

---

## ✅ What This Project Covers

- Containerised a simple Flask app using Docker
- Loaded the image into Minikube's internal image registry
- Created a Kubernetes **Pod** and later upgraded it to a **Deployment**
- Used Kubernetes **labels** and **selectors** to link resources
- Exposed the app with a **ClusterIP Service**
- Accessed the app locally using `kubectl port-forward`
- Debugged common K8s issues like `ImagePullBackOff` and Service mismatches

---

## Folder Structure

<pre> flask-k8s-demo/ ├── app.py # Flask app ├── requirements.txt # Python dependencies ├── Dockerfile # Builds a lightweight Flask image ├── pod.yaml # (Initial) K8s Pod definition ├── deployment.yaml # Production-ready Deployment with labels ├── service.yaml # ClusterIP Service to expose the app </pre>

## 1. Start Minikube

```bash
minikube start
```

## 2. Build and load image

```bash
docker build -t flak-k8s-demo .
minikube image load flask-k8s-demo
```

## 3. Apply Kubernetes configs

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

## 4. Access the app

```bash
kubectl port-forward service/flask-service 5000:80
```

Then open: http://localhost:5000

## Output

```csharp
👋 Hello from Flask inside Kubernetes!
```
