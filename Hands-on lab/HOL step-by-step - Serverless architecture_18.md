### Task 3: Add an Azure Cosmos DB output to the SavePlateData function

In this task, you will add an Azure Cosmos DB output binding to the SavePlateData function, enabling it to save its data to the Processed collection.

1. Close the Edit Trigger blade if it is still open. Select **+ Add output** under `Outputs` within Integrations. In the `Create Output` blade that appears, select the **Azure Cosmos DB** binding type.

    ![The Add Output link is highlighted with an arrow pointing to the highlighted binding type in the Create Output blade.](media/function-output-binding-type.png "Create Output")

2. Scroll down in the Create Output form, then select **New** underneath to the Azure Cosmos DB account connection field.

    ![The new button is selected next to the Azure Cosmos DB account connection field.](media/image49.png 'New button')

    > **Note**: If you see a notice for "Extensions not installed", select **Install**.

    ![A message is displayed indicating the Cosmos DB Extensions are not installed. The Install link is selected.](media/cosmos-extension-install.png 'Cosmos DB Extensions not installed')

3. Select your Cosmos DB account from the list that appears.

4. Specify the following configuration options in the Azure Cosmos DB output form:

    a. For database name, type **LicensePlates**.

    b. For the collection name, type **Processed**.

    ![Under Azure Cosmos DB output the following field values display: Document parameter name, outputDocument; Collection name, Processed; Database name, LicensePlates; Azure Cosmos DB account connection, tollbooths_DOCUMENTDB.](media/saveplatedata-cosmos-integration.png 'Azure Cosmos DB output section')

5. Select **OK**.

    > **Note**: you should wait for the template dependency to install if you were prompted earlier.

