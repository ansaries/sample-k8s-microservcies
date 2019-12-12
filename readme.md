# Basic Deployment options for Docker Microservices based Sample Application

## Docker Compose
You can simply use this to deploy your stack, using docker-compose will create a stack of applications but they will not support auto-scalling and other enterprise stack management features. It is recommended to use this mostly in development environment.

```docker-compose up```

## Docker Swarm
Docker Swarm is yet another container orchestration technology, which provides rich yet simple way to manage, scale and update an application stack. Just run following command to spin up the application stack.

```docker stack deploy -c docker-swarm/stack.yml voting-app```

## Kubernetes
Kubernetes on the other hand is the most comprehensive and advance tool for container orchestration. It provides comprehensive application stack management, scalling and updation tools. It also provides customised networking, storage, security and recovery.

To run the stack
```
kubectl create -f k8s/
```
The above command will:
1. Create Namespace
2. Create Deployments
3. Create ReplicaSets
4. Create Pods
5. Create Services
6. Create Storage

To scale the results or voting microservice
```
kubectl scale deployment docker-example-results-app --replicas=5
kubectl scale deployment docker-example-voting-app --replicas=5
```

To update one or more deployment, change the tag of the image in any of the deployment and then run:
```
kubectl apply -f deployment-results.yml
```
or
```
kubectl set image deployment/docker-example-results-app results=docker/example-voting-app-result:v1
```
