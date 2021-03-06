
# An end-to-end process for lifting and shifting your applications to Azure


**Overview**

Application overview
Parts Unlimited is a sample eCommerce website site built on .Net Core 2.0. The site includes a front-end ordering page, a mobile experience, an order database, and a variety of other common eCommerce features. The application features a modern HTML5 responsive layout using bootstrap for mobile, tablet, and PC. It supports multiple authentication options including Azure Active Directory, Google, and Facebook. At the same time, it leverages a variety of Azure App Service features including testing in production, staging slots, and environment variables for feature flags (to turn on/off recommendations). The site works with Visual Studio 2017 and includes a docker file and sample publishing profile to deploy as a docker container.

 

The application that will be migrated is hosted on a Windows server 2016 running Internet Information Services (IIS), while the database is hosted on a computer running SQL Server 2017.

 

You can find a repo with the site code here: http://aka.ms/pulabs


**Phases in the migration journey**
Migrating to the cloud involves moving your web apps and databases, and there are different tools and techniques for each. However, the typical migration journey consists of four phases: pre migration, migration, post migration, and optimization.

**Discovery**
 
The first step in the migration journey is to “discover” the servers hosting the application and databases to determine if there are the dependencies that would require migrating these entities to Azure together.

 

You can use Azure Migrate to assesses on-premises workloads for migration to Azure. The service discovers and assesses the migration suitability of on-premises virtual servers and servers running SQL Servers. Azure Migrate sizes things based on performance and provides cost estimations for running on-premises computers in Azure.

 

You can also use the Microsoft Assessment and Planning Toolkit (the "MAP Toolkit") to assess your current IT infrastructure for a variety of technology migration projects. This Solution Accelerator provides a powerful inventory, assessment, and reporting tool to simplify the migration planning process.


## Exercise 1: Migrating default web site using App Service Migration Assistant.

1. Run the **App Service Migration Assistant** from you Start Menu.

2. Select the default Web Site and click on Next button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/defau;t.png 'app service')

3. Please make sure on **Assessment Report** blade it should be on success note, and click on next button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/dw.png 'app service')
 
4. Click on **Copy Code & Open** it will open one browser window.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/code.png 'code')


5. Paste the code here and click on next and Enter you Azure credentials from you Lab Details Page.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/code2.png 'Select Top 1000')

6. You will see Azure App Service Migration Assistant Signed in page.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/signin.png 'Select Top 1000')

7. Now select the subscription and click Use existing Resource Group and select **Lift-and-Shift-######** Enter your unique destination    Site Name.
   ![The Select Top 1000 rows menu item is highlighted.](images/app.png 'Select Top 1000')
  
8. click on create new migration project. It will open new browser window, sign in using your credentials and click on Azure Tools          button and .
   ![The Select Top 1000 rows menu item is highlighted.](images/addtools.png 'Select Top 1000')

9. Select your resource group **Lift-and-Shift-######** and enter your migrate project name and click on next button.
   ![The Select Top 1000 rows menu item is highlighted.](images/portal.png 'Select Top 1000')

10. On Select assessment tool blade select the **Azure Migrate: Web App Assessment** and click on next button.
   ![The Select Top 1000 rows menu item is highlighted.](images/web.png 'Select Top 1000')

11. Select **Azure Migrate: Web App Migration** and click on next button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/migration.png 'Select Top 1000')

12. Click on **Add Tools** button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/tools.png 'Select Top 1000')

13. You should be able to see the migrate project selected.
   ![The Select Top 1000 rows menu item is highlighted.](images/migrateproject.png 'migrate')

14. Go back to your Azure App Service Migration Assistant and select the migrate project you just created and click on **Migrate**           button.

    **Note:** You might have to go back to the beginning of the Azure Migrate: Web App Migration and step through again to see  azure        migrate project name appear in the drop down list.
   ![The Select Top 1000 rows menu item is highlighted.](images/migrateapp.png 'project')

15. Now after migration you should be able to see **Got to your website** and click on the **Got to your website**. This will open one       browser window and you will be able to see **IIS** default page.
   ![The Select Top 1000 rows menu item is highlighted.](images/website.png 'Select Top 1000')

## Exercise 2: Create Azure SQL Database.

**Step 1:**

1. Create SQL Database from Azure portal.

2. Go to your azure portal, Open **Lift-and-Shift-#####** RG and click on add button and search for **SQL DATABASE** and click on create button. </br>
   ![The Select Top 1000 rows menu item is highlighted.](images/sqldatabase.png 'database')

3. On **SQL Database** blade, select your RG and enter unique name for SQL Database and click on **create new** option. </br>
   ![The Select Top 1000 rows menu item is highlighted.](images/server.png 'Select Top 1000')
  
   **A**. On SQL Server creation blade enter unique details, Name and credentials for SQL Server and click ok. </br>
     ![The Select Top 1000 rows menu item is highlighted.](images/server1.png 'Select Top 1000')
   
   **B**. Go to **Networking** on SQL database blade and select connectivity method to **Public Endpoint** and select yes on **Allow azure services and resources to access this server** and **Add current cliend IP address**, then Click on **Review and Create** button and then create button.</br>
     ![The Select Top 1000 rows menu item is highlighted.](images/network.png 'Select Top 1000')


