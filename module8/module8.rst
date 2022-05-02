.. _m8:

----------------
Secret Workflows
----------------

Introduction
------------

This eighth module will cover:

1. Checkout workflows
2. Request for access workflows

Overview
--------

In some situations, even when users have permissions to view or edit Secrets we may want to ‘gate’ access to the Secret with a workflow. There are a range of workflow options available within Secret Server that include:

- Checkout
- Request For Access
- Require Comment 
- ITSM ticket Validation

Each of the above options can be used in isolation or together to create highly customisable workflows.

Checkout
********

The TSS checkout feature forces accountability on secrets by granting exclusive access to a single user. If a secret is configured for check out, a user can then access it. If Change Password on Check In is turned on, after check in, SS automatically forces a password change on the remote machine. No other user can access a secret while it is checked out, except unlimited administrators. This guarantees that if the remote machine is accessed using the secret, the user who had it checked out was the only one with proper credentials at that time.

| There are a range of potential benefits to using Checkout, typically organisations have a one-to-one mapping for users and privileged accounts to ensure actions performed under the context of a given privileged account can always be attributed to an individual. This results in organisations having high volumes of privileged accounts. Checkout enables organisations to drastically reduce the number of privileged accounts while maintaining a full audit trail where any activity can be associated to an individual user. 

Lab 21 – Enabling Checkout
^^^^^^^^^^^^^^^^^^^^^^^^^^

Before enabling checkout, we will create an example secret. As with virtually all Secret security settings, checkout can be applied on individual secrets or from a Secret Policy.

#. Navigate to **Secret (double arrows) > IT Team > IT – Server Team** folder then click the **+** Icon to create a new secret
#. Select the *Active Directory Account* Template
#. Create the secret with the following information

   - **Secret Name:** Checkout Example
   - **Domain:** Thylab
   - **Username:** adm_checkout1
   - **Password:** *Provided by Trainer*

#. Your configuration should match the image below:

   .. figure:: images/lab-A-001.png

#. Click **Create Secret**
#. Open the **Checkout Example** secret, as the folder policy is still active, click **Enter Comment**, provide comment and click **Check Out Secret**
#. Navigate to the **Security** tab of the Secret.
#. In the *CheckOut* section click **Edit** then see that you are able to uncheck **Require Check Out**. Leave it *Checked*
  
   .. note:: 
       The reason for being able to do this, is that the created Secret Policy is set to *Default Only*
       
       .. figure:: images/lab-A-002.png

       The default checkout interval value can be configured from **Administration > Actions > Remote Password Changing**

#. Click **Save**
#. Open a new Incognito Window and navigate to \https://sspm.thylab.local/SecretServer
#. In the login screen, use the following parameters:

   - **Username:** STate
   - **Password:** *Provided by Trainer*
   - **Domain:** Thylab (we are going to use the AD to authenticate the user. *Local* means a local user in Secret Server)

#. Click **Log in**
#. Navigate to **Secret > IT Team > IT – Server Team** folder and try to open the **Checkout Example** secret
#. A screen will be shown that the secret is checked out and by whom. Account *STate* has the "power" to force the Check in.

   .. figure:: images/lab-A-003.png

   .. note:: 
       In certain scenarios organisations may need the ability to force the check in of a Secret. To do that a user must have at least **View permission** on the secret **AND** the **Force Check In** permission in their assigned role. 

#. Switch back to the Chrome session where the ss-admin account is logged in and check the secret back in by clicking on the time remaining before auto check in and click **Check In**

   .. figure:: images/lab-A-004.png


Request for Access
******************

Request For access ensures that before a user can access a secret they must make a request to do so, which then needs to be approved by an approver or multiple approvers depending on the workflow configuration

- Establishing a workflow model, the user must request access from the approval group or groups.
- An email is sent to everyone in the approval groups, notifying them of the request.
- The request can be approved or denied by any members of the approval groups.
- If Owners and Approvers also Require Approval is enabled, then even owners or those in an approval group needs to request access.

There are two types of access request workflow available within Secret Server:

- Basic Workflows – a list of individual users or groups are defined as approvers, any single user can approve or deny the request
- Multi-Tier Workflows – Allow for complex multi-tier workflows (max. 15 steps) where specific approval requirements can be specified at each tier. For more information see: https://docs.thycotic.com/ss/11.0.0/secret-workflow-templates/index.md

Lab 22 – Enabling Request for Access
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Before enabling request for access, we will create an example secret. As with virtually all Secret security settings, request for access can be applied on individual secrets or from a Secret Policy.

#. Navigate to **Secrets (double arrows) > IT Team > IT – Server Team** folder then click the **+** Icon to create a new secret
#. Select the *Active Directory Account* Template
#. Create the secret with the following information
    
   - **Secret Name:** RFA Example
   - **Domain:** Thylab
   - **Username:** adm_RFA1
   - **Password:** *Provided by Trainer*

#. Your configuration should match the image below:

   .. figure:: images/lab-A-005.png
 
#. Click **Create Secret**
#. Navigate to the **Security** tab of the Secret
#. Under *Approval*, click **Edit**
#. From the *Require Approval Type* dropdown, select **Everyone (including owners and approvers)**
#. In the *Approval Workflow* field, select **Create a basic (single level) workflow**
#. Under *Approvers*, search for and select the **Checkout Approvers** group we created earlier.

   .. figure:: images/lab-A-006.png

#. Click **Save**
#. After you have Clicked the **Save** button, you will get immediately the **Secret Access Required** screen as that is what we have defined.

   .. figure:: images/lab-A-007.png
 
#. Click **Request Access**
#. In the *Duration* field, set to **One Hour**
#. In the *Reason* field, specify the reason why you need access to the Secret
#. Click **Submit Request**
#. You should still have the Incognito Window where you logged in a s STate in the Thylab domain. If so, please log out the STate account by clicking the initials **ST** in the right top corner and select **Log Out**.

   .. figure:: images/lab-A-008.png

#. Click the **Log In** button
#. Log in using the following

   - **Username:** BSaunders
   - **Password:** *Provided by Trainer*
   - **Domain:** Thylab

#. Navigate to the **Dashboard**
#. On the right of the screen you will see the pending approval request:

   .. figure:: images/lab-A-009.png

#. Click **Approve**
#. Provide a reason for approval 
#. Click **Confirm Approval**
#. The screen wil have no more Approvals
#. *Go back to the ss_admin user session* and you will be allowed access to see the secret.
#. As the Request is valid for one hour, you will not be prompted for the Request anymore till the time expires.

.. raw:: html

    <hr><CENTER>
    <H2 style="color:#00FF59">This concludes this module</font>
    </CENTER>