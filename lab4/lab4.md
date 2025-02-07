
**Lab 4: Multi-Region Deployment with Load Balancing**
***************************************************

**High-Level Design (HLD) Document**
**********************************

**1. Solution Diagram**
********************



**2. Description of the target architecture**
******************************************
Key features:
*************
**2.1. Multi-region deployment:**
*****************************
    - The application is deployed in two regions(Region A and Region B) for high availability
    - Each region has its own load balancer to distribute traffic within the region
    
**2.2. Redundancy:** 
***************
    - Each VM(WebServer VM and SQLVM) is replicated in a secondary region to ensure failover capabilities
    
**2.3. Load balancing:**
*********************
    - a "Global Load Balancer" is used to direct traffic to the healthiest web server in the primary region. It the traffic fails,traffic is directed to the second region.
**2.4. Database replication:**
**************************
    - The SQL database will use geo-replication with automatic failover to maintain data integrity.
**2.5. Failover mechanism:**
*************************
    - If the primary region fails, application traffic and database requests will be directed to the secondary region

**3. Migration steps**
*******************

**3.1: Replicating virtural machines accross the two regions:**
****************************************************************
    - User Azure Site Recovery to replicate WebServerVM and SQLVM 
    - Deploy VMs (WebServerVM and SQLVM) in the primary region and secondary region 
    - Ensure VM configurations match original specifications

**3.2: Configure load balancers**
************************************
    - Deploy a Global Load Balancer to distribute traffic between regions.
    - Set up Regional Load Balancers in each region to handle local traffic.
    - Implement health checks to route traffic only to active servers.

**3.3: Implement database replication and failover**
*****************************************************
    - Configure SQLVM replication using geo-replication through Azure SQL Failover Groups.
    - Ensure asynchronous replication to minimize data loss.
    - Test automatic failover by simulating a region failure.