4. After the deployment completed go to SQL Database blade overview and Copy the Server name and save it in notepad for later use.
   ![The Select Top 1000 rows menu item is highlighted.](images/sm.png 'Select Top 1000')

 **Step 2:**

1. Go to your VM desktop and open **Microsoft Data Migration assistant**.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/dms.png 'Select Top 1000')

2. Click on **+** Sign and Select **Migration**, Enter your project name and please ensure that Source Sever type is selected to **SQL      Server** and target server is selected to **Azure SQL Database**, Migration Scope is selected to**Schema and data** after selecting      all   click on Create button.</br>

   ![The Select Top 1000 rows menu item is highlighted.](images/database.png 'Select Top 1000')

3. On Select source Blade add server name as **labvm**, Authentication type as **SQL Server authentication**, enter user name as            **demouser** Password **Password.1!!**. make sure you select **encrypt connection** and **trust server certificate** and click on        connect.</br>

   ![The Select Top 1000 rows menu item is highlighted.](images/labvm.png 'Select Top 1000')

4. You should be able to see one **partsunlimiteddb** database. select that and click on next button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/ld.png 'Select Top 1000')

5. Now on **select target** blade enter your SQL Server URL, select authentication type as **SQL Server authentication** and enter your credentials you enter while creating the SQL Server is previous step. Select **Trust server certificate** and click on connect.
   ![The Select Top 1000 rows menu item is highlighted.](images/target.png 'Select Top 1000')

6. After clicking on connect button select the database you created with SQL Server in previous step and click on **Next** button.


7. In the next blade click **Generate SQL Script**.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/sqlscript.png 'Select Top 1000')
 
8. After complete the Generate SQL Scripp click on **Deploy schema**, after **Schema deployment is completed** click on **MIgrate Data** button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/schema.png 'Select Top 1000')

9. Please ensure all 14 table are selected and click on **Start data migration**.
   ![The Select Top 1000 rows menu item is highlighted.](images/startdata.png 'Select Top 1000')

## Exercise 3: Publish Application in Azure App serice Using visual studio 2017 community.

1. Go to you Start menu and open **Visual Studio 2017**.

2. Click on Sign in button and login using your azure credentials from your lab details page.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/vs.png 'Select Top 1000')

3. click on **Open Project/ Solution** and navigate to **C:\PartsUnlimited-master** and double click on **PartsUnlimited.sln**.
   ![The Select Top 1000 rows menu item is highlighted.](images/project.png 'Select Top 1000')

4. Go to solution explorer and right click on **PartsUnlimitedWebsite** and select publish.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/publish.png 'Select Top 1000')

5. On **PartsunlimitedWebsite** page please make sure to click on **New Profile** and select **Select Existing** and click next button      and sign in using your azure credentials from Lab details page.</br></br>
   ![The Select Top 1000 rows menu item is highlighted.](images/nwqprofile.png 'Select Top 1000')

6. After Sign in select you subscription if you have multiple subscriptions, make sure you select right subscrtiption, Select same Resource Group where you create App Service and SQL Server in previously exercises, and expand your RG and select the **app service** you created and click **ok** button.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/selectapp.png 'Select Top 1000')

7. You should see **Web App was published successfully http://partsunlimited.azurewebsites.net/** in your visual studio 2017 output windows. you can copy your website URL and can check if it is working fine or not.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/published.png 'Select Top 1000')

## Exercise 4: Connect your SQL Server database to your website.

1. Go to your SQL Server database connection strings blade and copy your **ADO.NET** key and change your SQL Server user name and password, and save it in a notepad for later use.</br>
   ![The Select Top 1000 rows menu item is highlighted.](images/string.png 'Select Top 1000')

2. got to your **App Service** search for **App Service editor** and click on **Go** button.</br></br>
   ![The Select Top 1000 rows menu item is highlighted.](images/appservice.png 'Select Top 1000')

3. After clicking on go button, it will open a new tab in your browser and search for **config.json** and open it.
   ![The Select Top 1000 rows menu item is highlighted.](images/config1.png 'Select Top 1000')

4. Copy the below code and paste it in **config.json** file and it will save automattically. Please make sure to change your password in connection string otherwise it will not connect with your SQL Database.
   ![The Select Top 1000 rows menu item is highlighted.](images/sonnection.png 'Select Top 1000')

``` "ConnectionStrings": {
    "DefaultConnectionString": "Server=tcp:partsunlimited23.database.windows.net,1433;Initial Catalog=partunliitedDb;Persist Security Info=False;User ID=demouser;Password=Password.1!!;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;" }
```
  
5. You can test that by creating a new user in your application and try to order something from the website.

  

## Lab Ended


 
