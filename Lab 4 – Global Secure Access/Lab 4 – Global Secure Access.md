# Day 3 – Lab 4 – Global Secure Access​

## Objective:

I this lab we will configure Microsoft Entra Private Access and
Microsoft Entra Internet Access. We will then create conditional
policies using them and test them using the credentials of Joni Sherman.

**Note:** You may be asked for Multifactor authentication in the lab
when we log in as a user. Please make sure you have gone through
Exercise 4 in lab 1 to be able to use the authenticator app on your
phone.

## Exercise 1 – Prerequisites

### Task 1 – Register your VM with Microsoft Entra ID 

For GSA we need to install the clients on our VM. For that we will have
to register our Lab VM to the Contoso’s Entra ID.

1.  Open windows **Setting** on your VM.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Go to **Accounts** \> **Access work or school**. Click on
    **Connected to ADATUM AD domain** to expand it and the click on the
    **Disconnect** button.

![](./media/image2.png)

3.  On the prompt, click on Yes button.

    ![](./media/image3.png)

4.  On the Disconnect from the Organization window click on
    **Disconnect** button.

    ![](./media/image4.png)

5.  On the Enter alternate account info, provide the below details and
    click on the OK button.

    1.  Username – **+++.\Admin+++**

    2.  Password - **+++Pa55w.rd+++**

        ![](./media/image5.png)

6.  Click on the **Restart now** button when prompted to Restart your PC

    ![](./media/image6.png)

7.  Once the LON-CL1 is restarted login to the VM using the below
    credentials.

    1.  Username – **+++.\Admin+++**

    2.  Password - **+++Pa55w.rd+++**

8.  Waif for the profile to be created. Right-click on the Start Menu
    and click on **Settings**

    ![](./media/image7.png)

9.  Click on Accounts then select **Access work or school account**,
    click on **+ Connect**.

> ![](./media/image8.png)

10. In the **Set up a work or school account** prompt, click on **Join
    this device to Microsoft Entra ID**.

> ![](./media/image9.png)

11. In the sign in prompt, sign in using the following credentials.

    1.  Username – **+++jonis@+++paste the Tenant name from the
        Resources tab.**

    2.  Password – **paste the User Password from the Resources tab**
        and click on **Sign in**

![](./media/image10.png)

12. Press **Join** in the prompt **Make sure this is your
    organisation**.

![](./media/image11.png)

13. Once done you will see a confirmation window **You’re all set!**.
    Click on **Done**.

![](./media/image12.png)

14. Once again near **Access work or school**, click on **Connect**.

15. In the sign in prompt, sign in using the following credentials.

    1.  Username – **+++jonis@+++paste the Tenant name from the
        Resources tab.**

    2.  Password – **paste the User Password from the Resources tab**
        and click on **Sign in**

16. It will take a couple of seconds to sign in, click on the **Got it**
    button.

    ![](./media/image13.png)

17. You should be able to see 2 connections as shown in below image.

    ![](./media/image14.png)

18. Restart the VM. Make sure you do not shut it down.

19. Select the **LON-CL1** VM and on the user screen select **Other
    user**.

20. Enter your following credentials and log in to the VM.

    1.  Username – **+++jonis@+++paste the Tenant name from the
        Resources tab.**

    2.  Password – **paste the User Password from the Resources tab**
        and click on **Sign in**

> .

![](./media/image15.png)

21. You may be prompted to do MFA registration, complete the MFA
    registration followed by Setting the **PIN**. Set the PIN as
    **+++123654+++**.

22. The next exercises i.e. Exercise 2 and 3, should be performed under
    this user only.

### Task 2 – Activating Traffic Forwarding Profiles

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**. If you are automatically
    logged in with Joni Sherman, log out and login again with the Office
    365 Tenant Admin credentials.

    ![](./media/image16.png)

&nbsp;

1.  On the lefthand menu, under **Global Security Access select Get
    Started**. Then select **Activate** under step 3.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

2.  Once done, select **Get Started** under step 3.

![](./media/image18.png)

3.  From the left navigation, expand Global Secure Access and from the
    connect dropdown, select **Traffic Forwarding**. Select the check
    box near **Microsoft 365 access profile.**

![A screenshot of a computer Description automatically
generated](./media/image19.png)

4.  Select **OK** on the prompt.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

6.  Do the same for **Private access profile** and **Internet access
    profile**.

    ![](./media/image21.png)

    ![](./media/image22.png)

## Exercise 2 – Configuring Microsoft Entra Internet Access

### Task 1 – Download and install the client to your VMs

