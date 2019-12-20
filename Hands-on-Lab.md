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

1. Run the App Service Migration Assistant from you desktop.

2. Select the default Web Site and click on Next button.

3. Click on **Copy Code & Open** it will open one browser window.

4. Paste the code here and click on next and Enter you Azure credentials from you Lab Details Page.

5. You will see Azure App Service Migration Assistant Signed in page.

6. Now select the subscription and click Use existing Resource Group and select **Lift-and-Shift-######** Enter your unique destination    Site Name.
  
  
7. click on create new migration project. It will open new browser window, sign in using your credentials and click on Azure Tools          button.

8. Select your resource group **Lift-and-Shift-######** and enter your migrate project name and click on next button.

9. On Select assessment tool blade select the **Azure Migrate: Web App Assessment** and click on next button.

10. Select **Azure Migrate: Web App Migration** and click on next button.

11. Click on **Add Tools** button.

12. You should be able to see the migrate project select. After this click on **Add migration tools** and select the migration tool         **Azure Migrate: Web App Migration** and click on add tools.

13. Go back to your Azure App Service Migration Assistant and select the migrate project you just created and click on **Migrate**           button.

14. Now after migration you should be able to see **Got to your website** and click on the **Got to your website**. This will open one       browser window and you will be able to see **IIS** default page.


## Exercise 2: Create Azure SQL Database.

**Step 1:**

1. Create SQL server and database from Azure portal.

2. Select your RG and click on add button and search for **SQL SERVER** and create **SQL SERVER** and select you RG, enter unique          **Server Name** set location same as your RG and Enter login, Password for the **SQL Server**.


3. Click on networking blade select yes on **Allow Azure services and resources to access this server**. after this click on **Review +    create**.
  
4. You will see you deployment is completed after some time, copy the URL string of SQL Server in notebook for later use.


**Step 2:**

1. Go to your VM desktop and open **Microsoft Data Migration assistant**.

2. Click on **+** Sign and Select **Migration**, Enter your project name and please ensure that Source Sever type is selected to **SQL Server** and target server is selected to **Azure SQL Database**, Migration Scope is selected to**Schema and data** after selecting all click on Create button.

3.On Select source Blade add server name as **lift**, Authentication type as **SQL Server authentication**, enter user name as **demouser** Password **Password.1!!**. make sure you select **encrypt connection** and **trust server certificate** and click on connect.

4. You should be able to see one **partsunlimiteddb** database. select that and click on next button.

5. Now on **select target** blade enter your SQL Server URL, select authentication type as **SQL Server authentication** and enter your credentials you enter while creating the SQL Server is previous step. Select **Trust server certificate** and click on connect.

6. After clicking on connect button select the database you created with SQL Server in previous step and click on **Next** button.

7. In the next blade click **Generate SQL Scrippt**.

8. After complete the Generate SQL Scripp click on **Deploy schema**, after **Schema migration completed** click on **MIgrate Data** button.

9. Please ensure all 14 table are selected and click on **Start data migration**.


## Exercise 3: Publish Application in Azure App serice Using visual studio 2017 community.

1. Go to you desktop and open **Visual Studio 2017**.

2. click on **Open Project/ Solution** and navigate to **C:\PartsUnlimited-master** and double click on **PartsUnlimited.sln**.

3. Go to solution explorer and righnt click on **PartsUnlimitedWebsite** and select publish.

4. On **PartsunlimitedWebsite** page make sure to click on **New Profile** and select **Select Existing** and click next button and sign in using your azure credentials from Lab details page.

5. After Sign in select you subscription if you have multiple subscriptions, Select same Resource Group where you create App Service and SQL Server in previously exercises, and expand your RG and select the **app service** you created and click **ok** button.



 
