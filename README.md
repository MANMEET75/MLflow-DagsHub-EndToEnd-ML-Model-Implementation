# MLflow


Interactive Guide to Setting Up Collaborative MLflow on AWS using DagsHub

In this interactive guide, we'll walk you through the process of setting up a collaborative MLflow workflow on AWS using DagsHub. This will allow your team to work together efficiently and keep your data science projects confidential. Let's get started!

Step 1: Working Locally vs. Collaborating Remotely

Working locally on your MLflow projects is fine for personal use, but for team collaboration, it's better to work on a remote server.

Step 2: Using DagsHub for Collaborative Projects

Head to DagsHub (https://dagshub.com) and log in with your GitHub account.

Click on the "Create" button and connect your repository. DagsHub supports other platforms like GitLab and Bitbucket too.

Navigate to the "Experiments" section and click on "Remote." Copy the MLflow tracking remote link and paste it in your project's readme file for reference.

Step 3: Preparing Your Code for Collaboration

Modify your code by removing any hardcoded local paths, such as file paths for predictions and statements. This ensures flexibility when running on different environments.

Add the remote server URI for DagsHub to your code. This will redirect MLflow runs to the remote server instead of your local machine.

Step 4: Running Your MLflow Experiment

Execute your example.py code to run the MLflow experiment. Check the results on the MLflow UI in DagsHub.
Step 5: Sharing the MLflow Link

Share the MLflow link with your team. Everyone can access the link since you're using DagsHub's remote server.
Step 6: Enhancing Confidentiality with AWS

For maximum confidentiality, consider using Amazon Web Services (AWS) for hosting your MLflow experiments.

Log in to your AWS account and create an IAM user with administrator access.

Create an access key for the IAM user and download it as a CSV file.

Install the AWS CLI tool on your local machine and run "aws configure" to set up the access key, secret key, and region.

Create an S3 bucket with appropriate settings and permissions.

Create an EC2 instance (virtual machine) on AWS, selecting the Ubuntu machine and creating a key-value pair for secure access.

Connect to the EC2 instance using the instance ID and execute the provided code step by step.

Configure port mapping by adding a custom TCP rule for port 5000 in the security group.

Obtain your EC2 instance's public IPv4 DNS and access your MLflow instance by appending ":5000" to the link.

Congratulations! You've successfully set up a collaborative MLflow workflow on AWS using DagsHub. Now your team can work together on data science projects with enhanced confidentiality. Enjoy your collaborative journey!



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