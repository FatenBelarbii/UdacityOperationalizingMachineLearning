# Operationalizing-Machine-Learning
In this project, we are working with the Bank Marketing dataset. We use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. Then, we also create, publish, and consume a pipeline. 
We follow the below steps:
1- Authentication
2- Automated ML Experiment
3- Deploy the best model
4- Enable logging
5- Swagger Documentation
6- Consume model endpoints
7- Create and publish a pipeline
8- Documentation


## Architectural Diagram
![GitHub Logo](/Screenshots/Diagramme.PNG)

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 
### Step 1: Authentication
We used the lab Udacity provided to us, so we skipped this step since we are not authorized to create a security principal.

### Step 2: Automated ML Experiment
First, we created an new Automated ML run:
![GitHub Logo](/Screenshots/step2-1.PNG)
Then Bank-marketing dataset was already available in registered datasets so all we had to do is to select it.
![GitHub Logo](/Screenshots/step2-2.PNG)
We created and named a new ML experiment
![GitHub Logo](/Screenshots/Step2-3.PNG)
And configured the new compute cluster to be used
![GitHub Logo](/Screenshots/Step2-4.PNG)
We chose the Standard_DS12-v2, 1 as the minimum number of nodes and 6 as the maximum number
![GitHub Logo](/Screenshots/Step2-5.PNG)
![GitHub Logo](/Screenshots/Step2-6.PNG)
Then, we had to configure the classification parameters for the experiment
![GitHub Logo](/Screenshots/Step2-7.PNG)
We chose Accuracy as primary metric, 
![GitHub Logo](/Screenshots/Step2-8.PNG)
set the exit criterion, reducing the defalut (3 hours) to 1 and also reduced the Concurrency to 5.
![GitHub Logo](/Screenshots/Step2-9.PNG)
We saved and ran the experiment.
![GitHub Logo](/Screenshots/Step2-10.PNG)
This screenshot shows the experiment running.
![GitHub Logo](/Screenshots/Step2-11.PNG)
This screenshot shows the bank-marketting dataset in the Registred Datasets tab.
![GitHub Logo](/Screenshots/Step2-12.PNG)
This screenshot shows that the experiment completed running.
![GitHub Logo](/Screenshots/Step2-13.PNG)
These are the models with the best accuracy.
![GitHub Logo](/Screenshots/Step2-14.PNG)
And these are all the details of our run.
![GitHub Logo](/Screenshots/Step2-15.PNG)

### Step 3: Deploy the Best Model
We selected the best model (The first one with better accuracy)
![GitHub Logo](/Screenshots/step3-1.PNG)
And then we deployed it making sure we chose ACI: Azure Container Instance as compute type.
![GitHub Logo](/Screenshots/Step3-2.PNG)
This screenshot confirms that in the Step1 run, the model that we chose is the best model.
![GitHub Logo](/Screenshots/Step3-3.PNG)

### Step 4: Enable Application Insights
This screenshot shows that az is installed.
![GitHub Logo](/Screenshots/step4-1.PNG)
We downloaded our config file.
![GitHub Logo](/Screenshots/Step4-2.PNG)
We checked that application insights is not enabled for our endpoint,
![GitHub Logo](/Screenshots/Step4-3.PNG)
The we wrote the code to enable it and ran it.
![GitHub Logo](/Screenshots/Step4-6.PNG)
After that, we ran the logs.py file
![GitHub Logo](/Screenshots/Step4-5.PNG)
Here, we can see the content of the script
![GitHub Logo](/Screenshots/Step4-4.PNG)
Checking again our endpoint, application insights is enabled 
![GitHub Logo](/Screenshots/Step4-7.PNG)
And here is the result of running logs.py
![GitHub Logo](/Screenshots/Step4-8.PNG)

### Step 5: Swagger Documentation
We can download the swagger.json file by clicking the Swagger URI link:
![GitHub Logo](/Screenshots/Step5-1.PNG)
Here's a look at the file
![GitHub Logo](/Screenshots/Step5-2.PNG)
We ran the swagger.sh file
![GitHub Logo](/Screenshots/Step5-3.PNG)
And the we can use it by running the serve.py file
![GitHub Logo](/Screenshots/Step5-4.PNG)
Swagger is running on our localhost
![GitHub Logo](/Screenshots/Step5-5.PNG)

### Step 6: Consume Model Endpoints
Here, we can find our REST endpoint and the key that were generated after deployment.
![GitHub Logo](/Screenshots/Step6-1.PNG)
We add them to the endpoint.py file 
![GitHub Logo](/Screenshots/Step6-2.PNG)
and run it and have the expected result
![GitHub Logo](/Screenshots/Step6-3.PNG)

### Step 7: Create, Publish and Consume a Pipeline
We uploaded config.json and the aml-pipelines-with-automated-machine-learning-step.ipynb jupyter notebook and updated it to match our environment then ran through the cells.
In the pipelines section, we can verify that our pipeline has been created and that it is running.
![GitHub Logo](/Screenshots/Step9-1.PNG)
The run is complete here.
![GitHub Logo](/Screenshots/Step9-2.PNG)
![GitHub Logo](/Screenshots/Step9-3.PNG)
![GitHub Logo](/Screenshots/Step9-4.PNG)
This is the bankmarketting dataset with the AutoML module and the one the pipeline added and is using
![GitHub Logo](/Screenshots/Step9-5.PNG)
![GitHub Logo](/Screenshots/Step9-6.PNG)
The published pipeline overview shows a REST endpoint and a status of active
![GitHub Logo](/Screenshots/Step9-7.PNG)
The Use RunDetails Widget in the jupyter notebook shows the step runs
![GitHub Logo](/Screenshots/Step9-8.PNG)
![GitHub Logo](/Screenshots/Step9-9.PNG)




## Screen Recording
Link youtube: https://www.youtube.com/watch?v=wePBHiB-Wvs
Link youtube: https://www.youtube.com/watch?v=MXINKAYeyRs

## Future improvements:
1- Manually clean the dataset before performing AutoML run and pipeline creation.
2- Make changes while training the the models using AutoML(For example, Include deep learning models or increase the time for exit criterion while training and see if it will give a better accuracy). Deploy the model only after being sure that the best model obtained is actually the "best".
3- Trying different metrics like the mean_squared_error to check how the prediction deviated from the actual values to have a better idea of the performance of the model.
4- Check for overfitting or underfitting and implement ways to avoid them.
5- Add an interface for consuming the API.
6- Add more automation.
