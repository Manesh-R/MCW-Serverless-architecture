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

## Exercise 8: Rerun the workflow and verify data export

**Duration**: 10 minutes

With the latest code changes in place, run your Logic App and verify that the files are successfully exported.

