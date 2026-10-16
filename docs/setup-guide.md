\# Prometheus and Grafana Setup Guide



\## 1. Prerequisites



Install or configure the following tools:



\- Docker Desktop

\- Kubernetes enabled in Docker Desktop

\- kubectl

\- Helm

\- Git



Verify the tools:



```powershell

kubectl version --client

helm version

kubectl get nodes

```



\## 2. Create the Monitoring Namespace



```powershell

kubectl create namespace monitoring

```



If the namespace already exists, continue to the next step.



\## 3. Install Prometheus



Add the Prometheus Helm repository:



```powershell

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo update

```



Install Prometheus:



```powershell

helm install prometheus prometheus-community/prometheus -n monitoring

```



If Prometheus is already installed, inspect the existing release before attempting installation again.



\## 4. Access Prometheus



```powershell

kubectl port-forward -n monitoring svc/prometheus-server 9090:80

```



Open http://localhost:9090 in your browser.



\## 5. Install Grafana



Add the Grafana Helm repository:



```powershell

helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

```



Install Grafana:



```powershell

helm install grafana grafana/grafana -n monitoring

```



If Grafana is already installed, inspect the existing release before attempting installation again.



\## 6. Access Grafana



```powershell

kubectl port-forward -n monitoring svc/grafana 3000:80

```



Open http://localhost:3000 in your browser.



Retrieve the initial admin password securely using the chart's documented secret instructions. Do not commit passwords or other credentials to GitHub.



\## 7. Configure the Data Source



In Grafana:



1\. Open Connections and Data sources.

2\. Add Prometheus.

3\. Set the URL to `http://prometheus-server.monitoring.svc.cluster.local`.

4\. Save and test the connection.



\## 8. Verify the Installation



```powershell

kubectl get pods -n monitoring

kubectl get services -n monitoring

```



\## Important Notes



\- These are general installation commands for a local learning environment.

\- Existing installations may use custom Helm values.

\- Prometheus and Grafana chart versions and resource requirements may change.

\- Configure persistence, authentication, security, and alert notifications before considering a production deployment.

