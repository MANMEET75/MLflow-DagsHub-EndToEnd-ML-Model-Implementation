# MLflow
![image](https://github.com/MANMEET75/MLflow-DagsHub-EndToEnd-ML-Model-Implementation/assets/97391884/7a917e79-7e32-4ece-9970-08fffe213f57)


## Interactive Guide to Setting Up Collaborative MLflow on AWS using DagsHub

In this interactive guide, we'll walk you through the process of setting up a collaborative MLflow workflow on AWS using DagsHub. This will allow your team to work together efficiently and keep your data science projects confidential. Let's get started!

### Step 1: Working Locally vs. Collaborating Remotely

Working locally on your MLflow projects is fine for personal use, but for team collaboration, it's better to work on a remote server.

### Step 2: Using DagsHub for Collaborative Projects

Head to DagsHub (https://dagshub.com) and log in with your GitHub account.

Click on the "Create" button and connect your repository. DagsHub supports other platforms like GitLab and Bitbucket too.

Navigate to the "Experiments" section and click on "Remote." Copy the MLflow tracking remote link and paste it in your project's readme file for reference.

### Step 3: Preparing Your Code for Collaboration

Modify your code by removing any hardcoded local paths, such as file paths for predictions and statements. This ensures flexibility when running on different environments.

Add the remote server URI for DagsHub to your code. This will redirect MLflow runs to the remote server instead of your local machine.

### Step 4: Running Your MLflow Experiment

Execute your example.py code to run the MLflow experiment. Check the results on the MLflow UI in DagsHub.
### Step 5: Sharing the MLflow Link

Share the MLflow link with your team. Everyone can access the link since you're using DagsHub's remote server.
### Step 6: Enhancing Confidentiality with AWS

## For maximum confidentiality, consider using Amazon Web Services (AWS) for hosting your MLflow experiments.

1. Log in to your AWS account and create an IAM user with administrator access.

2. Create an access key for the IAM user and download it as a CSV file.

3. Install the AWS CLI tool on your local machine and run "aws configure" to set up the access key, secret key, and region.

4. Create an S3 bucket with appropriate settings and permissions.

5. Create an EC2 instance (virtual machine) on AWS, selecting the Ubuntu machine and creating a key-value pair for secure access.

6. Connect to the EC2 instance using the instance ID and execute the provided code step by step.

7. Configure port mapping by adding a custom TCP rule for port 5000 in the security group.

8. Obtain your EC2 instance's public IPv4 DNS and access your MLflow instance by appending ":5000" to the link.


### STEP 01- Create a conda environment after opening the repository

```bash
conda create -p mlproj python=3.11 -y
```

```bash
conda activate mlproj/
```


### STEP 02- install the requirements
```bash
pip install -r requirements.txt
```


```bash
# Finally run the following command
python app.py
```

Now,
```bash
open up you local host and port
```


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


Congratulations! You've successfully set up a collaborative MLflow workflow on AWS using DagsHub. Now your team can work together on data science projects with enhanced confidentiality. Enjoy your collaborative journey!




# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

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

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 566373416292.dkr.ecr.ap-south-1.amazonaws.com/mlproj

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

    AWS_ACCESS_KEY_ID=

    AWS_SECRET_ACCESS_KEY=

    AWS_REGION = us-east-1

    AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

    ECR_REPOSITORY_NAME = simple-app








Enjoy Coding!
