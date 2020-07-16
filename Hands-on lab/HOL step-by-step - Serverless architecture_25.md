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

