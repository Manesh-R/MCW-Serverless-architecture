## Exercise 1: Azure data, storage, and serverless environment setup

**Duration**: 30 minutes

You must provision a few resources in Azure before you start developing the solution. Ensure all resources use the same resource group for easier cleanup.

In this exercise, you will provision a blob storage account using the Hot tier, and create two containers within to store uploaded photos and exported CSV files. You will then provision two Function Apps instances, one you will deploy from Visual Studio, and the other you will manage using the Azure portal. Next, you will create a new Event Grid topic. After that, you will create an Azure Cosmos DB account with two collections. Finally, you will provision a new Cognitive Services Computer Vision API service for applying object character recognition (OCR) on the license plates.

### Help references

|                                            |                                                                                                                                                       |
| ------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------: |
| **Description**                            |                                                                       **Links**                                                                       |
| Creating a storage account (blob hot tier) | <https://docs.microsoft.com/azure/storage/common/storage-create-storage-account?toc=%2fazure%2fstorage%2fblobs%2ftoc.json%23create-a-storage-account> |
| Creating a function app                    |                                <https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal>                                |
| Concepts in Event Grid                     |                                                <https://docs.microsoft.com/azure/event-grid/concepts>                                                 |
| Creating an Azure Cosmos DB account        |                                              <https://docs.microsoft.com/azure/cosmos-db/manage-account>                                              |

### Task 1: Provision the storage account

1. Using a new tab or instance of your browser, navigate to the Azure portal, <http://portal.azure.com>.

2. If the left-hand menu is collapsed, select the menu button on the top-left corner of the portal to expand the menu.

    ![Expand the portal menu.](media/expand-portal-menu.png "Portal menu button")

3. Select **+ Create a resource**, then select **Storage**, **Storage account**.

    ![In the menu pane of Azure Portal, Create a resource is selected. Under Azure Marketplace, Storage is selected, and under Featured, Storage account is selected.](media/new-storage-account.png 'Azure Portal')

4. On the **Create storage account** blade, specify the following configuration options:

    a. For **Resource group**, select the **Use existing** radio button, and select the **ServerlessArchitecture** resource group.

    b. **Name**: enter a unique value for the storage account such as **tollboothstorage** (must be all lower case; ensure the green check mark appears).

    c. Ensure the **Location** selected is the same region as the resource group.

    d. For performance, ensure **Standard** is selected.

    e. For account kind, select **StorageV2 (general purpose v2)**.

    f. For replication, select **Locally-redundant storage (LRS)**.

    g. Select **Hot** for the access tier.

    ![Fields in the Create storage account blade are set to the previously defined values.](media/image12.png 'Create storage account blade')

5. Select **Review + create**, then select **Create**.

6. After the storage account has completed provisioning, open the storage account by selecting **Go to resource**.

    ![In the Azure Portal, once the storage account has completed provisioning a status message is displayed saying Your deployment is complete. Beneath the next steps section The Go to resource button is highlighted.](media/storage-go-to-resource.png "Go to resource")

7. On the **Storage account** blade, select **Access Keys**, under Settings in the menu. Then on the **Access keys** blade, select the **Click to copy** button for **key1 connection string.**

    ![In the Storage account blade, under Settings, Access keys is selected. Under Default keys, the copy button next to the key1 connection string is selected.](media/image15.png 'Storage account blade')

8. Paste the value into a text editor, such as Notepad, for later reference.

9. Select **Containers** under **Blob Service** in the menu. Then select the **+ Container** button to add a new container. In the **Name** field, enter **images**, select **Private (no anonymous access)** for the public access level, then select **OK** to save.

    ![In the Storage blade, under Settings, Containers is selected. In the Containers blade, the + (add icon) Container button is selected. Below, the Name field displays images, and the Public access level is set to Private (no anonymous access).](media/storage-new-container-images.png 'Storage and Containers blade')

