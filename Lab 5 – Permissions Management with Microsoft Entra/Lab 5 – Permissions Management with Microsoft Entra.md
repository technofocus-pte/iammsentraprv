# Lab 5 – Permissions Management with Microsoft Entra

## Exercise 1 – Assigning permissions on Subscription for Testing

### Task 1 – Create Security Groups and Manage Identity

1.  Select **LON-CL1** from the Virtual machines list on the Resources
    tab of your lab interface. Login to the VM using the using the
    password given on the **Home/Resources** tab of your environment.

2.  Open the Edge browser and login to the Azure
    Portal `https://portal.azure.com`. If prompted for
    credentials enter your **Office 365 tenant credentials**.

3.  In the Azure Portal search box type `managed identities` and
    click on **Managed Identities**.

    ![](./media/image1.png)

4.  Click on **Create**.

    ![](./media/image2.png)

5.  On the **Create User Assigned Managed Identity** page, provide the
    below details

    - Subscription – **Azure Pass – Sponsorship**

    - Resource group – click on **Create new** then provide the name
    – `RG4PMtest` and click **OK**.

    - Region – **WestUS**

    - Name – `MI4pmtesting`

    - Click on **Review + create**.

    ![](./media/image3.png)

6.  Once the **Validation is passed**, click on **Create**.

    ![](./media/image4.png)

7.  The **Deployment** will finish in few seconds.

    ![](./media/image5.png)

8.  Click on the **Azure Portal** menu and then select **Microsoft Entra
    ID**.

    ![](./media/image6.png)
    
9.  On the **Microsoft Entra ID** page click on **Groups**.

    ![](./media/image7.png)

10. Click on **New group**.

    ![](./media/image8.png)

11. On the **New Group** page, provide the below details.

    - Group type – **Security**

    - Group name – `SGLevel1`

    - Group description – `Security Group 1 for Level 1 Users`

    - Membership type - **Assigned**

    - Members – click on **No members selected** – choose members
      – `Dante` and `Federico` and click on **Select**.

    ![](./media/image9.png)

12. Click on **Create** button.

    ![](./media/image10.png)

13. Repeat the above steps to create another Group with below details

    - Group type – **Security**

    - Group name – `SGLevel2`

    - Group description – `Security Group 2 for Level 2 Users`

    - Membership type – **Assigned**

    - Members – `Huong` and `Logan`

    ![](./media/image11.png)

14. Once the **Groups** are created the list should appear as shown in
    below image

    ![](./media/image12.png)

### Task 2 – Create and register a Web App

1.  In the Azure Portal search box type `webapp` and then click
    on **App Services**.

    ![](./media/image13.png)

2.  Click on **+ Create Web App** to create app service.

    ![](./media/image14.png)

3.  On the **Create Web App** page, provide the below details

    - Subscription – **Azure Pass - Sponsorship**

    - Resource group – **RG4PMtest**

    - Name – `wa4pmtestxxxxxx` [ substitute **xxxxxx** with random
      number]

    - Publish – **Code**

    - Runtime stack – **.Net 8 (LTS)**

    - Operating System – **Windows**

    - Region – **West US**

    - Click on **Review + create**

    ![](./media/image15.png)

4.  Click on **Create**.

    ![](./media/image16.png)

5.  Wait for the deployment to complete, it will be finished in few
    seconds then click on **Go to resource**.

    ![](./media/image17.png)

6.  On the **Overview** page, note down the **Default domain** or
    the **App service** into **Notepad** file.

    ![](./media/image18.png)

7.  Click on the **Azure Portal** menu and then select **Microsoft Entra
    ID**.

    ![](./media/image6.png)

8.  Click on **App registrations** under Manage, the click on **New
    registration**.

    ![](./media/image20.png)

9.  On the **Register an application** page, provide the below details

    - Name – `TestApp1`

    - Supported account types – **Accounts in this organizational
      directory only (Contoso only - Single tenant)**

    - Redirect URI (optional) – **Web** – **domain of the Web App
      created** (`https://` apped the **Default domain** name noted in the previous step)

    - Click on **Register**

    ![](./media/image21.png)

