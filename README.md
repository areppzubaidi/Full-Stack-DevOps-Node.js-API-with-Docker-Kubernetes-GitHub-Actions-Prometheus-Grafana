# 🚀 Full-Stack DevOps: Node.js API with Docker, Kubernetes, GitHub Actions, Prometheus & Grafana

This project demonstrates a fully containerized and monitored Node.js + Express API. It uses:

- 🐳 Docker for containerization  
- ☸️ Kubernetes for deployment  
- 🤖 GitHub Actions for CI/CD  
- 📈 Prometheus & Grafana for metrics and monitoring  

Perfect for DevOps and cloud infrastructure learning or demonstration.

---

## 🔧 Tech Stack

| Technology       | Purpose                             |
|------------------|--------------------------------------|
| Node.js + Express | Backend API                         |
| Docker            | Containerize the app                |
| GitHub Actions    | Automate build, test, and Dockerize |
| Kubernetes        | Orchestrate deployment              |
| Prometheus        | Collect runtime metrics             |
| Grafana           | Visualize metrics in dashboards     |

---

## 📁 Project Structure

```

simple-node-api/
├── .github/
│   └── workflows/
│       └── ci-cd.yml          # GitHub Actions pipeline
├── k8s/
│   ├── deployment.yaml        # Node.js API deployment
│   ├── service.yaml           # Node.js API service
│   ├── prometheus-config.yaml# Prometheus scrape config
│   ├── prometheus-deploy.yaml# Prometheus deployment + service
│   └── grafana-deploy.yaml   # Grafana deployment + service
├── src/
│   └── index.js              # Express API + Prometheus metrics
├── Dockerfile                # Docker image build file
├── .dockerignore             # Exclude files from Docker image
├── package.json              # App dependencies
└── README.md                 # You're reading it :)

````

---

## 🧑‍💻 Local Development

### 1️⃣ Clone the Repo
```bash
git clone https://github.com/your-username/simple-node-api.git
cd simple-node-api
````

### 2️⃣ Install Dependencies

```bash
npm install
```

### 3️⃣ Run the App

```bash
npm start  # Runs on http://localhost:3000
```

### 4️⃣ Test the Metrics Endpoint

```bash
curl http://localhost:3000/metrics
```

---

## 🐳 Run with Docker

### Build the Image

```bash
docker build -t simple-node-api .
```

### Run the Container

```bash
docker run -p 3000:3000 simple-node-api
```

---

## 🤖 GitHub Actions CI/CD

### Location

`.github/workflows/ci-cd.yml`

### What It Does

| Step         | Task                                 |
| ------------ | ------------------------------------ |
| Checkout     | Pulls source code                    |
| Setup Node   | Uses Node.js 18                      |
| Install Deps | `npm install`                        |
| Run Tests    | `npm test` (currently a placeholder) |
| Docker Build | `docker build -t simple-node-api .`  |

> ✅ Triggered on push to `main`

---

## ☸️ Deploy to Kubernetes

### Prerequisites

* Kubernetes cluster (e.g. Minikube, EKS, GKE)
* `kubectl` installed
* Docker image pushed to Docker Hub

### Push Image

```bash
docker build -t your-dockerhub/simple-node-api .
docker push your-dockerhub/simple-node-api
```

### Apply K8s Manifests

```bash
kubectl apply -f k8s/
```

---

## 📈 Prometheus & Grafana Monitoring

### 📊 Metrics

The app exposes metrics on `/metrics` using [prom-client](https://github.com/siimon/prom-client).

Sample metric:

```
# HELP node_app_requests_total Total number of requests
# TYPE node_app_requests_total counter
node_app_requests_total 7
```

### 🔧 Prometheus

* Configured in `k8s/prometheus-config.yaml`
* Scrapes `simple-node-service:3000/metrics`

### 🖥 Grafana

* Access with: `minikube service grafana`
* Default login: `admin / admin`
* Add Prometheus as a data source (`http://prometheus:9090`)

---

## 💻 Minikube Test Guide

```bash
minikube start

# Deploy everything
kubectl apply -f k8s/

# Access services
minikube service grafana
minikube service prometheus
minikube service simple-node-service
```

---

## 🧪 Testing & Validation

### Test metrics endpoint:

```bash
curl http://localhost:3000/metrics
```

### View in Prometheus:

Visit http\://\<minikube\_ip>:30090 and query:

```
node_app_requests_total
```

### Create Grafana dashboard:

* Add Prometheus data source
* Create panel showing `node_app_requests_total`

---

## 📦 What's Next?

* Add Jest test coverage
* Add liveness/readiness probes in deployment.yaml
* Deploy to managed clusters (e.g., EKS, GKE, AKS)
* Add alerts in Prometheus + email/Slack integration

---

## 👤 Author

**Nur Ariff**
GitHub: [@your-username](https://github.com/your-username)
Portfolio: [nur-ariff.dev](https://nur-ariff.dev) *(optional)*

---

## 📄 License

MIT License – free to use and modify.

```

---

Would you like me to:

- Zip the full project?
- Generate a sample Grafana dashboard JSON?
- Add Helm chart for this setup?

You're now DevOps-pro-ready 🧠🔥
```
