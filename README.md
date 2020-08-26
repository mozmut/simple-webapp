# Simple Web Application with Kubernetes and Helm

This is a simple web application using [Python Flask](http://flask.pocoo.org/). 
This is used in the demonstration of development of helm and createing kubernetes pods
  
  Below are the steps required to get this working on a base macOs system.
  
  - Install brew  
  - Install docker
  - Install minikube
  - Install helm

## 1. Install brew
    
 Install brew
    
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   
## 2. Install docker
  
  Install latest version of docker

    $ curl -fsSL https://get.docker.com -o get-docker.sh
    $ sudo sh get-docker.sh

   
## 3. Install minikube
    
 Install minikube
    
    brew install minikube

## 4. Install Helm

 Install helm
    
    brew install helm
    
## Start minikube cluster

Need to start minikube kubernetes cluster

    minikube start

Wait until minikube cluster start

## Run helm

Need to change directory to helm charts and run helm command

    $ cd web-app-chart
    $ helm install --generate-name .
    NAME: chart-1598449367
    LAST DEPLOYED: Wed Aug 26 16:42:48 2020
    NAMESPACE: default
    STATUS: deployed
    REVISION: 1
    TEST SUITE: None

    
## Test

Need to test that pods are running

    $ kubectl get pods
    NAME                                                         READY   STATUS    RESTARTS   AGE
    chart-1598449367-web-app-chart-deployment-6d856b8cc6-lzddc   1/1     Running   0          11s

    $ kubectl get services
    NAME                                     TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
    chart-1598449367-web-app-chart-service   NodePort    10.99.109.55   <none>        8090:30008/TCP   45s
    kubernetes                               ClusterIP   10.96.0.1      <none>        443/TCP          3d17h
    
    $ minikube service chart-1598449367-web-app-chart-service
    |-----------|----------------------------------------|-------------|-------------------------|
    | NAMESPACE |                  NAME                  | TARGET PORT |           URL           |
    |-----------|----------------------------------------|-------------|-------------------------|
    | default   | chart-1598449367-web-app-chart-service |        8090 | http://172.17.0.3:30008 |
    |-----------|----------------------------------------|-------------|-------------------------|
    🏃  Starting tunnel for service chart-1598449367-web-app-chart-service.
    |-----------|----------------------------------------|-------------|------------------------|
    | NAMESPACE |                  NAME                  | TARGET PORT |          URL           |
    |-----------|----------------------------------------|-------------|------------------------|
    | default   | chart-1598449367-web-app-chart-service |             | http://127.0.0.1:54235 |
    |-----------|----------------------------------------|-------------|------------------------|
    🎉  Opening service default/chart-1598449367-web-app-chart-service in default browser...
    ❗  Because you are using a Docker driver on darwin, the terminal needs to be open to run it.


Then look up your default browser

    
