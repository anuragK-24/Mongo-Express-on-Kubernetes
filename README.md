# Mongo-express-K8s-Cluster
Complete app setup with `Kubernetes` components.<br>
First we have to create `Secret`<br>
In the Secret config file the value of `username` and `password` must be base 64 encoded value.<br>
In order to encode values, <br>
```
echo -n 'value' | base64
```
Take the value and paste into the secret username, and password. <br>
To create Secret,<br>
```
kubectl apply -f mongo-secret.yaml
```
In the mongo.yaml configuration file,<br>
The code before `---` is the deployment configuration code <br>
The code before `---` is services configuration code <br>
Now to cereate the `mongo deployment` and `Internal service` (inorder to communicate with the pod) by configuration file. <br>
```
kubectl apply -f mongo.yaml
```
In the next step, <br>
To create the `configmap` <br>
```
kubectl apply -f mongo-config.yaml
```
Now to cereate the `mongo-express deployment` and `External service`  by configuration file.
```
kubectl apply -f mongo-express.yaml
```

When working with minikube, External IP is not assign to external service. <br>
To assign external service, a Public IP address <br>
```
minikube service mongo-express-service
```
It assigns the IP address in the nodePort that we assign to external service.
