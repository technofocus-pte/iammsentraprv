# Lab 3 – Microsoft Entra Identity Governance

## Objective:

In this lab, the first exercise involves creating and managing a catalog
of resources, including tasks such as catalog creation, resource
addition, catalog owner addition, and catalog editing.

The second exercise focuses on adding terms of use and implementing
acceptance reporting, using a conditional access policy for a specific
user, Joni Sherman.

The third exercise delves into configuring basics for Microsoft Entra
External Identities and creating access reviews for guest users. In
exercise 4, we will explore how to manage the lifecycle of external
users.

In exercise 5 we will be configuring Microsoft Entra roles using PIM.

## Exercise 1 – Create and manage a catalog of resources in Microsoft Entra entitlement management.

A catalog is a container of resources and access packages. You create a
catalog when you want to group related resources and access packages.
Whoever creates the catalog becomes the first catalog owner. A catalog
owner can add additional catalog owners. You must create and configure a
catalog in your organization.

### Task 1 – Create a catalog

1.  Sign in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.

1.  In the left menu, expand **Identity Governance** and
    select **Entitlement management**. From the sub menu,
    select **Catalogs**. From the top menu, select **+ New Catalog**.

    ![computer ](./media/image1.png)

2.  In the New catalog pane, enter the following information and then
    select **Create**.

    - Name – `Marketing`

    - In the **Description** – `For marketing department users`

    - Under **Enabled, select No**.

    ![computer ](./media/image2.png)

3.  Stay on the Catalogs page and continue to the next exercise.

### Task 2 – Add resources to a catalog

To include resources in an access package, the resources must exist in a
catalog. The types of resources you can add are groups, applications,
and SharePoint Online sites. The groups can be cloud-created Microsoft
365 Groups or cloud-created Microsoft Entra security groups. The
applications can be Microsoft Entra enterprise applications, including
both SaaS applications and your own applications federated to Microsoft
Entra ID. The sites can be SharePoint Online sites or SharePoint Online
site collections.

1.  In the **Catalogs** list, select **Marketing**.

    ![computer ](./media/image3.png)

4.  In the left navigation, under **Manage**, select **Resources**. On
    the menu, select **+ Add resources**.

    ![computer ](./media/image4.png)

5.  In the **Add resources to catalog** page, add the following
    information:

    - Select **Groups and Teams**, select. The check box near
      **Research101**, and then choose **Select.**

    ![computer ](./media/image5.png)

    ![computer ](./media/image6.png)

    - Click on + Applications and choose the **Box** application and click
    on Select button.

    ![computer ](./media/image7.png)

    ![computer ](./media/image8.png)

    - SharePoint sites – **Sales and Marketing**

    ![computer ](./media/image9.png)

6.  When finished, Select **Add**. These resources can now be included
    in access packages within the catalog.

    ![computer ](./media/image10.png)

7.  Stay on the same page and move on to the next task.

### Task 3 – Add additional catalog owners

The user that created a catalog becomes the first catalog owner. To
delegate management of a catalog, you add users to the catalog owner
role. This helps share the catalog management responsibilities.

1.  In the Marketing catalog page, in the left navigation menu,
    select **Roles and administrators**. On the top menu, review the
    available roles and then select **+ Add catalog owner**.

    ![computer ](./media/image11.png)

2.  In **the Select members** pane, select your **Abbi Skinner** and
    then select **Select**.

    ![computer ](./media/image12.png)

3.  Stay on the same page and move on to the next task.

### Task 4 – Edit a catalog

You can edit the name and description for a catalog. Users see this
information in an access package’s details.

1.  In the **Marketing** page, in the left navigation,
    select **Overview**. On the top menu, select **Edit**.

    ![computer ](./media/image13.png)

2. Review the setting and, under **Properties** \ **Enabled**,
    select **Yes**. Select **Save**.

    ![computer ](./media/image14.png)

3. Stay on the same page and move on to the next task.

## Exercise 2 – Add terms of use and acceptance reporting

Microsoft Entra terms of use policies provide a simple method that
organizations can use to present information to end users. This
presentation ensures users see relevant disclaimers for legal or
compliance requirements. This article describes how to get started with
terms of use (ToU) policies.

You must create and enforce a ToU policy for your organization.

