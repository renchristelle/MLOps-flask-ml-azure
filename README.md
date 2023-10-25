# MLOps Flask Application on Azure App Service with Azure Pipelines 
This is a repository for deploying a Flask Machine Learning Application on Azure App Services with Azure Pipelines


This project is built with python 3.9


![continuous-delivery](https://user-images.githubusercontent.com/58792/85061538-f7352780-b174-11ea-8001-b0561c5bad73.jpg)



## To run it locally follow these steps

1.  Create virtual environment and source

```bash
python3 -m venv ~/.flask-ml-azure
source ~/.flask-ml-azure/bin/activate
```

2.  Install the required Python packages with `make install`

3.  Run `python app.py`

4.  In a separate shell run: `./make_prediction.sh`


## To run it in Azure (Refer to [Azure Official Documentation guide](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops))  
  
  
#### Create an App Service using Azure Cloud Shell from [Azure Portal](https://portal.azure.com/#home)  

1.  Clone the Github Repo (with Azure Pipelines Enabled) into Azure Cloud Shell (set up SSH key if needed)

2.  Create virtual environment and source 

```bash
python3 -m venv ~/.flask-ml-azure
source ~/.flask-ml-azure/bin/activate
```

3.  Install the required Python packages with `make install`

4.  Create an app service and initially deploy your app in Cloud Shell with python 3.9 `az webapp up --runtime "PYTHON|3.9" -n <your-appservice>`

5.  Verify deployed application works by browsing to deployed url: `https://<your-appservice>.azurewebsites.net/`.

6.  Verify Machine Learning predictions work by running `make_predict_azure_app.sh` (you might need to change the name of your service to match the deployed prediction)  

#### Run Python pipeline in [Azure DevOps](https://dev.azure.com/christelleren)  

1.  Create an Azure DevOps project

2.  [Connect to Azure Resource Manager](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops#create-an-azure-devops-project-and-connect-to-azure)

3.  [Create new Python Pipeline with Github Integration](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops#create-a-python-specific-pipeline-to-deploy-to-app-service)

This process will create a [YAML file](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops#yaml-pipeline-explained)

4. You can now verify Continuous Delivery of Azure Pipelines by modifying an element in the repository


Sources: 
https://github.com/noahgift/flask-ml-azure-serverless/tree/master
