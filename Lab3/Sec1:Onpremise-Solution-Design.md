
**Section 1: On-Premises Solution Design**
**Scenario:**
A mid-sized retail company currently runs a traditional on-premises solution consisting of:

Web Application (Monolithic) hosted on physical servers.
Backend database on an SQL server.
File storage using a local file system.
Basic networking handled by company-operated routers and firewalls.
email services for client notification 

For the purpose of designing an onpremise solution, apart from web application framework, backend and storage are key component of the task. Scalability and security are the key components of the onpreise architecture.
![image](https://github.com/user-attachments/assets/472ada04-2a43-4983-a281-6f6661214289)

In the above diagram any core network swithces like netger industrial controllers or cisco controller could be used to bifurcate the traffic. Web application could be hosted on the any of the hosting platform, for storage purpose any high performance tools like Netapp could  be used in this scenario.
Email services should include the spam filtiring mechanism and for database management PostgreSql or sqllite could be used if the database is concise.


