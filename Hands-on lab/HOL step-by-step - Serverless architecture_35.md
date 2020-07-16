### Task 1: Run the Logic App

1. Open your ServerlessArchitecture resource group in the Azure portal, then select your Logic App.

2. From the **Overview** blade, select **Enable**.

    ![In the TollBoothLogic Logic app blade, Overview is selected in the left menu, and the Enable enable button is selected in the right pane.](media/image113.png 'TollBoothLogic blade')

3. Now select **Run Trigger**, then select **Recurrence** to immediately execute your workflow.

    ![In the TollBoothLogic Logic app blade, Run Trigger and Recurrence are selected.](media/image114.png 'TollBoothLogic blade')

4. Select the **Refresh** button next to the Run Trigger button to refresh your run history. Select the latest run history item. If the expression result for the condition is **true**, then that means the CSV file should've been exported to Blob storage. Be sure to disable the Logic App so it doesn't keep sending you emails every 15 minutes. Please note that it may take longer than expected to start running, in some cases.

    ![In Logic App Designer, in the Condition section, under Inputs, true is highlighted.](media/image115.png 'Logic App Designer ')

