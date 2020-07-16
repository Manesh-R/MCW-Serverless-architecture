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

