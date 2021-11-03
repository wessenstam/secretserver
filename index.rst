.. title:: ThycoticCentrify - Secure Server Handson Training

.. toctree::
   :maxdepth: 2
   :caption: Era Lab Setup
   :name: _dbs
   :hidden:

..   labsetup/labsetup

.. toctree::
   :maxdepth: 2
   :caption: Era with MSSQL
   :name: _dbs
   :hidden:

   configure_mssql/configure_mssql
   admin_mssqldb/admin_mssqldb
   deploy_mssql_era/deploy_mssql_era
   patch_sql/patch_sql

.. toctree::
  :maxdepth: 2
  :caption: Optional Labs
  :name: _optional_labs
  :hidden:

  webtier/webtier
  prismops_appmonitoring_lab/prismops_appmonitoring_lab
  era_rest_api/era_rest_api


.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

  appendix/glossary
..  tools_vms/windows_tools_vm
..  tools_vms/linux_tools_vm


.. _getting_started:

---------------
Getting Started
---------------

Welcome to the Databases: Era with MSSQL bootcamp. This bootcamp is meant to provide you with first-hand experience to illustrate why Nutanix is an ideal platform for Database workloads.

Historically, it has been a challenge to virtualize SQL Server because of the high cost of traditional virtualization stacks and the impact that a SAN-based architecture can have on performance. Businesses and their IT departments have constantly fought to balance cost, operational simplicity, and consistent predictable performance.

The Nutanix Enterprise Cloud removes many of these challenges and makes virtualizing a business-critical application such as SQL Server much easier. The Acropolis Distributed Storage Fabric (DSF) is a software-defined solution that provides all the features one typically expects in an enterprise SAN, without a SAN’s physical limitations and bottlenecks. SQL Server particularly benefits from the following DSF features:

- Localized I/O and the use of flash for index and key database files to lower operation latency.
- A highly distributed approach that can handle both random and sequential workloads.
- The ability to add new nodes and scale the infrastructure without system downtime or performance impact.
- Nutanix data protection and disaster recovery workflows that simplify backup operations and business continuity processes.

In addition to solving common infrastructure problems for hosting business critical applications, Nutanix also seeks to address many of the key pain points associated with managing databases.

.. figure:: images/4.png

Based on a 2018 IDC study of 500 North American companies with more than 1,000 employees, they estimate:

- 77% of the organizations have more than 200 database instances in production
- 82% have more than 10 copies of each database
- 45%-60% the total storage capacity is dedicated to accommodating copy data
- 32% of database clones require daily refreshes for analytics or dev/test
- Copy data will cost IT organizations $55.63 billion in 2020

Maintaining the status quo leads to inefficient usage of both storage and worse, of administrator time. Meet Nutanix Era.

.. figure:: images/5.png