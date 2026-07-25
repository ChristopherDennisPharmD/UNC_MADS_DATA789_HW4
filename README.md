DATA-789 Data Science and AI in the Cloud
<br>Homework #4
<br>Christopher R. Dennis

# TrustBank Fraud Detection on Kubernetes

This project deploys the provided TrustBank fraud-prediction API and Redis to Kubernetes. It demonstrates resource management, health monitoring, horizontal autoscaling, self-healing, rolling updates, and blue-green deployment.

## Kubernetes Configuration

The baseline deployment includes:

- Three API replicas
- CPU requests of 100m and limits of 250m
- Memory requests of 128Mi and limits of 192Mi
- Liveness and readiness probes targeting /health
- An owner label on the Deployment and pod template
- A LoadBalancer Service
- An HPA configured for 40% CPU utilization, with 3–8 replicas
- A rolling-update strategy with maxUnavailable: 0 and maxSurge: 1

The health probes use /health because it is a lightweight endpoint that does not require a prediction payload or invoke the full prediction workflow.