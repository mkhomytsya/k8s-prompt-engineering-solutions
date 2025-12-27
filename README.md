
# Kubernetes Infrastructure Automation: Prompt Engineering Portfolio

This repository contains a collection of Kubernetes manifests generated using advanced Prompt Engineering techniques. The goal of this project is to demonstrate how AI-driven solutions can automate and optimize infrastructure-as-code (IaC) workflows for modern DevOps environments.

## Project Overview
As part of a marketing automation initiative, these solutions showcase the ability to translate complex infrastructure requirements into precise, production-ready Kubernetes YAML manifests through structured English prompts.

## Prompt Engineering Solutions

| NAME | PROMPT | DESCRIPTION | EXAMPLE |
| :--- | :--- | :--- | :--- |
| **app.yaml** | Generate a Kubernetes Pod manifest named 'app' with labels 'app: demo' and 'run: demo'. Use image 'gcr.io/k8s-k3s/demo:v1.0.0' and expose port 8000 named 'http'. | Basic Pod definition for the demo application with specific labels and port configuration. | [yaml/app.yaml](./yaml/app.yaml) |
| **app-livenessProbe.yaml** | Create a Kubernetes Pod named 'app-livenessprob' in 'demo' namespace. Use image 'gcr.io/k8s-k3s/demo:v1.0.0'. Add a livenessProbe (httpGet, port 8000, path '/') with 5s initial delay, 1s timeout, and 10s period. | Pod with a health check (liveness probe) to automatically restart the container if the application hangs. | [yaml/app-livenessProbe.yaml](./yaml/app-livenessProbe.yaml) |
| **app-readinessProbe.yaml** | Generate a Pod named 'app-readinessprob' with image 'gcr.io/k8s-k3s/demo:v2.0.0'. Include a livenessProbe (path '/') and a readinessProbe (path '/ready') on port 8000 with specific thresholds. | Ensures the container only receives traffic when it has finished its startup tasks and is ready to serve. | [yaml/app-readinessProbe.yaml](./yaml/app-readinessProbe.yaml) |
| **app-volumeMounts.yaml** | Create a Pod named 'app-volume' using image 'gcr.io/kuar-demo/kuard-amd64:1'. Mount a hostPath volume from '/var/lib/app' on the host to '/data' inside the container. | Demonstrates data persistence by mounting a directory from the host node's filesystem into the pod. | [yaml/app-volumeMounts.yaml](./yaml/app-volumeMounts.yaml) |
| **app-cronjob.yaml** | Create a Kubernetes CronJob named 'app-cronjob' with a schedule '*/5 * * * *'. Use the 'bash' image to run the command 'echo Hello world'. Set restartPolicy to 'OnFailure'. | Defines a scheduled task that runs a specific containerized command every 5 minutes. | [yaml/app-cronjob.yaml](./yaml/app-cronjob.yaml) |
| **app-job.yaml** | Create a Kubernetes Job named 'app-job-rsync'. Mount a GCE Persistent Disk 'glow-data-disk-200' to '/data/input'. Use 'google/cloud-sdk' image to run 'gsutil -m rsync'. | A one-time task for synchronizing data from a Google Cloud Storage bucket to a persistent disk. | [yaml/app-job.yaml](./yaml/app-job.yaml) |
| **app-multicontainer.yaml** | Create a multi-container Pod 'app-multi-containers' with a shared emptyDir volume. Container 1: nginx. Container 2: debian writing the current date to the shared volume every second. | Illustrates the Sidecar pattern where two containers share a volume to exchange data in real-time. | [yaml/app-multicontainer.yaml](./yaml/app-multicontainer.yaml) |
| **app-resources.yaml** | Create a Pod 'app-resource' using image 'gcr.io/kuar-demo/kuard-amd64:1'. Define resource requests (100m CPU, 128Mi RAM) and limits (100m CPU, 256Mi RAM). | Sets resource constraints to ensure application stability and prevent "noisy neighbor" issues in a cluster. | [yaml/app-resources.yaml](./yaml/app-resources.yaml) |
| **app-secret-env.yaml** | Create a Pod 'app-secret-env' with a 'redis' image. Inject environment variables 'SECRET_USERNAME' and 'SECRET_PASSWORD' from a K8s Secret named 'mysecret1'. | Demonstrates secure credential management by injecting sensitive data from Secrets into environment variables. | [yaml/app-secret-env.yaml](./yaml/app-secret-env.yaml) |

## Methodology
The manifests were generated following the **Google Prompt Engineering principles**:
1. **Clarity:** Providing specific names, images, and versions.
2. **Context:** Defining namespaces, labels, and specific resource paths.
3. **Constraints:** Setting explicit limits for resources and probe thresholds.

## Tools Used
- **kubectl-ai**: For AI-powered manifest generation.
- **Google Cloud AI**: For prompt optimization and analysis.
