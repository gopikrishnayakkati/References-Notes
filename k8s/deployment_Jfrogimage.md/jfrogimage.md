Kubernetes Deployment using docker images from private Jfrog Repository
-----------------------------------------------------------------------
* First create the Secrets using the command 
```bash
kubectl create secret docker-registry regcred --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
```

* Created a secreat file 
![alt text](image.png)

* Basic Deployment yaml
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: krishna0527.jfrog.io/gopi-docker/nginx:1.0
        ports:
        - containerPort: 80
      imagePullSecrets:
        - name: regcred
--- 
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      # By default and for convenience, the `targetPort` is set to
      # the same value as the `port` field.
      targetPort: 80
      # Optional field
      # By default and for convenience, the Kubernetes control plane
      # will allocate a port from a range (default: 30000-32767)
      nodePort: 30007
```
* Create the manifest file and apply 
![alt text](image-1.png)
* Access the application using nodeport
![alt text](image-2.png) 
