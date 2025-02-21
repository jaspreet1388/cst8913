**Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure**

**Scenario:** A company is currently running a monolithic web application on a Windows Server 2019 virtual machine (VM) hosted in Azure. The company wants to modernize the application by refactoring it into a cloud-native solution that leverages Azure services.

**Task1:** Assess the Existing Architecture
Identifying Monolithic Components of the Application
The legacy monolithic application consists of  components running on a single Windows Server 2019 VM. The key components are:

**Web Layer** (Frontend + Backend in a Single Codebase)

A traditional ASP.NET or .NET Core web application hosted on IIS.
Handles both UI interface and business logic for the interface.
Business logic is coupled with database access.

**Database Layer**
SQL Server running on the same or a separate VM.
SQl queries embedded in the application code itself.

**Background Processing**
Windows Scheduled Tasks or Windows Services for batch jobs, email notifications, data processing, etc.
Runs as part of the monolithic application, making scaling difficult.
Static File Storage & Logging

Static content (images, CSS, JS etc) stored locally on the VM.
Application logs stored on local disk and local servers, making monitoring and troubleshooting difficult.

```mermaid
graph TD;
    
    subgraph Legacy_Monolithic_Architecture
        VM[Windows Server 2019 VM] -->|Hosts| MonolithicApp[Monolithic Web App]
        MonolithicApp -->|Uses| VM_SQL[SQL Server on VM]
        MonolithicApp -->|Runs| BackgroundTasks[Scheduled Tasks & Windows Services]
        MonolithicApp -->|Stores| LocalStorage[Static Files & Logs]
    end
    
    subgraph Modern_Cloud_Native_Architecture
        AppService[Azure App Service] -->|Hosts| Frontend[Frontend]
        AppService -->|Hosts| Backend[Backend API]
        Backend -->|Uses| AzureSQL[Azure SQL Database]
        Backend -->|Auth via| AzureAD[Azure Active Directory]
        Backend -->|Triggers| Functions[Azure Functions]
        Functions -->|Processes| BackgroundJobs[Background Jobs & Scheduled Tasks]
        Backend -->|Stores| BlobStorage[Azure Blob Storage]
        Backend -->|Logs to| Monitor[Azure Monitor & App Insights]
    end
    
    Legacy_Monolithic_Architecture -->|Migration| Modern_Cloud_Native_Architecture
