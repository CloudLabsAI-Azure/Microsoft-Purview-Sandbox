# Part:1 Lab 04 - Configure DLP Policies

## Lab scenario
You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company that offers driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization.

**Note**: Please consider the lab user provided to you in the **Environment Details** page as a user id replacement of Joni Sherman. 

## Lab objectives
In this lab, you will complete the following tasks:

+ Task 1: Create a DLP policy in test mode
+ Task 2: Modify a DLP policy
+ Task 3: How to Activate a policy in test mode
+ Task 4: Modify policy priority
+ Task 5: Enable file monitoring in Microsoft Defender for Cloud Apps
+ Task 6: Create File Policy for Microsoft Defender for Cloud Apps
+ Task 7: Create a DLP Policy for PowerPlatform

## Architecture diagram
![](../media/part1lab4.png)  

### Task 1 – Create a DLP policy in test mode

In this exercise, you will create a Data Loss Prevention policy in the Microsoft Purview portal to protect sensitive data from being shared by users. The DLP Policy that you create will inform your users if they want to share content that contains Credit Card information and allow them to provide a justification for sending this information. The policy will be implemented in test mode because you do not want the block action to affect your users yet.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**. sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided).  Joni's password should be provided in environment details page.

1. If the **Stay signed in?** dialog box appears, select the **Don’t show this again** checkbox and then select **No**.

3. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window select the **Policies** tab, and then select **+Create policy** to start the wizard for creating a new data loss prevention policy.

1. On the **Start with a template or create a custom policy** page, scroll down and select **Custom** under **Categories** and **Custom policy** under **Templates**. By default, both  options should already be selected , select **Next**.

1. On the **Name your DLP policy** page, type *Credit Card DLP Policy* in the **Name** field and *Protect credit card numbers from being shared.* in the **Description** field. Select **Next**.

1. On the **Choose locations to apply the policy** page, enable the **Teams chat and channel messages** option only and select **Next**. 

1. On the **Define policy settings** page, select **Create or customize advanced DLP rules** and select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** page, type *Credit card information* in the **Name** field.

1. Under **Conditions**, select **+ Add Condition** and then select **Content contains** from the dropdown menu.

1. In the new **Content contains** area, select **Add** and select **Sensitive info types** from the dropdown menu.

1. On the **Sensitive info types** page, select **Credit Card Number** and select **Add**.

1. On the **Create rule** page, select **+ Add condition** and select **Content is shared from Microsoft 365** from the dropdown menu.

1. In the new **Content is shared from Microsoft 365** section, select the **Only with people inside my organization** option.

1. On the **Create rule** page, select **+ Add an action** and select **Restrict access or encrypt the content in Microsoft 365 locations**.

1. Check the box in front of **Restrict access or encrypt the content in Microsoft 365 locations** and then select **Block Everyone**.

1. On the **Create rule** page, in the **User notifications** section, select the switch to put it in the **On** position.

1. On the **Create rule** page, in the **User overrides** section, under the **Allow overrides from M365 services**, check the box **Allow overrides from M365 services. Allows users in Exchange, Sharepoint, OneDrive and Teams to override policy restrictions.**

	Note: If you were not able to select the check box of **Allow overrides from M365 services**, enable the check box of **Notify users in Office 365 with a policy tip** which can be found on the **Create rule** page under the **User notification >>  Microsoft 365 services** section from the previous step. Then select the check box of **Allow overrides from M365 services. Allows users in Exchange, Sharepoint, OneDrive and Teams to override policy restrictions.**

1. Check the box **Require a business justification to override**.

1. In the **Incident reports** section, in the **Use this severity level in admin alerts and reports** dropdown, select **Low**.

1. Select **Save**, then select **Next**.

1. On the **Test or turn on the policy** page select **Test it out first** and select **Show policy tips while in test mode**.

1. Select **Next** and review the policy configuration.

1. Select **Submit** to create the policy.

1. Once the policy is created select **Done**.

You have now created a DLP policy that scans for Credit Card numbers in Microsoft Teams chats and channels and allows users to provide a business justification to override the policy.

### Task 2 - Modify a DLP policy

In this task, you will modify the existing DLP policy you created in the previous step to also scan e-mails for Credit Card information and inform users if they want to share this content in an e-mail.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Purview portal**, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window select the **Policies** tab, then select the policy named **Credit Card DLP Policy** and then select **Edit policy** (pencil icon) to open the policy wizard.

1. On the **Name your DLP policy** page, select **Next**.

1. On the **Choose locations to apply the policy** page, enable the **Exchange email** option and then select **Next** until you reach the **Review your policy and create it** page.

1. Select **Submit** to apply the change you made in the policy.

1. Once the policy is updated select **Done**.

You have now modified an existing DLP policy and changed the locations it scans for content.


### Task 3 - How to Activate a policy in test mode

In this task, you will activate the credit card information DLP policy you created in test mode so it enforces its protective actions.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview portal** , in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window select the **Policies** tab, then select the policy named **Credit Card DLP Policy** and select **Edit policy** (pencil) to open the policy wizard.

1. Select **Next** until you reach the **Test or turn on the policy** page and select **Turn it on right away**.

1. Select **Next**, then select **Submit** to activate the policy.

1. Once the policy is updated select **Done**.

You have successfully activated the DLP Policy. If the policy detects an attempt to share credit card information, it will now block the attempt and allow the users to provide a business justification to override the block action.

### Task 4 - Modify policy priority

**Note**- If you have multiple DLP policies only then you can be able to perform the priority action

