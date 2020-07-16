### Task 1: Create function to save license plate data to Azure Cosmos DB

In this task, you will create a new Node.js function triggered by Event Grid and that outputs successfully processed license plate data to Azure Cosmos DB.

1. Using a new tab or instance of your browser navigate to the Azure portal, <http://portal.azure.com>.

2. Open the **ServerlessArchitecture** resource group, then select the Azure Function App you created whose name ends with **Events**. If you did not use this naming convention, make sure you select the Function App that you _did not_ deploy to in the previous exercise.

3. Select **Functions** in the left-hand menu, then select **+ Add**.

    ![In the Function Apps blade, the TollBoothEvents2 application is selected. In the Overview tab, the + New function button is selected.](media/functions-new.png 'TollBoothEvents2 blade')

4. Enter **event grid** into the template search form, then select the **Azure Event Grid trigger** template.

    ![In the Template search form, event grid is typed in the search field. Below, the Event Grid trigger tile is highlighted.](media/new-function-event-grid-trigger-template.png "Template search form")

5. In the _New Function_ form, enter `SavePlateData` for the **Name**, then select **Create Function**.

    ![In the New Function form, SavePlateData is entered in the Name field and the Create button is highlighted.](media/new-function-saveplatedata.png "New Function form")

6. Select **Code + Test**, then replace the code in the new SavePlateData function with the following:

    ```javascript
    module.exports = function(context, eventGridEvent) {
        context.log(typeof eventGridEvent);
        context.log(eventGridEvent);

        context.bindings.outputDocument = {
            fileName: eventGridEvent.data['fileName'],
            licensePlateText: eventGridEvent.data['licensePlateText'],
            timeStamp: eventGridEvent.data['timeStamp'],
            exported: false
        };

        context.done();
    };
    ```

    ![The function code is displayed.](media/saveplatedata-code.png "SavePlateData Code + Test")

7. Select **Save**.

8. If you see the following error about Application Insights not being configured, ignore for now. We will add Application Insights in a later exercise.

    ![Error about App Insights not being installed.](media/app-insights-error-message.png "App Insights error")

