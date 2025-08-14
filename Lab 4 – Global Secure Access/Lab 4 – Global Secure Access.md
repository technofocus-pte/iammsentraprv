# Lab 4 – Global Secure Access​

## Objective:

In this lab we will configure Microsoft Entra Private Access and
Microsoft Entra Internet Access. We will then create conditional
policies using them and test them using the credentials of Joni Sherman.

> **Note:** You may be asked for Multifactor authentication in the lab
when we log in as a user. Please make sure you have gone through
Exercise 4 in lab 1 to be able to use the authenticator app on your
phone.

## Exercise 1 – Prerequisites

### Task 1 – Register your VM with Microsoft Entra ID 

For GSA we need to install the clients on our VM. For that we will have
to register our Lab VM to the Contoso’s Entra ID.

1.  From the **Home/Resource** tab, ensure that you have selected **LON-CL1** VM, 

2. login to the VM using the below
    credentials.

    * Username – `.\Admin`

    * Password - `Pa55w.rd`

3. Open windows **Setting** on **LON-CL1** VM.

    ![ ](./media/image1.png)

9.  Click on Accounts then select **Access work or school account**,
    click on **+ Connect**.

     ![](./media/image8.png)

10. In the **Set up a work or school account** prompt, click on **Join
    this device to Microsoft Entra ID**.

     ![](./media/image9.png)

11. In the sign in prompt, sign in using the following credentials.

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

    ![](./media/image10.png)

12. Press **Join** in the prompt **Make sure this is your
    organisation**.

    ![](./media/image11.png)

13. Once done you will see a confirmation window **You’re all set!**.
    Click on **Done**.

    ![](./media/image12.png)

14. Once again near **Access work or school**, click on **Connect**.

15. In the sign in prompt, sign in using the following credentials.

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

16. It will take a couple of seconds to sign in, click on the **Got it**
    button.

    ![](./media/image13.png)

17. You should be able to see 2 connections as shown in below image.

    ![](./media/image14.png)


18. Restart the VM. Make sure you do not shut it down.

19. Select the **LON-CL1** VM and on the user screen select **Other
    user**.

20. Enter your following credentials and log in to the VM.

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

    ![](./media/image15.png)

21. You may be prompted to do MFA registration, complete the MFA
    registration followed by Setting the **PIN**. Set the PIN as
    `123654`

22. The next exercises i.e. Exercise 2 and 3, should be performed under
    this user only.

### Task 2 – Activating Traffic Forwarding Profiles

1.  Browse to `https://entra.microsoft.com/` and sign in using
    the **Office 365 tenant credentials**. If you are automatically
    logged in with Joni Sherman, log out and login again with the Office
    365 Tenant Admin credentials.

    ![](./media/image16.png)

1.  On the lefthand menu, under **Global Security Access** expand **Connect** and then select
**Traffic forwarding** and then click on the **Activate** button.

    ![](./media/image17.png)

2.  You should receive a notification as show in below image. 

    ![](./media/image18.png)

3. Click on **Traffic Forwarding** from the left menu and then from the notificaiton - To use these capabilities the following licenses may be required: Microsoft Entra Internet Access or Microsoft Entra Private Access. Activate or Learn more. Click on the **Activate** link.

    ![](./media/image18b.png)

3. Click on the **Activate** button.
    ![](./media/image18c.png)

3. Click on the **Continue** button.

    ![](./media/image18d.png)

3. Click on the **Try now** button.

    ![](./media/image18e.png)

3. Switch back to the Microsoft Entra Portal tab and refresh the browser.

3. From the left navigation, expand **Global Secure Access** and from the
    **Connect** dropdown, select **Traffic Forwarding**. Select the check
    box near **Microsoft traffic profile.**

    ![ ](./media/image19.png)


4.  Select **OK** on the prompt.

    ![ ](./media/image20.png)


6.  Do the same for **Private access profile** and **Internet access
    profile**.

    ![](./media/image21.png)

    ![](./media/image22.png)

9. We need to assign users to the Profile, click on the **View** link under **Microsoft traffic profile**.

    ![](./media/image22a.png)

10. Enable the toggle **Assign to all users**

    ![](./media/image22b.png)

11. Click on the **OK** button to confirm

    ![](./media/image22c.png)

12. Perform the same steps for below profiles.
    
    * **Private access profile**
    ![](./media/image22d.png)

    * **Internet access profile**
    ![](./media/image22e.png)

