
# DevOps - project

This project was carried out for academic purposes. It was suggested by the DevOps course, which we followed during our ING4 studies over the period September 2021 to December 2021. The project takes over the web application given by Mr.Kudinov in his Lab4 and aims to implement all the tools to carry out a DevOps cycle.

### Table of contents

- ###### [Getting started](#getting-started)

- ###### [Web application](#web-app)

- ###### [CI/CD pipeline](#ci-cd)

- ###### [Iac approach](#iac)

- ###### [Docker image](#docker-image)

- ###### [Docker compose](#docker-compose)

- ###### [Kubernetes](#kubernetes)

- ###### [Istio](#istio)

- ###### [Monitoring](#monitoring)



## <a id="getting-started"></a> 0. Getting started

- Clone this repository, from your local machine:

```
git clone https://github.com/maximeattal/DevOps.git
```

- Install node modules:

```
cd userapi
npm install
```

## <a id="web-app"></a> 1. Web application ✅

We used the draft application [userapi](https://github.com/adaltas/ece-devops-2021-fall/tree/master/courses/devops/modules/04.continuous-testing/assets/userapi) from the DevOps course. 

**Are proposed:**

- a little user API application with [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) user functionality
- storage in Redis database
- tests: unit, API, configuration, connection.

### Usage

*how to start and use the application, run the tests, ...*

* Start the Redis server:
  ```yaml
  redis-server
  ```

* Run the web application inside userapi, in another terminal window:   
  ```yaml
  cd userapi
  npm test
  npm start
  ```

- Go to  `http://localhost:3000` 

### Screenshots

*What you are supposed to see...*

- When you are executing test:

![Capture d’écran 2021-12-15 à 14.34.22](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2014.34.22.png?raw=true)

- When going to your `http://localhost:3000` :

![Capture d’écran 2021-12-15 à 14.35.32](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2014.35.32.png?raw=true)

## <a id="ci-cd"></a> 2. CI/CD pipeline ✅

Text

### Screenshots

*What you are supposed to see...*

In the GitHub Action section: 

![Capture d’écran 2021-12-15 à 15.29.15](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.29.15.png?raw=true)



## <a id="iac"></a> 3. Run application using IaC approach ✅

1. Configure with Vagrant: 1 VM running on a Linux distribution
2. Provision the VM with Ansible, which includes installing and running:
   - language runtime
   - database
   - the application
   - health check of the application

### Usage

*how to start and use the application, run the tests, ...*

* Start vagrant from the root directory:

  ```yaml
  cd iac
  vagrant up
  ```

> **Note!** If you are using a macOS computer, `vagrant up` may bring an error. To fix it you have to go the `iac` folder and edit `Vagranfile`. After line 20, add the following line `vb.gui = true` and save the file. 

- Go to `20.20.20.2` on your web browser.

### Screenshots

*What you are supposed to see...*

- In the console:

![Capture d’écran 2021-12-15 à 15.05.26](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.05.26.png?raw=true)

- At `20.20.20.2`:

![Capture d’écran 2021-12-15 à 15.05.59](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.05.59.png?raw=true)

## <a id="docker-image"></a> 4. Docker image ✅

Text

### Usage

*how to start and use the application, run the tests, ...*

* Build the image of the application, from the root directory:

  ```
  docker build -t devops-project .
  ```

- Run the docker image:

  ```
  docker run -p 12345:3000 -d devops-project
  ```

- Go to `http://localhost:12345` 

### Screenshots

*What you are supposed to see...*

![Capture d’écran 2021-12-15 à 15.10.48](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.10.48.png?raw=true)

## <a id="docker-compose"></a> 5. Docker compose ✅

Text

### Usage

- Run the docker compose:

  ```
  docker-compose up
  ```

- Go to `http://localhost:3000` 

### Screenshots

*What you are supposed to see...*

- In the console:

![Capture d’écran 2021-12-15 à 15.11.50](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.11.50.png?raw=true)

- When going to your `http://localhost:3000` :

![Capture d’écran 2021-12-15 à 15.12.29](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.12.29.png?raw=true)

## <a id="kubernetes"></a> 6. Docker orchestration using Kubernetes ✅

Text

### Usage

- Start minikube:

  ```
  minikube start
  ```

- Apply configuration files with:

  ```
  kubectl apply -f k8s/deployment.yaml
  kubectl apply -f k8s/service.yaml
  kubectl apply -f k8s/pers-volume.yaml
  kubectl apply -f k8s/pers-volume-claim.yaml
  ```

- Run the following command to access the web application:

  ```
  minikube service devops-project
  ```

### Screenshots

*What you are supposed to see...*

![Capture d’écran 2021-12-15 à 15.20.53](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.20.53.png?raw=true)

## <a id="istio"></a> 7. Docker orchestration using Istio ✅

Text

### Usage

- Start minikube:

  ```
  minikube config set vm-driver virtualbox
  minikube start --memory=16384 --cpus=4 --kubernetes-version=v1.18.0
  ```

  > **Note!** If you don’t have enough RAM to allocate to the minikube virtual machine then try to put the maximum you have on your laptop.

- Apply configuration files with:

  ```
  kubectl apply -f k8s/deployment.yaml
  kubectl apply -f k8s/service.yaml
  kubectl apply -f istio/gateway.yaml
  kubectl apply -f istio/destinationrules.yaml
  kubectl apply -f istio/virtualservice.yaml
  ```

  > **Note!** Wait until the deployment files run step is 1/1. You can verify it by running the command `kubectl get deployment`.

- Get your ip:

  ```
  minikube ip
  ```

- Get the ports on which the app is running:

  ```
  kubectl get svc -n istio-system
  ```

  At the ligne `istio-ingressgateway` and the column `port(s)` take the port after `80:` and before `/TCP`. 

- Go to `<ip>:<port>`.

### Screenshots

*What you are supposed to see...*

- 70% of the time:

![Capture d’écran 2021-12-15 à 15.26.44](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.26.44.png?raw=true)

- 30% of the time (if you refresh the pag multiple times quickly):

![Capture d’écran 2021-12-15 à 15.27.36](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2015.27.36.png?raw=true)

## <a id="monitoring"></a> 8. Monitoring ✅

Text

### Usage

- Before starting do the [docker orchestration using Istio](#7. Docker orchestration using Istio ✅) part.

- Apply Prometheus configuration files:

  ```
  kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.12/samples/addons/prometheus.yaml
  ```

- Apply Grafana configuration files:

  ```
  kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.12/samples/addons/grafana.yaml
  ```

- Verify that the Prometheus service is running in your cluster:

  ```
  $ kubectl -n istio-system get svc prometheus
  NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
  prometheus   ClusterIP   10.109.193.158   <none>        9090/TCP   4h5m
  ```

- Verify that the Grafana service is running in your cluster:

  ```
  $ kubectl -n istio-system get svc grafana
  NAME      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
  grafana   ClusterIP   10.97.232.47     <none>        3000/TCP   68m
  ```

- Forward the Prometheus server port to your local machine:  

  ```
  kubectl -n istio-system port-forward $(kubectl -n istio-system get pod -l app=prometheus -o jsonpath='{.items[0].metadata.name}') 9090:9090 &
  ```

- Forward the Grafana server port to your local machine:  

  ```
  kubectl -n istio-system port-forward $(kubectl -n istio-system get pod -l app=grafana -o jsonpath='{.items[0].metadata.name}') 3000:3000 &
  ```

- Open the Istio dashboard using Grafana, by going to `http://localhost:3000/d/G8wLrJIZk/istio-mesh-dashboard`.
- Refresh the web application page few times to generate a small amount of traffic.

### Screenshots

*What you are supposed to see...*

![Capture d’écran 2021-12-15 à 17.06.57](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2017.06.57.png?raw=true)

![Capture d’écran 2021-12-15 à 17.08.50](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2017.08.50.png?raw=true)

![Capture d’écran 2021-12-15 à 17.08.56](https://github.com/maximeattal/DevOps/blob/main/image/Capture%20d’écran%202021-12-15%20à%2017.08.56.png?raw=true)

## Authors

Maxime ATTAL

[maxime.attal@edu.ece.fr](mailto:maxime.attal@edu.ece.fr)

ING4 student at ECE Paris (SI Group inter 3)



Kevin ZHENG

[kevin.zheng@edu.ece.fr](mailto:kevin.zheng@edu.ece.fr)

ING4 student at ECE Paris (SI Group inter 3)