### Task 1 – Add terms of use

Once you have finalized your terms of use document, use the following
procedure to add it.

1.  Switch to the VM - **LON-SVR1** and open the Edge browser and Sign in to `https://entra.microsoft.com` using a your **Office
    365 tenant credentials**.

12. In the left menu, expand **Identity Governance** and
    select **Entitlement management**. Then from the sub menu, scroll
    down and select **Terms of use**. On the Terms of use page, on the
    top menu, select **+ New terms.**

    ![computer ](./media/image15.png)

13. **On the New Terms page, add the following information and select
    Create.**

- In the **Name** box, enter `Testing terms of use`.

    > **Note** - This is the terms of use that will be used in the Azure portal.

    - Select the **Terms of use document box**, browse to **C:\Labfiles**
    and select the file named **Contoso_TermsOfUse.pdf**.

    - Select **English** for the language for your terms of use document.

    > **Note** - The language option allows you to upload multiple terms of
     use, each with a different language. The version of the terms of use
     that an end user will see will be based on their browser preferences.

    - In the **Display name** box, enter `Contoso Terms of Use`.

    > **Note** - This is the title that users see when they sign in.

    - To require end users to view the terms of use prior to accepting them,
    set **Require users to expand the terms of use** to **On**.

    - To require end users to accept your terms of use on every device they
    are accessing from, set **Require users to consent on every
    device** to **Off**. Users may be required to install additional
    applications if this option is enabled.

     **Warning** - Consent on every device will require users to register
     each device with Microsoft Entra ID prior to getting access. It is a
     good practice to require this setting to On; however for the purpose
     of a cleaner lab, we are using Off.

    - If you want to expire terms of use consents on a schedule,
    set **Expire consents** to **On**. When set to On, two additional
    schedule settings are displayed.

    - Use the **Expire starting on** and the
    following **Frequency** settings to specify the schedule for terms of
    use expirations. Choose the date **6 months** from Today and Frequency **Monthly** and Duration before re-acceptance required (days) - **60**
 
    - Under **Conditional Access**, select Custom policy and then click on
    the Create button.

     ![computer Description automatically
 generated](./media/image16.png)

