**An end-to-end process for lifting and shifting your applications to Azure**


Overview 

Application overview
Parts Unlimited is a sample eCommerce website site built on .Net Core 2.0. The site includes a front-end ordering page, a mobile experience, an order database, and a variety of other common eCommerce features. The application features a modern HTML5 responsive layout using bootstrap for mobile, tablet, and PC. It supports multiple authentication options including Azure Active Directory, Google, and Facebook. At the same time, it leverages a variety of Azure App Service features including testing in production, staging slots, and environment variables for feature flags (to turn on/off recommendations). The site works with Visual Studio 2017 and includes a docker file and sample publishing profile to deploy as a docker container.

 

The application that will be migrated is hosted on a Windows server 2012 running Internet Information Services (IIS), while the database is hosted on a computer running SQL Server 2017.

 

You can find a repo with the site code here: http://aka.ms/pulabs
