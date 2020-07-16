### Task 5: Publish the Function App from Visual Studio

In this task, you will publish the Function App from the starter project in Visual Studio to the existing Function App you provisioned in Azure.

1. Navigate to the **TollBooth** project using the Solution Explorer of Visual Studio.

2. Right-click the **TollBooth** project and select **Publish** from the context menu.

    ![In Solution Explorer, the TollBooth is selected, and within its context menu, the Publish item is selected.](media/image39.png 'Solution Explorer ')

3. In the Publish window, select **Azure**, then select **Next**.

    ![In the Pick a publish target window, the Azure Functions Consumption Plan is selected in the left pane. In the right pane, the Select Existing radio button is selected and the Run from package file (recommended) checkbox is unchecked. The Create Profile button is also selected.](media/vs-publish-function.png 'Publish window')

    > **Note**: If you do not see the ability to publish to an Azure Function, you may need to update your Visual Studio instance.

4. In the App Service form, select your **Subscription**, select **Resource Group** under **View**, then expand your **ServerlessArchitecture** resource group and select the Function App whose name ends with **FunctionApp**. Finally, **uncheck the `Run from package file` option**.

5. Whatever you named the Function App when you provisioned it is fine. Just make sure it is the same one to which you applied the Application Settings in Task 1 of this exercise.

    ![In the App Service form, Resource Group displays in the View field, and in the tree-view below, the ServerlessArchitecture folder is expanded, and TollBoothFunctionApp is selected.](media/vs-publish-function2.png 'Publish window')

    > **Note**: We do not want to run from a package file, because when we deploy from GitHub later on, the build process will be skipped if the Function App is configured for a zip deployment.

6. After you select the Function App, select **Finish**.

    > **Note**: If prompted to update the functions version on Azure, select **Yes**.

7. Select **Publish** to start the process. Watch the Output window in Visual Studio as the Function App publishes. When it is finished, you should see a message that says, `========== Publish: 1 succeeded, 0 failed, 0 skipped ==========`.

    ![The Publish button is selected.](media/vs-publish-function3.png "Publish")

8. Using a new tab or instance of your browser navigate to the Azure portal, <http://portal.azure.com>.

9. Open the **ServerlessArchitecture** resource group, then select the Azure Function App to which you just published.

10. Select **Functions** in the left-hand menu. You should see both functions you just published from the Visual Studio solution listed.

    ![In the Function Apps blade, in the left tree-view both TollBoothFunctionApp, and Functions (Read Only) are expanded. Beneath Functions (Read Only), two functions ExportLicensePlates and ProcessImage are highlighted.](media/dotnet-functions.png 'TollBoothFunctionApp blade')

11. Now we need to add an Event Grid subscription to the ProcessImage function, so the function is triggered when new images are added to blob storage. Select the **ProcessImage** function, select **Integration** on the left-hand menu, select **Event Grid Trigger (eventGridEvent)**, then select **Create Event Grid subscription**.

    ![In the TollboothFunctionApp tree-view, the ProcessImage function is selected. In the code window pane, the Add Event Grid subscription link is highlighted.](media/processimage-add-eg-sub.png 'ProcessImage function')

12. On the **Create Event Subscription** blade, specify the following configuration options:

    a. **Name**: Unique value for the App name similar to **processimagesub** (ensure the green check mark appears).

    b. **Event Schema**: Select Event Grid Schema.

    c. For **Topic Type**, select **Storage Accounts (Blob & GPv2)**.

    d. Select your **subscription** and **ServerlessArchitecture** resource group.

    e. For resource, select your recently created storage account. Enter **processimagesubtopic** into the **System Topic Name** field.

    f. Select only the **Blob Created** from the event types dropdown list.

    g. Leave Azure Function as the Endpoint Type.

13. Leave the remaining fields at their default values and select **Create**.

    ![In the Create event subscription form, the fields are set to the previously defined values.](media/processimage-eg-sub.png)

## Exercise 3: Create functions in the portal

**Duration**: 45 minutes

Create two new Azure Functions written in Node.js, using the Azure portal. These will be triggered by Event Grid and output to Azure Cosmos DB to save the results of license plate processing done by the ProcessImage function.

