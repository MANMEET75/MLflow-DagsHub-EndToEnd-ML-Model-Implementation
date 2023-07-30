# MLflow-Basic-Demo



## For Dagshub:

MLFLOW_TRACKING_URI=https://dagshub.com/MANMEET75/MLFlow.mlflow \
MLFLOW_TRACKING_USERNAME=MANMEET75 \
MLFLOW_TRACKING_PASSWORD=9a3206cb528139663f5cb18b54def3c55029275b \
python script.py



```bash

set MLFLOW_TRACKING_URI=https://dagshub.com/MANMEET75/MLFlow.mlflow

set MLFLOW_TRACKING_USERNAME=MANMEET75 

set MLFLOW_TRACKING_PASSWORD=9a3206cb528139663f5cb18b54def3c55029275b


```


# MLflow on AWS

## MLflow on AWS Setup:

1. Login to AWS console.
2. Create IAM user with AdministratorAccess
3. Export the credentials in your AWS CLI by running "aws configure"
4. Create a s3 bucket
5. Create EC2 machine (Ubuntu) & add Security groups 5000 port

Run the following command on EC2 machine
```bash
sudo apt update

sudo apt install python3-pip

sudo pip3 install pipenv

sudo pip3 install virtualenv

mkdir mlflow

cd mlflow

pipenv install mlflow

pipenv install awscli

pipenv install boto3

pipenv shell


## Then set aws credentials
aws configure


#Finally 
mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-test-23

#open Public IPv4 DNS to the port 5000


#set uri in your local terminal and in your code 
export MLFLOW_TRACKING_URI=http://ec2-54-147-36-34.compute-1.amazonaws.com:5000/
```