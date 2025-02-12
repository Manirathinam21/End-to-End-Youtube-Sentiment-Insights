# End-to-End-Youtube-Sentiment-Insights

## Intial setup

1. To create an environment

```bash
 conda create -p venv python=3.11 -y

 source activate venv/

```
2. To Install the required python packages

```bash
pip install -r requirements.txt
```

## DVC commands

1. To intiate the DVC
```bash
dvc init
```
2. To run the different stages in automated way using dvc
```bash
dvc repro 
```
3. To see the DVC pipeline diagram
```bash
dvc dag
```

## MLflow Setup on AWS :
1. Login to AWS console.
2. Create IAM user with AdministratorAccess
3. Export the credentials in your AWS CLI by running "aws configure" in your local command prompt
4. Create a S3 bucket
5. Create EC2 machine (Ubuntu) & add Security groups 5000 port

Run the following command on EC2 machine

```bash

sudo apt update

sudo apt install python3-pip

sudo apt install pipenv

sudo apt install virtualenv

mkdir mlflow

cd mlflow

pipenv install mlflow

pipenv install awscli

pipenv install boto3

pipenv shell


## Then set aws credentials
aws configure


# Just change it and give your bucket name in last, after s3://
mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-test-23

# Go to EC2 instance and copy the Public IPv4 DNS address and run in browser and mention port-no as 5000 in last

# set uri in your local terminal and in your code 
export MLFLOW_TRACKING_URI=http://ec2-54-147-36-34.compute-1.amazonaws.com:5000/

```

### How to get youtube api key from gcp:
https://www.youtube.com/watch?v=i_FdiQMwKiw

## AWS-CICD-Deployment-with-Github-Actions

### 1. Login to AWS console.

### 2. Create IAM user for deployment
```bash
#with specific access

1. EC2 access : It is virtual machine

2. ECR: Elastic Container registry to save your docker image in aws


#Description: About the deployment

1. Build docker image of the source code

2. Push your docker image to ECR

3. Launch Your EC2 

4. Pull Your image from ECR in EC2

5. Lauch your docker image in EC2

#Policy:

1. AmazonEC2ContainerRegistryFullAccess

2. AmazonEC2FullAccess
```
### 3. Create ECR repo to store/save docker image
```bash
- Save the URI: 315865595366.dkr.ecr.us-east-1.amazonaws.com/youtube
```

### 4. Create EC2 machine (Ubuntu)

### 5. Open EC2 and Install docker in EC2 Machine:

```bash
#optinal

sudo apt-get update -y

sudo apt-get upgrade

#required

curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

sudo usermod -aG docker ubuntu

newgrp docker
```
### 6. Configure EC2 as self-hosted runner:

```bash
github>settings>actions>runner>new self hosted runner> choose os> then run command one by one in EC2 CLI

Enter the name of Runner: self-hosted
```

### 7. Setup github secrets:
```bash
AWS_ACCESS_KEY_ID=

AWS_SECRET_ACCESS_KEY=

AWS_REGION = us-east-1

AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

ECR_REPOSITORY_NAME = simple-app

```