13. Once all the profiles are configured, it should appear as below.

    ![](./media/image22f.png)

## Exercise 2 – Configuring Microsoft Entra Internet Access

### Task 1 – Download and install the client to your Client VM

The most current version of the Global Secure Access Client can be downloaded from the Microsoft Entra admin center. Ensure that you are on the **LON-CL1**

1.  Browse to `https://entra.microsoft.com/` and sign in using
    the **Office 365 tenant credentials**. If you are automatically
    logged in with Joni Sherman, log out and login again with the Office
    365 Tenant Admin credentials.

    ![](./media/image16.png)

1.  From the navigation bar, select **Global Secure Access** \ **Connect** \ **Client Download**. Select **Download
    Client**.

    ![ ](./media/image23.png)

5.  Once downloaded, select Open **file to** run the installer and
    install the client in your VM.

    ![ ](./media/image24.png)

6.  Accept the terms and conditions and select **Install**.

    ![](./media/image25.png)

7.  Select **yes** on the prompt.

    ![computer error ](./media/image26.png)

8.  Let the installation complete. Once done select **Close**.

    ![ ](./media/image27.png)

    > **Note** - If prompted to restart, then restart the LON-CL1 VM and login again with Joni Sherman credentials.

10. Once done, select the arrow on the bottom right corner and then
    hover on the small globe sign. You will see that the client is now
    **connected**.

    ![ ](./media/image29.png)

11. Right click on the icon and select **Advanced diagnostics**.

    ![ ](./media/image30.png)

12. For the prompt select **Yes**.

    ![computer error ](./media/image31.png)

13. Under the **Hostname acquisition** select **Start collecting**.

    ![ ](./media/image32.png)

14. After few minutes the Data should start appearing as shown in below
    image.

    ![](./media/image33.png)

15. Under the **Traffic** select **Start collecting**.

    ![ ](./media/image34.png)

16. After few minutes the Data should start appearing as shown in below
    image.

    ![](./media/image35.png)

17. Stay on the same VM and complete the following Task.

### Task 2 – Enable Tenant restrictions

1.  Browse to `https://entra.microsoft.com/` and sign in using
    the **Office 365 tenant credentials**.

2.  Browse to **Global Secure Access** \ **Settings**
    \ **Session management**. Under **Adaptive Access** tab, set the
    **Enable CA Signaling for Entra ID (covering all cloud apps)**,
    toggle to **ON**. 


    <Font color=DarkRed>

    > **Note - If the Enable CA Signaling for Entra ID (covering all cloud apps) is already turn on, turn off and turn on again, otherwise when creating Conditional Access the additional option will not appear.**
    
    </font>

      ![](./media/image36.png)

    ![](./media/image36a.png)

## Exercise 3 – Configuring Microsoft Entra Private Access

### **Task 1 – Install the Private Network connector**

1.  Switch to **LON-SVR1**, then open the **Edge Browser** and navigate to
    `https://entra.microsoft.com/` and sign in using the
    **Office 365 tenant credentials.**

23. Browse to **Global Secure Access** > **Connect** >
    **Connectors**. Select **Download connector service**.

    ![ ](./media/image49.png)

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
    Start menu. Search for and select `Services`.

    ![ ](./media/image54.png)

30. You will be able to see the **Microsoft Entra private network connector** service running in the **Standard** services tab.

    ![](./media/image55.png)

31. Return to the Microsoft Entra admin center in your browser and
    browse to **Global Secure Access** \ **Connect** \ **Connectors** refresh the page

32. View a connector to verify its details.

    ![](./media/image56.png)

33. Stay on the same page and continue to the next task.

### Task 2 – Create connector groups

To create as many connector groups as you want:

1.  From the top bar, select **New connector group**.

34. Provide `Test Connector Group` as the name, then use the
    dropdown menu to select the available connector. click on the **Save** button.

    ![](./media/image57.png)


35. You will see the notification and the group created.

    ![](./media/image58.png)

36. Stay on the same page and continue to the next task.

    ![](./media/image59.png)

## Exercise 4 – Configure Conditional Access policies.

### Task 1 – Creating and testing Conditional Access policies for Microsoft Entra Internet Access

#### Step 1 – Create Conditional Access Policy to allow Microsoft 365 Traffic from GSA Client

1.  Browse to `https://entra.microsoft.com/` and sign in using
    the **Office 365 tenant credentials**.

