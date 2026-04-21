\# 🚀 Kubernetes HPA Autoscaling Demo



This project demonstrates \*\*Horizontal Pod Autoscaling (HPA)\*\* in Kubernetes using CPU-based scaling.



It shows how Kubernetes automatically scales pods up and down based on application load.



\---



\## 📌 Project Overview



\* Deploy a sample application

\* Expose application using Service

\* Install Metrics Server (required for HPA)

\* Configure HPA based on CPU utilization

\* Generate load to trigger scaling

\* Observe automatic scaling behavior



\---



\## 🧠 Concepts Covered



\* Horizontal Pod Autoscaler (HPA)

\* Metrics Server

\* CPU Requests \& Limits

\* Load Testing in Kubernetes



\---



\## ⚙️ Prerequisites



\* Kubernetes cluster (Kind / Minikube)

\* kubectl configured



\---



\## 📂 Project Structure



```

k8s-hpa-autoscaling-demo/

│

├── manifests/

│   ├── deploy.yaml

│   ├── hpa.yaml

│   ├── metrics-server.yaml

│

├── screenshots/

│

└── README.md

```



\---



\## 🚀 Step-by-Step Implementation



\### 1️⃣ Install Metrics Server



```bash

kubectl apply -f manifests/metrics-server.yaml

```



Verify:



```bash

kubectl top pods

```



\---



\### 2️⃣ Deploy Application \& Expose Service



```bash

kubectl apply -f manifests/deploy.yaml

```



\---



\### 3️⃣ Create HPA



```bash

kubectl apply -f manifests/hpa.yaml

```



OR



```bash

kubectl autoscale deployment my-app --cpu-percent=50 --min=1 --max=10

```



\---



\### 4️⃣ Check HPA



```bash

kubectl get hpa

```



\---



\### 5️⃣ Generate Load



```bash

kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.1; do wget -q -O- http://php-apache; done"

```



\---



\### 6️⃣ Watch Scaling



```bash

kubectl get hpa -w

```



\---



\## 📸 Screenshots



All command outputs and observations are captured in the **[screenshots/](./screenshots)** folder.

\---



\## 📊 Key Points



\* HPA automatically adjusts pod count based on CPU usage

\* Metrics Server is required to provide resource metrics

\* CPU requests must be defined in deployment

\* Scaling happens dynamically based on load



\---



\## 🏁 Conclusion



This project demonstrates how Kubernetes handles \*\*automatic scaling\*\* using HPA to maintain application performance under varying load.



\---



\## 👨‍💻 Author



Kiran Kumatkar

