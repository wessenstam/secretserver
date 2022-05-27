.. _m5:

----------------
Secret Templates
----------------

Introduction
------------

This fifth module will cover:

1. Discuss built-in Secret Templates
2. Create a Secret Template

Built-In Secret Templates
-------------------------

When creating new secrets, a template is used to determine what information the secret should hold, password complexity requirements, launcher configuration and many other secret settings

| Secret Server comes with a range of built-in secret templates. These templates can be viewed and edited by navigating to Admin>Secret Template and selecting the relevant template:

.. figure:: images/lab-A-001.png

.. note::
    Demo: At this point your trainer will demonstrate and explain the available configuration options within a Secret Template

Lab 13 - Creating a Secret Template for Active Directory Service Accounts
*************************************************************************

In this exercise we will be creating a Secret template that can be used for Active Directory service accounts. This template will be the same as the regular AD template, but we will remove the launcher. Because service accounts are used to provide a security context to an application, users should not be able to use the account interactively with a launcher.

| As, in this case the Secret Template we are creating is very similar to the existing Active Directory account template we will create a copy rather than starting from scratch.

#. Navigate to the **Administration > Actions > Secret Templates** page
#. Click **Active Directory Account**
#. Click **Duplicate**

   .. figure:: images/lab-A-002.png

#. In the name new secret dialogue type: **Active Directory Service Account**

   .. figure:: images/lab-A-003.png

#. Click **Save**
#. In the new template select the **Mapping** tab

   .. figure:: images/lab-A-004.png

#. Click **Remove** next to the **Launcher Name**
#. Click **OK** in the warning box
 
We will now use this template to recreate the secret used Active Directory integration.

#. Navigate to the **Secrets** and click the **double arrows**
#. Select the **TSS Service Accounts** folder
#. Click the **+** Icon and select **New Secret**

   .. figure:: images/lab-A-005.png

#. The new secret dialogue appears, select the newly created **Active Directory Service Account** template
#. Add the following detail into the secret:

   - **Secret Name:** AD Sync
   - **Domain:** thylab.local
   - **Username:** svc_sync
   - **Password:** *Provided by Trainer*
   - **Notes:** type used for active directory integration and synchronization in Secret Server

#. Click **Create Secret**

  .. note::
     The new secret we have created does not have an RDP launcher so users cannot interactively use the credential from Secret Server. 

We can now delete the first AD Sync secret from the Ss_admin personal folder

#. Open **Personal Folders > ss_admin**
#. Check the box next to the **AD Sync** secret 
#. In the messagebar that appears at the bottom, click **More Options** and select Deactivate

   .. figure:: images/lab-A-006.png

#. In the *Confirm Bulk Deactivate* windows click **Confirm Action**
#. After the task completed, click **Close**

   .. figure:: images/lab-A-007.png

#. No secrets will be left in this folder
#. Now navigate to **Administration (double arrows) > Users, Roles, Access > Directory Services**
#. Select the **thylab.com** domain 
#. Click **Edit** in the *Active Directory* section
#. Next to **Synchronization Secret**, click **Clear** to remove the secret we previously deleted (*AD Sync (Deleted)*)
#. Click **No Secret Selected** and select the new **AD Sync** secret in the *TSS Service Accounts* folder
#. Click **Validate & Save** to complete


.. raw:: html

    <hr><CENTER>
    <H2 style="color:#00FF59">This concludes this module</font>
    </CENTER>