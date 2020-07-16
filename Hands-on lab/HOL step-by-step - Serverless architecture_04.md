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

