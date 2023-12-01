# Part:1 Lab 03 - Configure EAC rule to enable encryption

# Lab scenario

In this lab, you will take on the persona of Holly Dickson, Adatum’s Security Administrator. You have been tasked with piloting the use of Microsoft 365 message encryption in Adatum’s Microsoft 365 deployment.

In this lab you will set up Azure Rights Management for your tenant. You will also learn how to create a mail flow encryption rule using the Exchange Admin Center.

## Lab objectives

In this lab, you will complete the following task:

+ Task 1: Create a Mail Flow Encryption Rule using the Exchange admin center

## Architecture diagram
![](../media/part1lab3.png)

### Task 1 – Create a Mail Flow Encryption Rule using the Exchange admin center

In this task, you will create an encryption rule for messages inside your Exchange Online environment by using the Exchange admin center. 

1. In the **Edge** browse 

1. From the left navigation pane select **Show all** > **Exchange**. This will open the Exchange admin center.

1. In the **Exchange admin center**, select **Mail flow** > **Rules** > **+ Add a rule** > **Create a new rule**.

    ![Picture 1](../media/image1-lab3.png)

1. In the **Set rule conditions** window, in the **Name** box, enter **Encrypt mail** as the name of this rule.

1. Select the drop-down arrow in the **Apply this rule if** condition box. In the drop-down menu, select **the recipient** and **is this 
    person** and on **Select members** blabe select <inject key="AzureAdUserEmail"></inject> click on **Save**.
    ![Picture 1](../media/image2-lab3.png)
    ![Picture 1](../media/image3-lab(3).png)

1. You need to add more conditions, so next to **is this person** click the **+** to the right.
    ![Picture 1](../media/image4-lab3-4-(2).png)

1. Under **And** select **The recipient** and **is external/internal**. In the blade that opens to the right, select **Outside the organization** > **Save**.
   ![Picture 1](../media/image4-lab3-4.png)
   ![Picture 1](../media/image4-lab3-4-(1).png)

1. You now need to define an action to perform when this rule is applied. Under **Do the following…**, select **Modify the message security….** and **Apply Microsoft 365 Message Encryption and rights protection.**
    ![Picture 1](../media/image4-lab3.png)

1. In the **select RMS template** dialog box, select **Encrypt** > **Save**. Click **Next**.
   ![Picture 1](../media/image5-lab3.png)
1. On the **Set rule settings** window, click the checkbox next to **Activate this rule on**. That should automatically populate a date and time that will make the rule take effect immediately upon completion.
   ![Picture 1](../media/image6-lab3.png)
1. Click **Next** > **Finish** > **Done**.

1. In the **Rules** window, click the name of the rule under the **Rules** column. In the window that opens to the right, click the toggle under **Enable or disable rule** to enable the rule. Close the window.
   ![Picture 1](../media/image8-lab3.png)
1. Leave your browser session open for the next exercise.

## Review
In this lab, you will complete the following task:
+ Create a Mail Flow Encryption Rule using the Exchange admin center
