### Task 1: Use the Azure Cosmos DB Data Explorer

1. Open your Azure Cosmos DB account by opening the **ServerlessArchitecture** resource group, and then selecting the **Azure Cosmos DB account** name.

2. Select **Data Explorer** from the menu.

    ![In the Data Explorer blade, Data Explorer is selected from the left menu.](media/data-explorer-link.png 'Tollbooth - Data Explorer blade')

3. Expand the **Processed** collection, then select **Items**. This will list each of the JSON documents added to the collection.

4. Select one of the documents to view its contents. The first four properties are ones that were added by your functions. The remaining properties are standard and are assigned by Cosmos DB.

    ![In the tree-view beneath the LicensePlates Cosmos DB, the Processed collection is expanded with the Items item selected. On the Items tab, a document is selected, and to the side, the JSON data associated with the document is displayed. The first four properties of the document (fileName, licencePlateText, timeStamp, and exported) are displayed along with the standard Cosmos DB properties.](media/data-explorer-processed.png 'Tollbooth - Data Explorer blade')

5. Expand the **NeedsManualReview** collection, then select **Items**.

6. Select one of the documents to view its contents. Notice that the filename is provided, as well as a property named "resolved". While this is out of scope for this lab, those properties can be used together to provide a manual process for viewing the photo and entering the license plate.

    ![In the tree-view beneath the LicensePlates Cosmos DB, the NeedsManualReview collection is expanded, and the Items item is selected. On the Items tab, a document is selected, and to the side, the JSON properties of the document are displayed. The first four properties of the document (fileName, licencePlateText, timeStamp, and resolved) are shown along with the standard Cosmos DB properties.](media/data-explorer-needsreview.png 'Tollbooth - Data Explorer blade')

7. Select the ellipses (...) next to the **Processed** collection and select **New SQL Query**.

    ![In the tree-view beneath the LicencePlates Cosmos DB, the Processed collection is selected. From its right-click context menu, New SQL Query is selected.](media/data-explorer-new-sql-query.png 'Tollbooth - Data Explorer blade')

8. Modify the SQL query to count the number of processed documents that have not been exported:

    ```sql
    SELECT VALUE COUNT(1) FROM c WHERE c.exported = false
    ```

9. Execute the query and observe the results. In our case, we have 669 processed documents that need to be exported.

    ![In the Query window, the previously defined SQL query displays. Under Results, the number 669 is highlighted.](media/cosmos-query-results.png 'Query 1 tab')

## Exercise 6: Create the data export workflow

**Duration**: 30 minutes

In this exercise, you create a new Logic App for your data export workflow. This Logic App will execute periodically and call your ExportLicensePlates function, then conditionally send an email if there were no records to export.

