.. _m3:

-----------------------
Users, Groups and Roles
-----------------------

Introduction
------------

This first module will cover:

1. Creating Secret Server Users
2. Configure Active Directory Synchronisation
3. Creating a Local group
4. Roles

In this module we will be covering how users are created and managed within Secret Server and how role-based access control (RBAC) can be used to ensure users only have access to the areas of the application required in their specific job role.

Creating Secret Server Users
----------------------------

The initial configuration we have completed so far has been performed using the initial account created during the installation of Secret Server. We now need to consider how we will provide access to other users. There are three main ways in which user access can be provided within secret server

#. **Creating local users** – User accounts can be created within secret server
#. **Active Directory Sync** – Specific users or groups of users will be able to log in to secret server using the active directory domain credentials
#. **SSO Integration** – Secret server can integrate with many single sign on providers using SAML

In this section we will create a new local user as an example and then configure Active Directory synchronization to allow existing AD users to log into Secret Server with their domain credentials.

Lab 6 - Creating a local user
*****************************

#. Ensure you are logged in to Secret Server with the account created during the installation (ss_admin / *Provided by trainer*)
#. Navigate to the **Admin > Users page**
#. On the intro page, click **Continue**

   .. figure:: images/lab-ss-001.png

#. On the right of the page, click the **Create User** button, the **Add User** page will appear.
#. Create a new user account using the settings below or create your own local user

   - **Username:** JBloggs
   - **Display Name:** Joe Bloggs
   - **New Password:** *Provided by trainer*
   - **Confirm Password:** *Provided by trainer*
   - **Email:** bloggs@thylab.com
   - **Slack:** Leave Blank
   - Leave rest of the fields default, make suer **Enabled** is enabled!

   .. figure:: images/lab-ss-002.png

#. Click **Add User** to create the new user account. 
 
Lab 7 – Configuring Active Directory Synchronization
****************************************************

In this exercise will set up synchronization between secret server and an Active Directory domain. This will allow specific users or groups users access to Secret Server using their Domain credentials. 

#. Ensure you are logged in to Secret Server with the account created during the installation (ss_admin / *Provided by trainer*)
#. Navigate to the **Admin > Directory Services**
#. On the introduction screen, click **Continue**

   .. figure:: images/lab-ss-003.png

#. On the right of the screen, click the **Add Domain** button
#. From the list of available directory integrations, select **Active Directory Domain**
#. When the Active Directory dialogue appears enter the following information:
   
   - Fully Qualified Domain Name: thylab.local
   - Friendly Name: Thylab
   - Active:: Ticked
   - Use LDAPS: No

#. For the Synchronization Secret, we will need to create a new secret in secret server for the credentials of an account that has read access to Active Directory. Click **Create New Secret** on the right-hand side of the dialogue
#. The new secret page should now be opened in a new tab, configure the new secret with the following information:
#. Ensure secret template is set to Active Directory Account
#. Set Secret Name to **AD Sync**
#. Set Domain to **Thylab**
#. Set Username to **svc_sync**
#. Set Password to *Provided by trainer*
#. In the notes field, type: *Used for active directory integration and synchronization in Secret Server*
#. Click **Create Secret**
#. Leave **Multifactor Authentication** as None
#. Your settings should now match the image below:

   .. figure:: images/lab-ss-004.png
 
#. Click **Validate and Save**
#. Secret Server will check that the Domain can be contacted, you should now see the Thylab.com domain in the Active Directory Domains page. Now that the Domain has been configured, we need to identify which users or groups of users from Active Directory we want to synchronize into Secret Server.
#. From the drop-down list of available groups, select the following. 

   - Secret Server Administrators
   - IT – Database Team
   - IT – Desktop Team
   - IT – Server Team
   - IT – Unix Team

   .. figure:: images/lab-ss-006.png
 
#. Click the **Save** button
#. The Synchronize Now dialogue is displayed. Keep both **Enable Directory Services** and **Enable User Synchronization** checked
#. Click **Sync Now** (this will perform an initial, manual synchronization of all users present in the selected AD groups)
 
