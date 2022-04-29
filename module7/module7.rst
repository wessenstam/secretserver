.. _m7:

----------------------------
Remote Password Change (RPC)
----------------------------

Introduction
------------

This seventh module will cover:

1. RPC Overview
2. Auto change password using RPC

RPC Overview
------------

As well as storing the credentials of privileged accounts, Secret Server provides the ability to rotate or change passwords for corresponding accounts in Active Directory, local machines, Unix/Linux machines or other devices manually or via an automated schedule. This functionality ensures you that all accounts can be configured to meet your internal password expiration or rotation policy or external compliance rules that you need to adhere to. 

Lab 18 – RPC activation (pre/Post situation)
********************************************

Checking current situation
^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Navigate to the **Secrets (double arrows) > IT Team > IT - Server Team** 
#. Open the **Server Team - Domain Admin** secret, as the policy is still active, click **Enter Comment**, provide comment and click **Check Out Secret**
#. Click the **More** button in the top right corner. You should see something like the below screenshot:

   .. figure:: images/lab-A-001.png


Enabling RPC
^^^^^^^^^^^^

#. Navigate to **Administration (double arrows) > Actions > Remote Password Changing**
#. Click **Edit**
#. Check **Enable Remote Password Changing**
#. Check **Enable Password Changing on Check In**
#. Set the **Check Out Interval** to **Hours 1**
#. Check **Enable Heartbeat**
#. Your configuration should match the image below:

   .. figure:: images/lab-ss-001.png

#. Click **Save** 

Post enabling RPC
^^^^^^^^^^^^^^^^^

#. Navigate to the **Secrets (double arrows) > IT Team > IT - Server Team**
#. Open the **Server Team - Domain Admin** secret
#. You will now see two new options as buttons

   .. figure:: images/lab-A-002.png

Lab 19 – Manually changing a password
*************************************

Now that RPC has been enabled, all secrets will have a Change Password Now and Heartbeat button visible in the secret view. This allows a user with the relevant permission to change a password at any time. 

#. Within the Secret click **Change Password Now** the change password dialogue is displayed:
#. Choose **Randomly Generated**

   .. figure:: images/lab-A-003.png

#. Click **Change Password**
#. At the top of the secret the following message is displayed:

   .. figure:: images/lab-A-004.png

#. This bar will disappear once the password has changed. To check the new password, click on the :fa:`eye` icon next to *Password* to see the password (your password will be different)

   .. figure:: images/lab-A-005.png

RPC Auto Change
---------------

As we have previously seen, once RPC is configured users within sufficient permissions can manually rotate and validate passwords whenever required. For many secrets we will want to ensure that passwords are rotated on a regular schedule without the need for user intervention.

| For automatic password changing there are a number of configuration options to consider:

- The Secret Template used to configure the secret must have password changing enabled
- The Expiration Days field on the secret template or secret itself (Once the secret has expired, remote password configuration will apply)
- Is Remote Password Changing configured within the applied secret policy?

  .. figure:: images/lab-A-008.png

- Is remote password changing configured on the secret itself (*Remote Password Changing* tab)?

  .. figure:: images/lab-A-006.png
 
  .. note:: 
       The fact that RPC can be configured (and enforced) provides a high level of granularity.

If **ALL** secrets with a specific policy require RPC, then this should be enforced. Otherwise the RPC option in the secret policy can be left unset and RPC can be configured on individual secrets.
 
Lab 20 – Configuring RPC auto change 
*********************************************

In this exercise we will assume that all secrets with the IT Server Team – Domain Admin Policy applied should be configured for RPC auto change.
 
#. Navigate to **Administration (double arrows) > Actions > Secret Policy** 
#. Click **IT Server Team – Domain Admin Policy**
#. Click the **Remote Password Changing** tab
#. Click **Edit**
#. Set the **Auto Change** to **Yes** and make sure that the *Default Only* is checked

   .. figure:: images/lab-A-009.png

#. Scroll to the bottom of the screen and click **Save**
#. As setting will actively change settings on existing secrets, the following warning is shown:

   .. figure:: images/lab-A-010.png

#. Click **Ok** 
#. To validate, navigate to the **Secrets (double arrows) > IT Team > IT - Server Team** 
#. Open the **Server Team - Domain Admin** secret, as the policy is still active, click **Enter Comment**, provide comment and click **Check Out Secret**.
#. Click the **Remote Password Changing** tab and the **Auto Change Enabled** should read *Yes*. Also a schedule should be sown.

   .. figure:: images/lab-A-011.png

#. Click **Save**

.. raw:: html

    <hr><CENTER>
    <H2 style="color:#00FF59">This concludes this module</font>
    </CENTER>