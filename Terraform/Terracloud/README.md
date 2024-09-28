# Terraform Cloud Account 

* Create a Terraform account [Refer Here](https://app.terraform.io/session)
![alt text](Images/terrac1.png)
![alt text](Images/terrac2.png)
* Go to your mail and select the mail received from HCP 
![alt text](Images/terrac4.png)
![alt text](Images/terrac5.png)

* Create an Organization shown in the below images 

![alt text](Images/terrac6.png)
![alt text](Images/terrac7.png)
![alt text](Images/terrac8.png)

* Create a Project 

![alt text](Images/terrac9.png)
![alt text](Images/terrac10.png)

* Once the Project is created shows like this

![alt text](Images/terrac11.png)

### Connect to Registry
* Go Registry ==> Click on Add a VCS connection

![alt text](Images/terrac12.png)

* Select the Version control system provider where the terraform files are available

![alt text](Images/terrac13.png)
![alt text](Images/terrac14.png)

* Register your git hub account to Terraform Cloud, Follow the steps

![alt text](Images/terrac15.png)
![alt text](Images/terrac16.png)

* Give your client ID and client secrets to Terraform 

![alt text](Images/terrac17.png)
![alt text](Images/terrac18.png)

* Give Repository permission for Terraform cloud

![alt text](Images/terrac19.png)

* The Page redirected to Terraform Cloud and skip and finish

![alt text](Images/terrac20.png)
![alt text](Images/terrac21.png)

* VCS Connection Is Established

#### Adding AWS Credentials to Terraform cloud (Access Key & Secret key)
* Select the settings 
![alt text](Images/terrac22.png)
* click on variable sets and create a variable set
![alt text](Images/terrac23.png)
![alt text](Images/terrac24.png)
![alt text](Images/terrac25.png)
![alt text](Images/terrac26.png)
![alt text](Images/terrac27.png)
![alt text](Images/terrac28.png)

**Publish the terraform modules**
![alt text](Images/terrac29.png)
![alt text](Images/terrac30.png)

**Choose a repository**
* Choose the repository that hosts your module source code. We'll watch this for commits and tags. The format of your repository name should be terraform-<PROVIDER>-<NAME>.
![alt text](Images/terrac31.png)
![alt text](Images/terrac32.png)
![alt text](Images/terrac33.png)
![alt text](Images/terrac34.png)
![alt text](Images/terrac35.png)
![alt text](Images/terrac36.png)
* CLI Configuration File (.terraformrc or terraform.rc) [Refer Here](https://developer.hashicorp.com/terraform/cli/config/config-file)

![alt text](Images/terrac39.png)
![alt text](Images/terrac40.png)
![alt text](Images/terrac37.png)
![alt text](Images/terrac38.png)

* Create a workspace and select the Project
![alt text](Images/terrac44.png)
![alt text](Images/terrac43.png)
![alt text](Images/terrac45.png)

* Write a terraform module for creating VPC based on child module 

![alt text](Images/terrac41.png)

* Providers.tf
```t

terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.69.0"
    }
  }
  cloud { 
    
    organization = "GopiKrishna" 

    workspaces { 
      name = "terraform" 
    } 
  } 
}

provider "aws" {
  # Configuration options
  region = "ap-south-1"
}

```
* main.tf file
```t

# 
module "vpc" {
    source  = "app.terraform.io/GopiKrishna/vpc/aws"
    version = "1.0.0"

    vpc_configuration = {
        cidr_block = "10.0.0.0/16"
        instance_tenancy = "default"
        enable_dns_hostnames = true
        enable_dns_support = false
        tags = {
          Name = "three-tier-network"
          Environment = "dev"
        }

    }
    private_subnets = [
        {
            cidr_block = "10.0.1.0/24"
            availability_zone = "ap-south-1a"
            tags = {
                Name = "app-1"
                Environment = "dev"
            }
        },
        {
            cidr_block = "10.0.2.0/24"
            availability_zone = "ap-south-1a"
            tags = {
                Name = "db-1"
                Environment = "dev"
            }
        }
    ]
    public_subnets = [
        {
            cidr_block = "10.0.0.0/24"
            availability_zone = "ap-south-1a"
            tags = {
                Name = "web-1"
                Environment = "dev"
            }
        }
    ]
    is_nat_gateway_required = false
  
}

```
* Now initilize the terraform `terraform init`

![alt text](Images/terrac42.png)

* Now execute the `terraform plan` 
![alt text](Images/terrac46.png)

* Open the terraform cloud and see the status 

![alt text](Images/terrac47.png)
![alt text](Images/terrac48.png)

* Now execute the `terraform apply` 

![alt text](Images/terrac49.png)
![alt text](Images/terrac51.png)
![alt text](Images/terrac50.png)

* Check whether the AWS console vpc is created or not

![alt text](Images/terrac52.png)
![alt text](Images/terrac53.png)

* Check the state file 
![alt text](Images/terrac54.png)
![alt text](Images/terrac55.png)

* All resources are created 

* Destroy the all resources `terraform destroy`

![alt text](Images/terrac56.png) 
![alt text](Images/terrac57.png) 
![alt text](Images/terrac58.png) 
![alt text](Images/terrac59.png) 
![alt text](Images/terrac60.png)

------------