To AD Synchronization to run on a schedule
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Navigate to **Admin > Directory Services** if you opened another page, otherwise click the **Configuration** tab.
#. The settings will match the following:

   .. figure:: images/lab-ss-007.png

#. Under **User Synchronization**, click **Edit**.
#. Change the **Synchronization Interval** to run at a desired interval (default is every hour)
#. Change the **User Account Options** to **User Status Mirrors Active Directory** (this is the most commonly used option and means that whatever state a user is in within Active Directory (Enabled/Disabled) will be replicated in Secret Server)

   .. note:: 
        At this point your trainer will explain Automatic user management or visit https://docs.thycotic.com/ss/10.9.0/directory-services/active-directory/understanding-ad-automatic-user-management/index.md for more information
 
 
Groups
------

Within Secret Server groups are an important organizational container for user accounts. Although Roles (discussed in the next section) permissions and access to secrets can be determined at the individual user level, this approach can be highly complex, time consuming and difficult to manage. Adding users to groups means that configuration can then easily be applied to all users within the group while still providing the option for exceptions at the individual user level.

| If Active Directory integration and synchronization have been configured, then any selected groups and group memberships from Active Directory will be replicated within Secret Server. If these groups do not provide the level of granularity required in Secret Server, local groups can also be created.

Lab 8 – Creating a local group
******************************

#. Navigate to the **Admin > Groups** page, you should see the four groups that were synced from Active Directory plus a default local group called Everyone
#. To create a new group, click the **Create Group** button on the right of the screen
#. Set Group name to **Checkout Approvers**
#. Ensure **Enabled** is checked and click **Create Group**
#. Click the **Add** button
#. Select **Barry Saunders**, **Hardeep Patel** and **Kim Morris** 
#. Your group should now match the image below. If it is, click **Add**, this group will be used in later lab exercises

   .. figure:: images/lab-ss-008.png

Roles
-----

When users are created or synchronized into Secret Server they must be assigned to a role. This ensures that a strict role-based access (RBAC) approach can applied within secret server.

| A role in Secret Server is basically a permission set. There are 117 set highly granular permissions that can be included or excluded from a role to ensure that your organization can provide each user with the specific permissions they require without creating over privileged users.

| In this section we will cover the default roles available in Secret Server and how to apply roles to users or groups of users. We will also introduce several scenarios where you may want to create custom roles.

.. Note::
    By default, when users are first created or synchronized into secret server, they are assigned the **user role**. This can be changed by navigating to the **Admin > Configuration** page. Under the **User Experience** section, you will find the **Default New User Role** field. You can change this to any available role. 

Lab 9 – Applying Roles
**********************

Roles can be applied to individual user accounts or to groups. As a best practice, users should be added to groups and then roles applied at the group level. This provides a more scalable, manageable approach to role-based access control (RBAC).

| We will now apply the built in Administrators role to the Secret Server Administrators group we have previously synced from Active Directory

#. Navigate to the **Admin > Roles** page
#. Click the **Assign Roles** button on the right of the screen 
#. At this point, roles can be assigned by role (role is selected first then users added to the role) or by user or group (user or group is selected first then role added to the user or group). We will apply **By Role** 
#. Ensure the **Administrator** role is selected in the drop-down role field
#. Click **Edit**
#. Find and select the **thylab\Secret Server Administrators**’ group
#. Click the single left arrow button to move the group into the assigned field
#. Your configuration should match the image below:

   .. figure:: images/lab-ss-009.png

#. Click **Save Change**

Lab 10 – Creating Custom Roles
******************************

Out of the box, Secret Server provides a range of Roles that satisfy many common use cases. Thycotic does recommend that each customer creates custom roles based the needs of their organization

| In this lab exercise we will explore a common scenario where more granular permission sets may be required.

