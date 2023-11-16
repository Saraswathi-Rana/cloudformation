

# CI/CD PIPELINE - KUBERNETES AND ARGOCD
This repository contains the automation of CI/CD Pipeline - Kubernetes and ArgoCD using cloudformation

## Prerequisites
1. AWS account with appropriate permissions.
2. EC2 Instance with AWS CLI installed.

## CI using JENKINS
1. Deploy CloudFormation stack either through AWS Console or AWS CLI. The below stack creates EC2 instance and installs java, docker and jenkins. Installs required plugins in jenkins and creates a jenkins job.

2. Use a private git repo or codecommit to store xml file to create jenkins job and credentials file. Replace access key and key ID with your own in credentials.xml (example) file attached above. Replace the repo url in CI-jenkins.yaml.

```bash
 aws cloudformation create-stack --stack-name jenkins --template-body file://CI-jenkins.yaml 
```

## Creating EKS cluster and deploying ArgoCD

1. Create VPC for your EKS Cluster
To deploy VPC stack run the below command using AWS CLI.

```bash
 aws cloudformation create-stack --stack-name create-vpc --template-body file://create-vpc.yaml
```
2. To Activate third party cloudformation extensions required for cluster creation run the below stack.

```bash
 aws cloudformation create-stack --stack-name activate-extensions --template-body file://activate-extensions.yaml
```

3. Deploy eks cluster. Replace the arn of the user to allow the user to access the cluster in install-eks.yaml.

```bash
 aws cloudformation create-stack --stack-name install-eks --template-body file://install-eks.yaml
```

4. Install Argocd and deploy application .

```bash
 aws cloudformation create-stack --stack-name deploy-argocd --template-body file://Deploy-argocd.yaml
```


