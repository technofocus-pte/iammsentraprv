# Lab 6 – Workload Identities

## Objective:

Conditional Access policies historically applied only to users when they
access apps and services like SharePoint Online. Now the support is
extended for Conditional Access policies to be applied to service
principals owned by the organization. This capability is called
Conditional Access for workload identities. In this lab we will explore
how to opt for Workload Identities trial and create a CA Policy for any
service principle.

## Exercise 1 – Sign up for Workload Identities trial.

1.  Open the Edge browser and go to
    **+++https://admin.microsoft.com/#/catalog**.

2.  Search for **+++Workload+++** and select **Details** under
    **Microsoft Entra Workload ID**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  On the details page select **Start free trial**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Select Try now.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Then select **Continue**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  From the left navigation, select **Active us**ers under **Users**.
    Select the admin user **MOD Administrator** from the list, expand
    the three dots **(…)** in the top bar and select **Manage product
    Licenses**.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

7.  Select **Microsoft Entra Workload ID** and then select **Save
    changes**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

## Exercise 2 – Creating a Conditional Access policy for Workload Identities

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**.

2.  On the lefthand menu, under **Identity**, expand **Protection**, and
    then select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

![](./media/image7.png)

1.  On the **New Conditional Access Policy** page, provide the below
    details

    - Name – **+++CA for Workload IDs+++**

    - Under **Users**, select **0 users or workload identities
      selected**. Under **What does this policy apply to?**, select
      **Workload identities**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

- Under **Include**, choose **Select service principals**, and select
  **Box**. Then choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

- Under **Target resources** \> **Cloud apps** \> **Include**, select
  **All cloud apps**. The policy applies only when a service principal
  requests a token.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

- Under **Conditions** \> **Service principal risk**, set the
  **Configure** toggle to **Yes**. Select **High** as the levels of
  risk. Select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

- Under **Grant**, **Block access** is the only available option. Access
  is blocked when the specified risk levels are seen. Select the option
  and then choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

- Enable policy – **On**. Click on **Create**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

![A screenshot of a computer Description automatically
generated](./media/image14.png)

## Exercise 3 – View the Sign-in logs for Conditional Access policy for Workload Identities

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**.

&nbsp;

2.  On the lefthand menu, under **Identity**, click on **…Show more.**

    ![](./media/image15.png)

3.  Scroll down and expand **Monitoring & Health**, and then
    select **Sign-in logs.**

    ![](./media/image16.png)

4.  Click on the **Date** filter and select **Last 7 days** and then
    click on **Apply**.

    ![](./media/image17.png)

5.  Click on the **Service principal sign-ins** tab and review the
    **Conditional Access** column, here the event will appear if the
    Conditional Access Policy was triggered.

    ![](./media/image18.png)

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

    **You have completed Lab 6 !!!!!!!**
