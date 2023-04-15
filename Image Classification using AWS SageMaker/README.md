# Image Classification of Dog Breeds using AWS Sagemaker

This project classifies dog breeds using AWS Sagemaker to train a pretrained model that can perform image classification by using the Sagemaker profiling, debugger and hyperparameter tuning.

This assignment is a part of AWS Machine Learning Engineer Nanodegree Program.

The following tasks are performed:
 - A pretrained Resnet50 model from pytorch vision library is used in the project (https://pytorch.org/vision/master/generated/torchvision.models.resnet50.html)
 - Fine-tune the model with hyperparameter tuning and network re-shaping
 - Implement profiling and debugging with hooks
 - Deploy the model and perform inference

## Project Set Up and Installation

Enter AWS through the gateway in the course and open SageMaker Studio. 
Download the starter files.
Download/Make the dataset available. 

## Dataset

Udacity provided the dogbreed classification dataset which can be found in the classroom.\
In machine learning, a class refers to the set of possible values or categories that a variable or feature can take.\
In this dataset, the class would be dog breed.\
There are 133 dog breeds in this dataset.\
The images of the same dog breed are segregated into 133 subfolders respectively.\
The dataset can be downloaded [here](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip).

### Access

Upload the data to an S3 bucket through the AWS Gateway so that SageMaker has access to the data. 

## Hyperparameter Tuning

Finetune a pretrained model with hyperparameter tuning.

The ResNet model represents the deep Residual Learning Framework to ease the training process.\
AdamW from torch.optm is used as an optimizer.

The following hyperparameters are used:
 - Learning rate- 0.01x to 100x
 - eps - 1e-09 to 1e-08
 - Weight decay - 0.1x to 10x
 - Batch size - [ 64, 128 ]

The `hpo.py` script is used to perform hyperparameter tuning.

![Hyperparameters tuning jobs](Snapshots/Hyperparameter%20tuning%20jobs.png "Hyperparameters tuning jobs") 
![Best training job hyperparameters](Snapshots/Hyperparameter%20Tuning%20Jobs_best.png "Best training job hyperparameters")

Best Hyperparamters post Hyperparameter fine tuning are : 
 {'batch_size': 64, 'eps': '3.972559626859065e-09', 'lr': '0.0001471610534166238', 'weight_decay': '0.005026032640569199'}

## Debugging and Profiling

Using the best hyperparameters, create and finetune a new model.

The `train_and_deploy.py` script is used to perform model profiling and debugging.

![training jobs](Snapshots/training%20jobs.png "training jobs") 
![training jobs_final](Snapshots/training%20jobs_final.png "training jobs_final")

Cross Entropy Loss Graph

![Cross Entropy Loss](Snapshots/Cross%20Entrophy%20Loss%20Graph.png "Cross Entropy Loss")

The graph shows the loss function, which measures how good the machine learning model is at making predictions. The lower the loss, the better the model. The blue line represents the training loss, which is the error calculated during training. The orange line represents the validation loss, which is the error calculated on a separate validation set that the model has not seen before. The idea is that the validation loss should follow the training loss closely, indicating that the model is not overfitting to the training set.

If the validation loss starts increasing while the training loss is still decreasing, it indicates that the model is starting to overfit and memorize the training data, which is not good. In this case, we may need to stop training earlier, or try using techniques like regularization to prevent overfitting. On the other hand, if the validation loss is significantly higher than the training loss, it indicates that the model is not generalizing well to new data, and we may need to adjust the model or collect more data to improve its performance.


### Profiler Output

The profiler report can be found [here](profiler_report/profiler-output/profiler-report.html).




## Model Deployment
- Model was deployed to a "ml.t2.medium" instance type and "endpoint_inference.py" script is used to setup and deploy our working endpoint.
- For testing purposes ,few test images are stored in the "testImages" folder.
- Those images are fed to the endpoint for inference/
- The inference is performed using both the approaches. 

![End Point Deployment](Snapshots/Initialise%20End%20Point.png "End Point")


