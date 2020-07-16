## Exercise 4: Monitor your functions with Application Insights

**Duration**: 45 minutes

Application Insights can be integrated with Azure Function Apps to provide robust monitoring for your functions. In this exercise, you will provision a new Application Insights account and configure your Function Apps to send telemetry to it.

### Help references

|                                                               |                                                                                  |
| ------------------------------------------------------------- | :------------------------------------------------------------------------------: |
| **Description**                                               |                                    **Links**                                     |
| Monitor Azure Functions using Application Insights            |     <https://docs.microsoft.com/azure/azure-functions/functions-monitoring>      |
| Live Metrics Stream: Monitor & Diagnose with 1-second latency | <https://docs.microsoft.com/azure/application-insights/app-insights-live-stream> |

### Task 1: Provision an Application Insights instance

1. Navigate to the Azure portal, <http://portal.azure.com>.

2. Select **+ Create a resource**, then type **application insights** into the search box on top. Select **Application Insights** from the results.

    ![In the Azure Portal menu pane, Create a resource is selected. In the New blade, application insights is typed in the search box, and Application insights is selected from the search results.](media/new-application-insights.png 'Azure Portal')

3. Select the **Create** button on the **Application Insights overview** blade.

4. On the **Application Insights** blade, specify the following configuration options:

    a. **Name**: Unique value for the App name similar to **TollboothMonitor** (ensure the green check mark appears).

    b. **Resource Group**: Select **ServerlessArchitecture**.

    c. Select the same **Region** as your Resource Group region.

    d. **Resource Mode**: Select **Classic**.

    ![Fields in the Application Insights blade are set to the previously defined settings.](media/application-insights-form.png 'Application Insights blade')

5. Select **Review + Create**, then choose **Create**.

### Task 2: Enable Application Insights integration in your Function Apps

Both of the Function Apps need to be updated with the Application Insights instrumentation key so they can start sending telemetry to your new instance.

1. After the Application Insights account has completed provisioning, open the instance by opening the **ServerlessArchitecture** resource group, and then selecting the your recently created application insights instance.

2. Copy the **Instrumentation Key** from the Essentials section of the **Overview** blade.

    > **Note**: You may need to expand the **Essentials** section.

    ![In Application Insights blade, Overview is selected in the left-hand menu. In the right pane, the copy button next to the Instrumentation Key is selected.](media/app-insights-key.png 'TollBoothMonitor blade')

3. Open the Azure Function App you created whose name ends with **FunctionApp**, or the name you specified for the Function App containing the ProcessImage function.

4. Select **Configuration** in the left-hand menu.

5. Scroll down to the **Application settings** section. Use the **+ Add new setting** link and name the new setting **APPINSIGHTS_INSTRUMENTATIONKEY**. Paste the copied instrumentation key into its value field.

    ![In the TollBoothFunctionApp blade, the + Add new setting link is selected. In the list of application settings, APPINSIGHTS_INSTRUMENTATIONKEY is selected along with its value.](media/app-insights-key-app-setting.png "Application settings")

6. Select **OK**.

7. Select **Save**.

    ![Screenshot of the Save icon.](media/image36.png 'Save icon')

8. Follow the steps above to add the APPINSIGHTS_INSTRUMENTATIONKEY setting to the function app that ends in **Events**.

### Task 3: Use the Live Metrics Stream to monitor functions in real time

Now that Application Insights has been integrated into your Function Apps, you can use the Live Metrics Stream to see the functions' telemetry in real time.

1. Open the Azure Function App you created whose name ends with **FunctionApp**, or the name you specified for the Function App containing the ProcessImage function.

2. Select **Application Insights** on the left-hand menu. Select **Turn on Application Insights** in the Application Insights blade.

    ![In the TollBoothFunctionApp blade, under Configured features, the Application Insights link is selected.](media/image64.png 'TollBoothFunctionApp blade')

3. Make sure **Enable** is selected. Notice that your app is already linked to your Application Insights instance at this point. Select **Apply**. Select **Yes** when prompted to apply monitoring settings.

    ![Activation Insights is enabled.](media/enable-app-insights.png "Application Insights")

4. Open the Azure Function App you created whose name ends with **Events**, or the name you specified for the Function App containing the NodeJS functions.

5. Select **Application Insights** on the left-hand menu. Select **Turn on Application Insights** in the Application Insights blade.

    ![In the TollBoothFunctionApp blade, under Configured features, the Application Insights link is selected.](media/events-function-app-turn-on-app-insights.png 'TollBoothFunctionApp blade')

6. Make sure **Enable** is selected. Notice that your app is already linked to your Application Insights instance at this point. Select **Apply**. Select **Yes** when prompted to apply monitoring settings.

    ![Activation Insights is enabled.](media/enable-app-insights-function.png "Application Insights")

7. Select your Application Insights name under `Link to an Application Insights resource`.

    ![The App Insights link is highlighted.](media/app-insights-link.png "Application Insights link")

8. In Application Insights, select **Live Metrics Stream** underneath Investigate in the menu.

    ![In the TollBoothMonitor blade, in the pane under Investigate, Live Metrics Stream is selected. ](media/live-metrics-link.png 'TollBoothMonitor blade')

9. Leave the Live Metrics Stream open and go back to the starter app solution in Visual Studio.