The most current version of the Global Secure Access Client can be
downloaded from the Microsoft Entra admin center.

1.  From the navigation bar, select **Global Secure Access
    (Preview)** \> **Connect** \> **Client Download**. Select **Download
    Client**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

5.  Once downloaded, select Open **file to** run the installer and
    install the client in your VM.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

6.  Accept the terms and conditions and select **Install**.

![](./media/image25.png)

7.  Select **yes** on the prompt.

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

8.  Let the installation complete. Once done select **Close**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

9.  You will be asked to sign into the client. Use the following
    credentials to log in to the client.

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**

![A screenshot of a computer Description automatically
generated](./media/image28.png)

10. Once done, select the arrow on the bottom right corner and then
    hover on the small globe sign. You will see that the client is now
    connected.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

11. Right click on the icon and select **Advanced diagnostics**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

12. For the prompt select **Yes**.

![A screenshot of a computer error Description automatically
generated](./media/image31.png)

13. Under the **Hostname acquisition** select **Start collecting**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

14. After few minutes the Data should start appearing as shown in below
    image.

    ![](./media/image33.png)

15. Under the **Traffic** select **Start collecting**.

![A screenshot of a computer Description automatically
generated](./media/image34.png)

16. After few minutes the Data should start appearing as shown in below
    image.

    ![](./media/image35.png)

17. Stay on the same VM and complete the following Task.

### Task 2 – Enable Tenant restrictions

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**.

2.  Browse to **Global Secure Access (preview)** \> **Global settings**
    \> **Session management**. Under **Adaptive Access**, toggle the
    **Enable Global Secure Access signaling in Conditional Access**,
    button to **ON**. Then select **Save**.

![](./media/image36.png)

## Exercise 3 – Configuring Microsoft Entra Private Access

### **Task 0 – Create a Windows Server 2019**

1.  While still on LON-CL1, in a new tab navigate to the Azure portal
    **+++<https://portal.azure.com>+++** login using the **Office 365
    Tenant credential**.

2.  From the Portal menu or from the **Home** page, select **Create a
    resource**.

    ![](./media/image37.png)

3.  Select **Create** under **Virtual Machines**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  Enter these values for the virtual machine:

[TABLE]

> ![](./media/image39.png)

![](./media/image40.png)

5.  Click on **Review + create**.

6.  Review the settings on the summary page, and then select **Create**.

> ![](./media/image41.png)

7.  Once the deployment is complete select **Go to resource**.

> ![](./media/image42.png)

8.  Select **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

9.  Under **Native** **RDP** click on the **Download RDP file**, also
    make a note of the **Public IP address** and if prompted for
    downloading the RDP file click on **Keep** button.

    ![](./media/image44.png)

### **Task 1 – Install the Private Network connector**

1.  Using the RDP file downloaded in **Task 0** log into the **Windows
    Server 2019** VM, using the following credentials.

[TABLE]

18. Open the Server Manager and Select Local Server, then click on
    **On** link for **IE Enhanced Security Configuration**, the set the
    **Administrator** and **Users** switch to **Off**

    ![](./media/image45.png)

19. Open the browser and download and install **Microsoft Edge** from
    the Link **+++
    https://go.microsoft.com/fwlink/?linkid=2109047&Channel=Stable&language=en&brand=M100+++.**

    ![](./media/image46.png)

20. Click on the **Start menu** and type **+++Default+++** and select
    **Default apps**

    ![](./media/image47.png)

21. Scroll down and then under **Web browser**, click on Internet
    Explorer, and then choose **Microsoft Edge**.

    ![](./media/image48.png)

22. Open the **Edge Browser** and navigate to
    **+++https://entra.microsoft.com/+++** and sign in using the
    **Office 365 tenant credentials.**

23. Browse to **Global Secure Access (preview)** \> **Connect** \>
    **Connectors**. Select **Download connector service**.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

24. On the **Private Network Connector Download** Window,
    select **Accept terms & Download**.

![](./media/image50.png)

25. At the top corner of the window, select **Open file** to install the
    connector. An install wizard opens.

![](./media/image51.png)

26. Click on the checkbox for **I agree to the license terms and
    conditions** and then click on the **Install** button.

![](./media/image52.png)

27. Follow the instructions in the wizard to install the service.

28. When you're prompted to register the connector with the Application
    Proxy for your Microsoft Entra tenant, sign in using the **Office
    365 tenant credentials**.

    ![](./media/image53.png)

29. To check that the connector is installed successfully, click on the
    Start menu. Search for and select **Services**.

