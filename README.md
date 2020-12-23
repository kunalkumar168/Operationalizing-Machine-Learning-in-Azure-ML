## Operationalizing Machine Learning

## Project overview

In this project, I will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. I will also create, publish, and consume a pipeline. In the end, I will fully demonstrate all of my work in this README file.

I will be working with the Bank Marketing dataset, it is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (y). It consists of 20 input variables (columns) and 32,950 rows with 3,692 positive classes and 29,258 negative classes. I will use AutoML to train a model, then deploy the model as a REST endpoint, and test that it's working.

## Architectural Diagram
TODO: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model".

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

#### Publish a pipeline.

![create](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20endpoint.PNG)

#### Consume a pipeline.
![pipelines](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/published%20pipelines.PNG)

## Screen Recording 
Link to the screen recording is https://youtu.be/tZX-4e9Np5E
## Standout Suggestions
TODO (Optional): This is where you can provide information about any standout suggestions that you have attempted.
