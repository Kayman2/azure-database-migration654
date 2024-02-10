**Azure Database Migration Project 654**

**Description \#\#**

**What i learnt \#\#**

**Tasks accomplished in each milestone \#\#**

**Milestone 1: Set up the Environment**

1.  Set up this GitHub Repo to document the development of this project.
2.  Set up an Azure account with login credentials that will be use throughout this project.

    **![](media/50a76a49f3eca32e0ae840dabb8b1993.JPG)**

**Milestone 2: Set up the Production Environment**

This milestone focuses on the creation and configuration of a robust production environment, pivotal for the project’s success. Key steps include:

1\. Virtual Machine Creation

-   Successfully deployed a Windows-based Virtual Machine (VM), named \`productionVM\`, tailored for production-level tasks.
-   Integrated \`productionVM\` into the \`dbmigrationRG\` resource group, ensuring organized resource management and streamlined access.

2\. Network Configuration

-   Implemented advanced network settings, prioritizing secure communication channels to safeguard data integrity.
-   Activated the Remote Desktop Protocol (RDP) to facilitate secure, remote administrative access.

3\. Remote Connection Establishment

-   Established a secure remote connection to \`productionVM\` via Microsoft Remote Desktop, utilizing the RDP protocol for reliable and secure remote management.

    ![](media/f631c8419dffad35457032f6c33a34a4.JPG)

    ![](media/410e1a7958883e54167c03240bc18929.JPG)

4\. SQL Server and SSMS Installation

-   Installed SQL Server on \`productionVM\`, setting the foundation for a robust database server capable of handling intensive data operations.
-   Equipped the environment with SQL Server Management Studio (SSMS) to enable efficient and effective database management and maintenance.

    ![](media/5dc2ce672379b27424c4d60f4d011bac.jpg)

    ![](media/8bbd9b26c148f6dd0b3c0a726399d587.jpg)

5\. AdventureWorks Database Restoration

-   Procured and restored the AdventureWorks 2022 database from a .bak file, laying the groundwork for realistic data management scenarios.
-   The AdventureWorks database simulates the operations of a fictional manufacturing company, providing a practical model for testing and development within the production environment.
-   

    ![](media/9a3a67bd8f654b830e1702d27bda54ce.jpg)

**Milestone 3: Migrate to Azure SQL Database**

1.  SQL Database Setup
    -   Created a SQL Database named azAdventureworks
    -   Placed the database in the resource group named dbmigrationRG.
    -   Assigned the database to a server named adm-production-svr.
2.  Configure SQL Firewall Rules
    -   Added a firewall rule for SQL Server with the VM's IP address as the start and end IP addresses.
    -   Ensured that the VM can securely connect to the SQL Server.
3.  Azure Data Studio installation
    -   Set up Azure Data Studio on the production Windows VM. Azure Data Studio is installed when SSMS is installed.
    -   Established a connection to the existing on-premise database using Azure Data Studio.
    -   Established a connection to the newly created Azure SQL Database.
4.  Install SQL Server Schema Compare Extension
    -   Installed the SQL Server Schema Compare extension within Azure Data Studio.
    -   Utilised this extension to compare and migrate the schema from the on-premise database to the Azure SQL Database.
5.  Install Azure SQL Migration Extension
    -   Installed the Azure SQL Migration extension within Azure Data Studio.
    -   Utilised this extension to facilitate the migration of data from the on-premise database to the Azure SQL Database.
    -   Installed the Microsoft Integration Runtime
6.  Database Migration Validation
    -   Confirmed the success of the migration process through a comprehensive validation.
    -   Thoroughly inspected the migrated database, including data, schema, and configurations, to ensure a successful migration that adheres to principles of data integrity.

![](media/5f898bdd566740c01ee5b696b158e5ef.JPG)

**Milestone 4:**: **Data Backup and Restore**

Milestone 4 marks a critical juncture in our Azure project, where we shift our focus towards safeguarding our valuable data assets. This phase is dedicated to implementing a comprehensive and secure backup mechanism for our on-premise database and ensuring that our development environment is equipped with robust data recovery capabilities.

1\. Backup of the On-Premise Database

-   Successfully generated a comprehensive backup of the production database hosted on the productionVM. This step ensures a reliable fallback for the production environment.

2\. Creation of Blob Storage

-   Established and configured a Blob storage account, along with a dedicated container. This serves as a secure, cloud-based repository for storing our database backups, reinforcing data safety.

3\. Uploading Backup to Blob Storage

-   Executed the upload of the previously created database backup file into the Blob storage container. This additional measure provides an extra layer of data protection.

![](media/a76e5f2bfed5096c1a24c924b201726f.jpg)

4\. Database Restoration in the Development Environment

-   Initialized a new virtual machine, named developmentVM, tailored for testing, development, and experimental tasks.
-   Installed SQL Server and SSMS (SQL Server Management Studio) to set up the essential database infrastructure on this VM.
-   Downloaded the database backup file from the Blob storage, ensuring data consistency.
-   Successfully restored the database on developmentVM, effectively replicating the production environment for development purposes.

5\. Automating Backups for the Development Database

-   Established credentials for accessing the Azure storage account via SSMS.
-   Developed a maintenance plan within SSMS to automate regular, weekly backups of the development database directly to Azure Blob Storage. This automation not only secures our ongoing work but also simplifies the recovery process for the development environment, if necessary.

**Milestone 5:**: **Disaster Recovery Simulation**

This phase of the project provides testing of disaster recovery procedures, including backups restoration, failover processes, and data integrity checks.

The developmentVM closely mirrors my productionVM environment. This includes having the same SQL Server version, database structure, and ideally, a similar volume of data.

The data loss simulations performed in the developmentVM environment were truncating a [Humanresources].[jobCandidate] table and Updating [Production].[ProductCostHistory] table columns with the wrong amount.

Task 1: Mimic Data Loss in Production Environment

![A screenshot of a computer Description automatically generated](media/9c967c7d8ef5cb7e931c31ac25afb84c.jpg)

After Truncate 13 records were deleted.

After Restore:

![A screenshot of a computer Description automatically generated](media/6721fc91bef0fca7521960176df64b79.jpg)

Before [Production].[ProductCostHistory] UPDATE:

![A screenshot of a computer Description automatically generated](media/5f891c101bc5333213978b30d869d05f.jpg)

After ProductCostHistory UPDATE:

![A screenshot of a computer Description automatically generated](media/6ab3b6e8bf6894fa4011214ee15946e6.JPG)

After Database Restore ProductCostHistory UPDATE:

![A screenshot of a computer Description automatically generated](media/2df8e7399763c81fb3d0cb29da4586a7.JPG)
