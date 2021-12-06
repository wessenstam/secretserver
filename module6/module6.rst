.. _m6:

---------
Launchers
---------

Introduction
------------

This sixth will cover:

1. Launchers overview
2. Creating launchers (ssh)
3. Custom launchers
4. Create custom launchers

Launchers overview
------------------

Secret Server provides the ability to launch remote desktop or SSH sessions, run applications or log into web pages directly, using the credentials from a secret. This provides users with a ‘single pane of glass’ where they not only have access to all credentials required for a role but also all the tools necessary to perform tasks using the credentials. 

| The biggest benefit of launchers aside from this efficiency gain is that because Secret Server can seamlessly inject the credentials into the session, application or website, the user never needs visibility of the username and password. This means that passwords can be hidden from users, which, in turn provides a whole range of benefits:

- Prevents users from circumnavigating audit trails or monitoring from Secret Server or other security tools
- Prevents users from sharing credentials with non-authorized parties
- Allows for highly complex passwords as users don’t need to remember or input them
- Allows for regular password rotation

Out of the box, Secret Server provides the following launchers:

- Remote Desktop
- PuTTy
- Website Login
- Powershell Launcher
- SQL Server Management Studio Launcher
- Sybase isql Launcher
- z/OS Launcher
- IBM iSeries Launcher

In addition to these ‘out of the box’ launchers, custom launchers can be created to execute any process that can be executed from the command line. Secret Server can pass secret text fields such to seamlessly run applications with a range of command line arguments. 

.. note:: 
    Your trainer will now demonstrate a number of built in launchers and explain their functionality 

Lab 14 - Creating a 'restricted launch' RDP launcher
****************************************************

The built-in remote desktop launcher allows the user to enter the hostname, fully qualified domain name (FQDN) or IP address of a target machine they want to connect to. In some scenario’s users may not know this information or we may only want them to able to connect to a defined list of endpoints. In this scenario a modified RDP launcher can be created with a defined list of target endpoints.

| As launchers are linked to a secret template, the first step is to create a new template to contain the launcher

.. note:: 
    This lab exercise should be performed from the client lab machine (Client)

#. Navigate to the **Admin > Secret Templates**
#. Make sure **Active Directory Account** is selected in the drop-down
#. Click **Edit**
#. Select **Copy Secret Template**
#. Name the new template: *Active Directory Account (Restricted Launch)*
#. Click **Ok**
#. Click **Continue**
#. Create a new Field and use the following parameters:

   - **FIELD NAME:** Allowed Servers
   - **FIELD SLUG NAME:** allowed-servers (auto populated)
   - **Description:** These servers are allowed to connect to
   - **TYPE:** List (has to be list otherwise we can not select it for restriction)
   - **IS REQUIRED:** Checked
   - **SEARCHABLE:** Unchecked
   - *Leave the rest default*
   - Click the **+** sign to add the line

Now we can configure a modified RDP launcher for the new template

#. Click **Configure Launcher**
#. Click **Edit**
#. Leave all basic settings as they are
#. Under **Advanced Settings**, check **Restrict User Input**
#. Ensure the following settings are configured:

   - **Restrict as:** Allow List
   - **Restrict by Secret Field:** Notes
   - **Include machines from dependencies:** Unchecked

#. Click Save

This configuration means that the user will be presented with a list of endpoints to connect to that will be held in the Notes field of the secret. To test the new template and launcher we will create a secret to launch from.

#. From the Home screen expand the secret folder structure
#. Navigate to IT > IT – Server Team
#. Click the + icon next to Secrets to create a new secret in this folder
#. The Create New Secret Dialogue appears
#. Select Active Directory Account (Restricted Launch)
#. Configure the secret with the following settings:

   - **Name:** Server Team - Domain Admin
   - **Domain:** Thylab
   - **Username:** adm_serverteam1
   - **Password:** Thycotic@2021!
   - **Notes:** DC1, SSPM

19.	Your configuration should match the image below:
 
20.	Click Create Secret
21.	To test our configuration, open the secret (note: Because of the Secret Policy configured earlier, this secret will require checkout and comment) and select the launcher.














.. raw:: html

    <hr><CENTER>
    <H2 style="color:#80BB01">This concludes this module</font>
    </CENTER>