![A screenshot of a computer Description automatically
generated](./media/image54.png)

30. You will be able to see the **Microsoft AAD Application Proxy
    Connector** service running in the **Standard** services tab.

![](./media/image55.png)

31. Return to the Microsoft Entra admin center in your browser and
    browse to **Global Secure Access
    (preview)** \> **Connect** \> **Connectors**

32. View a connector to verify its details.

![](./media/image56.png)

33. Stay on the same page and continue to the next task.

### Task 2 – Create connector groups

To create as many connector groups as you want:

1.  From the top bar, select **New connector group**.

&nbsp;

34. Provide **+++Test Connector Group+++** as the name, then use the
    dropdown menu to select the available connector. Select **Create**.

![](./media/image57.png)

35. You will see the notification and the group created.

![](./media/image58.png)

36. Stay on the same page and continue to the next task.

    ![](./media/image59.png)

### Task 3 – Create an Enterprise Application and configure quick access

1.  Browse to **Global Secure Access (preview)** \> **Applications** \>
    **Enterprise applications**. Select **New application**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

37. Provide **+++RDP to DC+++** as the name. Select **Test Connector
    Group** in the **Connector Group** dropdown. Then select **Save**.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

38. Once you get the notification that the Network access settings
    updated successfully, navigate to **Applications** \> **Enterprise
    applications. You will see your application in the list.**

![](./media/image62.png)

39. Select the application and then select **Network access properties**
    from the sub-navigation pane. Then select **Add application
    segment**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

40. Provide the following information and select **Apply**.

    - Destination type – **IP address range (CIDR)**

    - Starting address – **+++10.0.0.0+++**

    - Network mask – **/25**

    - Ports – **+++3389,80,445+++**

![](./media/image64.png)

41. Then select **Save**.

![](./media/image65.png)

42. While still on the **RDP to DC** application page, click on
    **Properties** under Manage, for **Assignment required?** Setting
    select **No**, then click on **Save** button.

    ![](./media/image66.png)

43. You should get the notification as shown in below image

    ![](./media/image67.png)

## Exercise 4 – Configure Conditional Access policies.

### Task 1 – Creating and testing Conditional Access policies for Microsoft Entra Internet Access

#### Step 1 – Create Conditional Access Policy to allow Microsoft 365 Traffic from GSA Client

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**.

&nbsp;

44. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

![](./media/image68.png)

45. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – **+++Allow Microsoft 365 Traffic from GSA Client+++**

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image70.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Select what this policy applies to**, choose **Global
  Secure Access (Preview)**. Under Select the traffic profiles this
  policy applies to, choose **Microsoft 365 traffic**.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

- Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the Grant pane, select **Allow access** \>
  **Require multifactor authentication** | **Required all the selected
  controls** and then choose **Select**.

![](./media/image72.png)

- Enable policy – **On**. Click on **Create**.

![](./media/image73.png)

![](./media/image74.png)

#### Step 2 – Test Conditional Access Policy to Allow Microsoft 365 Traffic from GSA Client

1.  Make sure you are logged into the **LON-CL1** VM using the following
    credentials.

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

![](./media/image75.png)

2.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Pause**.

![A screenshot of a computer Description automatically
generated](./media/image76.png)

46. Open the browser in InPrivate mode and navigate
    to **+++https://www.office.com+++**.

47. When prompted, log in as **Joni Sherman**:

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

&nbsp;

3.  Click on **Explore apps**

    ![A screenshot of a computer Description automatically
    generated](./media/image77.png)

4.  You will be able to log in to the **Office 365** portal. Select on
    the **Engage** icon to see that it loads correctly.

![](./media/image78.png)

![](./media/image79.png)

#### Step 3 – Create Conditional Access Policy ‘Block Viva Engage access over Internet’.

1.  Switch back to the Browser with **Office 365 tenant Admin** signed
    in.

&nbsp;

48. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

49. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – **+++Block Viva Engage access over Internet+++**

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

