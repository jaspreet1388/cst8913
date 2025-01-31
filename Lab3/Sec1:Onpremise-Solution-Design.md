
**Section 1: On-Premises Solution Design**
**Scenario:**
A mid-sized retail company currently runs a traditional on-premises solution consisting of:

Web Application (Monolithic) hosted on physical servers.
Backend database on an SQL server.
File storage using a local file system.
Basic networking handled by company-operated routers and firewalls.
email services for client notification 

For the purpose of designing an onpremise solution, apart from web application framework, backend and storage are key component of the task. Scalability and security are the key components of the onpreise architecture.

┌───────────────────────┐  
│        Internet       │  
└───────────────────────┘  
           │  
           ▼  
┌───────────────────────┐  
│  Firewall Cluster     │  
│                       │  
└───────────────────────┘  
           │  
           ├───────────────────────────────┐  
           ▼                               │  
┌───────────────────────┐        ┌───────────────────────┐ (Optional)  
│  Core Net Switches    │        │         DMZ           │  
│                       │        | (Public-facing apps)  │  
└───────────────────────┘        └───────────────────────┘  
           │  
           ├───────────────────────────────────────────────────┐  
           ▼                                                   ▼  
┌───────────────────────┐                          ┌───────────────────────────┐  
│  Web Application Tier │                          │      Database Tier         │  
│ ├── Load Balancer     │                          │ ├── Primary SQL Server     │  
│                       │                          │   (sqllite/PostgreSql)     │                                                   |_______________________│                          | ___________________________ |  
                                                                                                             
                                                                    │                 
           │                                                   ▲  
           ▼                                                   │  
┌───────────────────────┐                          ┌───────────────────────────┐  
│    Storage Tier       │                          │     Email Services        │  
│ ├── SAN/NAS           │                          │ ├── Mail Server Cluster   │  
│ │   (NetApp)          │                          │ │   (Postfix/Exchange HA) │  
│ └── Object Storage    │                          │ └── Spam  Filter        │  
│     (MinIO S3)        │                          |___________________________|
└───────────────────────┘                          
           │  
           ▼  
┌───────────────────────────┐  
│ Management & Monitoring   │  
│ ├── Hypervisor Hosts      │  
│ │   (VMware/Hyper-V)      │  
│ ├── Monitoring Tools      │  
│                           │  
└───────────────────────────┘  
           │  
           ▼  
┌───────────────────────┐  
│ SD-WAN Router         │  
│                       │  
└───────────────────────┘  
           │  
           ▼  
┌───────────────────────┐  
│ IDPS                  │     
└───────────────────────┘  
