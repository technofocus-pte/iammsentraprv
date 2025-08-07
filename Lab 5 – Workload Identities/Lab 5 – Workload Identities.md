# Lab 5 – Workload Identities

## Objective:

Conditional Access policies historically applied only to users when they
access apps and services like SharePoint Online. Now the support is
extended for Conditional Access policies to be applied to service
principals owned by the organization. This capability is called
Conditional Access for workload identities. In this lab we will explore
how to opt for Workload Identities trial and create a CA Policy for any
service principle.

## Exercise 1 – Sign up for Workload Identities trial.

1. Log into the **LON-CL1** with the credentials provided on the Home/Resources tab.

2. Open the Edge browser and go to
    `https://admin.microsoft.com/#/catalog` and select the **All products** tab.

2.  Search for `Workload` and select **Details** under
    **Microsoft Entra Workload ID**.

    ![computer ](./media/image1.png)

3.  On the details page select **Start free trial**.

    ![computer ](./media/image2.png)

4.  Select **Try now**.

    ![computer ](./media/image3.png)

5.  Then click on **Go to Admin Home**.

    ![computer ](./media/image4.png)

6.  From the left navigation, select **Active us**ers under **Users**.
    Select the admin user **MOD Administrator** from the list, expand
    the three dots **(…)** in the top bar and select **Manage product
    Licenses**.

    ![computer ](./media/image5.png)

7.  Select **Microsoft Entra Workload ID** and then select **Save
    changes**.

    ![computer ](./media/image6.png)


## Exercise 2 – Creating a Conditional Access policy for Workload Identities

1.  Browse to `https://entra.microsoft.com/` in another tab and sign in using
    the **Office 365 tenant credentials**.

2.  On the lefthand menu, under **Identity**, expand **Protection**, and
    then select **Conditional access**. On the **Overview**,
    click **+ Create new policy**.

    ![](./media/image7.png)

1.  On the **New Conditional Access Policy** page, provide the below
    details

    - Name – `CA for Workload IDs`

    - Under **Users**, select **0 users or workload identities
      selected**. Under **What does this policy apply to?**, select
      **Workload identities**.

    ![computer ](./media/image8.png)

    - Under **Include**, choose **Select service principals**, and select
    **Box**. Then choose **Select**.

    ![computer ](./media/image9.png)

    - Under **Target resources** > **Resources (formerly cloud apps)** > **Include**, select
    **All resources (formerly 'All cloud apps')**. The policy applies only when a service principal
    requests a token.

    ![computer ](./media/image10.png)

    - Under **Conditions** \> **Service principal risk**, set the
    **Configure** toggle to **Yes**. Select **High** as the levels of
    risk. Select **Done**.

    ![computer ](./media/image11.png)

    - Under **Grant**, **Block access** is the only available option. Access
    is blocked when the specified risk levels are seen. Select the option
    and then choose **Select**.

    ![computer ](./media/image12.png)

    - Enable policy – **On**. Click on **Create**.

    ![computer ](./media/image13.png)

    ![computer ](./media/image14.png)


## Exercise 3 – View the Sign-in logs for Conditional Access policy for Workload Identities

1.  Browse to `https://entra.microsoft.com/` and sign in using
    the **Office 365 tenant credentials**.

2.  On the lefthand menu, under **Entra ID**, scroll down and expand **Monitoring & Health**, and then
    select **Sign-in logs.**

    ![](./media/image16.png)

4.  Click on the **Date** filter and select **Last 7 days** and then
    click on **Apply**.

    ![](./media/image17.png)

5.  Click on the **Service principal sign-ins** tab and review the
    **Conditional Access** column, here the event will appear if the
    Conditional Access Policy was triggered.

    ![](./media/image18.png)

    > **Note** - As this is a Demo environment, so you may not be able to see any Service principal sign-ins


6.  Click on the **User sign-ins (interactive)** tab, then click on
    **Add** **filters** and choose **Conditional Access** then click on
    **Apply**.

    ![](./media/image19.png)

7.  Click on the **Conditional Access** filter and then choose
    **Success** and **Failure**, the click on **Apply**.

    ![](./media/image20.png)

8.  You should be able to **Sign-ins** with **Success** and **Failure**
    logs.

    ![](./media/image21.png)
    
    ![](./media/image22.png)
    
 
**You have completed Lab 5 !!!!!!!**