10. Navigate to the **UploadImages** project using the Solution Explorer of Visual Studio. Right-click on **UploadImages**, then select **Properties**.

    ![In Solution Explorer, the UploadImages project is expanded, and Properties is selected from the right-click context menu.](media/vs-uploadimages.png 'Solution Explorer')

11. Select **Debug** in the left-hand menu, then paste the connection string for your Blob storage account into the **Command line arguments** text field. This will ensure that the required connection string is added as an argument each time you run the application. Additionally, the combination of adding the value here and the `.gitignore` file included in the project directory will prevent the sensitive connection string from being added to your source code repository in a later step.

    ![The Debug menu item and the command line arguments text field are highlighted.](media/vs-command-line-arguments.png "Properties - Debug")

12. Save your changes.

13. Right-click the **UploadImages** project in the Solution Explorer, then select **Debug** then **Start new instance** from the context menu.

    ![In Solution Explorer, the UploadImages project is selected. From the context menu, Debug then Start new instance is selected.](media/vs-debug-uploadimages.png 'Solution Explorer')

14. When the console window appears, enter **1** and press **ENTER**. This uploads a handful of car photos to the images container of your Blob storage account.

    ![A Command prompt window displays, showing images being uploaded.](media/image69.png 'Command prompt window')

15. Switch back to your browser window with the Live Metrics Stream still open within Application Insights. You should start seeing new telemetry arrive, showing the number of servers online, the incoming request rate, CPU process amount, etc. You can select some of the sample telemetry in the list to the side to view output data.

    ![The Live Metrics Stream window displays information for the two online servers. Displaying line and point graphs including incoming requests, outgoing requests, and overall health. To the side is a list of Sample Telemetry information. ](media/image70.png 'Live Metrics Stream window')

16. Leave the Live Metrics Stream window open once again, and close the console window for the image upload. Debug the UploadImages project again, then enter **2** and press **ENTER**. This will upload 1,000 new photos.

    ![The Command prompt window displays with image uploading information.](media/image71.png 'Command prompt window')

17. Switch back to the Live Metrics Stream window and observe the activity as the photos are uploaded. You can see the number of servers online, which translate to the number of Function App instances that are running between both Function Apps. You should also notice things such as a steady cadence for the Request Rate monitor, the Request Duration hovering below \~200ms second, and the Incoming Requests roughly matching the Outgoing Requests.

    ![In the Live Metrics Stream window, two servers are online. Under Incoming Requests. the Request Rate heartbeat line graph is selected, as is the Request Duration dot graph. Under Overall Health, the Process CPU heartbeat line graph is also selected, the similarities between this graph and the Request Rate graph under Incoming Requests are highlighted for comparison.](media/image72.png 'Live Metrics Stream window')

18. After this has run for a while, close the image upload console window once again, but leave the Live Metrics Stream window open.

### Task 4: Observe your functions dynamically scaling when resource-constrained

In this task, you will change the Computer Vision API to the Free tier. This will limit the number of requests to the OCR service to 10 per minute. Once changed, run the UploadImages console app to upload 1,000 images again. The resiliency policy programmed into the FindLicensePlateText.MakeOCRRequest method of the ProcessImage function will begin exponentially backing off requests to the Computer Vision API, allowing it to recover and lift the rate limit. This intentional delay will greatly increase the function's response time, thus causing the Consumption plan's dynamic scaling to kick in, allocating several more servers. You will watch all of this happen in real time using the Live Metrics Stream view.

1. Open your Computer Vision API service by opening the **ServerlessArchitecture** resource group, and then selecting the **Cognitive Services** service name.

2. Select **Pricing tier** under Resource Management in the menu. Select the **F0 Free** pricing tier, then choose **Select**.

    > **Note**: If you already have an **F0** free pricing tier instance, you will not be able to create another one.

    ![In the Cognitive Services blade, under Resource Management, the Pricing tier item is selected. In the Choose your pricing tier blade, the F0 Free option is selected.](media/image73.png 'Choose your pricing tier blade')

3. Switch to Visual Studio, debug the **UploadImages** project again, then enter **2** and press **ENTER**. This will upload 1,000 new photos.

    ![The Command prompt window displays image uploading information.](media/image71.png 'Command Prompt window')

4. Switch back to the Live Metrics Stream window and observe the activity as the photos are uploaded. After running for a couple of minutes, you should start to notice a few things. The Request Duration will start to increase over time. As this happens, you should notice more servers being brought online. Each time a server is brought online, you should see a message in the Sample Telemetry stating that it is "Generating 2 job function(s)", followed by a Starting Host message. You should also see messages logged by the resilience policy that the Computer Vision API server is throttling the requests. This is known by the response codes sent back from the service (429). A sample message is "Computer Vision API server is throttling our requests. Automatically delaying for 16000ms".

    > **Note**: If you select a sample telemetry and cannot see its details, drag the resize bar at the bottom of the list up to resize the details pane.

    ![In the Live Metrics Stream window, 11 servers are now online.](media/image74.png 'Live Metrics Stream window')

5. After this has run for some time, close the UploadImages console to stop uploading photos.

6. Navigate back to the **Computer Vision** API and set the pricing tier back to **S1 Standard**.

