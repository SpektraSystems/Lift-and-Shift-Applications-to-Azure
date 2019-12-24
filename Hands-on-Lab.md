![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')




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

2. Select the default Web Site and click on Next button.
![The Select Top 1000 rows menu item is highlighted.](images/defau;t.png 'app service')

3. Click on **Copy Code & Open** it will open one browser window.
![The Select Top 1000 rows menu item is highlighted.](images/code.png 'code')


4. Paste the code here and click on next and Enter you Azure credentials from you Lab Details Page.
![The Select Top 1000 rows menu item is highlighted.](images/code2.png 'Select Top 1000')

5. You will see Azure App Service Migration Assistant Signed in page.
![The Select Top 1000 rows menu item is highlighted.](images/signin.png 'Select Top 1000')

6. Now select the subscription and click Use existing Resource Group and select **Lift-and-Shift-######** Enter your unique destination    Site Name.
  ![The Select Top 1000 rows menu item is highlighted.](images/app.png 'Select Top 1000')
  
7. click on create new migration project. It will open new browser window, sign in using your credentials and click on Azure Tools          button and .
![The Select Top 1000 rows menu item is highlighted.](images/addtools.png 'Select Top 1000')

8. Select your resource group **Lift-and-Shift-######** and enter your migrate project name and click on next button.
![The Select Top 1000 rows menu item is highlighted.](images/portal.png 'Select Top 1000')

9. On Select assessment tool blade select the **Azure Migrate: Web App Assessment** and click on next button.
![The Select Top 1000 rows menu item is highlighted.](images/web.png 'Select Top 1000')

10. Select **Azure Migrate: Web App Migration** and click on next button.
![The Select Top 1000 rows menu item is highlighted.](images/migration.png 'Select Top 1000')

11. Click on **Add Tools** button.
![The Select Top 1000 rows menu item is highlighted.](images/migration.png 'Select Top 1000')

12. You should be able to see the migrate project select. After this click on **Add migration tools** and select the migration tool         **Azure Migrate: Web App Migration** and click on add tools.
![The Select Top 1000 rows menu item is highlighted.](images/migrateproject.png 'Select Top 1000')

13. Go back to your Azure App Service Migration Assistant and select the migrate project you just created and click on **Migrate**           button.
![The Select Top 1000 rows menu item is highlighted.](images/migrateapp.png 'Select Top 1000')
14. Now after migration you should be able to see **Got to your website** and click on the **Got to your website**. This will open one       browser window and you will be able to see **IIS** default page.
![The Select Top 1000 rows menu item is highlighted.](images/website.png 'Select Top 1000')

## Exercise 2: Create Azure SQL Database.

**Step 1:**

1. Create SQL server and database from Azure portal.
![The Select Top 1000 rows menu item is highlighted.](images/ads-reviews-select-top-1000.png 'Select Top 1000')

2. Open your RG and click on add button and search for **SQL SERVER** and create **SQL SERVER** and select you RG, enter unique          **Server Name** set location same as your RG and Enter login, Password for the **SQL Server**.
![The Select Top 1000 rows menu item is highlighted.](images/sqlserver.png 'Select Top 1000')

3. Click on networking blade select yes on **Allow Azure services and resources to access this server**. after this click on **Review +    create**.
  ![The Select Top 1000 rows menu item is highlighted.](images/yes'.png 'Select Top 1000')
  
4. After deployment completed open sql server blade and click in new database and create a new database for migration.

5. Enter unique name for database and source select empty and click on **ok**.
 ![The Select Top 1000 rows menu item is highlighted.](images/dbnew.png 'Select Top 1000')

4. Copy the Server name of SQL Server Database in notepad for later use.
![The Select Top 1000 rows menu item is highlighted.](images/sql.png 'Select Top 1000')

**Step 2:**

1. Go to your VM desktop and open **Microsoft Data Migration assistant**.
![The Select Top 1000 rows menu item is highlighted.](images/dms.png 'Select Top 1000')

2. Click on **+** Sign and Select **Migration**, Enter your project name and please ensure that Source Sever type is selected to **SQL Server** and target server is selected to **Azure SQL Database**, Migration Scope is selected to**Schema and data** after selecting all click on Create button.
![The Select Top 1000 rows menu item is highlighted.](images/database.png 'Select Top 1000')

3. On Select source Blade add server name as **labvm**, Authentication type as **SQL Server authentication**, enter user name as **demouser** Password **Password.1!!**. make sure you select **encrypt connection** and **trust server certificate** and click on connect.
![The Select Top 1000 rows menu item is highlighted.](images/db.png 'Select Top 1000')

4. You should be able to see one **partsunlimiteddb** database. select that and click on next button.
![The Select Top 1000 rows menu item is highlighted.](images/dbnew.png 'Select Top 1000')

5. Now on **select target** blade enter your SQL Server URL, select authentication type as **SQL Server authentication** and enter your credentials you enter while creating the SQL Server is previous step. Select **Trust server certificate** and click on connect.
![The Select Top 1000 rows menu item is highlighted.](images/target.png 'Select Top 1000')

6. After clicking on connect button select the database you created with SQL Server in previous step and click on **Next** button.


7. In the next blade click **Generate SQL Script**.
![The Select Top 1000 rows menu item is highlighted.](images/sqlscript.png 'Select Top 1000')
8. After complete the Generate SQL Scripp click on **Deploy schema**, after **Schema migration completed** click on **MIgrate Data** button.
![The Select Top 1000 rows menu item is highlighted.](images/schema.png 'Select Top 1000')

9. Please ensure all 14 table are selected and click on **Start data migration**.
![The Select Top 1000 rows menu item is highlighted.](images/startdata.png 'Select Top 1000')

## Exercise 3: Publish Application in Azure App serice Using visual studio 2017 community.

1. Go to you Start menu and open **Visual Studio 2017**.

2. Click on Sign in button and login using your azure credentials from your lab details page.
![The Select Top 1000 rows menu item is highlighted.](images/vs.png 'Select Top 1000')

2. click on **Open Project/ Solution** and navigate to **C:\PartsUnlimited-master** and double click on **PartsUnlimited.sln**.
![The Select Top 1000 rows menu item is highlighted.](images/prject.png 'Select Top 1000')

3. Go to solution explorer and right click on **PartsUnlimitedWebsite** and select publish.
![The Select Top 1000 rows menu item is highlighted.](images/publish.png 'Select Top 1000')

4. On **PartsunlimitedWebsite** page please make sure to click on **New Profile** and select **Select Existing** and click next button and sign in using your azure credentials from Lab details page.
![The Select Top 1000 rows menu item is highlighted.](images/nwqprofile.png 'Select Top 1000')

5. After Sign in select you subscription if you have multiple subscriptions, make sure you select right subscrtiption, Select same Resource Group where you create App Service and SQL Server in previously exercises, and expand your RG and select the **app service** you created and click **ok** button.
![The Select Top 1000 rows menu item is highlighted.](images/selectapp.png 'Select Top 1000')

7. You should see **Web App was published successfully http://partsunlimited.azurewebsites.net/** in your visual studio 2017 output windows. you can copy your website URL and can check if it is working fine or not.
![The Select Top 1000 rows menu item is highlighted.](images/published.png 'Select Top 1000')

## Exercise 4: Connect your SQL Server database to your website.

1. Go to your SQL Server database connection strings blade and copy your **ADO.NET** key and change your SQL Server user name and password, and save it in a notepad for later use.
![The Select Top 1000 rows menu item is highlighted.](images/string.png 'Select Top 1000')

2. got to your **App Service** search for **App Service editor** and click on **Go** button.
![The Select Top 1000 rows menu item is highlighted.](images/appservice.png 'Select Top 1000')

3. After clicking on go button, it will open a new tab in your browser and search for **config.json** and open it.
![The Select Top 1000 rows menu item is highlighted.](images/config1.png 'Select Top 1000')

4. Copy the below code and paste it in **config.json** file and it will save automattically. Please remember to change your password in connection string otherwise it will not connect with your SQL server.
![The Select Top 1000 rows menu item is highlighted.](images/sonnection.png 'Select Top 1000')

``` "ConnectionStrings": {
    "DefaultConnectionString": "Server=tcp:partsunlimited23.database.windows.net,1433;Initial Catalog=partunliitedDb;Persist Security Info=False;User ID=demouser;Password=Password.1!!;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;" }
```
  
5. You can test that by creating a new user in your application and try to order something from the website.

  
  ## After the hands-on lab

Duration: 10 mins

In this exercise, you will delete any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab to ensure your account does not continue to be charged for lab resources.

### Task 1: Delete the resource group

1. Using the [Azure portal](https://portal.azure.com), navigate to the Resource group you used throughout this hands-on lab by selecting Resource groups in the left menu.
2. Search for the name of your resource group, and select it from the list.
3. Select Delete in the command bar, and confirm the deletion by re-typing the Resource group name, and selecting Delete.

You should follow all steps provided _after_ attending the Hands-on lab.
 




 
