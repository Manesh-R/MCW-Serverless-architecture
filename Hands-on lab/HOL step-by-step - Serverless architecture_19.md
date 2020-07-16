### Task 4: Create function to save manual verification info to Azure Cosmos DB

In this task, you will create a new function triggered by Event Grid and outputs information about photos that need to be manually verified to Azure Cosmos DB.

1. Close the `SavePlateData` function. Select the **+ Add** button within the **Functions** blade of the Function App.

    ![In the left-hand menu next to the Functions item, the + button is highlighted along with its tooltip Create new displaying.](media/new-function-button.png "Create new function")

2. Enter **event grid** into the template search form, then select the **Azure Event Grid trigger** template.

    ![Event grid is entered into the search field, and in the results, Azure Event Grid trigger tile displays.](media/new-function-event-grid-trigger-template.png 'Event grid trigger')

3. In the **New Function** form, fill out the following properties:

    a. For name, type **QueuePlateForManualCheckup**

    ![In the Azure Event Grid trigger form, QueuePlateForManualCheckup is typed in the Name field along with a Create and Cancel button.](media/image51.png 'Event Grid trigger, New Function form')

4. Select **Create Function**.

5. Select **Code + Test**, then replace the code in the new SavePlateData function with the following:

    ```javascript
    module.exports = async function(context, eventGridEvent) {
        context.log(typeof eventGridEvent);
        context.log(eventGridEvent);

        context.bindings.outputDocument = {
            fileName: eventGridEvent.data['fileName'],
            licensePlateText: '',
            timeStamp: eventGridEvent.data['timeStamp'],
            resolved: false
        };

        context.done();
    };
    ```

6. Select **Save**.

7. If you see the following error about Application Insights not being configured, ignore for now. We will add Application Insights in a later exercise.

    ![Error about App Insights not being installed.](media/app-insights-error-message.png "App Insights error")