| Secret Server provides an important break glass mechanism called **Unlimited Administration Mode**.  If this administration mode is enabled, any user with a specified permission will automatically gain access to **all secrets stored in secret server, regardless of any permissions applied at the folder or individual secret level**. 

| There are three role permissions relevant to Unlimited Administration:

- **Administer Configuration Unlimited Admin** – Users with this role permission can enable or disable unlimited administration mode
- **Unlimited Administrator** – Users with this role permission receive unlimited secret access if unlimited administration mode is enabled
- **View Configuration Unlimited Admin** – Users with this role permission can view the current administration mode configuration

As a best practice, Thycotic recommends splitting the Administrator role out to ensure a least privilege approach

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - User
     - Administrator (Super User)
   * - Description
     - Can configure and receive unlimited administration
   * - Permissions	
     - Administer Configuration Unlimited Access
   * - 
     - Unlimited Administrator
   * - 
     - View Configuration Unlimited Administrator


.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - User
     - Administrator (Unlimited Admin Configure)
   * - Description	
     - Can configure **but NOT** receive unlimited administration
   * - Permissions
     - View Configuration Unlimited Administrator
   * - 
     - Administer Configuration Unlimited Access

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - User
     - Administrator (Unlimited Admin User)
   * - Description	
     - Can receive but NOT configure unlimited administration
   * - Permissions
     - Unlimited Administrator
   * - 
     - View Configuration Unlimited Administrator

#. Navigate to the **Admin > Roles** page
#. Select the **Administrator** role
#. Scroll to the bottom of the page and click **Edit**
#. Scroll back to the top of the page and change the Role Name field to **Administrator (Super User)**
#. Click **Save**
#. Go back to the **Admin > Roles page**
#. Click the **Create Role** button on the right of the screen
#. Enter a role name of Administrator (Unlimited Admin Configure)
#. Click the double left arrow to move all permissions from the *Permissions Unassigned* field to *Permissions Assigned*
#. Move the following permissions back to *Permissions Unassigned* (using the single arrow pointing right and using CTRL to multiple select):

   - Access Offline Secrets on Mobile
   - Allow Access Challenge
   - Privilege Manager MacOS Admin
   - Privilege Manager User
   - Privilege Manager Windows Admin
   - Unlimited Administrator
   - Web Services impersonate

#. Click **Save**
#. Repeat steps 6-11 for the **Administrator (Unlimited Admin User)** where all permissions are included apart from the following:

   - Access Offline Secrets on Mobile
   - Administer Configuration Unlimited Admin
   - Allow Access Challenge
   - Privilege Manager MacOS Admin
   - Privilege Manager User
   - Privilege Manager Windows Admin
   - Web Services impersonate

#. Go to **Assign Roles**
#. Now unassign the Administrator (Super User) role from the Secret Server Administrators AD group by clicking **Edit** and the single arrow pointing right after selecting the group.

   .. figure:: images/lab-ss-010.png

#. Click **Save Changes**
#. Click the dropdown box where **Administrator (Super User)** is mentioned
#. Select **Administrator (Unlimited Admin Configure)** role and assign **Sarah Tate**
#. Click **Save Changes**
#. Click the dropdown box where **Administrator (Unlimited Admin Configure)** is mentioned
#. Select **Administrator (Unlimited Admin User)** role and assign **Tom Smith**
#. Click **Save Changes**
#. Click **Back** twice

Check role assignment
^^^^^^^^^^^^^^^^^^^^^

#. To check the role assigment, click **Admin > Users**
#. click on account names **STate** and click the **Roles** Tab. This shows the assigned role and should correspond with the steps above for Sarah Tate

   .. figure:: images/lab-ss-011.png

   .. note::
       To see the full Role name, hoover your mouse over the name and after a few seconds the full name is given as shown in the screenshot.

#. Repeat the steps for Tom Smith (TSmith) and check that his roles are also correct.



.. raw:: html

    <hr><CENTER>
    <H2 style="color:#80BB01">This concludes this module</font>
    </CENTER>