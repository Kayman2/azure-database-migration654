	
# **Azure Database Migration Project 654**

**Description ##**
Overview
This project is dedicated to designing and deploying a robust cloud-based database system utilizing Microsoft Azure, demonstrating practical proficiency and innovative strategies in cloud engineering.  The project unfolds through a series of structured phases, each one addressing key components and processes essential to the architecture and implementation of a Azure cloud database solution. 

**What i learnt ##**

**Tasks accomplished in each milestone M1-M4##**

**Milestone 1: Set up the Environment**

1. Set up this GitHub Repo to document the development of this project.
		             GitHub used to track changes to code and save them online in a   
		             GitHub repo.   
		             https://github.com/Kayman2/azure-database-migration654

1. Set up an Azure account with login credentials that will be use throughout this project.

![](RackMultipart20240126-1-r4g7g3_html_11a37cf5049e166b.jpg)

**Milestone 2: Set up the Production Environment**

This milestone focuses on the creation and configuration of a robust production environment, pivotal for the project's success. Key steps include:

1. Virtual Machine Creation

- Successfully deployed a Windows-based Virtual Machine (VM), named `productionVM`, tailored for production-level tasks.
- Integrated `productionVM` into the `dbmigrationRG` resource group, ensuring organized resource management and streamlined access.

2. Network Configuration

- Implemented advanced network settings, prioritizing secure communication channels to safeguard data integrity.
- Activated the Remote Desktop Protocol (RDP) to facilitate secure, remote administrative access.

3. Remote Connection Establishment

- Established a secure remote connection to `productionVM` via Microsoft Remote Desktop, utilizing the RDP protocol for reliable and secure remote management.

![](RackMultipart20240126-1-r4g7g3_html_e80d0171ee4a9a4b.jpg)

![](RackMultipart20240126-1-r4g7g3_html_6a1ae5a8151c2ea9.jpg)

4. SQL Server and SSMS Installation

- Installed SQL Server on `productionVM`, setting the foundation for a robust database server capable of handling intensive data operations.
- Equipped the environment with SQL Server Management Studio (SSMS) to enable efficient and effective database management and maintenance.

  - ![](RackMultipart20240126-1-r4g7g3_html_59a06884a6c5e0a1.png)

![](RackMultipart20240126-1-r4g7g3_html_fe360f1cbeb544cc.png)

5. AdventureWorks Database Restoration

- Procured and restored the AdventureWorks 2022 database from a .bak file, laying the groundwork for realistic data management scenarios.
- The AdventureWorks database simulates the operations of a fictional manufacturing company, providing a practical model for testing and development within the production environment.

![](RackMultipart20240126-1-r4g7g3_html_bc5d90f291c3a084.png)

**Milestone 3: Migrate to Azure SQL Database**

1. SQL Database Setup
  - Created a SQL Database named azAdventureworks
  - Placed the database in the resource group named dbmigrationRG.
  - Assigned the database to a server named adm-production-svr.
2. Configure SQL Firewall Rules
  - Added a firewall rule for SQL Server with the VM's IP address as the start and end IP addresses.
  - Ensured that the VM can securely connect to the SQL Server.
3. Azure Data Studio installation
  - Set up Azure Data Studio on the production Windows VM. Azure Data Studio is installed when SSMS is installed.
  - Established a connection to the existing on-premise database using Azure Data Studio.
  - Established a connection to the newly created Azure SQL Database.
4. Install SQL Server Schema Compare Extension
  - Installed the SQL Server Schema Compare extension within Azure Data Studio.
  - Utilised this extension to compare and migrate the schema from the on-premise database to the Azure SQL Database.
5. Install Azure SQL Migration Extension
  - Installed the Azure SQL Migration extension within Azure Data Studio.
  - Utilised this extension to facilitate the migration of data from the on-premise database to the Azure SQL Database.
  - Installed the Microsoft Integration Runtime
6. Database Migration Validation
  - Confirmed the success of the migration process through a comprehensive validation.
  - Thoroughly inspected the migrated database, including data, schema, and configurations, to ensure a successful migration that adheres to principles of data integrity.

![](RackMultipart20240126-1-r4g7g3_html_ac955d84eee9efec.jpg)

**Milestone 4:** : **Data Backup and Restore**

Milestone 4 marks a critical juncture in our Azure project, where we shift our focus towards safeguarding our valuable data assets. This phase is dedicated to implementing a comprehensive and secure backup mechanism for our on-premise database and ensuring that our development environment is equipped with robust data recovery capabilities.

1. Backup of the On-Premise Database

- Successfully generated a comprehensive backup of the production database hosted on the productionVM. This step ensures a reliable fallback for the production environment.

2. Creation of Blob Storage

- Established and configured a Blob storage account, along with a dedicated container. This serves as a secure, cloud-based repository for storing our database backups, reinforcing data safety.

3. Uploading Backup to Blob Storage

- Executed the upload of the previously created database backup file into the Blob storage container. This additional measure provides an extra layer of data protection.

![](RackMultipart20240126-1-r4g7g3_html_2e83c696f498e78f.jpg)

4. Database Restoration in the Development Environment

- Initialized a new virtual machine, named developmentVM, tailored for testing, development, and experimental tasks.
- Installed SQL Server and SSMS (SQL Server Management Studio) to set up the essential database infrastructure on this VM.
- Downloaded the database backup file from the Blob storage, ensuring data consistency.
- Successfully restored the database on developmentVM, effectively replicating the production environment for development purposes.

5. Automating Backups for the Development Database

- Established credentials for accessing the Azure storage account via SSMS.
- Developed a maintenance plan within SSMS to automate regular, weekly backups of the development database directly to Azure Blob Storage. This automation not only secures our ongoing work but also simplifies the recovery process for the development environment, if necessary.