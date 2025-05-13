## Exercise 5 : Creating Mirrored Azure Cosmos DB (Optional)

Mirroring in Fabric provides an easy experience to avoid complex ETL (Extract Transform Load) and integrate your existing Azure Cosmos Database estate with the rest of your data in Microsoft Fabric.


1. Select **<inject key= "WorkspaceName" enableCopy="true"/>** workspace from the left navigation pane.

   ![Task-1.1_1.png](../media/p14.png)

2. Click on the **New item** icon, search for **Cosmos** in the search bar then select **Mirrored Azure Cosmos DB...**.

   ![Task-1.1_1.png](../media/p15.png)

3. When prompted to **Choose a database connection to get started**, look for **New sources** and select **Azure Cosmos DB v2**.

   ![Task-1.1_3.png.png](../media/p16.png)

    >**Note:** To fill in the details for required fields, we need to fetch the data from the Cosmosdb resource deployed in the Azure Portal.

4. In the **Cosmos DB Endpoint** field, paste: **<inject key="CosmosEndpoint" enableCopy="true"/>**

5. Select **Account key** for Authentication kind, paste the following in the **Account Key** field: **<inject key="CosmosPrimaryKey" enableCopy="true"/>** and click on the **Connect** button.

    ![Task-1.1_4.png.png](../media/p19.png)

6. Click on the dropdown for Database, then select **Telemetry** and click on **Connect** button.
    >**Note**: If you do not see the database immediately, please wait a few seconds for it to finish loading.

    ![Task-1.1_5.png.png](../media/p20.png)

7. Click on the **Connect** button.

    ![Task-1.1_6.png.png](../media/p21.png)

8. In the **Name** field, paste ```Telemetry```,click on the **Create mirrored database** button.
    >**Note:** If the name isn't unique, you'll see an error asking for a different name. **Provide a unique name**.

    >**Note**: If the following error: `Continuous backup must be enabled before you mirror an Azure Cosmos DB database to Fabric. Please enable 7-day or 30-day continuous backup on your Azure Cosmos DB account from Azure portal` appears go to the next step and enable continuous backup. (else skip to **step 14**)

    ![Task-1.1_7.png.png](../media/p22.png)

9. Open the following Cosmos DB Backup & Restore page in a new browser window on the VM.**<inject key="CosmosBackupRestoreUrl" enableCopy="true"/>**.

10. Click on the Backup policy mode **(change)**.

    ![Task-1.1_7.png.png](../media/backuppolicy.png)

11. In the Backup policy mode click on **Continuous (7 days)** radio button, and click on **Save** button.

    ![Task-1.1_7.png.png](../media/continuous7.png)

12. Click on the bell icon and Wait for the Backup policy to get updated.

    ![Task-1.1_7.png.png](../media/notify.png)

13. Go back to the Fabric and click on the **Create mirrored database** button.

    >**Note:** If the name isn't unique, you'll see an error asking for a different name. **Provide a unique name**.

    ![Task-1.1_7.png.png](../media/mirror.png)

14. Wait until the **Rows replicated** statistics are displayed. If not, **Refresh** the **Monitor replication** tab as shown in the following screen. Now, Azure Cosmos DB has been successfully mirrored.

    >**Note**: It may take approximately 3–4 minutes for the Cosmos DB mirrored data to appear.
    >**Note**: Ignore the "Running with warnings" status if it appears. Ensure that Rows replicated shows 247.

    ![Task-1.1_9.png.png](../media/p23.png)

15. Select **SQL analytics endpoint** from top right **dropdown** box.

    ![Task-1.1_10.png](../media/p24.png)

16. Click on the mirrored table **Inventory_Data** to see data preview.

    ![Task-1.1_11.png](../media/p25.png)

17. Click on **New SQL query** 

    ![cosmosdb](../media/p26.png)

18. Copy the following **SQL query** in query editor and click on the **Run** button.

This query retrieves the average available inventory per product. Since the mirrored database resides in OneLake, we can create a semantic model that combines data from both the SQL database in Fabric and the mirrored database to enable advanced analytics.

```
    SELECT ProductId, AVG(AvailableInventory) AS AvgInventory
    FROM [Telemetry].[Telemetry].[Inventory_Data]
    GROUP BY ProductId;

```
  ![cosmosdb](../media/p27.png)