14. When the terms of use is created, you will automatically be
    redirected to the Conditional access policy page.

    - On the page, in the **Name** box, enter `Enforce ToU`.

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

    ![computer ](./media/image17.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

    ![computer ](./media/image18.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Select apps**. Under select, choose
  **None**. In the side pane, search for and select **Office 365** by
  selecting the check box near the app. Then choose **Select**.

    ![computer ](./media/image19.png)

- Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the **Grant** pane, select **Testing terms of
  use** and then select **Select**.

    ![computer ](./media/image20.png)

- Under **Enable policy**, select **On**.

    ![computer ](./media/image21.png)

- When complete, select **Create**.

    ![computer ](./media/image22.png)

### Task 2 - Log in as Joni Sherman

1.  Launch a new InPrivate browser window in your lab VM.

2. Navigate to `https://www.office.com`.

3.  When prompted, log in as **Joni Sherman**:

    Username – `jonis@`paste the Tenant name from the **Home/Resources**
    tab.

    Password – **paste the User Password from the Resources tab** and click on **Sign in**

    <font color=red>

    > **Note** - if the password does not work, then switch back to the tab with the Office 365 Tenant Admin login and navigate to `https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId` choose the User **Joni Sherman** and then **reset the password**. The new password need to be changed, you can use `Pa55w.rd98` as the new password. 

    </font>

4. Expand to View the **Terms of Use**.

     ![computer Description automatically
 generated](./media/image23.png)

5. Scroll down and click on the **Accept** button to complete the
    login.

    ![computer Description automatically
    generated](./media/image24.png)

6. Once you have accepted the Terms of Use agreement, you should be
    successfully signed in

    ![computer Description automatically
    generated](./media/image25.png)

## Exercise 3 – Microsoft Entra External Identities

### Task 1 – Configure basics

1.  Sign in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.

2. In the left menu, expand **Identity Governance** and
    select **Entitlement management**. Then from the sub menu, scroll
    down and select **Access packages**. Select **New access package**.

     ![computer Description automatically
 generated](./media/image26.png)

3. Enter the following details and then select **Next: Resource roles**.

    - Name – `External user package`

    - Description – `Access for external users pending approval`.

    - You can leave the **Catalog** drop-down list set to **General**.

    ![computer ](./media/image27.png)

4. Select **Groups and Teams**.

    ![computer ](./media/image28.png)

5. Tick the checkbox **See all Group and Team(s) not in the ‘General’
    catalog**. Then search for your group **External collaboration** and
    click on **Select** button.

    ![computer ](./media/image29.png)

6. In the role dropdown, select **Member**. Select **Next**: **Requests** tab.

    ![computer ](./media/image30.png)

    - In the **Users who can request access** section, select **For users not in your directory** and then select **All users (All connected organizations + any new external users)**.

    ![](./media/image31.png)

    - Require approval - **Yes** will be greyed out.

    - For **Require requestor justification**, leave this as **Yes**.

    - For **How many stages** leave this as **1**.

    ![computer Description automatically
  generated](./media/image32.png)

    - For **First Approver** scenario select **Choose specific approvers**.

    - Select **Add Approvers**.

     ![computer Description automatically
 generated](./media/image33.png)

- Choose Select **MOD Admin** user and then choose **Select**.

    ![computer ](./media/image34.png)

    - For **Decision must be made in how many days?** leave this as **14**.

    - For **Require approver justification** leave this as **Yes**.

    - Set **Enable new requests** to **Yes** to enable this access package
    to be requested as soon as it's created.

7. Select **Next: Requestor information** tab.

    ![computer ](./media/image35.png)

8. Select **Next: Lifecycle** tab.

    ![computer ](./media/image36.png)

- In the **Expiration** section, set **Access package assignment
  expire** to **Number of days**.

- Set **Assignment expire after** to **60** days. This field determines
  when your guest users will have to renew their access.

- Set **Require access review** to **No**.

- Select **Next: Rules**.

    ![computer ](./media/image37.png)

9. Select **Next: Review + Create**.

    ![computer ](./media/image38.png)

10. Select **Create**.

    ![computer ](./media/image39.png)

11. Stay on the same page and move on to the next task.

    ![computer ](./media/image39a.png)

### Task 2 – Create Access reviews for guest users

Access reviews can manage the access lifecycle. Microsoft Entra Identity
Governance provides an overview dashboard showing the status of access
reviews.

1.  In the left menu, expand **Identity Governance** and
    select **Entitlement management**. From the sub menu,
    select **Access reviews**. Select **+ New access review**.

    ![computer ](./media/image40.png)

2. Fill in the following information and select **Next: Reviews**.

    - Select what to review - Choose **Teams + Groups**

    - Review scope - Select **All Microsoft 365 groups with guest users**

    - Select user scope - **Guest users only**.

    ![computer ](./media/image41.png)

3. Fill in the following information and select the tab **Review +
    Create.**

    - Select reviewers - Choose **Group owners** 

    > **Note**: Guest users should not be allowed to review their own
    access as a good identity governance practice.

    - Enter a **Duration (in days)**, default is **3**, choose **Weekly**
    as **Review recurrence** and **today’s date** as a **Start date** for
    the review.

    ![computer ](./media/image42.png)

4. Select **Create** to create the new **Access review**.

    ![computer ](./media/image43.png)

5. The Access review should now appear in the list.
    ![computer ](./media/image42a.png)

## Exercise 4 – Manage the lifecycle of external users in Microsoft Entra Identity Governance settings

You can select what happens when an external user, who was invited to
your directory through an access package request being approved, no
longer has any access package assignments. This can happen if the user
relinquishes all their access package assignments, or their last access
package assignment expires. By default, when an external user no longer
has any access package assignments, they are blocked from signing in to
your directory. After 30 days, their guest user account is removed from
your directory.

1.  Sign in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.

2.  In the left menu, expand **Identity Governance** and
    select **Entitlement management**. From the sub menu,
    select **Settings**. Select **Edit**.

    ![computer ](./media/image44.png)

3. In the **Manage the lifecycle of external users** section, review
    the different settings for external users.

    - Set the **Block external user from signing in to this
      directory** to **Yes**.

    - Set **Remove external** user to **Yes**.

    - Set **Number of days before removing external user from this
      directory** to **0**.

    > **Note –** If the save button is not enabled, then switch the
      toggle to No and then Yes, then the Save button will be enabled.

    - If you’ve made any changes, select **Save**.

    ![computer ](./media/image45.png)

4. Stay on the same page and continue to the next exercise.

## Exercise 5 – Microsoft Entra roles using PIM

A Privileged role administrator can customize Privileged Identity
Management (PIM) in their Microsoft Entra organization, including
changing the experience for a user who is activating an eligible role
assignment. You must become familiar with configuring PIM.

Follow these steps to make a user eligible for an Microsoft Entra admin
role.

### Task 1 - Configure Microsoft Entra role settings

#### Step 1 – Open role settings

Follow these steps to open the settings for an Microsoft Entra role.

1.  Sign in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.

2.  In the left menu, expand **Identity Governance** and
    select **Privileged Identity management**. From the sub menu,
    select **Microsoft Entra roles.**

    ![computer ](./media/image46.png)

3. On the **Quick start** page, in the left navigation,
    select **Settings.** Review the list of roles and then,
    select **Compliance Administrator**.

    ![computer ](./media/image47.png)

4. Review the role setting details information. Stay on the same page
    and continue to the next step.

    ![computer Description automatically
    generated](./media/image48.png)

#### Step 2 – Require approval to activate.

If setting multiple approvers, approval completes as soon as one of them
approves or denies. You cannot require approval from at least two users.
To require approval to activate a role, follow these steps.

1.  In the **Role setting** details page, on the top menu,
    select **Edit**.

    ![computer ](./media/image49.png)

38. In the **Edit role setting – Compliance Administrator** page, select
    the **Require approval to activate** check box. Then select No
    **approver selected**.

    ![computer ](./media/image50.png)

39. In the **Select a member** pane, select the **Office 365 Tenant
    administrator** account, and then choose **Select**.

    ![computer ](./media/image51.png)

40. Once you have configured the role settings, select **Update** to
    save your changes.

    ![computer ](./media/image52.png)

41. Stay on the same page and continue to the next Task.

### Task 2 – Configure Microsoft Entra roles

#### Step 1 – Assign a role

With Microsoft Entra ID, a Global administrator can make permanent
Microsoft Entra admin role assignments. These role assignments can be
created using the Microsoft Entra admin center, the Azure portal, or
using PowerShell commands.

The Privileged Identity Management (PIM) service also allows Privileged
role administrators to make permanent admin role assignments.
Additionally, Privileged role administrators can make users eligible for
Microsoft Entra admin roles. An eligible administrator can activate the
role when they need it, and then their permissions expire once they’re
done.

Follow these steps to make a user eligible for a Microsoft Entra admin
role.

1.  In the left menu, expand **Identity Governance** and
    select **Privileged Identity Management**. Then select **Microsoft
    Entra roles.**

    ![computer ](./media/image53.png)

42. On the **Quick start** page, in the left navigation,
    select **Roles**. Then select **+ Add assignments.**

    ![computer ](./media/image54.png)

43. In the **Add assignments** page, on the **Membership** tab,
    select **Compliance Administrator** from the **Select
    role** dropdown.

    ![computer ](./media/image55.png)

44. Under **Select member(s)**, select **No members selected**.

    ![computer ](./media/image56.png)

45. In the **Select a member** pane, select **Abbi Skinner** and then
    select **Select**.

    ![computer ](./media/image57.png)

46. Select **Next**.

    ![computer ](./media/image58.png)

47. On the **Settings** tab, under **Assignment type**, review the
    available options. For this task, use the default setting.

48. Review the remaining settings and then select **Assign**.

    ![computer ](./media/image59.png)

#### Step 2 – Log in with Abbi Skinner

1.  Open the new tab in Edge browser using **InPrivate** mode and sign
    in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.

2.  In the sign in prompt, sign in using the following credentials and
    complete the authentication.

    Username – `Abbi@`paste the **Tenant name** from the
    **Resources** tab.

    - Password – `Pa55w.rd`

    > **Note** – You may be requested to do MFA registration, if so, proceed
    ahead and complete the MFA registration process

3. From the **Identity** menu, open **Users** and then select **All
    users**. Select **Abbi** in the list of users.

    ![computer ](./media/image60.png)

4. From the navigation, look for the **Assigned roles**.
    Select **Eligible assignments tab**.

    ![computer ](./media/image61.png)

5. Notice that the **Compliance Administrator** role is now available
    to Abbi.

    ![computer ](./media/image62.png)

6. Stay on the same page and continue to the next step.

#### Step 3 – Activate your Microsoft Entra roles.

When you need to assume any Microsoft Entra role, you can request
activation by opening **My roles** in Privileged Identity Management.

1.  Make sure you are signed into the **Microsoft Entra admin center**
    as **Abbi Skinner**.

2.  In the left menu, expand **Identity Governance** and
    select **Privileged Identity management**. From the sub menu,
    select **My roles.**

    ![computer ](./media/image63.png)

53. In the **My roles** page, review the list of **Eligible
    assignments**. In the **Compliance Administrator** role row,
    select **Activate**.

    ![](./media/image64.png)

54. In the **Activate – Compliance Administrator** pane, select
    **Activate** tab. In the **Reason** box, enter the `This is my
    justification for activating this role`. Select **Activate**.

    ![computer ](./media/image65.png)

    > **Important Note** - the principle of least privilege, you should only
    activate the account for the amount of time you need it. If the work
    needed to be done, only takes 1.5 hours, then set the duration to two
    hours. Similarly, if you know that you won’t be able to do the work
    until after 3pm, choose a Custom activation time.

5. You will see the notification that your request is pending for
    approval.

    ![computer ](./media/image66.png)

#### Step 4 – Approve the role request

1.  Switch back to the tab logged in with **Office 365
    tenant credentials**. or open a New edge browser in a normal mode and navigate to `https://entra.microsoft.com` sign in using your **Office 365
    tenant credentials**.

2.  In the left menu, expand **Identity Governance** and
    select **Privileged Identity management**. From the sub menu,
    select **Microsoft Entra roles.**

    ![computer ](./media/image46.png)

3.  Select **Approve Request**. You will be able to see the request from
    **Abbi Skinner** under **Requests for role activations**. Select the
    request. Then select **Approve**.

    ![computer ](./media/image67.png)

4.  In the **Justification** box, enter the `This is my
    justification for activating this role`. Select **Confirm**.

    ![computer ](./media/image68.png)

5.  The role of Compliance Administrator has now been assigned to Abbi
    Skinner for next 8 hours.

#### Step 5 – Assign a role with restricted scope.

For certain roles, the scope of the granted permissions can be
restricted to a single admin unit, service principal, or application.
This procedure is an example if assigning a role that has the scope of
an administrative unit.

1.  Sign in to `https://entra.microsoft.com` using your **Office 365
    tenant credentials**.
     
2.  In the left menu, expand **Identity Governance** and
    select **Privileged Identity management**. From the sub menu,
    select **Microsoft Entra roles.**

    ![computer ](./media/image46.png)

3. Select **Roles**. In the Roles page, on the top menu, select **+ Add
    assignments.**

    ![computer ](./media/image69.png)

4. In the Add assignments page, select the **Select role** menu and
    then select **User administrator.** Select the **Scope type** menu
    and review the available options. For now, you will use
    the **Directory** scope type.

    ![computer ](./media/image70.png)

5. As you did when assigning a role without a restricted scope, you
    would add members and complete the settings options. For now,
    select **Cancel**.

    ![computer ](./media/image71.png)

6. Stay on the same page and continue to the next step.

### Step 6 – Update or remove an existing role assignment.

Follow these steps to update or remove an existing role assignment.

1.  In the left sub-navigation, select **Assignments**.

2. In **Assignments** list, for **Compliance Administrator**, review
    the options in the **Action** column.

    ![computer ](./media/image72.png)

    - Select **Update** and review the options available in the Membership
    settings pane. When complete, close the pane.

    - Select **Remove** to remove the assignment.

## Summary:

In this lab we focused on creating and managing a catalog of resources,
adding terms of use, and implementing acceptance reporting, configuring
basics for external identities, conducting access reviews for guest
users, and managing the lifecycle of external users. Additionally,
learnt to configure Microsoft Entra roles using Privileged Identity
Management (PIM) and understand the role activation process with
approval requirements, role assignment, activation, approval, and
updating or removing existing role assignments.