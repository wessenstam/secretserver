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
#. On the intro page, click Continue
#. On the right of the page, click the Create User button, the new user page will appear.
#. Create a new user account using the settings from the image or create your own local user
#. Click Add User to create the new user account. 
 
Lab – Configuring Active Directory Synchronization
**************************************************

In this exercise will set up synchronization between secret server and an Active Directory domain. This will allow specific users or groups users access to Secret Server using their Domain credentials. 

1.	Ensure you are logged in to Secret Server with the account created during the installation (ss_admin / *Provided by trainer*)
2.	Navigate to the Admin > Directory Services
3.	On the introduction screen, click Continue
4.	On the right of the screen, click the Add Domain button
5.	From the list of available directory integrations, select Active Directory Domain
6.	When the Active Directory dialogue appears enter the following information:
a.	Fully Qualified Domain Name: Thylab.local
b.	Friendly Name: Thylab
c.	Active:: Ticked
d.	Use LDAPS: No
7.	For the Synchronization Secret, we will need to create a new secret in secret server for the credentials of an account that has read access to Active Directory. Click Create New Secret on the right-hand side of the dialogue
8.	The new secret page should now be opened in a new tab, configure the new secret with the following information:
9.	Ensure secret template is set to Active Directory Account
10.	Set Secret Name to AD Sync
11.	Set Domain to Thylab
12.	Set Username to svc_sync
13.	Set Password to *Provided by trainer*
14.	In the notes field, type used for active directory integration and synchronization in Secret Server
15.	Click Create Secret
16.	Leave multifactor Authentication as None
17.	Your settings should now match the image below:
 
18.	Click Validate and Save
19.	Secret Server will check that the Domain can be contacted, you should now see the Thylab.com domain in the Active Directory Domains page:
20.	The domain Groups dialogue will now be shown.
21.	Now that the Domain has been configured, we need to identify which users or groups of users from Active Directory we want to synchronize into Secret Server.
22.	From the drop-down list of available groups, select the following. 
a.	Secret Server Administrators
b.	IT – Database Team
c.	IT – Desktop Team
d.	IT – Server Team
e.	IT – Unix Team

 
23.	Click the Save button
24.	The Synchronize Now dialogue is displayed. 
25.	Keep both Enable Directory Services and Enable User Synchronization checked
 
26.	Click Sync Now (this will perform an initial, manual synchronization of all users present in the selected AD groups)
 
To AD Synchronization to run on a schedule
27.	Navigate to the Configuration tab within Admin > Directory Services.
28.	Select the Thylab.local domain.
29.	The settings will match the following:
 
30.	Under User Synchronization, click Edit.
31.	Change the Synchronization Interval to run at the desired interval (default is every hour)
32.	Change the User Account Options to User Status Mirrors Active Directory (this is the most commonly used option and means that whatever state a user is in within Active Directory (Enabled/Disabled) will be replicated in Secret Server)
Extra; At this point your trainer will explain Automatic user management or visit https://docs.thycotic.com/ss/10.9.0/directory-services/active-directory/understanding-ad-automatic-user-management/index.md for more information
 
 
3.2 Groups
Within Secret Server groups are an important organizational container for user accounts. Although Roles (discussed in the next section) permissions and access to secrets can be determined at the individual user level, this approach can be highly complex, time consuming and difficult to manage. Adding users to groups means that configuration can then easily be applied to all users within the group while still providing the option for exceptions at the individual user level.
If Active Directory integration and synchronization have been configured, then any selected groups and group memberships from Active Directory will be replicated within Secret Server. If these groups do not provide the level of granularity required in Secret Server, local groups can also be created.
Lab Exercise 8 – Creating a local group
1.	Navigate to the Admin > Groups page, you should see the four groups that were synced from Active Directory plus a default local group called Everyone
2.	To create a new group, click the Create Group button on the right of the screen
3.	Create a new group with the following details:
4.	Set Group name to Checkout Approvers
5.	Ensure Enabled is checked and click Create Group
6.	Click the Edit Members button
7.	Leave the Managed By field set to Group Administrators
8.	Hold down the CTRL and select Barry Saunders, Hardeep Patel and Kim Morris 
9.	Your group should now match the image below, this group will be used in later lab exercises
 
 
3.3 Roles
When users are created or synchronized into Secret Server they must be assigned to a role. This ensures that a strict role-based access (RBAC) approach can applied within secret server.
A role in Secret Server is basically a permission set. There are 117 set highly granular permissions that can be included or excluded from a role to ensure that your organization can provide each user with the specific permissions they require without creating over privileged users.
 In this section we will cover the default roles available in Secret Server and how to apply roles to users or groups of users. We will also introduce several scenarios where you may want to create custom roles.
Note: By default, when users are first created or synchronized into secret server, they are assigned the user role. This can be changed by navigating to the Admin > Configuration page. Under the User Experience section, you will find the Default New User Role field. You can change this to any available role. 
Lab exercise 9 – Applying Roles.
Roles can be applied to individual user accounts or to groups. As a best practice, users should be added to groups and then roles applied at the group level. This provides a more scalable, manageable approach to role-based access control (RBAC).
We will now apply the built in Administrators role to the Secret Server Administrators group we have previously synced from Active Directory
1.	Navigate to the Admin > Roles page
2.	Click the Assign Roles button on the right of the screen 
3.	At this point, roles can be assigned by role (role is selected first then users added to the role) or by user or group (user or group is selected first then role added to the user or group). We will apply By Role 
4.	Ensure the Administrator role is selected in the drop-down role field
5.	Click Edit
6.	Find and select the thylab\secret server administrators’ group
7.	Click the single left arrow button to move the group into the assigned field
8.	Your configuration should match the image below:
 
9.	Click Save Change

