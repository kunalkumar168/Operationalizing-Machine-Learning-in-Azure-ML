## Operationalizing Machine Learning

## Project overview

In this project, I will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. I will also create, publish, and consume a pipeline. In the end, I will fully demonstrate all of my work in this README file.

I will be working with the Bank Marketing dataset, it is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (y). It consists of 20 input variables (columns) and 32,950 rows with 3,692 positive classes and 29,258 negative classes. I will use AutoML to train a model, then deploy the model as a REST endpoint, and test that it's working.

## Architectural Diagram
TODO: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model".

## Key Steps
Firstly, upload the bank marketing datasets to the azure machine learning studio, so that it becomes a readily available registered dataset for use.

![dataset](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/Registered%20dataset.PNG)

Next, create an experiment using Automated ML, configure a compute cluster with vm_size of 'STANDARD_DS12_V2, and use that cluster to run the experiment.

![automl](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/experiment%20shown%20as%20completed.PNG)

We'll in turn get our best performing model to be VotingEnsemble with an AUC_weighted score of 0.94687.


![bestmodel](https://github.com/OREJAH/nd00333_AZMLND_C2/blob/master/starter_files/best%20model%20(2).PNG)

## Screen Recording
TODO Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
TODO (Optional): This is where you can provide information about any standout suggestions that you have attempted.
