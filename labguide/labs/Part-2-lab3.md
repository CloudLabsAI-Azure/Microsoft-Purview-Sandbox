# Part:2 Lab 03 - Explore on updating Enable Encryption

# Lab scenario

In this lab, you will take on the persona of Holly Dickson, Adatum’s Security Administrator. You have been tasked with piloting the use of Microsoft 365 message encryption in Adatum’s Microsoft 365 deployment.

In this exercise you will set up Azure Rights Management for your tenant. You will also learn how to create a mail flow encryption rule using the Exchange Admin Center.

## Lab objectives

In this lab, you will complete the following task:

+ Task 1 : Updating the EAC mail flow rule

## Architecture diagram
![](../media/part2lab3.png)

### Task 1 – Updating the EAC mail flow rule

**EAC to update an existing mail flow rule to use Microsoft Purview Message Encryption**

1. In a web browser, using a work or school account that has been granted global administrator permissions, sign in to **Office 365**.

2. Choose the **Admin tile**.

3. In the Microsoft **365 admin center**, choose **Admin centers** > **Exchange**
  
4. In the **Exchange Admin Center**, go to **Mail flow** > **Rules**.

5. In the list of mail flow rules, select the rule you want to modify to use with Microsoft Purview Message Encryption and then choose **Edit** icon.
   ![Picture 1](../media/image9-lab3.png)

6. To enable encryption using Microsoft Purview Message Encryption, from **Do the following**, choose **Modify the message security**and then 
   choose **Apply Office 365  Message Encryption and rights protection**. choose **Save** and then choose**OK**.
    ![Picture 1](../media/image10-lab3.png)

7. From the **Do the following list**, remove any actions that are assigned to **Modify the message security** > **Apply the previous version of 
   OME**.

8. Choose **Save**.

## Review
In this lab, you will complete the following task:
+ Updating the EAC mail flow rule
