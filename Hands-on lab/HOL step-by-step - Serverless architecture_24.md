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

