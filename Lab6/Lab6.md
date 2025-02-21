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

