CI/CD PIPELINE - KUBERNETES AND ARGOCD


This repository contains the automation of CI/CD Pipeline - Kubernetes and ArgoCD using cloudformation

## Prerequisites
AWS account with appropriate permissions
EC2 Instance with AWS CLI installed

## CI using JENKINS
Clone the repository:

git clone 
cd 

Deploy CloudFormation stack either through AWS Console or AWS CLI.
## CD 
1. Creating a VPC for your Amazon EKS cluster

## 

To deploy VPC stack run the below command using AWS CLI

```bash
 aws cloudformation create-stack --stack-name create-vpc --template-body file://create-vpc.yaml
```