10. The newly create App registration should appear in the List, as
    shown in below image.

    ![](./media/image22.png)

### Task 3 – Configure Permissions on the Subscription

1.  In the **Azure Portal**, search box type `subscriptions` and then click
    on **Subscriptions**.

    ![](./media/image23.png)

2.  From the list of **Subscriptions** select the **Azure Pass –
    Sponsorship**.

    ![](./media/image24.png)

3.  On the **Azure Pass – Sponsorship** page click on **Access control
    (IAM)**, then click on **+ Add** drop-down and select **Add role
    assignment**.

    ![](./media/image25.png)

4.  On the **Add role assignment** page, under the **Privileged
    administrator roles** tab select **Contributor** and then click
    on **Next**.

    ![](./media/image26.png)

5.  On the **Members** tab, click on **+ Select members**, then
    choose `Beatrise` and `Lara` and then click on
    the **Select** button.

    ![](./media/image27.png)

6.  Click on **Review + assign** button.

    ![](./media/image28.png)

7.  Click on **Review + assign** button again.

    ![](./media/image29.png)

8.  You should get the notification as shown in below image.

    ![](./media/image30.png)

9.  Click on the **Role assignments** tab to view the role assigned in
    the previous step. We can see the **Users** listed to whom
    the **Contributor** role was assigned.

    ![](./media/image31.png)

10. Now repeat the above steps to assign the below roles to the
    listed **Users**.

    - Automation Contributor - `Augusta Moore` and `Bing` (Service
      Principal)

    - Data Box Reader – `Anastasia Rojas`

    - Key Vault Contributor – `Kasey Shepard`

    - Owner – `Maj Hojski` - On the **Conditions** tab select the **Allow user to assign all roles (highly privileged)** option.

    - Security Admin – `SGLevel1` and `Viva Engage` (Service
      Principal)

    - Reader – `SGLevel2`

    - Contributor – `TestApp1` ( Web App created in Task 2)

11. On the **Azure Pass – Sponsorship** page click on **Access control
    (IAM)**, then click on **+ Add** drop-down and select **Add role
    assignment**.

    ![](./media/image25.png)

12. On the **Add role assignment** page, under the **Privileged
    administrator roles** tab select **Contributor** and then click
    on **Next**.

    ![](./media/image26.png)

13. On the **Members** tab, under **Assign access**, select **Managed
    Identity**.

14. Click on **Select members**, under Managed Identity,
    select **User-assigned managed identity (1)**,
    choose **MI4pmtesting** and then click on the **Select** button.

    ![](./media/image32.png)

15. Click on **Review + assign**.

    ![](./media/image33.png)

16. Click on **Review + assign** again.

    ![](./media/image34.png)

17. We have set the Roles for testing on the Subscription

18. Click on the **Role assignments** tab, to see the updates as shown
    in below image

    ![](./media/image35.png)

## Exercise 2 – Enabling Permissions management for your Organization’s
Tenant

1.  Browse to `https://entra.microsoft.com` and sign in using
    the **Office 365 tenant credentials**.

2.  On the left-hand menu, select the link to the **Permissions
    Management** portal. Then select **Launch portal**.

    ![](./media/image36.png)


3.  The **Permissions Management** will be launched in a new tab. If
    asked, use the **Office 365 tenant credentials** to sign into the
    portal.

4.  You will get the error message “**Your onboarding Failed. Please try
    again.**” as shown in below image.

    ![](./media/image37.png)

5.  Click on the link **aka.ms/TryPermissionsManagement**.

    ![](./media/image38.png)

6.  On the **Microsoft Entra Permissions Management Trial** page click on the **Continue** button.

    ![](./media/image39.png)

8.  On the **Checkout – confirm your order** page click on **Try
    now** button

    ![](./media/image41.png)

