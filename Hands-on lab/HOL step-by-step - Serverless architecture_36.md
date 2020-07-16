### Task 2: View the exported CSV file

1. Open your ServerlessArchitecture resource group in the Azure portal, then select your **Storage account** you had provisioned to store uploaded photos and exported CSV files.

2. In the Overview pane of your storage account, select **Containers**.

    ![In the Overview blade, Containers is selected.](media/storage-containers.png 'Services section')

3. Select the **export** container.

    ![Export is selected under Name.](media/image117.png 'Export option')

4. You should see at least one recently uploaded CSV file. Select the filename to view its properties.

    ![In the Export blade, under Name, a .csv file is selected.](media/blob-export.png 'Export blade')

5. Select **Download** in the blob properties window.

    ![In the Blob properties blade, the Download button is selected.](media/blob-download.png 'Blob properties blade')

    The CSV file should look similar to the following:

    ![A CSV file displays with the following columns: FileName, LicensePlateText, TimeStamp, and LicensePlateFound.](media/csv.png 'CSV file')

6. The ExportLicensePlates function updates all of the records it exported by setting the exported value to true. This makes sure that only new records since the last export are included in the next one. Verify this by re-executing the script in Azure Cosmos DB that counts the number of documents in the Processed collection where exported is false. It should return 0 unless you've subsequently uploaded new photos.

## After the hands-on lab

**Duration**: 10 minutes

In this exercise, attendees will deprovision any Azure resources that were created in support of the lab.