![](./media/image81.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Select apps**. Under select, choose
  **None**. In the side pane, search for and select **Viva Engage** by
  selecting the check box near the app. Then choose **Select**.

![](./media/image82.png)

- Under **Conditions**, select **0 conditions selected**. Under
  **Locations**, select **Not configured**. Select **Yes** under
  **Configure.** Under **Include**, select **Any location**.

![A screenshot of a computer Description automatically
generated](./media/image83.png)

- Choose **Selected locations** under **Exclude**. Then select **None**.

![](./media/image84.png)

- In the Select Locations pane **All Compliant Network** **locations**,
  and then choose **Select**.

![](./media/image85.png)

- Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the Grant pane, select **Block access** and
  then choose **Select**.

![](./media/image86.png)

- Enable policy – **On**. Click on **Create**.

![](./media/image87.png)

![](./media/image88.png)

#### Step 4 – Test Conditional Access Policy ‘Block Viva Engage access over Internet’.

1.  While still logged into the **LON-CL1** VM using the following
    credentials.

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

> .

![A screenshot of a computer Description automatically
generated](./media/image75.png)

5.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Pause** if not already paused.

![A screenshot of a computer Description automatically
generated](./media/image76.png)

50. Close any InPrivate Browser window, then open the browser in
    InPrivate mode and navigate to **+++https://www.office.com+++**.

51. When prompted, log in as **Joni Sherman**:

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

&nbsp;

6.  Click on **Explore apps**

&nbsp;

52. You will be able to log in to the Office 365 portal. Select on
    the **Engage** icon.

![](./media/image78.png)

53. You will get the notification that **You cannot access this right
    now**.

![](./media/image89.png)

7.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Resume**.

![](./media/image90.png)

8.  Once connected, reload the **Viva Engage** page.

![](./media/image91.png)

Hence, we tested the Microsoft Entra Internet Access available in Global
Secure Access.

### Task 2 – Creating and testing Conditional Access policies for Microsoft Entra Private Access

#### Step 1 – Test access to the server through the application ‘RDP to DC’ as Joni Sherman

1.  While still logged into the **LON-CL1** VM using the following
    credentials.

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

9.  Click on the Start menu and then search for **RDP** and select
    **Remote Desktop Connection.**

![](./media/image92.png)

10. In the **Computer** field, type **+++10.0.0.4+++ Private IPv4
    Address** of the **Windows Server 2019** VM created in **Exercise
    3** and select **Connect**.

![](./media/image93.png)

54. When prompted, log in as **Joni Sherman**:

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

&nbsp;

11. You will NOT be able to log in to the server through the app proxy.

![A screenshot of a computer Description automatically
generated](./media/image94.png)

#### Step 2 – Create Conditional Access Policy to grant the access to Joni Sherman

1.  Browse to **+++https://entra.microsoft.com/+++** and sign in using
    the **Office 365 tenant credentials**.

&nbsp;

55. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview (Preview)**,
    click **+ Create new policy**.

![A screenshot of a computer Description automatically
generated](./media/image95.png)

56. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – **+++Microsoft Entra Private Access Policy+++**

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

![A screenshot of a computer Description automatically
generated](./media/image96.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Select apps**. Under select, choose
  **None**. In the side pane, search for and select **RDP to DC** by
  selecting the check box near the app. Then choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image97.png)

- Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the Grant pane, select **Grant access \>
  Require multifactor authentication** and then choose **Select**.

![A screenshot of a computer Description automatically
generated](./media/image98.png)

- Enable policy – **On**. Click on **Create**.

![A screenshot of a computer Description automatically
generated](./media/image99.png)

![A screenshot of a computer Description automatically
generated](./media/image100.png)

#### Step 3 – Test access to the server through the application ‘RDP to DC’ as Joni Sherman after the policy

1.  While still logged into the **LON-CL1** VM using the following
    credentials.

    - Username – **+++jonis@+++paste the Tenant name from the Resources
      tab.**

    - Password – **paste the User Password from the Resources tab** and
      click on **Sign in**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

12. Click on the Start menu and then search for **RDP** and select
    **Remote Desktop Connection.**

![](./media/image92.png)

13. In the **Computer** field, type **+++10.0.0.4+++ Private IPv4
    Address** of the **Windows Server 2019** VM created in **Exercise
    3** and select **Connect**.

![](./media/image93.png)

57. When prompted, log with below credentials:

    - Username – **+++Admin01+++**

    - Password – **+++Pa55w.rd@123+++**

      ![](./media/image101.png)

&nbsp;

14. You will be able to log in to the server through the app proxy using
    the **Local IP- 10.0.0.4** of the Windows Server 2019 VM, confirming
    that the Application is granting the required access.

    ![](./media/image102.png)

15. In your **Global Secure Access – Advanced diagnostics**, under
    **Forwarding Profile** you will see the private access rules
    applying to your client.

![](./media/image103.png)

16. Review the various tabs of the **Global Secure Access – Advanced
    diagnostics**

![](./media/image104.png)

## Summary:

In this lab, we tested the Microsoft Entra private Access and Microsoft
Entra Internet Access available in Global Secure Access.
