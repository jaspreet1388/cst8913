**Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure**

**Scenario:** A company is currently running a monolithic web application on a Windows Server 2019 virtual machine (VM) hosted in Azure. The company wants to modernize the application by refactoring it into a cloud-native solution that leverages Azure services.

**Task1:** **Assessing the Existing Architecture**
The legacy monolithic application consists of  components running on a single Windows Server 2019 VM. The key components of legacy architecture are:

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

**Static content** (images, CSS, JS etc) stored locally on the VM.
Application logs stored on local disk and local servers, making monitoring and troubleshooting difficult.



**Task2: Refactoring Strategy for Migration**
The purpose of this  refactoring is to transition the monolithic web application running on an Azure Virtual Machine (VM) into a  scalable, resilient, and cost-efficient cloud-native architecture using Azure services.

1. Break Down the Monolithic Application into Microservices
The existing monolithic system consists of a UI, API, background tasks, database, and storage, all tightly coupled in a single deployment. To modernize it, we will decompose it into modular microservices.

Microservices Breakdown:
Monolithic Component	Microservice	Technology / Service
Frontend UI & API together	Frontend UI	Azure App Service (Static Web Apps)
Backend API (Business Logic & Data Access Layer)	API Service	Azure App Service (API Backend)
SQL Server (Database)	Database Service	Azure SQL Database
Background Jobs (Scheduled Tasks & Windows Services)	Background Processing	Azure Functions (Event-driven)
Static File Storage (On VM)	Storage Service	Azure Blob Storage
Logging (Stored Locally in Text Files)	Monitoring & Logging	Azure Monitor & Application Insights
Each microservice will run independently and communicate using REST APIs, Azure Service Bus, or Event Grid.

2. Select Azure Services for Migration
Each component of the monolithic app will be replaced with Azure-native services to enhance scalability, performance, and cost efficiency.

Service Mapping:
Functionality	Current Monolithic Implementation	Refactored Azure Service	Key Benefits
Frontend Hosting	Hosted inside the VM	Azure App Service (Static Web Apps)	Managed hosting, auto-scaling
Backend Hosting	ASP.NET API running in the VM	Azure App Service (API Backend)	Decoupled backend, auto-scaling
Database	SQL Server on VM	Azure SQL Database	Fully managed, high availability, backup support
Background Jobs	Windows Services / Task Scheduler	Azure Functions (Timer/Event Triggered)	Serverless execution, cost-effective
File Storage	Stored on VM disk	Azure Blob Storage	Scalable, cost-effective, high durability
Authentication	Custom user authentication in the app	Azure Active Directory (Azure AD) & Managed Identity	Secure authentication with SSO
Logging & Monitoring	Logs stored in local files	Azure Monitor & Application Insights	Centralized, real-time monitoring
3. Authentication and Authorization Strategy Using Azure AD
A robust authentication and authorization strategy ensures secure access to microservices.

🔐 Frontend Authentication
Users authenticate using Azure AD B2C (for customer access) or Azure AD Enterprise SSO (for internal users).
Supports OAuth 2.0, OpenID Connect, SAML, and Multi-Factor Authentication (MFA).
🔒 API Authorization
Azure AD tokens are required for accessing backend APIs securely.
Role-Based Access Control (RBAC) will be applied to control access based on user roles.
🔑 Secure Service Communication
Azure Managed Identity will be used to enable secure, passwordless authentication between services (e.g., API → Azure SQL, API → Azure Blob Storage).
Ensures no hardcoded credentials in the application.
Next Steps for Implementation:
✅ Step 1: Migrate the frontend to Azure App Service (Static Web Apps)
✅ Step 2: Deploy the API separately to Azure App Service (API Backend)
✅ Step 3: Migrate SQL Server database to Azure SQL Database
✅ Step 4: Convert background jobs to Azure Functions
✅ Step 5: Move static content to Azure Blob Storage
✅ Step 6: Implement authentication using Azure AD
✅ Step 7: Set up monitoring with Azure Monitor & Application Insights

This approach ensures a scalable, resilient, and cost-optimized solution.


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
    
  
