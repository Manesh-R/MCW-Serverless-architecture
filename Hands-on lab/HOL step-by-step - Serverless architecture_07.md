### Task 6: Provision Azure Key Vault

Azure Key Vault is used to securely store all secrets, such as database connection strings and keys.

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, then enter **key vault** into the search box on top. Select **Key Vault** from the results.

    ![In the Azure Portal, Create a resource is selected from the left menu and Key Vault is typed in the search box with Key Vault displaying in the suggested results.](media/search-key-vault.png 'Azure Portal')

3. Select the **Create** button on the **Key Vault** **overview** blade.

4. On the **Create key vault** blade, specify the following configuration options:

    a. **Subscription**: Select your Azure subscription used for this lab.

    b. **Resource group**: Select **ServerlessArchitecture**.

    c. **Key vault name**: Unique value for the name such as **TollBoothVaultINIT** (ensure the green check mark appears).

    d. **Region**: Select the same region as your Resource Group.

    e. **Pricing tier**: Select **Standard**.

    f. **Soft delete**: Select **Enable**.

    g. **Retention period (days)**: Leave at 90.

    h. **Purge protection**: Select **Disable**.

    ![In the Create key vault blade, fields are set to the previously defined values.](media/create-key-vault.png 'Create blade')

5. Select **Review + create**, then select **Create**.

6. After the deployment completes, select **Go to resource**.

    ![When the deployment completes, a message is displayed indicating Your deployment is complete. The Go to resource button is highlighted in the next steps section.](media/key-vault-deployment-complete.png "Your deployment is complete")

7. Select **Secrets** under Settings in the left-hand menu.

8. Select **Generate/Import** to add a new key.

    ![The Secrets menu item and the Generate/Import button are highlighted.](media/generate-secret.png "Key Vault - Secrets")

9. Use the table below for the Name / Value pairs to use when creating the secrets. You only need to populate the **Name** and **Value** fields for each secret, and can leave the other fields at their default values.

    |                          |                                                                                                                                                             |
    | ------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------: |
    | **Name**      |                                                                          **Value**                                                                          |
    | computerVisionApiKey     |                                                                   Computer Vision API key                                                                   |
    | eventGridTopicKey        |                                                                 Event Grid Topic access key                                                                 |
    | cosmosDBAuthorizationKey |                                                                    Cosmos DB Primary Key                                                                    |
    | blobStorageConnection    |                                                               Blob storage connection string                                                                |

    When you are finished creating the secrets, your list should look similar to the following:

    ![The listing of secrets is displayed matching the previously defined values.](media/key-vault-keys.png "Key Vault Secrets")

