# Part:1 Lab 01 - Protect Sensitive Data

## Lab scenario
In this lab, you will get know how on what are the basic primary steps to protect the sensitive data.

## Lab objectives

In this lab, you will complete the following tasks:

+ Task 1: know how on sensitivity labels
+ Task 2: Classification on sensitive data

## Architecture diagram
![](../media/part1lab1.png)

### Protecting your data using Microsoft Purview 

1. Open the Microsoft edge and in the Search bar browse **https://compliance.microsoft.com/homepage**,

1. Sign in using the following **credentials**.
    
    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
 
1. you can protect your sensitive data using **Sensitivity label, Encryption messages and documents, Microsoft Defender, Microsoft Information Protection SDK extension for web browser, Data classification**.

   **Note**: We will take a look into how they work in preceding labs and providing brief information about the steps to configure.

### Task 1: Know how sensitivity label 

In this task, you will create a sensitivity label to protect the data.

**Note**: You can find complete steps on how to create sensitivity label in the next lab.

1. Navigate to the labels section to create a label which you want to apply to your data.

   ![Picture 1](../media/Purview_Label_01.png)

1. After creating the label you also need to **publish** it so it can gets applied to your intended data.

1. Select the **Label Policies** create a policy.

   ![Picture 1](../media/Purview_Label_Policies_02.png)

1. Select **Label** to apply the policy to and provide the respective details to complete the policy.

    ![Picture 1](../media/Purview_Label_Policies_attachlabel_03.png)

### Task 2: Classification on sensitive data

In this task, you will be able to classify the sensitive data to detect it, protect it, retain it. Classifiers used to detect the specific contents  like budget, hr records, medical forms, credit card info, etc.

 ![Picture 1](../media/Purview_Classifiers_07.png)

## Review
In this lab, you will complete the following tasks:
+  know how on sensitivity labels
+  Classification on sensitive data

In the Next lab you'll get more deep knoweldge on how to create and work with sensitivity labels and policies in Microsoft Purview.
