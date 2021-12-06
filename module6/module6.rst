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
    Demo: Your trainer will now demonstrate a number of built in launchers and explain their functionality 















.. raw:: html

    <hr><CENTER>
    <H2 style="color:#80BB01">This concludes this module</font>
    </CENTER>