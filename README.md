# Operationalizing Machine Learning

## Project overview

In this project, I will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. I will also create, publish, and consume a pipeline. In the end, I will fully demonstrate all of my work in this README file.

I will be working with the Bank Marketing dataset, it is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (y). It consists of 20 input variables (columns) and 32,950 rows with 3,692 positive classes and 29,258 negative classes. I will use AutoML to train a model, then deploy the model as a REST endpoint, and test that it's working.

The bank marketing dataset used in this project can be found in the link below:
https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv

## Architectural Diagram

![archi](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/project%202.png)

The diagram above shows the workflow of operationalizing machine learning starting from the creation of an experiment using Automated ML, deployment of the best performing model after the completion of the experiment, enabling Application Insights and retrieving logs, consuming the deployed model using Swagger and lastly, consuming the deployed model endpoints by using the endpoint.py script provided to interact with the trained model.

## Key Steps

#### Firstly, upload the bank marketing datasets to the azure machine learning studio, so that it becomes a readily available registered dataset for use.

![dataset](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/Registered%20dataset.PNG)

#### Next, create an experiment using Automated ML, configure a compute cluster with vm_size of 'STANDARD_DS12_V2, and use that cluster to run the experiment.

![automl](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/experiment%20shown%20as%20completed.PNG)

#### Get the best performing model to be VotingEnsemble with an AUC_weighted score of 0.94687.

![bestmodel](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/best%20model%20(2).PNG)

#### Besides the VotingEnsemble model, we have other models that were generated during the iteration procees.

![other models](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/best%20model.PNG)

#### Next, deploy the Best Model(VotingEnsemble) to allow the interaction with the HTTP API service and interact with the model by sending data over POST requests. After enabling authentication, deploy the model using the Azure Container Instance(ACI).

![deploy](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/deploy%20healthy.PNG)

#### Enable Application Insights is the next step, we'll add: service.update(enable_app_insights=True) to the logs.py file to enable logging.

![logs](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/app%20insights%20enabled.PNG)

#### Next, we're going to make use of localhost on port 9000 to display the Swagger page while ensuring that the updated port is used when trying to reach the swagger instance by localhost, for example localhost:9000

![swagger1](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/swagger1.PNG)
![swagger2](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/swagger2.PNG)
![swagger3](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/swagger3.PNG)
![swagger4](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/swagger4.PNG)

#### Modify the scoring uri and key to match the deployed service generated and execute the endpoint.py file with python. You can then benchmark the endpoint using Apache benchmark to run against the HTTP API using authentication keys to retrieve performance.

![endpoint](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/endpoint.PNG)
![benchmark](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/benchmark1.PNG)
![benchmark2](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/benchmark2.PNG)

#### Create a Pipeline.

You will use the Jupyter Notebook provided in the starter files. You must make sure to update the notebook to have the same keys, URI, dataset, cluster, and model names already created.

![create](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/pipeline%20has%20been%20created.PNG)

#### Publish a pipeline using the pipeline_run object that is created.

![create](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20endpoint.PNG)

#### Consume a pipeline using the post request that will help trigger the pipeline, it also shows you how to monitor the status of the pipeline run using RunDetails Widget.

![pipelines](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20pipelines.PNG)
![pipelines](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20pipeline%20overview.PNG)
![pipelines](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20endpoint.PNG)

## Screen Recording 

Link to the screen recording is https://youtu.be/oCkMY3Axhsw
## Standout Suggestions

The use of ParallelRunSteps can help in creating an Azure Machine Learning Pipeline step to process large amounts of data asynchronously and in parallel. It simplifies scaling up and out large machine learning workloads so data scientists and engineers can spend less time developing computer programs and focus on business objectives. It is a resilient and highly available solution. While the system manages the strategy, you also have the control of when to timeout your job, how many times to retry and how many errors to tolerant. ParallelRunStep is flexibly designed for a variety of workloads. It’s not just for batch inference, but also other workloads which necessitate parallel processing, for example, training many models concurrently, or processing large amount of data.
