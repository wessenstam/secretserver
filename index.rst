.. title:: ThycoticCentrify - Secure Server Handson Training

.. toctree::
   :maxdepth: 2
   :caption: Module 1
   :name: _m1
   :hidden:

   module1/module1

.. toctree::
  :maxdepth: 2
  :caption: Module 2 - Basic Configuration
  :name: _m2
  :hidden:

  module2/module2

.. toctree::
  :maxdepth: 2
  :caption: Module 3 - Users, Groups and Roles
  :name: _m3
  :hidden:

  module3/module3

.. toctree::
  :maxdepth: 2
  :caption: Module 4 - Folder and Policies
  :name: _m4
  :hidden:

  module4/module4

.. toctree::
  :maxdepth: 2
  :caption: Module 5 - Secret Templates
  :name: _m5
  :hidden:

  module5/module5

.. toctree::
  :maxdepth: 2
  :caption: Module 6 - Launchers
  :name: _m6
  :hidden:

  module6/module6

.. toctree::
  :maxdepth: 2
  :caption: Module 7 - Remote Password Changers
  :name: _m7
  :hidden:

  module7/module7

.. toctree::
  :maxdepth: 2
  :caption: Module 8 - Secret Workflows
  :name: _m8
  :hidden:

  module8/module8

.. toctree::
  :maxdepth: 2
  :caption: Module 9 - Discovery
  :name: _m9
  :hidden:

  module9/module9

.. toctree::
  :maxdepth: 2
  :caption: Module 10 - Auditing and Security
  :name: _m10
  :hidden:

  module10/module10
  
.. _getting_started:

----------------
Before You Begin
----------------

Purpose
-------

This training and lab guide is designed to accompany a Thycotic trainer lead course. During your training course the trainer will regularly reference this guide as well as demonstrating lab exercises within a shared desktop environment and discussing common use cases and real-world scenarios.

Your training pack
------------------

Before you start this training course, ensure you have received lab details from your Thycotic trainer.
The Secret Server lab consists of the following machines:

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Machine Name
     - Internal Lab Name
     - Internal IP
     - Description
   * - DC1
     - DC1
     - 172.31.32.10
     - Domain Controller - contains all AD configuration used within the lab
   * - SSPM
     - SSPM
     - 172.31.32.114
     - This machine will be used to install and host Secret Server
   * - Client
     - Client01
     - 172.31.32.118
     - Windows server, used to test a range of Secret Server functionalities during the training course
   * - CENTOS
     - 
     - 172.31.32.121
     - CentOS machine, used to test a range fo Secret Server functionalities during the training course


You will need to initiate a remote desktop connection to the **PUBLIC IP** address of the Win machine. This IP address is dynamic and will change whenever the lab environment is restarted. The Win server machine serves as a jump box from which you can then RDP to the other windows machines by hostname. Lab Exercise 1 explains the process of identifying the IP address of your lab jump box and connecting to it.

To log into the Virtual Machines with administrative rights, the below information is providing you the credentials for Windows and Linux.

**Windows Domain Admin Account**

| Username: **thylab\\adm-training**
| Password: **Provided by trainer**

**Centos SSH Account**

| Username: **thycotic**
| Password: **Provided by trainer**


Introduction
------------

Your trainer will provide a slide-based introduction to Secret Server, the slide deck used will be shared. 

.. raw:: html

    <hr><CENTER>
    <H2 style="color:#80BB01">This concludes this module</font>
    </CENTER>