44. On the lefthand menu, expand **Entra ID** and select **Conditional access**. On the **Overview** page, click **+ Create new policy**.

    ![](./media/image68.png)

45. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – `Allow Microsoft 365 Traffic from GSA Client`

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

    ![ ](./media/image69.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

    ![ ](./media/image70.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Select what this policy applies to**, choose **Resources (formerly cloud apps)**. Under include choose **All internet resources with Global Secure Access**.

    ![ ](./media/image71.png)

- Under **Access controls**, within the **Grant** section, select **0
  controls selected**. In the Grant pane, select **Allow access** \
  **Require multifactor authentication** | **Required all the selected
  controls** and then choose **Select**.

    ![](./media/image72.png)

- Enable policy – **On**. Click on **Create**.

    ![](./media/image73.png)

    ![](./media/image74.png)

#### Step 2 – Test Conditional Access Policy to Allow Microsoft 365 Traffic from GSA Client

1.  Make sure you are logged into the **LON-CL1** VM using the following
    credentials.

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

    ![](./media/image75.png)

2.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Disable**.

    ![ ](./media/image76.png)

46. Open the browser in InPrivate mode and navigate
    to `https://www.office.com`

47. When prompted, log in as **Joni Sherman**:

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

3.  Click on **Explore apps**

    ![computer Description automatically
    generated](./media/image77.png)

4.  You will be able to log in to the **Office 365** portal. Select on
    the **Engage** icon to see that it loads correctly.

    ![](./media/image78.png)

    ![](./media/image79.png)

#### Step 3 – Create Conditional Access Policy ‘Block Viva Engage access over Internet’.

1.  Switch back to the Browser with Microsoft Entra  tba and **Office 365 tenant Admin** signed
    in.

48. On the lefthand menu, under Identity, expand Protection, and then
    select **Conditional access**. On the **Overview**,
    click **+ Create new policy**.

    ![ ](./media/image68.png)

49. On the **New Conditional Access Policy** page, provide the below
    details

    - Name – `Block Viva Engage access over Internet`

    - Under **Users**, select **0 users and groups selected/Specific
      users included**. Then under **Include**, choose **Select users
      and groups**. Select the check box near **Users and groups**. Then
      under **Select**, choose **0 users and groups selected**.

    ![ ](./media/image80.png)

- Scroll down on the **Select users and groups** page, select **Joni
  Sherman**. Choose **Select**.

    ![](./media/image81.png)

- Under **Target Resources**, select **No target resources selected**.
  Then under **Include**, choose **Resources**. Under select, choose
  **None**. In the side pane, search for and select **Viva Engage** by
  selecting the check box near the app. Then choose **Select**.

    ![](./media/image82.png)

- Under **Conditions**, select **0 conditions selected**. Under
  **Locations**, select **Not configured**. Select **Yes** under
  **Configure.** Under **Include**, select **Any location**.

    ![ ](./media/image83.png)

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

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

     ![ ](./media/image75.png)

5.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Pause** if not already paused.

    ![ ](./media/image76.png)

50. Close any InPrivate Browser window, then open the browser in
    InPrivate mode and navigate to `https://www.office.com`

51. When prompted, log in as **Joni Sherman**:

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

6.  Click on **Explore apps**

52. You will be able to log in to the Office 365 portal. Select on
    the **Engage** icon.

    ![](./media/image78.png)

53. You will get the notification that **You cannot access this right
    now**. Close the Inprivate browser tabs completely.

    ![](./media/image89.png)

7.  Right click on the **GSA Client** icon at the bottom right corner of
    the screen. And select **Enable**.

    ![](./media/image90.png)

46. Open the browser in InPrivate mode and navigate
    to `https://www.office.com`

47. When prompted, log in as **Joni Sherman**:

    *   Username – `jonis@`

        Paste the Tenant name from the **Home/Resources** tab.

    *   Password – **paste the User Password from the Home/Resources tab** or `Pa55w.rd98` 
    
        [This Password was set in Lab 3] and click on **Sign in**

3.  Click on **Explore apps**

    ![computer Description automatically
    generated](./media/image77.png)

4.  You will be able to log in to the **Office 365** portal. Select on
    the **Engage**.

    ![](./media/image78.png)

5. This time via the Global Secure Access the Engage application should be accessible.

    ![](./media/image79.png)

## Summary:

In this lab, we tested the Microsoft Entra private Access and Microsoft Entra Internet Access available in Global Secure Access.
