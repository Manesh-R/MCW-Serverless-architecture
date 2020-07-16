### Task 6: Add an Azure Cosmos DB output to the QueuePlateForManualCheckup function

In this task, you will add an Azure Cosmos DB output binding to the QueuePlateForManualCheckup function, enabling it to save its data to the NeedsManualReview collection.

1. Close the Edit Trigger blade if it is still open. Select **+ Add output** under `Outputs` within Integrations. In the `Create Output` blade that appears, select the **Azure Cosmos DB** binding type.

    ![The Add Output link is highlighted with an arrow pointing to the highlighted binding type in the Create Output blade.](media/function-output-binding-type.png "Create Output")

2. Specify the following configuration options in the Azure Cosmos DB output form:

    a. For database name, enter **LicensePlates**.

    b. For collection name, enter **NeedsManualReview**.

    c. Select the **Azure Cosmos DB account connection** you created earlier.

    ![In the Azure Cosmos DB output form, the following field values display: Document parameter name, outputDocument; Collection name, NeedsManualReview; Database name, LicensePlates; Azure Cosmos DB account connection, tollbooths_DOCUMENTDB.](media/manualcheckup-cosmos-integration.png 'Azure Cosmos DB output form')

3. Select **OK**.

## Exercise 4: Monitor your functions with Application Insights

**Duration**: 45 minutes

Application Insights can be integrated with Azure Function Apps to provide robust monitoring for your functions. In this exercise, you will provision a new Application Insights account and configure your Function Apps to send telemetry to it.

