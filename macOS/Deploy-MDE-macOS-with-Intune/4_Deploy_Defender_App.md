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
2. Modify the file (REM application check)

## Step 2: Install Rosetta on macOS

This is optional. If device is ARM chip, but it's reauired for script


## Step 3: Upload and deploy script file

1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Devices** > **Monitor** > **By Platform** > **macOS**
3. Go to **Monitor** > **Manage Device** > **Scripts**
4. Click **Add**
5. In Basics page, enter name for Script (For example, "Install Defender Application") and click **Next**
6. Upload the script you downloaded in Step 1. Also use following settings and then click **Next**
   - Run acript as signed in user = No  
   - Hide Script notifications on devices = Not configured  
   - Script frequency = Not configured
   - Max Number of times to retry if script fails = 3  
7. xxx

## Step 4: Create MDE App package and assign it to the group

## Step 1: Create MDE App package and assign it to the group

1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Apps** > **Monitor** > **Platforms** > **macOS**
3. Click **Create** button.
4. Click pull down menu in **App type** and you will see a list of apps.  
   Select **macOS** under **Microsoft Defender for Endpoint**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage1.png)
6. You will see **Microsoft Defender for Endpoing (macOS)**.  
   Click **Select** to continue.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage2.png)
7. In **App information** page, use default value and click **Next** (Of course you can choose to change if needed)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage3.png)
8. In **Scope tag** page, click **Next**. (You can set scope tag if you need)
9. In **Assignments** page, click **Add group** under Required
10. Select your device group. In my case "MDE macOS devices" group created in previous step and click **select** button
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage4.png)
11. Click **Next**
12. Click **Create**.

## Step 2: Verify MDE App package deployment

> It may take some time for the installation status to update in the Intune portal.  
> You can proceed to the next section and return later to verify the installation status.

1. In **Intune portal**, go to **Apps** > **Monitor** > **Platforms** > **macOS**
2. Click on the **MDE app** from the applications.
3. Review the **installaiton status** of MDE application.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage5.png)
