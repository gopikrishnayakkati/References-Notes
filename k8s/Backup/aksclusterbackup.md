Azure Kubernetes Backup
----------------------------

# Create a Azure kubernetes cluster using azure AKS documnetation 
 
```bash
export RANDOM_ID="$(openssl rand -hex 3)"
export MY_RESOURCE_GROUP_NAME="myAKSResourceGroup$RANDOM_ID"
export REGION="westeurope"
export MY_AKS_CLUSTER_NAME="myAKSCluster$RANDOM_ID"
export MY_DNS_LABEL="mydnslabel$RANDOM_ID"
```
# Create a resource group using the az group create command
```bash
az group create --name $MY_RESOURCE_GROUP_NAME --location $REGION
```
# Create an AKS cluster using the az aks create command

```bash
az aks create --resource-group $MY_RESOURCE_GROUP_NAME --name $MY_AKS_CLUSTER_NAME --node-count 1 --generate-ssh-keys
```
# Configure kubectl to connect to your Kubernetes cluster using the az aks get-credentials command
```bash
az aks get-credentials --resource-group $MY_RESOURCE_GROUP_NAME --name $MY_AKS_CLUSTER_NAME
```
# Verify the connection to your cluster using the kubectl get command
```
kubectl get nodes
```
![alt text](images/backup1.png)
![alt text](images/backup2.png)
# Apply the manifest file 
##  craetiong pod and Persistant volume Claim
```yaml
---
apiVersion: v1
kind: Pod
metadata:
  name: mysql-pod
  labels:
    app: db
spec:
  containers:
    - name: nopdb
      image: mysql:8.0-debian
      env:
        - name: MYSQL_ROOT_PASSWORD
          value: admin123
        - name: MYSQL_DATABASE
          value: nop
        - name: MYSQL_USER
          value: ltdevops
        - name: MYSQL_PASSWORD
          value: admin123
      resources:
        limits:
          memory: 512Mi
          cpu: 1000m
      volumeMounts:
        - name: nop-vol
          mountPath: /var/lib/mysql
  volumes:
    - name: nop-vol
      persistentVolumeClaim: 
        claimName: nop-pvc
--- 
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: nop-pvc
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: managed-csi
  resources:
    requests:
      storage: 1Gi
```
## Apply the manifest file for Deplyment and Service 
```yaml
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
        image: nginx:1.14.2
        ports:
        - containerPort: 80
--- 
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: LoadBalancer
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      
```
```
kubectl apply -f <fileName>
```

![alt text](images/backup3.png)
# now check the azure portal
![alt text](images/backup4.png)
# Connect to Lens to see the Cluster information
![alt text](images/backup5.png)
## Now back up the k8s 
![alt text](images/backup6.png)
![alt text](images/backup7.png)
![alt text](images/backup8.png)
![alt text](images/backup9.png)
![alt text](images/backup10.png)

# instalation  is completed and click on backup and give the necessary values

![alt text](images/backup11.png)
![alt text](images/backup12.png)
![alt text](images/backup13.png)

# Create a backup policy

![alt text](images/backup14.png)
![alt text](images/backup15.png)
![alt text](images/backup16.png)
![alt text](images/backup17.png)
![alt text](images/backup18.png)
![alt text](images/backup19.png)
![alt text](images/backup20.png)

# Now Backup the cluster 

![alt text](images/backup22.png)
![alt text](images/backup21.png)

#  Check the backup status

![alt text](images/backup23.png)

# Select the Deployment and delete the Deployment 

![alt text](images/backup24.png)
![alt text](images/backup25.png)

# To Restore the Deployment 

![alt text](images/backup26.png)
![alt text](images/backup27.png)
![alt text](images/backup28.png)

# Check the restore process => go to backup vaults and select the vault 

![alt text](images/backup29.png)

# Completed the Restore check the Deployment 

![alt text](images/backup30.png)

## Delete the Resource group 

```bash
az group delete --name $MY_RESOURCE_GROUP_NAME --no-wait --yes 
```