9.  On the **Order receipt** page, click on **Continue** button.

    ![](./media/image42.png)

10. You should now be re-directed to the **Microsoft 365 admin center**.

    ![](./media/image43.png)

11. Switch back to the browser tab with the **Microsoft Entra admin
    center** and on the lefthand menu, select the link to
    the **Permissions Management** portal. Then select **Launch
    portal**.

    ![](./media/image36.png)

12. You should receive the message as shown in the below image

    ![](./media/image44.png)

13. Now the **Permissions Management** portal will show the available
    options.

    ![](./media/image45.png)

14. Keep the tab open and continue to the next exercise.

> **Note** - If you receive error **permissions management No access
Access required. Contact your global administrator.** then log out from all tabs and login again to the **Microsoft Entra Portal** `https://entra.microsoft.com` then open the **Permissions Management** portal. 

## Exercise 3 – Configure settings for data collection.

1.  Once in the **Permissions Management** portal, click on the **Data
    Collectors** tab, select your authorization system type
    as **Azure** for Microsoft Azure, then click on **Create
    Configuration**

    ![](./media/image46.png)

2.  Under the **Manage Authorization Systems** select
    the **Automatically Manage** option

    ![](./media/image47.png)

3.  Scroll down under the **Next Step: Create Role Assignments** under
    the **Azure Command-Line** copy both commands using the copy link
    and paste in Notepad.

    ![](./media/image48.png)

4.  In another tab, open the Azure Portal by navigating
    to `https://portal.azure.com`. If prompted for credentials then
    enter the **Office 365 tenant credentials**.

5.  In the Search type `management` and select **Management
    groups**.

    ![](./media/image49.png)

6.  On the **Overview** page of Management Groups, click on **+ Create**.

    ![](./media/image50.png)

7.  On the **Create management group** tab, provide the following
    details and select **Submit**.

    - Management group ID – `MgmtGrp4Entra1`

    - Management group display name – `Management Group for Entra 1`

    ![](./media/image51.png)

8.  Once the Management group is created it will be listed as shown in
    below image.

    ![](./media/image52.png)

9.  Note down the **Management Group ID** and **Subscription ID** from
    here as it would be used in upcoming steps for enabling data
    collection for Permissions Management.

    ![](./media/image53.png)

10. The Azure Command line copied should appear as shown in below
    image  
    ![](./media/image54.png)

11. Launch the **Azure Cloud Shell** as shown in the image below

    ![](./media/image55.png)

12. Choose **PowerShell** on the **Welcome to Azure Cloud Shell
    screen**.

    ![](./media/image56.png)

13. On the **Getting started** screen choose **Mount storage account** and choose the Storage account subscription as - Azure Pass - Sponsorship then click
    on **Apply** button.

    ![](./media/image57.png)

13. On the **Mount storage account** screen choose **We will mount a storage account for you** then click on **Next** button.

    ![](./media/image57a.png)


14. Now run the below commands from the Notepad in Azure CLI ensure that
    you have substituted your **Subscription ID**.

    `az role assignment create --assignee
    b46c3ac5-9da6-418f-a849-0a07a10b3c6c --role "Reader" --scope
    /subscriptions/<subscriptionID>`

    ![](./media/image58.png)

15. Now replace the role from **Reader** to **User Access
    Administrator** in the command and run the command in Cloud Shell.

    `az role assignment create --assignee
    b46c3ac5-9da6-418f-a849-0a07a10b3c6c --role "User Access
    Administrator" --scope /subscriptions/<subscriptionID>`

    ![](./media/image59.png)

16. Run the below Commands.

    `az role assignment create --assignee
    b46c3ac5-9da6-418f-a849-0a07a10b3c6c --role "Reader" --scope
    "/providers/Microsoft.Management/managementGroups/MgmtGrp4Entra1"`

    ![](./media/image60.png)
    
    `az role assignment create --assignee
    b46c3ac5-9da6-418f-a849-0a07a10b3c6c --role "User Access
    Administrator" --scope
    "/providers/Microsoft.Management/managementGroups/MgmtGrp4Entra1"`

    ![](./media/image61.png)

