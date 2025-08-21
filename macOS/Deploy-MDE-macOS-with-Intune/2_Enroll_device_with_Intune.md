# 2: Enroll the device with Intune

## What's covered in this section
- Enroll your macOS device into Intune (BYOD scenario)
- Create a devcie group in Intune. (This group will be used later to deploy the Microsoft Defender for Endpoint (MDE) app and associated policies)  
> You may skip this section if your macOS device is already enrolled in Microsoft Intune or if you're familiar with creating device groups in Intune.

## Prerequiristie
Ensure your Intune tenant is already configured for macOS device enrollment. If you haven’t completed the configuration, please follow the steps in the [Intune documentation](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/macos-enroll) before proceeding.

## Additional notes
This guide explains how to enroll a macOS device in a BYOD (Bring Your Own Device) scenario.  
If you intend to enroll a company-owned macOS device such as using Automated Device Enrollment (ADE), refer to the [Intune documentation](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/macos-enroll) for detailed instructions:  

## Step 1: Install Intune Company portal app for macOS

1. **Open your browser** on your macOS device and go to https://aka.ms/EnrollMyMac.
2. When prompted with the message **"Do you want to allow downloads on officecdn.microsoft.com?"**, click **Allow** to proceed with the download  
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/07a5c99eb247631274801302a602b27f7b92bf86/Images/macOS/Download-IntuneApp.png)
3. Once the download is complete, run the file named **CompanyPortal-Installer.pkg**.
4. On welcome screen, click **Contine**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/ca29f659c7991b751e9d055015d4b274a617b99e/Images/macOS/IntuneSetup1.png)
5. Read the Software License Agreement, then click **Continue**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/ca29f659c7991b751e9d055015d4b274a617b99e/Images/macOS/IntuneSetup2.png)
6. Click **Agree** to accept the Software License Agreement and proceed
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/ca29f659c7991b751e9d055015d4b274a617b99e/Images/macOS/IntuneSetup3.png)
7. Click **Install** to beging the installation. You may be prompted to enter **admin credentials** of your macOS device. Do so to continue.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/ca29f659c7991b751e9d055015d4b274a617b99e/Images/macOS/IntuneSetup4.png)
12. After installation completes, click **Close**.
13. You can optionally click **Move to Trash** to delete the installer file once setup is complete.

## Step 2: Sign in to Componay portal and rgister with Intune

1. On your macOS device, **Launch Company portal** and click **Sign in**.
2. **Enter user account** and click **Next** (Ensure the user has both Intune and MDE licenses assigned.)
3. **Enter you password**
4. **Complete Multi-Factor Authentication (MFA)** if prompted.
5. When the Setup screen appears, click **Begin**.
6. Review the **Privacy Information**, then click **Continue**.
8. Click **Download profile** button and  wait for download to complete.
9. The **Device Management** screen will open. Click on **Management Profile**, then click **Install**.
10. enter **admin credentials** of your macOS device and then click **Enroll**.
11. Click **Done** to complete the setup
12. You will now see your device registered in the company portal app (ADD IMAGE)

## Step 3: Confirm device object and create Deice group in Intune  portal

### 1: Confirm device object
1. Go to **Devices** > **Monitor** > **By platform** > **macOS**
2. Confirm that you will see your macOS device in the Intune portal.
     (Note: If you’ve just registered the device, it may take a while before it shows up)   

### 2: Create a Device Group
1. Go to **Groups** > **All groups** in the Intune portal.
2. Click **New Group**
    - Set **Group type** to **Security**
    - Enter **Group name**. Pick any name you want. I used **MDE macOS devices** as group name.
3. Click **"No memberrs selected** link under **Members**.
    - Search and select your macOS device form the list.
    - Click **Select** button. 
 4. Now 1 member is selected. Click **Create** to create a group

### 3: Verify Device Group Membership
1. Go to **Groups** > **All groups**. Search the group you just created. Click the group once its found.
2. Go to **Manage** > **Members** in the selected group page.
3. Confirm your macOS device is listed as the group member. (We will use this device group for policy assignment in later sections)  
![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/f7db997688e5748fe26800357b66912550846632/images/Intune-GroupMembership.png)  
Screenshot - Device group membership in Intune portal