10. Repeat these steps to create a container named **export**.

    ![In the Storage blade, under Settings, Containers is selected. In the Containers blade, the + (add icon) Container button is selected. Below, the Name field displays export, and the Public access level is set to Private (no anonymous access).](media/new-container-export.png 'Storage and Containers blade')

### Task 2: Provision the Function Apps

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, then enter **function** into the search box on top. Select **Function App** from the results.

    ![In the menu pane of the Azure Portal, the Create a resource button is selected. Function is typed in the search field, and Function App is selected from the search results.](media/image17.png 'Azure Portal')

3. Select the **Create** button on the **Function App overview** blade.

4. Within the **Create Function App** *Basics* blade, specify the following configuration options:

    a. **Subscription**: Select your Azure subscription for this lab.

    b. **Resource Group**: Select **ServerlessArchitecture**.

    c. **Name**: Unique value for the App name (ensure the green check mark appears). Provide a name similar to **TollBoothFunctionApp**.

    d. **Publish**: Select **Code**.

    e. **Runtime stack**: Select **.NET Core**.

    f. **Version**: Select **3.1**.

    g. **Region**: Select the region you are using for this lab, or the closest available one.

    ![In the basics tab of the Create Function App blade, the form fields are set to the previously defined values.](media/new-functionapp-net-basics.png 'Function App Basics blade')

5. Select **Next: Hosting >**.

6. Within the **Hosting** blade, specify the following configuration options:

    a. **Storage account**: Leave this option as **create new**.

    b. **Operating system**: Select **Windows**.

    c. **Plan type**: Select **Consumption (Serverless)**.

    ![In the Hosting tab of the Create Function App blade, the form fields are set to the previously defined values.](media/new-functionapp-net-hosting.png "Function App Hosting blade")