17. Once all the commands have been run successfully as shown in the
    images, switch back to the tab with the **Permissions
    Management** portal opened.

18. Click on **Verify Now & Save**.

    ![](./media/image62.png)

    ![](./media/image62a.png)

19. Monitor the **Status** of the **Data Collector – Azure**, it would
    be showing as **Discovering** as shown in below image.

    ![](./media/image63.png)

20. Click on **Reload** to refresh the status, the **Status** should now
    be updated to **Consented**.

    ![](./media/image64.png)

21. Click on **Reload** after 10-15 minutes, then the status should be
    updated to **Onboarded** and **Authorization Systems
    Status** – **ONLINE – 1** as shown in below image

    ![](./media/image65.png)

    <font color=red>

    > **Note** - It is is taking longer than 10-15 minutes, then click on the 3 dots and choose the **Rediscover** option. Then click on the **Reload** button after few minutes.

    ![](./media/image65a.png)

    </font>

22. Keep the tab open and continue to the next exercise.

## Exercise 4 – Start collecting data from an authorization system.

1.  Click on the **Authorization Systems** tab, and then
    select **Azure** authorization system type.

    ![](./media/image66.png)

    > **Note** – It is important that the Controller Status should
    be **Enabled**

2.  Select the ellipses (**…**) at the end of the row in the table and
    then click on **Collect Data**.

    ![](./media/image67.png)

3.  A message displays to confirm data collection has started as shown
    in below image

    ![](./media/image68.png)

4.  Stay on the same page and continue to the next exercise.

## Exercise 5 – View key statistics and data about your authorization system

Permissions Management provides a summary of key statistics and data
about your authorization system regularly.

### Task 1 – Components of the Permissions Management Dashboard

1.  While in the Permissions Management Portal, click on **DASHBOARD**.

    ![](./media/image69.png)

2.  Review the Dashboard to gather details.

    - Authorization system types – **Azure**

    - Authorization System – Displays a List of accounts and Folders in the
    selected authorization system you can access. **Review** and
    press **Apply**.

    ![](./media/image70.png)

    - Highest PCI change: Displays a list of your accounts and information
    about the PCI and Change in the index over the past 7 days.

    ![](./media/image71.png)

1.  Additionally, the report can be downloaded by clicking on the
    Download link, the file will be emailed.

    ![](./media/image72.png)

2.  You can open another tab and login to `https://outlook.office365.com` with the Office 365 Tenant account credentials that was used for **Permissions Management** portal. It will be emailed as **All Files.zip**.

    ![](./media/image73.png)


3.  You can extract and view the Excel file as shown in the below image.

    ![](./media/image74.png)

4.  Review the **Identity** section for findings as shown below, you can
    click on each to get more information.

    ![](./media/image75.png)

5.  Select **2 Super Users \ 2 Azure Pass - Sponsorship** to get the
    details.

    ![](./media/image76.png)

    ![](./media/image77.png)

6.  The details would appear as shown in below images.

    ![](./media/image78.png)

7.  Back on the Dashboard page, the **Resources** will show a summary of the **Findings**.
    Select **Microsoft managed keys**.

    ![](./media/image79.png)
   
8.  Select the listed **1 Azure Pass – Sponsorship**.

    ![](./media/image80.png)

9.  It will show the resource details.

    ![](./media/image81.png)

10. You can check the same details for the **Open Network Security Groups** listed under **Findings**

    ![](./media/image81a.png)

11. Keep the tab open and continue to the next exercise.

### Task 2 – The PCI heat map

The **Permission Creep Index** heat map shows the incurred risk of users
with access to high-risk permissions.

1.  PCI Heat map shows 1 bubble for our tenant with the number 13.

    ![](./media/image82.png)