After creating two DLP policies, you want to make sure that the more restrictive policy is processed at a higher priority than the less restrictive policy. For this reason, you want to move the EmployeeID DLP Policy into the higher priority.

1. You should still be logged into your lab-VM as the **lab-vm\labuser** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window select the **Policies** tab, select the policies you want to prioritize **Reprioritize** to open the **Actions** selection.

1. Select **Move to top**.

1. In the **Data loss prevention** window, select **Refresh** and review the priority in the **Order** column of the policy table.

You successfully modified the priority of your DLP policies. If both policies match the same content the action of the higher priority policy will be enforced.

### Task 5 - Enable file monitoring in Microsoft Defender for Cloud Apps

You want to use file policies in Microsoft Defender for Cloud Apps to protect files in your OneDrive and SharePoint Online locations. Before you can create a file policy, you need to enable file monitoring so Microsoft Defender for Cloud Apps can scan files in your organization.

1. You should still be logged into your lab-vm as the **lab-vm\labuser** account.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. Select the **Profile picture** of Joni Sherman in the top right and select **Sign out**, then close the browser.

1. Open **Microsoft Edge** and navigate to **https://portal.cloudappsecurity.com** and log into the Microsoft Defender for Cloud Apps portal as **MOD Administrator**. labuser@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. In the left side, scroll down to settings, select the **CloudApps**,

1. On the **CloudApps** page, under **Information Protection** select **Files**.

1. Select the **Enable file monitoring** checkbox and then select **Save** if it is not already marked.

You successfully enabled file monitoring in Microsoft Defender for Cloud Apps and can now scan files for sensitive content using file policies.

### Task 6 - Create File Policy for Microsoft Defender for Cloud Apps

In this task, you want to create a file policy in Microsoft Defender for Cloud Apps to scan files in OneDrive and SharePoint Online and automatically quarantine files containing credit card information if they are shared.

1. You should still be logged into your lab-vm as the **labvm\labuser** account.

1. In **Microsoft Edge**, the Microsoft Defender for Cloud Apps portal tab should still be open. Select the **Profile picture** of the MOD Admin in the top right and select **Sign out** next to the cogwheel, then close the  browser..

1. Open **Microsoft Edge** and navigate to **https://portal.cloudappsecurity.com** and log into the Microsoft Defender for Cloud Apps portal as **labuser** labuser@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni Shermans password should be provided by your lab hosting provider.

1. In the **Microsoft Defender for Cloud Apps** portal, in the left navigation pane, expand **Control** and select **Policies**.

1. On the **Policies** page, expand **Policy** and then select **Policy Management** click on Create **policy** Select **File Policy**.

1. On the **Create file policy** page, type *Credit Card Information for files* in the **Policy name** field, and type *Protect credit card numbers from being shared in files.* in the **Description** field.

1. Keep the **Policy Severity** on **Low** (one lighted icon) and make sure the **Category** is set to **DLP**. For a file policy, this should be the default.

1. In the **Files matching all of the following** area, expand the dropdown menu **Public (Internet), External, Public** and add **Internal**.

1. In the **Inspection Method** dropdown menu, select **Data Classification Service**.

1. In the **Choose inspection type...** dropdown menu, select **Sensitive information type...**.

1. In the **Select a sensitive information type** dialog, select **Credit Card Number**, then select **Done** in the upper right corner.

1. Under **Alerts**, check the **Create an alert for each matching file** checkbox and review your options. Keep the settings at the default by selecting **Save as default settings**.

1. In the **Governance actions** section, expand **Microsoft OneDrive for Business** and select **Put in user quarantine**.

1. In the **Governance actions** section, expand **Microsoft SharePoint Online** and select **Put in user quarantine**.

1. Select **Create** at the bottom of the page.

You have now created a file policy that will continuously scan files saved in OneDrive and SharePoint for credit card information and quarantine them if they are shared inside your organization.

### Task 7 - Create a DLP Policy for PowerPlatform

Your company uses PowerAutomate flows to share data between SharePoint Online and SalesForce. In this task, you will create a DLP policy for PowerPlatform that allows your existing flows to keep working, but prevents the creation of flows that will share data between SharePoint Online and Apps defined as non-business.

1. Log into the Client 2 VM (LON-CL1) as the **lon-cl2\admin** account.

1. In **Microsoft Edge**, navigate to **https://admin.powerplatform.microsoft.com** and log into the Power Platform admin center as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. In the **Power Platform admin center**, in the left navigation pane, select the drop-down for **Policies** and then select **Data policies**.

1. On the **Data policies** page, select **+ New Policy**.

1. On the **Name your policy** page, type *Tenant-wide SharePoint Policy*, then select **Next**.

1. On the **Non-business|Default** tab on the **Assign connectors** page, select **SharePoint** and **Salesforce**, then select **Move to Business** at the top of the page.

1. In the **Assign connectors** page, select the **Business** tab to make sure both SharePoint and Salesforce now appear.

1. Select **Next** twice.

1. On the **Define scope** page, select **Add all environments**, then select **Next**.

1. On the **Review and create policy** page, review your policy settings, then select **Create policy**.

You have now created a PowerPlatform DLP policy that prevents users from creating flows involving a SharePoint Online Connector and any connector that is not SalesForce.

## Review
In this lab, you will complete the following task:
+ Create a DLP policy in test mode
+ Modify a DLP policy
+ How to Activate a policy in test mode
+ Modify policy priority
+ Enable file monitoring in Microsoft Defender for Cloud Apps
+ Create File Policy for Microsoft Defender for Cloud Apps
+ Create a DLP Policy for PowerPlatform
  
