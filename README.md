# Kubernetes Networking

```sh
    # Start Minikube - our development cluster
    minikube start

    cd kubernetes

    kubectl apply -f users-service.yaml,users-deployment.yaml,auth-service.yaml,auth-deployment.yaml,tasks-service.yaml,tasks-deployment.yaml,frontend-service.yaml,frontend-deployment.yaml
```

```sh
    # Check services IPs - Used internally by Kubernetes Cluster
    kubectl get services
```

```sh
    kubectl delete -f users-service.yaml,users-deployment.yaml,auth-service.yaml,auth-deployment.yaml,tasks-service.yaml,tasks-deployment.yaml,frontend-service.yaml,frontend-deployment.yaml
```

## Environment Variables for Pod-to-Pod Communication

When we create a service Kubernetes autocreate environment variables for these services.
A service named: "auth-service" have a autogenerated "AUTH_SERVICE_SERVICE_HOST" environment variable name.

## DNS for Pod-to-Pod Communication

We can use the service name as a URL to communicate with the service/pod/container.
A application that uses de port 3000 exposed by a Kubernetes Service Object named: "auth-service.default" can be reached by specifying https://auth-service.default:3000
`default` is the default namespace when the namespace is not created/specified on Kubernetes configuration.

```sh
    kubectl get namespaces
```

To learn more about check the files:
* [Kubernetes YAML files](kubernetes)
* [nginx.conf](frontend/conf/nginx.conf) - _Using reserse proxy settings_
* [App.js](frontend/src/App.js) - _sending requests using the nginx reverse proxy_
