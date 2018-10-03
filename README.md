# Azure Container Repository / App Service

## Prerequisites
- Azure Account
- Azure CLI
- Git
- Node 8 LTS or later
- VS Code
    - Azure Tools ([ms-vscode.vscode-node-azure-pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack))

## Steps
1. Run the command `npx create-next-app my-app` in a terminal.

    ![Generate React app](images/create-next-app.png)

1. Open `./my-app` in VS Code.

    ![Open VS Code](images/open-code.png)

1. Create an `create-acr.azcli` file and enter the following:

    ```bash
    az group create --name ReactApp --location westus
    # replace reactappregistry01 with a unique name
    az acr create --name reactappregistry01 --resource-group ReactApp --admin-enabled true --sku Basic
    ```

    ![Create azcli file](images/create-azcli-file.png)

1. Run each command in order.

    ![Run line in terminal](images/run-line-in-terminal.png)

1. Run the VS Code Command `Docker: Add Docker files to workspace`.

    ![Add Docker files](images/add-docker-files-to-workspace.png)

1. Select Node.js.

    ![Select Node.js](images/add-docker-files-platform.png)

1. Use default port (`3000`).

    ![Select port](images/add-docker-files-port.png)

1. Remove `&& mv node_modules ../` from `Dockerfile`.

    ![Remove command](images/docker-delete-command.png)

1. Add `RUN npm run build` after `COPY . .` to `Dockerfile`.

    ![Add command](images/docker-add-build-command.png)

1. Save the changes.

1. Open the context menu on `Dockerfile` and click `Build Image`.

    ![Build the image](images/docker-build-image.png)

1. Add the URL to your Azure Container Repository to the image tag (`youracrname.azurecr.io/`).

    ![Add tag](images/docker-build-image-tag.png)

1. Open a terminal and login to your Azure Container Repository (`az acr login --name youracrname`).

    ![Login](images/az-acr-login.png)

1. Push your image to Azure Container Repository.

    ![Push image](images/docker-push.png)

1. Wait for the push to finish.

    ![Wait](images/docker-push-wait.png)

1. Deploy the image to Azure App Service.

    ![Deploy](images/deploy-image.png)

1. Choose the Resource Group created in step 3

    ![Choose Resource Group](images/deploy-resource-group.png)

1. Create an App Service Plan.

    ![Create App Service Plan](images/deploy-app-service-plan.png)

1. Choose a pricing tier.

    ![Choose pricing tier](images/deploy-choose-tier.png)

1. Create a unique name.

    ![Create name](images/deploy-name.png)

1. Wait for your app to be created then open the URL given in your browser.

    ![Wait](images/wait-for-app-ready.png)

1. It will take a second to spin up, but your app is now deployed.

    ![View Site](images/view-site.png)
