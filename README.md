# MLOps-flask-ml-azure-serverless
This is a repo for deploying a Flask Machine Learning Application on Azure App Services

![continuous-delivery](https://user-images.githubusercontent.com/58792/85061538-f7352780-b174-11ea-8001-b0561c5bad73.jpg)



## To run it locally follow these steps (on Python 3.9)

1.  Create virtual environment and source

```bash
python3 -m venv ~/.flask-ml-azure
source ~/.flask-ml-azure/bin/activate
```

2.  Run `make install`

3.  Run `python app.py`

4.  In a separate shell run: `./make_prediction.sh`

## To run it in Azure Pipelines

1.  Refer to [Azure Official Documentation guide](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops)

2. Launch Azure Shell  

3.  Create Github Repo with Azure Pipelines Enabled 

4. Clone the repo into Azure Cloud Shell (set up SSH key if needed)

5.  Create virtual environment and source

```bash
python3 -m venv ~/.flask-ml-azure
source ~/.flask-ml-azure/bin/activate
```

6.  Run `make install`

7.  Create an app service and initially deploy your app in Cloud Shell `az webapp up -n <your-appservice>`

8. Verify deployed application works by browsing to deployed url: `https://<your-appservice>.azurewebsites.net/`

9.  Verify Machine Learning predictions work by running `make_predict_azure_app.sh` (you might need to change the name of your service to match the deployed prediction)

10. Create an Azure DevOps project and connect to Azure Resource Manager (refer to the [Official Documentation guide](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops))

11. Create new Python Pipeline with Github Integration (refer to ther [Official Documentation guide](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops#create-a-python-specific-pipeline-to-deploy-to-app-service))

This process will create a YAML file that looks roughly like the YAML output shown below.  Refer to the [official Azure Pipeline YAML documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops#yaml-pipeline-explained) for more information about it.

12. Verify Continuous Delivery of Azure Pipelines by modifying an element in the repository
