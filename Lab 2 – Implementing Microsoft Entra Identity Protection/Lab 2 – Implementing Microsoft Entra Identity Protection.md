# Day 2 – Lab 2 – Implementing Microsoft Entra Identity Protection​

## Objective:

In this lab we will explore how to configure and enable user risk
policy. We will also explore how to block a user or a group of users
from using any cloud app using a conditional policy.

We will also see how to monitor and manage security posture using
Identity Secure Score.

## Exercise 1 – Enable User risk policy.

### Task 1 – Configure a user risk policy

1. Sign in to the `https://entra.microsoft.com` using your
    **Office 365 tenant credentials**.

1. On the lefthand menu, under **Identity**, expand **Protection**, and
    then select **Identity protection**.

    ![](./media/image1.png)

2. In the **Identity protection** page, in the left navigation,
    select **User risk policy**.

    ![](./media/image2.png)

3. Under **Assignments**, select **All users** and review the available
    options. Then choose **Select individuals and groups**. 

    ![](./media/image3.png)

4. In the **Select Users** pane, select the group **Sales101**. Then
    choose **Select**.

    ![](./media/image4.png)

5. Under **User risk**, select **Low and above**. In the User risk
    pane, select **High** and then select **Done**.

    ![](./media/image5.png)

6. Under **Controls** \ **Access**, select **Allow access** and
    **Require password change**, then select **Done**.

    ![](./media/image6.png)

7. Under **Policy enforcement**, select **Enabled** and then
    select **Save**.

    ![](./media/image7.png)

    ![](./media/image8.png)

### Task 2 – Enable Sign-in risk policy

1. On the **Identity Protection** page, in the left navigation,
    select **Sign-in risk policy**.

    ![](./media/image9.png)

8. Under **Assignments**, select **All users** and review the available
    options. Then choose **Select individuals and groups**. We will
    limit our policy rollout to **Sales** team.

    ![A screenshot of a computer Description automatically
generated](./media/image10.png)

9. In the **Select Users** pane, select the group **Sales101**. Then
    choose **Select**.

    ![](./media/image11.png)

10. Under **User risk**, select **Low and above**. In the User risk
    pane, select **High** and then select **Done**.

    ![](./media/image12.png)

11. Under **Controls** \ **Access**, select **Block access**. Select
    the **Require multi-factor authentication** check box and then
    select **Done**.

    ![A screenshot of a computer screen Description automatically
generated](./media/image13.png)

12. Under **Policy enforcement**, select **Enabled** and then
    select **Save**.

    ![A screenshot of a computer Description automatically
generated](./media/image14.png)

    ![](./media/image15.png)

Your organization needs to be able to limit user access to its internal
applications. You must deploy a Conditional access policy.

## Exercise 2 – Set a conditional access policy to block a user from accessing Viva Engage

### Task 1 – Confirm Allan Deyoung has access to Engage

1. Launch a new InPrivate browser window in your lab VM.



13. Navigate to `https://www.office.com`.

14. When prompted, log in as **Allan Deyoung**:

    * Username – `alland@` Paste the Tenant name from the **Home/Resources
    tab**

    * Password – Paste the User Password from the Resources tab.

15. Click on **Explore App** and then click on the **Engage** icon to
    see that it loads correctly.

    ![](./media/image16.png)

16. Click on **Log in with Microsoft account**.

    ![](./media/image17.png)

17. The portal should load successfully.

    ![](./media/image18.png)

### Task 2 – Create a conditional access policy

Microsoft Entra conditional access is an advanced feature of Microsoft
Entra ID that allows you to specify detailed policies that control who
can access your resources. Using Conditional Access, you can protect
your applications by limiting users’ access based on things like groups,
device type, location, and role.

1. Browse to `https://entra.microsoft.com` and sign in using
    the **Office 365 tenant credentials**.



18. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

    ![A screenshot of a computer Description automatically
generated](./media/image19.png)

19. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – `Block Engage for Allan Deyoung`

    - Under **Users**, select **0 users and groups selected/Specific
    users included**. Then under **Include**, choose **Select users
    and groups**. Select the check box near **Users and groups**. Then
    under **Select**, choose **0 users and groups selected**.

    ![A screenshot of a computer Description automatically
generated](./media/image20.png)

    - Scroll down on the **Select users and groups** page, select **Allan
  Deyoung**. Choose **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image21.png)

  - Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Select apps**. Under select, choose
  **None**. In the side pane, search for and select **Viva Engage** by
  selecting the check box near the app. Then choose **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image22.png)

  - Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the Grant pane, select **Block access** |
  **Required all the selected controls** and then choose **Select**.

    ![](./media/image23.png)

  - Enable policy – **On**. Click on **Create**.

    ![A screenshot of a computer Description automatically
generated](./media/image24.png)

    ![](./media/image25.png)

**Note** - This policy is being configured for the exercise only and is
being used to quickly demonstrate a conditional access policy.