7. Select **Next: Monitoring >**.

    a. **Enable Application Insights**: Select **No** (we'll add this later).

    ![In the Monitoring tab of the Create Function App blade, the form fields are set to the previously defined values.](media/new-functionapp-net-monitoring.png "Function App Monitoring blade")

8. Select **Review + create**, then select **Create** to provision the new Function App.

9. **Repeat steps 1-3** to create a second Function App.

10. Within the **Create Function App** blade *Basics* tab, specify the following configuration options:

    a. **Subscription**: Select your Azure subscription for this lab.

    b. **Resource Group**: Select **ServerlessArchitecture**.

    c. **Name**: Unique value for the App name (ensure the green check mark appears). Provide a name similar to **TollBoothEvents**.

    d. **Publish**: Select **Code**.

    e. **Runtime stack**: Select **Node.js**.

    f. **Version**: Select **12**.

    g. **Region**: Select the region you are using for this lab, or the closest available one.

    ![Fields in the Create Function App blade Basics tab are set to the previously defined values.](media/new-functionapp-nodejs-basics.png 'Function App Basics blade')

11. Select **Next: Hosting >**.

12. Within the **Hosting** blade, specify the following configuration options:

    a. **Storage account**: Leave this option as **create new**.

    b. **Operating system**: Select **Windows**.

    c. **Plan type**: Select **Consumption**.

    ![Fields in the Create Function App blade Hosting tab are set to the previously defined values.](media/new-functionapp-net-hosting.png "Function App Hosting blade")

13. Select **Next: Monitoring >**.

    a. **Enable Application Insights**: Select **No** (we'll add this later).

    ![Fields in the Create Function App blade Monitoring tab are set to the previously defined values.](media/new-functionapp-net-monitoring.png "Function App Monitoring blade")

14. Select **Review + create**, then select **Create** to provision the new Function App.

### Task 3: Provision the Event Grid topic

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, then enter **event grid** into the search box on top. Select **Event Grid Topic** from the results.

    ![In the menu pane of the Azure Portal, the New button is selected. Event grid is typed in the search field, and Event Grid Topic is selected from the search results.](media/image19.png 'Azure Portal')

3. Select the **Create** button on the **Event Grid Topic overview** blade.

4. On the **Create Topic** blade, specify the following configuration options:

    a. **Name:** Unique value for the App name such as **TollboothEventGrid** (ensure the green check mark appears).

    b. Select the Resource Group **ServerlessArchitecture**.

    c. Ensure the **Location** selected is set to the same region as your Resource Group.

    ![In the Create Topic blade, the Name field is set to TollBoothTopic, and the Resource Group selected is ServerlessArchitecture.](media/new-eventgrid-topic.png 'Create Topic blade')

5. Select **Next: Advanced >**.

6. Make sure **Event Grid Schema** is selected as the event schema.

    ![Select the event grid scema.](media/new-eventgrid-topic-advanced.png "Create Topic - Advanced")

7. Select **Review + Create**, then select **Create** in the screen that follows.

8. After the Event Grid topic has completed provisioning, open the account by opening the **ServerlessArchitecture** resource group, and then selecting the **Event Grid** topic name.

7. Select **Overview** in the menu, and then copy the **Topic Endpoint** value.

    ![In the TollBoothTopic blade, Overview is selected, and the copy button next to the Topic Endpoint is called out.](media/image21.png 'TollBoothTopic blade')

8. Select **Access Keys** under Settings in the menu.

9. Within the **Access Keys** blade, copy the **Key 1** value.

    ![In the TollBoothTopic blade, in the left menu under Settings, Access keys is selected. In the listing of Access keys, the copy button next to the Key 1 access key is selected.](media/image22.png 'TollBoothTopic - Access keys blade')

10. Paste the values into a text editor, such as Notepad, for later reference.

### Task 4: Provision the Azure Cosmos DB account

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, select **Databases** then select **Azure Cosmos DB**.

    ![In Azure Portal, in the menu, New is selected. Under Azure marketplace, Databases is selected, and under Featured, Azure Cosmos DB is selected.](media/image23.png 'Azure Portal')

3. On the **Create new Azure Cosmos DB** **account** blade, specify the following configuration options:

    a. Specify the Resource Group **ServerlessArchitecture**.

    b. For Account Name, type a unique value for the App name such as **tollboothdb** (ensure the green check mark appears).

    c. Select the **Core (SQL)** API.

    d. Select the same **Location** as your Resource Group if available. Otherwise, select the next closest **region**.

    e. Ensure **Notebooks** is disabled.

    f. Ensure **Apply Free Tier Discount** is disabled.

    g. Select **Production** for the Account Type.

    h. Ensure **Geo-Redundancy** is disabled.

    i. Ensure **Multi-region writes** is disabled.

    j. Ensure **Availability Zones** is disabled.

    ![Fields in the Azure Cosmos DB blade are set to the previously defined settings.](media/new-cosmosdb.png 'Azure Cosmos DB blade')

4. Select **Review + create**, then select **Create**.

5. After the Azure Cosmos DB account has completed provisioning, open the account by opening the **ServerlessArchitecture** resource group, and then selecting the **Azure Cosmos DB** account name.

6. Select **Data Explorer** in the left-hand menu, then select **New Container**.

    ![In the Data Explorer blade, the Data Explorer item is selected in the left menu. The New Container button is selected in the Data Explorer pane.](media/data-explorer-new-container.png 'Data Explorer blade')

7. On the **Add Container** blade, specify the following configuration options:

    a. Enter **LicensePlates** for the **Database id**.

    b. Leave **Provision database throughput** unchecked.

    c. Enter **Processed** for the **Container id**.

    d. Partition key: **/licensePlateText**

    e. Throughput: **5000**

    ![In the Add Container blade, fields are set to the previously defined values.](media/cosmosdb-add-processed-collection.png 'Add Container blade')

8. Select **OK**.

9. Select **New Container** to add another container.

10. On the **Add Container** blade, specify the following configuration options:

    a. For Database id, choose **Use existing** and select **LicensePlates**.

    b. Enter **NeedsManualReview** for the **Container id**.

    c. Partition key: **/fileName**

    d. Throughput: **5000**

    ![In the Add Container blade, fields are set to the previously defined values.](media/cosmosdb-add-manualreview-collection.png 'Add Collection blade')

11. Select **OK**.

12. Select **Firewall and virtual networks** in the left-hand menu.

13. Select **+ Add my current IP** to add your IP address to the IP list under Firewall. Next, check the box next to **Accept connections from within public Azure datacenters**. This will enable Azure services, such as your Function Apps to access your Azure Cosmos DB account.

    ![The checkbox is highlighted.](media/cosmos-db-firewall.png "Firewall and virtual networks")

14. Select **Save**.

15. Select **Keys** under Settings in the left-hand menu.

16. Underneath the **Read-write Keys** tab within the Keys blade, copy the **URI** and **Primary Key** values.

    ![In the tollbooth - Keys blade, under Settings, Keys is selected. On the Read-write Keys tab, the copy buttons for the URI and Primary Key fields are selected.](media/image28.png 'tollbooth - Keys blade')

17. Paste the values into a text editor, such as Notepad, for later reference.

### Task 5: Provision the Computer Vision API service

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, then enter **computer vision** into the search box on top. Select **Computer Vision** from the results.

    ![In the Azure Portal, Create a resource is selected in the left menu and Computer vision is typed in the search box with Computer Vision displaying in the suggested results.](media/search-computer-vision.png 'Azure Portal')

3. Select the **Create** button on the **Computer Vision API** **Overview** blade.

4. On the **Create Computer Vision API** blade, specify the following configuration options:

    a. **Name**: Unique value for the App name such as **tollboothvisionINIT** (ensure the green check mark appears).

    b. Ensure the **Location** selected is the same region as your Resource Group.

    c. For pricing tier, select **S1 (10 Calls per second)**.

    d. Specify the Resource Group **ServerlessArchitecture**.

    ![In the Create Computer Vision blade, fields are set to the previously defined values.](media/create-computer-vision.png 'Create blade')

5. Select **Create**.

    ![Screenshot of the Create button.](media/image13.png 'Create button')

6. After the Computer Vision API has completed provisioning, open the service by opening the **ServerlessArchitecture** resource group, and then selecting the **Computer Vision** **API** service name.

7. Under Resource Management in the left-hand menu, select **Keys and Endpoint**.

8. Within the **Keys and Endpoint** blade, copy the **ENDPOINT** value and **KEY 1** value.

    ![In the Cognitive Services blade, under Resource Management, Keys and Endpoint is selected. The Copy button next to the Endpoint and Key 1 values are selected.](media/copy-computer-vision-key.png 'Keys and Endpoint information')

9. Paste the values into a text editor, such as Notepad, for later reference.

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

### Task 7: Retrieve the URI for each secret

When you set the App Settings for the Function App in the next section below, you will need to reference the URI of a secret in Key Vault, including the version number. To do this, perform the following steps for each secret and **copy the values** to Notepad or similar text application.

1. Open your Key Vault instance in the portal.

2. Select **Secrets** under Settings in the left-hand menu.

3. Select the secret whose URI value you wish to obtain.

4. Select the **Current Version** of the secret.

    ![The secret's current version is selected.](media/key-vault-secret-current-version.png "Current Version")

5. Copy the **Secret Identifier**.

    ![The Secret Identifier field is highlighted. Next to this field is a copy button.](media/key-vault-secret-identifier.png "Secret Identifier")

    When you add the Key Vault reference to this secret within a Function App's App Settings, you will use the following format: `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is replaced by the Secret Identifier (URI) value above. **Be sure to remove the curly braces (`{}`)**.

    For example, a complete reference would look like the following:

    `@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/blobStorageConnection/d6ea0e39236348539dc33565e031afc3)`

When you are done creating the values, you should have a list similar to the following:

```text
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/blobStorageConnection/771aa40adac64af0b2aefbd741bd46ef)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/computerVisionApiKey/ce228a43f40140dd8a9ffb9a25d042ee)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/cosmosDBAuthorizationKey/1f9a0d16ad22409b85970b3c794a218c)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/eventGridTopicKey/e310bcd71a72489f89b6112234fed815)
```

