![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
**An end-to-end process for lifting and shifting your applications to Azure**
 <\div>


**overview**

Application overview
Parts Unlimited is a sample eCommerce website site built on .Net Core 2.0. The site includes a front-end ordering page, a mobile experience, an order database, and a variety of other common eCommerce features. The application features a modern HTML5 responsive layout using bootstrap for mobile, tablet, and PC. It supports multiple authentication options including Azure Active Directory, Google, and Facebook. At the same time, it leverages a variety of Azure App Service features including testing in production, staging slots, and environment variables for feature flags (to turn on/off recommendations). The site works with Visual Studio 2017 and includes a docker file and sample publishing profile to deploy as a docker container.

 

The application that will be migrated is hosted on a Windows server 2012 running Internet Information Services (IIS), while the database is hosted on a computer running SQL Server 2017.

 

You can find a repo with the site code here: http://aka.ms/pulabs


**Phases in the migration journey**
Migrating to the cloud involves moving your web apps and databases, and there are different tools and techniques for each. However, the typical migration journey consists of four phases: pre migration, migration, post migration, and optimization.

**Discovery**
 
The first step in the migration journey is to “discover” the servers hosting the application and databases to determine if there are the dependencies that would require migrating these entities to Azure together.

 

You can use Azure Migrate to assesses on-premises workloads for migration to Azure. The service discovers and assesses the migration suitability of on-premises virtual servers and servers running SQL Servers. Azure Migrate sizes things based on performance and provides cost estimations for running on-premises computers in Azure.

 

You can also use the Microsoft Assessment and Planning Toolkit (the "MAP Toolkit") to assess your current IT infrastructure for a variety of technology migration projects. This Solution Accelerator provides a powerful inventory, assessment, and reporting tool to simplify the migration planning process.

Exercise 1
 
