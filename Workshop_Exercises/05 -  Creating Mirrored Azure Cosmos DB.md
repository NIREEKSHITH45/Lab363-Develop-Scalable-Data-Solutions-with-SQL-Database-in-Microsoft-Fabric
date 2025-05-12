## Exercise 5 : Creating Mirrored Azure Cosmos DB (Optional)

Mirroring in Fabric provides an easy experience to avoid complex ETL (Extract Transform Load) and integrate your existing Azure Cosmos Database estate with the rest of your data in Microsoft Fabric.


1. Select **<inject key= "WorkspaceName" enableCopy="true"/>** workspace from the left navigation pane.

   ![Task-1.1_1.png](../media/p14.png)

2. Click on the **New item** icon, search for **Cosmos** in the search bar then select **Mirrored Azure Cosmos DB...**.

   ![Task-1.1_1.png](../media/p15.png)

3. When prompted to **Choose a database connection to get started**, look for **New sources** and select **Azure Cosmos DB v2**.

   ![Task-1.1_3.png.png](../media/p16.png)

    >**Note:** To fill in the details for required fields, we need to fetch the data from the Cosmosdb resource deployed in the Azure Portal.

10. In the **Cosmos DB Endpoint** field, paste: <inject key="CosmosEndpoint" enableCopy="true"/>

11. Select **Account key** for Authentication kind, paste the following in the **Account Key** field: <inject key="CosmosEndpoint" enableCopy="true"/>  and click on the **Connect** button.

    ![Task-1.1_4.png.png](../media/p19.png)

12. Click on the dropdown for Database, then select **Telemetry** and click on **Connect** button.

    ![Task-1.1_5.png.png](../media/p20.png)

13. Click on the **Connect** button.

    ![Task-1.1_6.png.png](../media/p21.png)

14. In the **Name** field, paste ```Telemetry```,click on the **Create mirrored database** button.

    ![Task-1.1_7.png.png](../media/p22.png)

<!-- 15. Click on **Monitor replication** button to track the replication status.

![Task-1.1_8.png.png](media/Task-1.1_8.png) -->

15. Wait until the **Rows replicated** statistics are displayed. If not, **Refresh** the **Monitor replication** tab as shown in the following screen. Now, Azure Cosmos DB has been successfully mirrored.

    ![Task-1.1_9.png.png](../media/p23.png)

<!-- 17. Close the **Monitor replication** window. -->

<!-- ![Task-1.1_9.png.png](media/Task-1.1_9.png) -->

16. Select **SQL analytics endpoint** from top right **dropdown** box.

    ![Task-1.1_10.png](../media/p24.png)

17. Click on the mirrored table **Inventory_Data** to see data preview.

    ![Task-1.1_11.png](../media/p25.png)

18. Click on **New SQL query** 

    ![cosmosdb](../media/p26.png)

19. Copy the following **SQL query** in query editor and click on the **Run** button.

This query retrieves the average available inventory per product. Since the mirrored database resides in OneLake, we can create a semantic model that combines data from both the SQL database in Fabric and the mirrored database to enable advanced analytics.

```
    SELECT ProductId, AVG(AvailableInventory) AS AvgInventory
    FROM [Telemetry].[Telemetry].[Inventory_Data]
    GROUP BY ProductId;

```
  ![cosmosdb](../media/p27.png)
