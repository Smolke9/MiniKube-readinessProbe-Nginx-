
# 🌐 Nginx Pod with Readiness Probe on Minikube

This project shows how to deploy an Nginx pod with a **readinessProbe** in a **Minikube** Kubernetes cluster. The readiness probe checks if Nginx is ready to serve HTTP traffic.

---

## 📁 Project Structure

```
nginx-readiness/
├── nginx-readiness.yaml   # Kubernetes pod with readinessProbe
└── README.md              # Project documentation
```

---

## 🛠️ Prerequisites

- ✅ Minikube installed and running
- ✅ kubectl configured with Minikube

Start Minikube:
```bash
minikube start
```

---

## 📄 Step 1: Create the YAML file

Create a file named `nginx-readiness.yaml`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-readiness
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
    readinessProbe:
      httpGet:
        path: /
        port: 80
      initialDelaySeconds: 5
      periodSeconds: 5
```

---

## 🚀 Step 2: Apply the YAML Configuration

Deploy the pod using:
```bash
kubectl apply -f nginx-readiness.yaml
```

---

## 🔍 Step 3: Check Readiness Status

Check the pod status:
```bash
kubectl get pods
kubectl describe pod nginx-readiness
```

You should see readiness probe configuration and status under "Conditions".

---

## 🧪 Step 4: Simulate Probe Failure (Optional)

Delete the index.html page to simulate readiness failure:

```bash
kubectl exec -it nginx-readiness -- /bin/bash
rm /usr/share/nginx/html/index.html
exit
```

Check the status again:
```bash
kubectl get pods
```

You should see the pod marked as **Not Ready** (`0/1`).

---

## 🧹 Cleanup

To delete the pod:
```bash
kubectl delete pod nginx-readiness
```

---

## 📸 Screenshots (Optional)

> Add your screenshots and update the paths.

![Apply YAML](./apply-readiness-yaml.jpg)


---

## 🧑‍💻 Author

**Suraj Molke**  
[GitHub](https://github.com/smolke9)

---

## 🏷️ Tags

`#kubernetes` `#nginx` `#minikube` `#readinessprobe` `#devops` `#yaml`