2.  Click on the bubble to see more details, here you can
    see **Users**, **Applications** and **Managed Identities** listed
    with different level of the Permissions.

    ![](./media/image83.png)

    - Permissions are classified as high, medium, and low.

    - **High (displayed in red)** – The score is between 68 and 100. The
    user has access to many high-risk permissions they aren't using and
    has high resource reach.

    - **Medium (displayed in yellow)** – The score is between 34 and 67. The
    user has access to some high-risk permissions that they use or have
    medium resource reach.

    - **Low (displayed in green)** – The score is between 0 and 33. The user
    has access to few high-risk permissions. They use all their
    permissions and have low resource reach.

3.  Click on 11 Total Users to display the details about the users.

    ![](./media/image84.png)

    ![](./media/image85.png)

4.  Select **Maj Hojski** User identity to gather more information about
    the Permission.

    ![](./media/image86.png)

5.  As you can see in the above image the user is the **Owner** of
    the **Subscription**.

    ![](./media/image87.png)

6.  Keep the tab open and continue to the next exercise.

## Exercise 6 – Explore the Analytics dashboard

Analytics dashboard provides analytic information for Amazon Web
Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).

1.  While in the **Permissions Management** portal, click
    on **ANALYTICS** tab. Review the information given on the dashboard.

    ![](./media/image88.png)

2.  From the drop-down list at the top of the screen ensure
    that **Users** is selected.

    ![](./media/image89.png)

3.  To form the query, provide the below details

    - Authorization System Type – **Azure**

    - Authorization System – **Azure Pass - Sponsorship**

    - Identity Type – **User**

    - Identity Subtype – **All**

    - Identity State – **All**

    - Identity Filters - **Risky**

    - Identity PCI State – **All**

    - Task Type – **High Risk Tasks**

    - Task Sub Type - **All**

    - Click on **Apply**

    ![](./media/image90.png)

4.  The result of the above query will be displayed.

    ![](./media/image91.png)

5.  From the drop-down list at the top of the screen select **Active
    Tasks**.

    ![](./media/image92.png)

6.  To form the query, provide the below details

    - Authorization System Type – **Azure**

    - Authorization System – **Azure Pass - Sponsorship**

    - Task Type – **High Risk Tasks**

    - Click on **Apply**

    ![](./media/image93.png)

7.  The result of the above query will be displayed.

    ![](./media/image94.png)

8.  You can expand each task to gather more details for the same.

    ![](./media/image95.png)

9.  Keep the tab open and continue to the next exercise.

## Exercise 7 – Explore the Remediation dashboard

The Remediation dashboard in Permissions Management provides an overview
of roles/policies, permissions, a list of existing requests for
permissions, and requests for permissions you have made.

### Task 1 – View the Remediation Roles/Policies

1.  While still in the Permissions Management portal click
    on **REMEDIATION** tab.

    ![](./media/image96.png)

2.  Ensure that the **Roles/Policies** sub-tab is selected, then to
    query the Roles create the query with the below details.

    - Authorization System Type – **Azure**

    - Authorization System – **Azure Pass - Sponsorship**

    - Role Type – **All**

    - Role Status – **Assigned**

    - Role Usage – **All**

    - Click on **Apply**

    ![](./media/image97.png)

1.  From the displayed result click on the **Contributor** role.

    ![](./media/image98.png)

2.  View the listed **Users**.

    ![](./media/image99.png)

3.  Click on **Enterprise Applications (1)** to display to which
    application the role has been assigned. We can see that
    the **Role** has been assigned for the **Application – TestApp1**.

    ![](./media/image100.png)

4.  The result can be exported to **CSV** by clicking on **Export
    CSV** button.

    ![](./media/image101.png)

5.  An email with the exported **CSV** will be delivered.

    ![](./media/image102.png)

    ![](./media/image103.png)

6.  Stay on the same page and continue to the next task.

### Task 2 – View Remediation Permission

1.  While still in the **Permissions Management** portal click
    on **REMEDIATION** tab.

