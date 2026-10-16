\# Monitoring Architecture



\## Overview



This project uses Prometheus and Grafana to monitor a Student API running in a local Kubernetes cluster.



\## Architecture



```mermaid

flowchart TD

&#x20;   A\[Student API Pods] --> B\[Kubernetes Metrics]

&#x20;   B --> C\[Prometheus]

&#x20;   C --> D\[PromQL Queries]

&#x20;   D --> E\[Grafana Dashboard]

&#x20;   E --> F\[Monitoring and Alerts]

```



\## Components



\- \*\*Kubernetes:\*\* Runs the Student API containers.

\- \*\*Prometheus:\*\* Collects and stores available metrics.

\- \*\*PromQL:\*\* Queries metrics stored in Prometheus.

\- \*\*Grafana:\*\* Displays monitoring dashboards and evaluates alert rules.

\- \*\*kubectl:\*\* Helps inspect and manage Kubernetes resources.



\## Monitoring Scope



The dashboard includes Student API replica availability, CPU usage, memory usage, and container restart metrics.



\## Environment



The project was tested with Docker Desktop Kubernetes. Some infrastructure metrics may be unavailable because this is a local learning environment.

