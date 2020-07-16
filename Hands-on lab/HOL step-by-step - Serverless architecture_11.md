## Exercise 7: Configure continuous deployment for your Function App

**Duration**: 40 minutes

In this exercise, configure your Function App that contains the ProcessImage function for continuous deployment. You will first set up a GitHub source code repository, then set that as the deployment source for the Function App.

### Help references

|                                           |                                                                                    |
| ----------------------------------------- | :--------------------------------------------------------------------------------: |
| **Description**                           |                                     **Links**                                      |
| Creating a new GitHub repository          |           <https://help.github.com/articles/creating-a-new-repository/>            |
| Continuous deployment for Azure Functions | <https://docs.microsoft.com/azure/azure-functions/functions-continuous-deployment> |

### Task 1: Add git repository to your Visual Studio solution and deploy to GitHub

1. Open the **TollBooth** project in Visual Studio.

2. Right-click the **TollBooth** solution in Solution Explorer, then select **Add Solution to Source Control**.

    ![In Solution Explorer, TollBooth solution is selected. From its right-click context menu, the Add Solution to Source Control item is selected.](media/vs-add-to-source-control.png 'Solution Explorer')

3. Select **View** in Visual Studio's top menu, then select **Team Explorer**.

    ![The View menu is expanded with the Team Explorer menu item selected.](media/vs-view-team-explorer.png 'Visual Studio')

4. Select **Sync** in the Team Explorer.

    ![The Sync link is highlighted.](media/vs-sync.png "Changes")

5. Choose the **Publish to GitHub** button, then sign in to your GitHub account when prompted.

    ![The Publish to GitHub button is highlighted in the Publish to GitHub section.](media/vs-publish-to-github.png "Push")

6. Type in a name for the new GitHub repository, then select **Publish**. This will create the new GitHub repository, add it as a remote to your local git repo, then publish your new commit.

    ![In the Push form, the repository name is highlighted along with the Publish button.](media/vs-publish-to-new-github.png "Push")

7. Refresh your GitHub repository page in your browser. You should see that the project files have been added. Navigate to the **TollBooth** folder of your repo. Notice that the local.settings.json file has not been uploaded. That's because the .gitignore file of the TollBooth project explicitly excludes that file from the repository, making sure you don't accidentally share your application secrets.

    ![On the GitHub Repository webpage for serverless-architecture-lab, on the Code tab, the project files are displayed.](media/github-repo-page.png 'GitHub Repository page')

### Task 2: Configure your Function App to use your GitHub repository for continuous deployment

1. Open the Azure Function App you created whose name ends with **FunctionApp**, or the name you specified for the Function App containing the ProcessImage function.

2. Select **Deployment Center** underneath Deployment in the left-hand menu.

    ![The Platform features tab is displayed, under Code Deployment, Container settings is selected.](media/functionapp-menu-deployment-center-link.png 'TollBoothFunctionApp blade')

3. Select **GitHub** in the **Deployment Center** blade. Enter your GitHub credentials if prompted. Select **Continue**.

    ![The GitHub tile is selected from a list of repository options.](media/functionapp-dc-github.png 'Deployment Center blade')

4. Select **App Service build service**, then select **Continue**.

    ![Under the Build Provider step, App Service build service tile is selected.](media/functionapp-dc-build-provider.png 'Deployment Center blade')

5. **Choose your organization**.

6. Choose your new repository under **Choose project**. Make sure the **master branch** is selected.

    ![Fields in the Deployment option blade set to the following settings: Choose your organization, obscured; Choose repository, serverless-architecture-lab; Choose branch, master.](media/functionapp-dc-configure.png 'Deployment Center blade')

7. Select **Continue**.

8. On the Summary page, select **Finish**.

9. After continuous deployment is configured, all file changes in your deployment source are copied to the function app and a full site deployment is triggered. The site is redeployed when files in the source are updated.

    ![The Deployment Center tab is shown with a pending build.](media/functionapp-dc.png 'Function App Deployment Center')

### Task 3: Finish your ExportLicensePlates function code and push changes to GitHub to trigger deployment

1. Navigate to the **TollBooth** project using the Solution Explorer of Visual Studio.

2. From the Visual Studio **View** menu, select **Task List**.

    ![Task List is selected from the Visual Studio View menu.](media/image37.png 'Visual Studio View menu')

3. There you will see a list of TODO tasks, where each task represents one line of code that needs to be completed.

4. Open **DatabaseMethods.cs**.

5. The following code represents the completed task in DatabaseMethods.cs:

    ```csharp
        // TODO 5: Retrieve a List of LicensePlateDataDocument objects from the collectionLink where the exported value is false.
        licensePlates = _client.CreateDocumentQuery<LicensePlateDataDocument>(collectionLink,
                new FeedOptions() { EnableCrossPartitionQuery=true,MaxItemCount = 100 })
            .Where(l => l.exported == false)
            .ToList();
        // TODO 6: Remove the line below.
    ```

6. Make sure that you deleted the following line under TODO 6: `licensePlates = new List<LicensePlateDataDocument>();`.

7. Save your changes then open **FileMethods.cs**.

8. The following code represents the completed task in DatabaseMethods.cs:

    ```csharp
    // TODO 7: Asyncronously upload the blob from the memory stream.
    await blob.UploadFromStreamAsync(stream);
    ```

9. Save your changes.

10. Right-click the **TollBooth** project in Solution Explorer, then select **Commit...** under the **Source Control** menu item.

    ![In Solution Explorer, the TollBooth project is selected. From its right-click context menu, Source Control and Commit... are selected.](media/image101.png 'Solution Explorer')

11. Enter a commit message, then select **Commit All**.

    ![In the Team Explorer - Changes window, "Finished the ExportLicensePlates function" displays in the message box, and the Commit All button is selected.](media/image110.png 'Team Explorer - Changes window')

12. After committing, select the **Sync** link. This will allow us to add the remote GitHub repository.

    ![Under Team Explorer - Changes, in the informational message Commit 02886e85 created locally. Sync to share your changes with the server. The Sync link is selected.](media/image103.png 'Team Explorer - Changes window')

13. Select the **Sync** button on the **Synchronization** step.

    ![Under Synchronization in the Team Explorer - Synchronization window, the Sync link is selected.](media/image111.png 'Team Explorer - Synchronization window')

    Afterward, you should see a message stating that the incoming and outgoing commits were successfully synchronized.

14. Go back to Deployment Center for your Function App in the portal. You should see an entry for the deployment kicked off by this last commit. Check the timestamp on the message to verify that you are looking at the latest one. **Make sure the deployment completes before continuing**.

    ![The latest deployment is displayed in the Deployment Center.](media/functionapp-dc-latest.png 'Deployment Center')

