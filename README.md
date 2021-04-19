# Operationalizing ML Using Azure

*Project Overview:*  
This project is part of _Udacity Azure Machine Learning Engineer Nanodegree_.
In this project we worked with bank-marketing dataset to predict if a customer will take term policy or not. Here we use AutoML to train the model and then deployed the bset model which is VotingEnsemble in this usecase. Also we used Swagger to consume the endpoint and finally created and published pipeline for a production ready model, thus automating the whole procedureis

## Architectural Diagram
![image](https://user-images.githubusercontent.com/27814345/115305289-b686b000-a183-11eb-8691-f3662d3c1274.png)
 

## Key Steps
**1. Authentication**  
As I have used the Udacity lab, I didn't have to do this step as it authentication was already present. In case of personal account I would have to create service principle for authorization  
**2. Create AutoML Model**  
  a. Upload and register the dataset
  b. Create a new AutoML run for the bank-marketing dataset  
  c. Configure compute cluster as per requirement  
  d. Running experiment using classification
Registered Dataset  
![image](https://user-images.githubusercontent.com/27814345/115306363-57c23600-a185-11eb-8d99-1ea06e1034a3.png)

Run completed  
![image](https://user-images.githubusercontent.com/27814345/115306586-abcd1a80-a185-11eb-9f7f-18ac327631f3.png)

**3. Deploy Best Model** 
Select the best model for deployment and deploy the model using Azure Conatiner Instance(ACI) with authetication enabled. Here VotingEnsemble is the best model.
![image](https://user-images.githubusercontent.com/27814345/115306824-ff3f6880-a185-11eb-94eb-79df44fc7ab0.png)

**4. Enable Logging** 
Modify and run log.py to enable Application insights.

Before running logs.py  
![image](https://user-images.githubusercontent.com/27814345/115307492-e8e5dc80-a186-11eb-8517-25cac9127d10.png)


logs from logs.py  
![image](https://user-images.githubusercontent.com/27814345/115307604-16cb2100-a187-11eb-9bf1-42f62453ddfa.png)

After running logs.py  
![image](https://user-images.githubusercontent.com/27814345/115307653-277b9700-a187-11eb-9031-387333f540e6.png)

Application Insights:  
![image](https://user-images.githubusercontent.com/27814345/115308410-47f82100-a188-11eb-9f53-9b8b3718882c.png)


**5. Swagger Documentation** 
Swagger is an Interface Description Language for describing RESTful APIs expressed using JSON. For this we need a running Docker. Once docker is running, we need to run serve.py and swagger.sh. Swagger.sh file will dowload the Swagger conatiner to run on port 9000. By running serve.py the content of swagger.json can be consumed locally.  

Swagger running on localhost:  
![image](https://user-images.githubusercontent.com/27814345/115309060-5c88e900-a189-11eb-8e07-320f8e3c5df6.png)

GET method on Swagger:  
![image](https://user-images.githubusercontent.com/27814345/115309156-8510e300-a189-11eb-94eb-e4c6e84a60d7.png)

POST method on Swagger:  
![image](https://user-images.githubusercontent.com/27814345/115309212-96f28600-a189-11eb-964e-c96b6d0a580d.png)

**6. Consume Model Endpoints**  
The endpoint.py sends a POST request to the deployed model and get the response as a JSON file.  
![image](https://user-images.githubusercontent.com/27814345/115309747-53e4e280-a18a-11eb-93b0-7be1db70fbf8.png)

**7. Benchmark the model**
Run the benchmark.py script to benchmark the model
![image](https://user-images.githubusercontent.com/27814345/115309907-8ee71600-a18a-11eb-8989-a16fb7724b67.png)

![image](https://user-images.githubusercontent.com/27814345/115309943-9a3a4180-a18a-11eb-9ad3-42a287c233d0.png)

**8. Create Publish and Consume Pipeline**
Pipeline is created through Azure Python sdk  
![image](https://user-images.githubusercontent.com/27814345/115310230-192f7a00-a18b-11eb-80b1-fa86c56a1823.png)

Pipeline Endpoint:  
![image](https://user-images.githubusercontent.com/27814345/115310311-3a906600-a18b-11eb-8103-fcf40046ef39.png)

Pipeline published:   
![image](https://user-images.githubusercontent.com/27814345/115310406-657aba00-a18b-11eb-8eaf-b63261d52106.png)

Bank marketing Dataset experience:  
![image](https://user-images.githubusercontent.com/27814345/115310549-965aef00-a18b-11eb-9478-b9d1e2968040.png)

Scheduled run:  
![image](https://user-images.githubusercontent.com/27814345/115310620-b4c0ea80-a18b-11eb-8d12-391e36ffe4a6.png)


## Screen Recording
Click [here](https://drive.google.com/file/d/12XJKjaxUsgBWBLr8-EDEL0R9iGnGkvcF/view?usp=sharing) to watch the screencasting.


## Standout Suggestions
•	I would like to try experimenting with different type of dataset and compare the best run model
•	In the notebook I would like to try different configurations
•	I would like to run the experiment for longer time and compare the results