2.  Ensure that the **Permissions** sub-tab is selected, then to query
    the Permissions create the query with the below details.

    - Authorization System Type – **Azure**

    - Authorization System – **Azure Pass - Sponsorship**

    - Search for – from the drop-down select **User**

    - User Status – **Any**

    - Permission Creep Index – **High**

    - Task Usage – **Any**

    - Click on **Apply**

    ![](./media/image104.png)


3.  From the results pane, select **Beatrise Jaunzema** user.

    ![](./media/image105.png)

4.  Once the **User** has been selected, the details will be listed, the
    reason this user is listed is due to the High permission role
    – **Contributor** which gives the user the **High Permission Creep
    Index**.

    ![](./media/image106.png)

5.  You have additional button to make changes to the **Role** for the
    user, make sure the user **Beatrise Jaunzema** is selected and then click
    on **Remove Role**.

    ![](./media/image107.png)

6.  On the **Remove Role** window click on
    the **Contributor** role **+** sign, it will move to the **Selected
    Roles** column.

    ![](./media/image108.png)

7.  Then click on **Submit**.

    ![](./media/image109.png)

8.  On the **Confirmation** prompt select, **Execute**.

    ![](./media/image110.png)

9.  You should get the notification as shown in below image. A request to remove the Role has been initiated.

    ![](./media/image111.png)

10. Keep the tab open for the next exercise.


### Task 3 – Setting selections for requests

The **Settings** subtab provides the options to configure **Request
Role/Policy Filters**, **Request Settings**.

1.  Still the browser tab to display the **Permissions
    Management** portal click on **REMEDIATION** tab.

2.  Ensure that the **Settings** sub-tab is selected, also ensure
    that **Authorization System Type** is set
    to **Azure** and **Authorization System** is set to **Azure Pass –
    Sponsorship**, select **Apply**.

    ![](./media/image113.png)

3.  Click on the **Create Filter** button.

    ![](./media/image114.png)

4.  On the **Create Filter** window, provide the below details.

    - Filter Name – `Reader role`

    - Authorization System Type – **Azure**

    - Authorization System – **Azure Pass - Sponsorship**

    - Select a type – **Role Name** – Contains – `Reader` click on
      the **+** sign

    - Click on **Save**

    ![](./media/image115.png)

5.  You should get the notification as shown in below image.

    ![](./media/image116.png)

    ![](./media/image117.png)

6.  Click on the **Request Settings** sub-tab, on this sub-tab
    additional options for the request can be set like.

    - Duration

    - OTP Settings

    ![](./media/image118.png)

    - Set the Request Duration limit to **30 days** – **720** **Hours**

    - Turn off the OTP setting for Request: **For an approver to Approve,
    Reject and Cancel requests**.

    - Click on the **Save** button.

    ![](./media/image119.png)

7. You should get the notification as shown in below image.

    ![](./media/image120.png)

8. Keep the tab open and continue to the next exercise.

## Exercise 8 – Manage users and groups with the User management dashboard

From the User Management Portal, we can assign Groups
with **Admin**, **Viewer, Controller** and **Approver** to the
available *Authorization System Types* and *Authorization System*
and *View currently active Users with Permissions on the Authorization
System*.

1.  Click on the logged in user initials on the top right corner and
    then select **User Management**.

    ![](./media/image121.png)

2.  The **Group** tab would be shown, here we can assign permission to
    the security group we had created earlier. Click on **Create
    Permission**.

    ![](./media/image122.png)

3.  On the **Set Group Permission** window provide the below details.

    - Group Name – type **sgl** and then select **SGLevel1** security
      group

    - Permission – **Custom**

    - Click on **Next**

    ![](./media/image123.png)

4.  Click on the check box for Viewer for **Azure Pass –
    Sponsorship** and the click on **Next**. Select **Save**.

    ![](./media/image124.png)

5.  Then select **Save**.

    ![](./media/image125.png)

6.  This above action would give the members of the security group
    – **SGLevel1** the Viewer Permission for **Azure Pass –
    Sponsorship** subscription for the **Permissions
    Management** portal.

    ![](./media/image126.png)

