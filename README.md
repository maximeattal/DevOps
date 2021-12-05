
# DevOps - project

*presentation, introduction, ...*

## 1. Web application ✅

We used the draft application [userapi](http://courses/devops/modules/04.continuous-testing/assets/userapi) from the DevOps course. 

**Are proposed:**

- a little user API application with [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) user functionality
- storage in Redis database
- tests: unit, API, configuration, connection.

### Usage

*how to start and use the application, run the tests, ...*

* Clone this repository, from your local machine:

  ```
  git clone https://github.com/maximeattal/DevOps.git
  cd userapi
  npm install
  ```

* Start the Redis server:
  ```yaml
  redis-server
  ```
  
* Run the web application inside userapi, in another terminal window:   
  ```yaml
  npm test
  npm start
  ```

- Go to  `http://localhost:3000` 

### Screenshots

*What you are supposed to see...*



## 2. CI/CD pipeline ✅

Text

### Screenshots





## 3. Run application using IaC approach ✅

1. Configure with Vagrant: 1 VM running on a Linux distribution
2. Provision the VM with Ansible, which includes installing and running:
   - language runtime
   - database
   - the application
   - health check of the application

### Usage

*how to start and use the application, run the tests, ...*

* Start vagrant:

  ```yaml
  vagrant up
  ```

### Screenshots

*What you are supposed to see...*

## 4. Docker image ✅

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

## 5. Docker compose ✅

Text

### Usage

- Run the docker compose:

  ```
  docker-compose up
  ```

- Go to `http://localhost:3000` 

### Screenshots

*What you are supposed to see...*

## 6. Docker orchestration using Kubernetes ✅

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

## 7. Docker orchestration using Istio ✅

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

  Under the ligne `istio-ingressgateway` and the column `port(s)` take the port after `80:` and before `/TCP`. 

- Go to `ip:port`.

### Screenshots

*What you are supposed to see...*

## 8. Monitoring ❌

Text

### Usage

- 

### Screenshots

*What you are supposed to see...*



## Author

*name, email, ...*

## Bonus

*place your graduation and comments*
