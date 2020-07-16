### Task 2: Configure application settings

In this task, you will apply application settings using the Microsoft Azure Portal.

1. Select **Configuration** in the left-hand menu.

    ![In the TollBoothFunctionApp blade on the Overview tab, under Configured features, the Configuration item is selected.](media/image34.png 'TollBoothFunctionApp blade')

2. Scroll to the **Application settings** section. Use the **+ New application setting** link to create the following additional Key/Value pairs (the key names must exactly match those found in the table below). **Be sure to remove the curly braces (`{}`)**.

    |                          |                                                                                                                                                             |
    | ------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------: |
    | **Application Key**      |                                                                          **Value**                                                                          |
    | computerVisionApiUrl     | Computer Vision API endpoint you copied earlier. Append **vision/v2.0/ocr** to the end. Example: `https://<YOUR-SERVICE-NAME>.cognitiveservices.azure.com/vision/v2.0/ocr` |
    | computerVisionApiKey     |                                                                   Enter `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is the URI for the **computerVisionApiKey** Key Vault secret                                                                   |
    | eventGridTopicEndpoint   |                                                                  Event Grid Topic endpoint                                                                  |
    | eventGridTopicKey        |                                                                 Enter `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is the URI for the **eventGridTopicKey** Key Vault secret                                                                 |
    | cosmosDBEndPointUrl      |                                                                        Cosmos DB URI                                                                        |
    | cosmosDBAuthorizationKey |                                                                    Enter `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is the URI for the **cosmosDBAuthorizationKey** Key Vault secret                                                                    |
    | cosmosDBDatabaseId       |                                                            Cosmos DB database id (LicensePlates)                                                            |
    | cosmosDBCollectionId     |                                                        Cosmos DB processed collection id (Processed)                                                        |
    | exportCsvContainerName   |                                                       Blob storage CSV export container name (export)                                                       |
    | blobStorageConnection    |                                                               Enter `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is the URI for the **blobStorageConnection** Key Vault secret                                                                |

    ![In the Application Settings section, the previously defined key / value pairs are displayed.](media/application-settings.png 'Application Settings section')

3. Select **Save**.

    ![Screenshot of the Save icon.](media/image36.png 'Save icon')

