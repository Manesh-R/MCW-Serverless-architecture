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

