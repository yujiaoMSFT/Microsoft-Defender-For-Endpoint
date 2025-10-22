# 3: Deploy MDE onboarding Package

## What's covered in this section
The MDE onboarding package must be assigned to each macOS device. If this step is missed, the device will likely display a "license is not assigned" error message, and MDE will not function properly on macOS.  
Following will be covered in this section.    
- Download the Microsoft Defender for Endpoint onboarding package from Defender portal
- Create and deploy the Microsoft Defender for Endpoint onboarding package for MacOS in Intune portal.

## Step 1: Download the Microsoft Defender for Endpoint onboarding package
1. Open [Microsoft Defender portal](https://security.microsoft.com)
2. Go to **Settings** > **Endpoints** > **Device management** > **Onboarding**
3. To select operating system, choose **macOS** from pull down menu.
4. In connectivity type, select **Streamlined** from pull down menu.  
   ([Streamlined connectibity](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity?view=o365-worldwide&branch=connect-devices) is recommended since it requlres less required URLs compared to Standard connectivitry. However, you can chooose Standard if you prefereed)
5. In deployment method, select **Mobile Device Management / Microsoft Intune**.
6. Click **Download onboarding package** button and download onboarding package in zip format. (GatewayWindowsDefenderATPOnboardingPackage.zip will be downloaded if you choose Streamlined connectivity)

I'll add a portal screenshot below for reference.
If you don't see these menus, it's possible you don't have sufficient permissions in Defender. Please refer to this document to verify your access.
![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/c2241e2fa4df4f6a4ca655f2cb7270106de7378b/images/macOS/MDE-Download-OnboardingPackage1.png)

7. Extract the zip file. If you are using Windows, right click the file in the file explorere and select **Extract all**.
9. A File "MicrosoftDefenderATPOnboardingMacOs.sh" will be extracted.
10. ou will see **Microsoft Defender for Endpoing (macOS)**. Click **Select** to continue.
11. In **App information** page, use default value and click **Next** (Of course you can choose to change if needed)
12. In **Scope tag** page, click **Next**. (You can set scope tag if you need)
13. In **Assignments** page, click **Next** at this moment. (We will app assignments to the device group later, so fo now, let's skip this process)
14. Click **Create**.
15. Go to **Apps** > **Monitor** > **Platforms** > **macOS** and confirm MDE app is created.

## Step 2: Deploy the Microsoft Defender for Endpoint onboarding package for MacOS

1. Open [Microsoft Intune portal](https://aka.ms/memac)
2. Go to **Devices** > **Monitor** > **Managed Devices** > **Configuration**
3. Click **Create** > **New Policy**.
4. Select **macOS** in platform, and select **Templates** in profile type.
5. Select **Custom** from Template name, and click **Create**.
6. Specify name for configuration. (In my case, "MDE onboarding WOW"). This will be visible at XXXXX on macOS once policy applied correctly.
7. Specify Custom Configuration profile name (In my case, MDE Onboarding. 
8. To select operating system, choose **macOS** from pull down menu.
9. In connectivity type, select **Streamlined** from pull down menu. (Streamlined connectibity requlres less required URLs compared to Standard connectivitry. However, you can chooose Standard if you prefereed)
10. In deployment method, select **Mobile Device Management / Microsoft Intune**.
11. Click **Download onboarding package** button and download onboarding package in zip format. (GatewayWindowsDefenderATPOnboardingPackage.zip)
12. Extract the zip file.
13. 
14. ou will see **Microsoft Defender for Endpoing (macOS)**. Click **Select** to continue.
15. In **App information** page, use default value and click **Next** (Of course you can choose to change if needed)
16. In **Scope tag** page, click **Next**. (You can set scope tag if you need)
17. In **Assignments** page, click **Next** at this moment. (We will app assignments to the device group later, so fo now, let's skip this process)
18. Click **Create**.
19. Go to **Apps** > **Monitor** > **Platforms** > **macOS** and confirm MDE app is created.
