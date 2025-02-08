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
3. Export the credentials in your AWS CLI by running "aws configure"
4. Create a s3 bucket
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


#Just change and give your bucket name in last after s3://
mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-test-23

#Go to EC2 instance and copy the Public IPv4 DNS address and run in browser and mention port-no as 5000 in last

#set uri in your local terminal and in your code 
export MLFLOW_TRACKING_URI=http://ec2-54-147-36-34.compute-1.amazonaws.com:5000/

```