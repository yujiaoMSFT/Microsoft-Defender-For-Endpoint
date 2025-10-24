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
2. Open the downloaded script file using a text editor such as Notepad. 
3. Locate the line containing waitForOtherApps() in the script.
4. Comment out the **waitForOtherApps()** line by adding a # at the beginning of the line. (See example in below screnshot)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/InstallerScript1.png)
5. Save the modified script file.
   
## Step 2: Deploy the script file using Microsoft Intune
1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Devices** > **Monitor** > **By Platform** > **macOS**
3. Go to **Monitor** > **Manage Devices** > **Scripts**
4. Click **Add** to begin the script deployment process.
5. On Basics page, enter a name for the script (e.g., Install Defender Application) and click **Next**
6. Upload the installDefender.sh from Step 1. Apply the following settings and click **Next**
   - Run acript as signed in user: No  
   - Hide Script notifications on devices: Not configured  
   - Script frequency: Not configured
   - Max Number of times to retry if script fails: 3  
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/IntuneMDEScript1.png)
7. On Scope tags page, click **Next**
8. On Assignments page, click **Add groups** under Included groups to select target groupo. After selecting the group, click **Next**
9. On Review + add page, click **Add** to complete the script deployment.

## Step 4: View Script Execution Logs on macOS Devices
1. Go to your macOS device.
2. Navigate to the following folder: */Library/Logs/Microsoft/IntuneScripts/installDefender*
3. Open the file: *Microsoft Defender.log*
4. Review the log details to confirm successful installation or identify any errors that may have occurred.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/DefenderApp_ScriptLog.png)

***
## Go to next section  
Once completed, go to next section [5: Verify Installation](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/macOS/Deploy-MDE-macOS-with-Intune/5_Verify_Installation.md)
