## Creating  a vpc network, subnets, firewall and virtual machine 

```
# Create network using help command
gcloud compute networks create --help
# Creating a network name my-vpc
gcloud compute networks create my-vpc --subnet-mode=custom
# Creating a subnet name web
gcloud compute networks subnets create web  --network=my-vpc --range=192.168.0.0/24 --region=asia-south1
# Creating a subnet name app
gcloud compute networks subnets create app  --network=my-vpc --range=192.168.1.0/24 --region=asia-south1
# Creating a subnet name db
gcloud compute networks subnets create db  --network=my-vpc --range=192.168.2.0/24 --region=asia-south1
# Creating a firewall rules allow 80 port
gcloud compute firewall-rules create web --network my-vpc --allow tcp:80 --source-ranges 0.0.0.0/0
# Creating a firewall rules allow 22 port
gcloud compute firewall-rules create ssh --network my-vpc --allow tcp:22 --source-ranges 0.0.0.0/0
# Creating a firewall rules allow 8080 port
gcloud compute firewall-rules create https --network my-vpc --allow tcp:8080 --source-ranges 0.0.0.0/0 --priority=1010
# Creating an virtual instance using the my-vpc and subnet as web 
gcloud compute instances create gopi --machine-type=e2-micro  --network=my-vpc --subnet=web --zone=asia-south1-a
```
# clean up 

```
# delete the virtual instance 
gcloud compute instances delete gopi --zone=asia-south1-a
# delete the firewalls 
gcloud compute firewall-rules delete ssh
gcloud compute firewall-rules delete web
gcloud compute firewall-rules delete https
# delete the subnets
gcloud compute networks subnets delete app web db --region=asia-south1
# delete the vpc
gcloud compute networks delete my-vpc
```