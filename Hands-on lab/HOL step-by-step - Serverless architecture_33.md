### Task 2: Configure your Function App to use your GitHub repository for continuous deployment

1. Open the Azure Function App you created whose name ends with **FunctionApp**, or the name you specified for the Function App containing the ProcessImage function.

2. Select **Deployment Center** underneath Deployment in the left-hand menu.

    ![The Platform features tab is displayed, under Code Deployment, Container settings is selected.](media/functionapp-menu-deployment-center-link.png 'TollBoothFunctionApp blade')

3. Select **GitHub** in the **Deployment Center** blade. Enter your GitHub credentials if prompted. Select **Continue**.

    ![The GitHub tile is selected from a list of repository options.](media/functionapp-dc-github.png 'Deployment Center blade')

4. Select **App Service build service**, then select **Continue**.

    ![Under the Build Provider step, App Service build service tile is selected.](media/functionapp-dc-build-provider.png 'Deployment Center blade')

5. **Choose your organization**.

6. Choose your new repository under **Choose project**. Make sure the **master branch** is selected.

    ![Fields in the Deployment option blade set to the following settings: Choose your organization, obscured; Choose repository, serverless-architecture-lab; Choose branch, master.](media/functionapp-dc-configure.png 'Deployment Center blade')

7. Select **Continue**.

8. On the Summary page, select **Finish**.

9. After continuous deployment is configured, all file changes in your deployment source are copied to the function app and a full site deployment is triggered. The site is redeployed when files in the source are updated.

    ![The Deployment Center tab is shown with a pending build.](media/functionapp-dc.png 'Function App Deployment Center')

