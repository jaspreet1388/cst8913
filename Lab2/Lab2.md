
Scenario: The following application consists of a Web Server written in Flask. A UI front end written in React. A database layer consisting of Postgres.

**Describe how this application can be deployed in the cloud using IaaS infrastructure**
IAAS model gives more flexcibility to the customers because servers, storage and networking is managed by the customer itself.

So, for a IAAS model the above scenario could be described as :
**IaaS Architecture Diagram:**
![image](https://github.com/user-attachments/assets/3d0bd365-4fcf-4e87-a7c2-c3c232a84605)


**Steps for the above IAAS plan could be simplied as :**
1. **User’s Device** ( Web Browser):
    The user accesses the application through their browser.

2. **React Frontend:**
    The React frontend is hosted on Azure CDN or Azure Static Web Hosting for file delivery.

3. **Azure Load Balancer:**
    Used to balance traffic for the between multiple Azure VMs running the Flask Web Application.

4. **Azure Virtual Machines (VMs):**
    **Flask Web Server**: Flask application is deployed on Azure VMs. We have to configure, patch, and scale these VMs manually.
    **PostgreSQL Database on VM**: PostgreSQL database is also running on an Azure VM, and database management including backups and scaling should be handled by the customer.
    **Azure Blob Storage**: Used for storing  files like images, media and other supporting documents . This is a scalable and secure service for web pages and other supporting data.