7.  Open the new tab in Edge browser using **InPrivate** mode and login
    to **Permission Management Portal** using the link
    – `https://pm.cloudknox.io/portal`

8.  When prompted for credential enter the below

    - Username – `Dante@` paste the Tenant name from the
      Resources tab

    - Password – Paste the password from the **Home/Resources** tab 
    
9.  You should be able to login successfully and have
    only **Viewer** access to the **Portal**.

    ![](./media/image127.png)

10. Switch back to the Edge browser tab that has **Office 365 Tenant
    Admin** logged in with the **User Management** page open. Click
    on **Create Permission**.

    ![](./media/image128.png)

11. On the **Set Group Permission** window provide the below details.

    - Group Name – type **sgl** and then select **SGLevel2** security
      group

    - Permission – **Admin for selected Authorization System Types**

    - Click on **Next**

    ![](./media/image129.png)

12. Click on the check box for **Viewer,
    Controller** and **Approver** for **Azure** and then click
    on **Next**.

    ![](./media/image130.png)

13. Click on **Save**.

    ![](./media/image131.png)

14. This above action would give the Members of the Security Group
    – **SGLevel2** the **Admin access** for all Azure Subscriptions in
    the **Permissions Management** portal.

    ![](./media/image132.png)

15. Close and reopen Edge browser using **InPrivate** mode and login
    to **Permission Management Portal** using the link
    – `https://pm.cloudknox.io/portal`

16. When prompted for credential enter the below

    - Username – `Logan@` paste the Tenant name from the
      Resources tab

    - Password – Paste the password from the **Home/Resources** tab 

17. You should be able to login successfully and have the assigned
    access to the Portal.

    ![](./media/image133.png)

18. Switch back to the Edge browser tab that has **Office 365 Tenant
    Admin** logged in with the **User Management** page open and review
    the **Permissions** for the **Groups.**

    ![](./media/image134.png)

19. Click on the **Users** tab.

    ![](./media/image135.png)

20. On the **Users** tab individual users with **Permissions** on
    the **Permissions Management** portal are listed.

21. Click on the ellipses for the User MOD Administrator then
    select **View Permissions**.

    ![](./media/image136.png)

22. Notice that we can only view the permissions, click on **Next**.

    ![](./media/image137.png)

23. Click on **Close**.

    ![](./media/image138.png)

24. Keep the tab open and continue to the next exercise.

## Exercise 9 – Create a rule in the Autopilot dashboard

The **Autopilot** dashboard in Permissions Management provides a table
of information about Autopilot rules for administrators.

1.  Click on the **AUTOPILOT** tab. You will notice that we do not have
    any rules created by default. Click on **New Rule**.

    ![](./media/image139.png)

2.  On the New Rule windows provide the name as `Rule1` select the
    Rule – **Remove Permissions for Unused Applications/Managed
    Identities** and then select **Next**.

    ![](./media/image140.png)

    > **Note** – Currently there is only 1 rule available in the Portal
    selection.

3.  On the Authorization Systems sub-tab, select **Azure Pass -
    Sponsorship**.

    ![](./media/image141.png)

    > **Note** – Ensure that the Status is **Online**, and Controller
    is **Enabled**, for the Autopilot to function correctly.

4.  Click on the **Mode** tab and review the setting.

    ![](./media/image142.png)

5.  Navigate to the **Configure** tab and specify the criteria to
    be **Unused is 60 Days**, then Select **Save** button.

    ![](./media/image143.png)

6.  Now you can see the newly created **Rule** listed and then Generate
    and View recommendations.

    ![](./media/image144.png)

7.  Select the rule and then select on **Generate Recommendations**.

    ![](./media/image145.png)

    ![](./media/image146.png)

10. As this is a test environment, we have no accounts that have been
    idle for over 60 days, but in actual environment this would be very
    helpful to remove unused permissions.

    ![](./media/image150.png)

**You have completed all the Tasks in this lab.**
