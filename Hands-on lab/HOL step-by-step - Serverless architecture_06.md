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

