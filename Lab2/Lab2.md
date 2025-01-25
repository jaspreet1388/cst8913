
Scenario: The following application consists of a Web Server written in Flask. A UI front end written in React. A database layer consisting of Postgres.

1.**Describe how this application can be deployed in the cloud using IaaS infrastructure**
IAAS model gives more flexcibility to the customers because servers, storage and networking is managed by the customer itself.
For the purpose of IAAS model we can deploy the web servers, and database on the VMs, for the purpose of storage we can use the azure blob, load balancer can be deployed to handle the heavy traffic flask web application, finally for hosting the frontend we can use azure CDN.
For the purpose of accessing the application user can use his web browser.

2.**Describe how this application can be deployed in the cloud using PaaS infrastructure.**
As far as PAAS model is concerned, we can run the flask web application using the azure app services, azure application gateway can be used for the purose of load balancing and handling the traffic, front end could be hosted using the azure CDN, for the purpose of media files we can use azure blob.


3.**For each case, draw a diagram that represents the target architecture and describe each of the chosen cloud components**
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



   Coming to the PAAS architecture:
   We can make the PAAS architecture for above scenario as :
   ![image](https://github.com/user-attachments/assets/8d577f36-2935-497c-93ce-c86d35ceb0dd)


   
**Steps for the above IAAS plan could be simplied as :**
1. **User’s Device (Browser):**
   The user accesses the application via their browser.

2. **React Frontend:**
   The React frontend is hosted as a static web app using Azure Static Web Apps or via Azure CDN for efficiently delivery of pages.

3. **Azure Front Door / Load Balancer:**
   Azure Front Door or Azure Application Gateway handles global traffic management, routing requests to the nearest or available instances of the app, with automatic load balancing.

4. **Azure App Service (Flask Web Server):**
    The Flask Web Application runs on Azure App Service, a fully managed platform. This removes the need for the customer to manage the operating system, scaling, or load balancing.

5. **Azure Database for PostgreSQL:**
    A managed PostgreSQL service provided by Azure, which takes care of backups, scaling, failover, and maintenance for the customer . But it is easier to manage than running PostgreSQL on a VM.

6. **Azure Blob Storage:**
    Used for storing static content like images and other media files. This service scales automatically and is managed by Azure.


   



