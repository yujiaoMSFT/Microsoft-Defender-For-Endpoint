# 4: Deploy Defender application

## What's covered in this section
This section outlines the deployment of the Microsoft Defender application on macOS devices using Intune. The process includes:
- Automating the download and installation of the Defender pakage (.pkg) file via an [Intune shell script](https://learn.microsoft.com/en-us/intune/intune-service/apps/macos-shell-scripts).
- Verifying the deployment status of the Defender application in the Intune portal.
- Checking the installation script logs directly on the macOS device for troubleshooting or validation.
  
> There are multiple methods available for deploying applications to macOS devices. In this case, I chose to use a shell script for installation. Alternatively, you can follow the application deployment steps described in [Step 12: Publish the Microsoft Defender application](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune#step-12-publish-the-microsoft-defender-application) in the official documentation.
> To explore other deployment options and understand the pros and cons of each method, refer to this [blog post](https://techcommunity.microsoft.com/blog/intunecustomersuccess/deploying-microsoft-365-apps-for-mac-with-microsoft-intune---a-deep-dive/2243040).

## Step 1: Download Sample shell script for Defender application installation
1. Download [Defender installation script file](https://github.com/microsoft/shell-intune-samples/blob/master/macOS/Apps/Defender/installDefender.sh) from Github.

> Note  
> The original script includes a condition that checks whether Microsoft Office is installed. **If Office is not present, the script halts and does not proceed with the installation of Microsoft Defender.**
However, since our current focus is solely on testing the Defender application, I’ll explain how to modify the script by commenting out this check. This adjustment ensures that Defender will be installed regardless of whether Microsoft Office is installed.
If Microsoft Office is already installed on your macOS device, you can continue using the original script without any changes by following below steps.

2. Once downloaded the script file, open it with editor such as Notepad. 
3. Modify the script by comment out **waitForOtherApps()** by adding **#**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/InstallerScript1.png)

4. xxxx  
   
## Step 3: Upload and deploy script file
1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Devices** > **Monitor** > **By Platform** > **macOS**
3. Go to **Monitor** > **Manage Devices** > **Scripts**
4. Click **Add**
5. In Basics page, enter name for Script (For example, "Install Defender Application") and click **Next**
6. Upload the script (installDefender.sh) you downloaded and modified in Step 1. Also use following settings and then click **Next**
   - Run acript as signed in user = No  
   - Hide Script notifications on devices = Not configured  
   - Script frequency = Not configured
   - Max Number of times to retry if script fails = 3  
7. In Scope tags page, click **Next**
8. In Assignments page, click **Add groups** under Included groups to select target groupo. And then click **Next**
9. In Review + add page, click **Add**

## Step 4: Check Script logs on macOS device

1. Go to your macOS device
2. Open Intune Application
3. 
4. Open following folder /Library/Logs/Microsoft/IntuneScripts/installDefender



1. In **Intune portal**, go to **Apps** > **Monitor** > **Platforms** > **macOS**
2. Click on the **MDE app** from the applications.
3. Review the **installaiton status** of MDE application.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage5.png)
