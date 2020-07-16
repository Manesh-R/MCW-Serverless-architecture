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

