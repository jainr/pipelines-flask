# python-flask-docker
Sample python flask application that shows how to continously integrate and release your application using Azure DevOps.
The application uses docker to create an image,save the image in ACR and then deploy it to Azure WebApp for containers.

# Here are the steps in Build/Continous Integration Phase
- Create or reuse Azure Container Registry using Azure Resource Manager ARM template
- Set up Python environment with dependencies on build machine
- Execute Unit Test using Pytest
- Publish Test report
- Build a docker image
- Push the image to a repository in Azure container registry.
- Publish current working directory which contains source code as artifact (drop) for release pipeline.

# Here are the steps in Release/Continous Deployment Phase
- It's triggered every time a new artifact drop is available
- Using another ARM template, we create Azure Web App service for containers, as part of this step you will provide the docker image that you want to be deployed on this webapp, select the image created as part of build pipeline.
- Publish the web app
- Execute integration Tests using Pytest against the deployed app.
- Publish Test results.


We only show one environment but the example could be extended for multiple environments.


**Note: Code copied from portal.azure.com DevOps sample, couldn't find their source repo to fork**
