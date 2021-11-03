.. _m1:

------------------------------------
Installing Secret Server
------------------------------------

Introduction
------------

This first module will cover:

1. What are the Secret Server components?
2. What are the pre-requirements (minimum and recommended)?
3. What ports does Secret Server use?
4. Lab exercises
5. Managing the Secret Server encryption key

Secret Server components
************************

- Front end ASP.NET web Application
- Back end SQL database

Pre-Requisites
**************
 
**Minimum Requirements - Basic Deployments**

.. list-table::
    :widths: 50 50
    :header-rows: 1

    * - Web Server
      - Database Server
    * - 2 CPU Cores
      - 2 CPU Cores
    * - 4 GB RAM
      - 4 GB RAM
    * - 25 GB Disk Space
      - 50 GB Disk Space
    * - Windows Server 2008 R2 SP1 or newer
      - Windows Server 2008 R2 SP1 or newer
    * - IIS 7 or newer
      - SQL Server 2012 or newer
    * - .NET 4.5.1. or newer
      - 

.. note::
    SQL Express is supported but not recommended for production environments

**Recommended Requirements - Basic Deployments**

.. list-table::
    :widths: 50 50
    :header-rows: 1

    * - Web Server
      - Database Server
    * - 4 CPU Cores
      - 4 CPU Cores
    * - 16 GB RAM
      - 16 GB RAM
    * - 25 GB Disk Space
      - 100+ GB Disk Space
    * - Windows Server 2008 R2 SP1 or newer
      - Windows Server 2008 R2 SP1 or newer
    * - IIS 7 or newer
      - SQL Server 2012 or newer
    * - .NET 4.6.1. or newer
      - 

.. warning::
    For advanced deployments where discovery, session recording or increased numbers of distributed engines are being used, please see feature specific knowledge base guides for detailed requirements.

Ports used by Secret Server
***************************
The table below identifies ports and/or port ranges that may be required by Secret Server

.. list-table:: Ports and/or port ranges used
    :widths: 40 30 30
    :header-rows: 1

    * - Process
      - Type of traffic
      - Port number/range
    * - Active Directory
      - LDAPS
      - 636
    * -
      - LDAP
      - 389
    * -
      - Kerberos
      - 88
    * -
      - NTLM
      - 445 
    * - Discovery
      - RPC Dynamic Port Range*
      - 49152 - 65535
    * - 
      - Microsoft DS
      - 445
    * - 
      - Epmap
      - 135
    * - 
      - SSH
      - 22
    * - Remote Password Changing
      - RPC Dynamic Port Range*
      - 49152 - 65535
    * - 
      - SSH
      - 22
    * - 
      - Telnet
      - 23
    * - 
      - MS SQL
      - 1433
    * - 
      - NTLM
      - 445
    * - 
      - LDAP
      - 389
    * - 
      - LDAPS
      - 636
    * - 
      - Sybase
      - 5000
    * - 
      - Oracle
      - 1521
    * - 
      - Kerberos
      - 88
    * - Ports Incoming to Webserver
      - HTTP
      - 80
    * - 
      - HTTPS
      - 443
    * - Ports Incoming to Database Server
      - SQL Connection TCP and UDP
      - 1433
    * - Email 
      - SMTP
      - 25
    * - RADIUS Server
      - RADIUS
      - 1812

* The RPC Dynamic Port ranges are a range of ports utilized by Microsoft’s Remote Procedure Call (RPC) functionality. This port range varies by operating system. For Windows Server 2008 or greater, this port range is 49152 to 65535 and this entire port range must be open for RPC technology to work. The RPC range is needed to perform Remote Password Changing since Secret Server will need to connect to the computer using DCOM protocol. To see your ipv4 dynamic range on a given machine, type netsh int ipv4 show dynamicport tcp in the commandline. To specify a specific port on your environment that Secret Server will communicate to, you can also `enable WMI ports on Windows client machines <https://thycotic.force.com/support/s/article/Enabling-WMI-ports-on-Windows-client-machines>`_.
    

Lab Exercise 1 – Connecting to the lab environment
**************************************************

In this exercise will access the Thycotic training lab environment.

#. Navigate to the URL of the training lab environment provided by the Thycotic training team.
#. Click the power on instances button, the virtual machines within the lab environment will now be powered on. They should be available in one to two minutes
#. Select and copy in the IP address of the win machine as in the image below:

.. note::
    this IP address is dynamic and will change every time the lab environment is stopped and restarted.
      
    
      