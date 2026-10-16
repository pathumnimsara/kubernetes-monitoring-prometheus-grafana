\# PromQL Queries for Kubernetes Monitoring



PromQL (Prometheus Query Language) is used to query and analyse metrics collected by Prometheus.



\## 1. Student API CPU Usage



```promql

sum(rate(container\_cpu\_usage\_seconds\_total{pod=\~".\*student-api.\*"}\[5m]))

```



\*\*Purpose:\*\* Measures the total CPU usage rate of containers matching the Student API pod name pattern.



\## 2. Student API Memory Usage



```promql

sum(container\_memory\_working\_set\_bytes{pod=\~".\*student-api.\*"}) / 1024 / 1024

```



\*\*Purpose:\*\* Calculates the total working memory usage in MiB for matching containers.



\## 3. Student API Container Restarts



```promql

sum(kube\_pod\_container\_status\_restarts\_total{namespace="default", pod=\~".\*student-api.\*"})

```



\*\*Purpose:\*\* Shows the total reported container restart counts for matching Student API pods.



\## 4. Available Student API Replicas



```promql

kube\_deployment\_status\_replicas\_available{namespace="default", deployment="student-api"}

```



\*\*Purpose:\*\* Shows how many replicas of the Student API deployment are currently available.



\## 5. Student API Pod Information



```promql

sum(kube\_pod\_info{namespace="default", pod=\~"student-api-.\*"})

```



\*\*Purpose:\*\* Counts matching Student API pod information series in the default namespace.



\## Important Notes



\- These queries depend on the relevant metrics being available in Prometheus.

\- Pod names, namespaces, and deployment names must match the Kubernetes environment.

\- CPU and memory queries return aggregate values for matching containers; verify the selected series when interpreting results.

\- A restart count is a cumulative counter, not necessarily the number of restarts during the last five minutes.

