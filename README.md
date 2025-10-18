# LemiciIQ DevOps Exercise

# Part-1 : Version Control (Git & SSH):

## 1. Difference between git pull vs git fetch:

- git fetch: It downloads changes from remote repository but does not merge them automatically.  
- git pull: It downloads and merges changes from the remote repository into your branch.


## 2. Git Merge conflict example:
I created 2 branches(feature-A & feature-B) and made changes to the same file. When merging, git gave a following conflict:


```
Auto-merging code.txt
CONFLICT (add/add): Merge conflict in code.txt
Automatic merge failed; fix conflicts and then commit the result.

```


In order to perform this conflict I manually edited the file to keep both the changes:
"Hello from Feature-A and Feature-B"
and added the file to repository


# Part-2: Docker & Containerization: 

## 1. Difference between Dockerfile, Docker Image & Docker Container:

- Dockerfile: This file contains step by step instructions/commands to build our application.
- Docker Image: It is portable package that contains our application, created using dockerfile.
- Docker Container: It is a running instance of our application. Docker containers are lightweight, ephimeral and portable in nature.

## 2. How you would reduce the image size if your first build is too large: 
1. We can use smaller and lighter base images like alpine, python-slim.
2. We can optimize layers in docker image by executing multiple commands in a single command.
3. We can avoid copying unnecessary files into docker by mentioning those file in .dockerignore file.

## 3. Application Container:
![Container Stats](./images/docker.png)

# Part-3: Kubernetes: 
## 1. Difference between Pods, Deployment, Service: 
- Pods: Pods are the smallest deployable units that runs containerized application inside a Kuberenetes cluster.
- Deployment: Deployment is a high level Kubernetes api object that manages pods. It ensures that the desired numbers of pods are always running and provides autoscaling.
- Service: Another high level Kuberenetes api object defines a policy to access the pods. It load balances the traffic across pods. There are 3 types of services mainly:
     1. Loadbalancer
     2. NodePort
     3. ClusterIP

## 2. Why do we need EKS instead of running Kubernetes on VMs:
We use Elastic Kuberentes Service to avoid the operational complexity of managing Kubernetes by ourselves on VMs. EKS handles the control plane, scaling, upgrades, security that allows teams to focus on applications rather than cluster maintenance.


# Part-4: CI-CD Pipeline:
## 2. Explain how this pipeline would change if we wanted to deploy to Kubernetes after building:
- After building and pushing the Docker image in Jenkins, we can add an additional stage such as:
- Deployment Stage:
```
sh 'kubectl set image deployment/my-app my-container=portfloio-image:latest'
sh 'kubectl apply -f k8s-deployment.yaml'
```


# Part-5: Monitoring and Logs: 
## 1. Explain the difference between metrics, logs, and traces:
- Metrics: Metrics is a numerical measurement collected over time for monitoring performance and setting alerts. Ex,CPU Usage, Network Latency.
- Logs: Logs contains the detailed timestamped records of events produced by applications or systems used for troubleshooting and audits.
- Traces: Traces helps us to understand request flow and identify bottlenecks in complex systems. It provides end-to-end tracking of a single request across multiple services.

## 2.If your Kubernetes pod crashes, how would you debug the issue:
1. Check Pod Status: 
``` 
kubectl get pods
```
Quickly shows if the pod is in CrashLoopBackOff, Error, or Pending state to identify the nature of the failure.
   
2. Getting pod events:
```
kubectl describe pod <pod-name>
```
Provides detailed information on events.

3. Checking Logs:
```
kubectl logs <pod-name>
```
Shows application-level errors.

4. Execute inside pods:
```
kubectl exec -it <pod-name> -- /bin/sh
```
Allows to access pods using interactice shell.