Keep the page open we will return to this page in **Task 4**.

### Task 3 – Test the conditional access policy

You should test your conditional access policies to ensure they working
as expected.

1. Close the InPrivate Window or Log out completely.

2. Launch a new InPrivate browser window in your lab VM.

21. Navigate to `https://www.office.com`.

22. When prompted, log in as **Allan Deyoung**:

    * Username – `alland@` copy and paste the Tenant name from the **Resources tab**

    * Password – Paste the User Password from the Resources tab.

23. Click on **Explore App** and then click on the **Engage** icon to
    see that it loads correctly.

24. Verify you are prevented from accessing **Viva Engage**.

    ![](./media/image26.png)

    > **Note** - If you are signed in, close the tab, wait 1 minute, and then
    retry. If you are auto-logged into Engage as Allan, then you will need
    to manually log out. Your credentials / access were cached. Once you log
    out and sign-in, your Engage session should deny access. To disable the
    policy, follow the given steps.

25. Close the tab and return to the Conditional Access page.

26. Select the **Block Engage for Allan Deyoung** policy.

27. Under **Enable policy**, select **Off** and then select **Save**.

### Task 4 – Use ‘What if’ to test conditional access policies

1. Browse to `https://entra.microsoft.com` and sign in using
    the **Office 365 tenant credentials**.

2. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access.** In the navigation pane,
    select **Policies**. Select **What If**.

    ![A screenshot of a computer Description automatically
generated](./media/image27.png)

28. Under **User or Workload identity**, select **No user or service
    principal selected**. Under **Select identity type**, select
    **User**, and then choose **No user selected**.

    ![](./media/image28.png)

29. Choose **Allan Deyoung** as the user. Then choose **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image29.png)

30. Under **Cloud apps, actions, or authentication context**,
    select **Any cloud app**. Under **Select what this policy applies
    to**, choose **Select apps** and then **None** under **Select**.

    ![](./media/image30.png)

31. In the select pane, choose **Viva Engage**. And then choose
    **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image31.png)

32. Select **What if**.

    ![A screenshot of a computer Description automatically
generated](./media/image32.png)

33. You will be provided with a report at the bottom of the tile
    for **Policies that will apply** and **Policies that will not
    apply**.

    ![A screenshot of a computer Description automatically
generated](./media/image33.png)

This allows you to test the policies and their effectiveness before
enabling the policies.

### Task 5 – Configure sign in frequency controls using a conditional access policy

As part of your company’s larger security configuration, you must test a
conditional access policy that can be used to control sign in frequency.

1. Browse to `https://entra.microsoft.com` and sign in using
    the **Office 365 tenant credentials**.



34. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

    ![A screenshot of a computer Description automatically
generated](./media/image19.png)

35. On the **New Conditional Access Policy** page, provide the below
    details.

    - Name – `Sign in frequency`

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

    ![A screenshot of a computer Description automatically
generated](./media/image34.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image35.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Select apps**. Under select, choose
  **None**. In the side pane, search for and select **Office 365** by
  selecting the check box near the app. Then choose **Select**.

    ![A screenshot of a computer Description automatically
generated](./media/image36.png)

- Under **Access controls**, within the **Sessions** section, select **0
  controls selected**. In the **Grant** pane, select **Sign-in
  frequency,** in the value box, enter **14**. Select the units menu,
  select **Days**, and then choose **Select.**

    ![](./media/image37.png)

- Enable policy – **On**. Click on **Create**.

    ![](./media/image38.png)

    ![A screenshot of a computer Description automatically
generated](./media/image39.png)

## Exercise 3 – Monitor and managed security posture with Identity Secure Score

1. Browse to `https://entra.microsoft.com` and sign in using
    the **Office 365 tenant credentials**.

36. On the left hand menu, under **Protection,** click on **… Show more**,
    select **Identity Secure Score.** Select **Identity Secure Score
    from the sub-menu.** This will take you to the Identity Secure Score
    dashboard.

    ![A screenshot of a computer Description automatically
generated](./media/image40.png)

37. You may not see many recommendations but in a production environment
    you can view the **Improvement actions**. Sort the recommendations
    by **User impact**.

    ![A screenshot of a computer Description automatically
generated](./media/image41.png)

38. Select the first Improvement action. Review the recommendations
    under **WHAT AM I ABOUT TO CHANGE?** section and then you can select
    the status of the action from the dropdown. Change it to **Planned**
    and then select **Save**.

    ![](./media/image42.png)

In contrast to the improvement actions in Microsoft Defender for Cloud
and Microsoft 365 Defender, these improvement actions are specific to identity. This provides a more focused list of potential actions to your security posture management. Any improvement actions initiated from this
list will also provide an impact to your overall tenant security
posture.

## Summary:

In this lab we enabled user risk policy, created a conditional access policy to block a user from accessing a cloud app, and explored the Identity Secure Score.