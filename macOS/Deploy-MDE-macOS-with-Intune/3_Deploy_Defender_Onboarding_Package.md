# 3: Deploy Defender onboarding Package

## What's covered in this section
The Defender onboarding package must be assigned to each macOS device. If this step is missed, the device will likely display a "license is not assigned" error message, and Defender will not function properly on macOS.  
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

7. Extract the zip file. If you are using Windows, right click the file in the file explorere and select **Extract all**. (We will use extracted file at next step)

## Step 2: Deploy the Microsoft Defender for Endpoint onboarding package for MacOS

1. Open [Microsoft Intune portal](https://aka.ms/memac)
2. Go to **Devices** > **Monitor** > **Managed Devices** > **Configuration**
3. Click **Create** > **New Policy**.
4. Select **macOS** in platform, and select **Templates** in profile type.
5. Select **Custom** from Template name, and click **Create**.
6. Specify name for configuration. (For example, "MDE onboarding package"). 
7. Specify Custom Configuration profile name (For example, "MDE Onboarding profile").
8. Select Deployment channel **"Device channel"**.
9. In the configurationp porfile, select the configuratin profile (WindowsDefenderATPOnboarding.xml in extracted Intune folder) which we downloaded in step 1.
10. Click **Next** to proceed.
11. Click **Next** to proceed in Scope tag page.
12. In assignments tab, click add groups. Select target group and cick next
13. In review + create tab, click **Create** to finish.
