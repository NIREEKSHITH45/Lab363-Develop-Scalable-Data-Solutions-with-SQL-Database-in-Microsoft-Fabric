### Exercise 2: Introduction to Copilot for SQL Database

In this exercise, you will use **Copilot** to assist with T-SQL queries, including **auto-suggestions**, **fixing error**, and **natural language query**, again contributing to Contoso developer efficiency!

#### Task 2.1: Use Copilot in SQL Database

#### Activity: Write SQL queries in the SQL query editor in Microsoft Fabric

1. In the **Query Editor**, paste the query ```SELECT TOP(10) ``` and observe how Copilot suggests code to complete your query.

```
SELECT TOP(10)
```
 >**Note:** Copilot responses may not match what is shown in the screenshot but will provide similar results.

   ![](../media/p3.png)

2. Press the **Tab** key on your keyboard to accept the suggestion or continue typing to ignore it.

   ![](../media/p4.png)

3. Select the query and click on the **Run** icon.

   ![](../media/p5.png)


### Task 2.2: Fixing errors with Quick Actions

1. Paste the following query with a syntax error and click on the **Run** icon.

    ```
    SELECT d.CalendarYear, SUM(f.SalesAmount) AS TotalSalesAmount
    FROM dbo.factinternetsales f
    JOIN dbo.dimdate d ON f.OrderDateKey = d.DateKey
    GROUP BY d.CalYear
    ORDER BY d.CalendarYear;
    ```
   ![](../media/database7.png)

2. Click on **Fix query errors** and observe the updated query along with the comment that clearly states where the issue was in the query. Then, click on **Run** to see the results.

    >**Note:** Copilot responses may not match what is shown in the screenshot but will provide similar results.

    ![](../media/database8.png)

### Task 2.3: Chat Pane : Natural Language to SQL

1. Click on the **Copilot** option.

   ![](../media/database9.png)

2. Click on the **Get started** button.

   ![](../media/database10.png)

3. Paste the following question in the **Copilot** chat box and click on **Send**.

    ```
    What is the most sold dim product?
    ```

    >**Note:** Copilot responses may not match what is shown in the screenshot but will provide similar results.

   ![](../media/database11.png)

4. Click on the **Insert** button.

   ![](../media/database12.png)

5. Select the query that was inserted by Copilot, click on the **Run** icon and check the **Results**.

   ![](../media/database13.png)

6. Paste the following question in the Copilot chat box and click on **Send**.

    > **Note:** Copilot responses may not match what is shown in the screenshot but will provide similar results.

    ```
    Who are the top 5 customers by total sales amount?
    ```

   ![](../media/database14.png)

7. Click on the **Insert** button.

   ![](../media/database15.png)

8. Select the query that was inserted by Copilot, click on the **Run** icon and check the **Results**.

   ![](../media/database16.png)

Congratulations! You have learned how to leverage **Copilot** for SQL Database in Microsoft Fabric to enhance your **query-writing** experience. With these skills, you are now better equipped to write SQL queries faster and troubleshoot errors effectively using Copilot. You are ready to move on to the next exercise: **Data Enrichment and Transformation**
