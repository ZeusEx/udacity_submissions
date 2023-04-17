# Operationalizing an AWS ML Project

## Step 1: Training and deployment on Sagemaker

Setup notebook instance (ml.t3.medium selected as it provides sufficient resources and is the lowest in costs)

![Sagemaker_instance_setup.png](snapshots/step1/Sagemaker_instance_setup.png)

Create an S3 bucket in AWS workspace

![S3_bucket.png](snapshots/step1/S3_bucket.png)

Download data to an S3 bucket

![S3_bucket_data.png](snapshots/step1/S3_bucket_data.png)

Training jobs

![training_jobs.png](snapshots/step1/training_jobs.png)

Single-instance training

![training_jobs_single.png](snapshots/step1/training_jobs_single.png)

End point deployment (trained on single instances)

![end_point_single.png](snapshots/step1/end_point_single.png)

Multiple-instance training

![training_jobs_multiple.png](snapshots/step1/training_jobs_multiple.png)

End point deployment (trained on multiple instances)

![end_point_multiple.png](snapshots/step1/end_point_multiple.png)

## Step 2: EC2 Training

EC2 Setup

![EC2_config.png](snapshots/step2/EC2_config.png)

![EC2_dashboard.png](snapshots/step2/EC2_dashboard.png)

Training and saving on EC2

 - connect to EC2 terminal

 - download and unzip dogImages

'wget https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip'
'unzip dogImages.zip'

 - create TrainedModels folder to store model

'mkdir TrainedModels'

 - edit solution.py with vim program
 
'vim solution.py'
 
 - activate paste
 
':set paste'
 
 - paste code from 'ec2train1.py'
 
 - save file and exit vim
 
'wq!'
 
 - run code
 
 'python solution.py'
 
 - navigate to TrainedModels folder
 
'cd TrainedModels'

 - display concents in TrainedModels folder

'ls'

![EC2_model_deployed.png](snapshots/step2/EC2_model_deployed.png)

## Step 3: Lambda function setup

Setup lambda function and add end point deployed in Step 1

![lambda_function_setup.png](snapshots/step3/lambda_function_setup.png)

## Step 4: Security and testing

Attach security policy to Lambda function

![attach_security_policy.png](snapshots/step4/attach_security_policy.png)

Test Lambda function

![lambda_test_result.png](snapshots/step4/lambda_test_result.png)

## Step 5: Concurrency and auto-scaling

Concurrency

![lambda_concurrency.png](snapshots/step5/lambda_concurrency.png)

Auto-scaling

![variant_automcatic_scaling.png](snapshots/step5/variant_automcatic_scaling.png)

![built-in_scaling_policy.png](snapshots/step5/built-in_scaling_policy.png)

![auto-scaling_final.png](snapshots/step5/auto-scaling_final.png)