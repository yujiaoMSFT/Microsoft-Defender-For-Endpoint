# 2.	Deploy configuration policies for Defender (using Graph API)

## What's covered in this section

In this section, we will cover the creation of multiple configuration policies required for Microsoft Defender for Endpoint on macOS.  
While the  [public documentation](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune) outlines these steps using manual profile creation through the Intune portal, you can certainly choose that approach.  
However, I will instead **leverage a sample Graph API script** created by my collegue [Chris Kunze](https://github.com/CKunze-MSFT) from Intune CXE (Customer Experience and Enginneirng ) team to simplify these manual tasks by automation and efficient.
> If you're anything like me and prefer to avoid repetitive manual tasks, you'll love this method. It saves time and effort! Thanks Chris!

## Prerequisite

-  PC with PowerShell installed
      -   For **macOS users**: Follow the official installation guide here: [Installing PowerShell on macOS](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-macos?view=powershell-7.5)
      -   For **Windows users**: PowerShell comes pre-installed with the operating system..
-  Graph API permission
      -   An account assigned to the **Intune Administrator role** under Entra ID built-in roles)

## What this script does?

Before running script, let me explain what this script does.  Once this script runs, it connects to Graph API and complete following. 
- Download configuration files from [GitHub repository](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles)
- Create policy settings in Microsoft Intune portal (See below tables)


| No | Configuration | Configuration File | Policy Type in Intune | description |
| ------ | ------ | ------ | ------ | ------ |
| 1 | Approve system extensions | sysext.mobileconfig | Custom | System extension permissions |
| 2 | System extensions restricted | sysext_restricted.mobileconfig | Custom | Restricted system extension permissions |
| 3 | Network Filter | netfilter.mobileconfig | Custom | Defender on macOS inspects socket traffic and reports this information to the Defender XDR portal | 
| 4 | Full Disk Access | fulldisk.mobileconfig | Custom | This configuration profile grants Full Disk Access to Microsoft Defender for Endpoint This configuration profile grants Full Disk Access to Microsoft Defender for Endpoint |
| 5  | Background services | background_services.mobileconfig | Custom | This configuration profile grants Background Service permission to Microsoft Defender for Endpoint |
| 6 | Notifications | notif.mobileconfig	| Custom | This profile is used to allow Microsoft Defender for Endpoint on macOS and Microsoft AutoUpdate to display notifications in UI |
| 7 | Accessibility | accessibility.mobileconfig | Custom | This profile is used to allow Microsoft Defender for Endpoint on macOS to access the accessibility settings on Apple macOS |
| 8 | Bluetooth permissions | bluetooth.mobileconfig | Custom | Microsoft Defender for Endpoint uses it if you configure Bluetooth policies for Device Control |
| 9 | Kext (Kernel extension) | kext.mobileconfig | Custom |  We don't deploy this policy because no longer needed. (Kernel Extension only works on macOS versions prior to 11)" |

**How does it look like in Intune portal?**  
After running this script successfully, it creates the following policies in Intune portal like below screenshot.
Each policy name start with a **"MDE (imported) -"**

![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/4a59bfcee1ddef91783cac9e1bc2097d6e89315d/Images/macOS/Intune-DeviceConfiguration.png)

> Policy assignments must be configured individually after each policy is created. Some policies may not be deployed since they are not required for the current macOS versions

Now let's start!

## Step 1: Download Sample PowerShell script

1. Download the PowerShell script **(AddDefenderConfigsToIntune.ps1)** from [GitHub](https://github.com/microsoft/shell-intune-samples/tree/master/macOS/Config/Defender%20Configuration)  

     > You will find the **download raw file** button circled in red at the top right corner.

     ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/bc8fadc2fa049bc8b7cc81ac004b08b1586eb5fe/Images/macOS/GitHub-IntuneScript.png)

     I also **highly recommend reading the guidance provided in the script**, specifically the sections titled 'Configuration Variables' and 'Prerequisites and Authentication'.
   
## Step 2: Install Microsoft Graph PowerShell SDK
   
> You can skip this step if you already installed the Microsoft Graph SDK on your device.

1. Launch PowerShell and run command below to start installing [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/ja-jp/powershell/microsoftgraph/installation?view=graph-powershell-1.0):  
     ```sh
     Install-Module Microsoft.Graph -Scope CurrentUser
     ```
2. During installation, you may encounter message dialogs. When they appear, click the 'Yes' or 'Yes to all' button to proceed.
3. Once installation completes, run following command to validate the installation and installed version.

     ```sh
     Get-InstalledModule Microsoft.Graph
     ```
     ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/PS_Install_GraphSDK.png)  

## Step 3: Grant API access

The following access permissions are required to execute the PowerShell script for making changes in Intune via API."
Connect-MgGraph -NoWelcome -Scopes "DeviceManagementConfiguration.ReadWrite.All"

1. In the browser, open [Azure portal](https://portal.azure.com/)
2. In the search box on the top, search with keyword **Intune Graph API**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/cb9be79b5259eb053027be5470151c880e78931f/Images/macOS/Intune-GraphConfig1.png)
3. Click **Intune Gpaph API** from the search result.
4. Intune Graph API appears. Go to **Manage** > **API permissions**
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/cb9be79b5259eb053027be5470151c880e78931f/Images/macOS/IntuneGraph-Config2.png)
5. Click **Add a permission**
6. Select **Microsoft Graph** in Microsoft APIs tab
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/cb9be79b5259eb053027be5470151c880e78931f/Images/macOS/IntuneGraph-Config3.png)
7. Select **Delegated Permissions**
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/cb9be79b5259eb053027be5470151c880e78931f/Images/macOS/IntuneGraph-Config4.png)
8. In the search box, type **DeviceManagementConfiguration.ReadWrite.All**. You will see the permission listed
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/cb9be79b5259eb053027be5470151c880e78931f/Images/macOS/IntuneGraph-Config5.png)
9. Select the **DeviceManagementConfiguration.ReadWrite.All** and click **Add permissions**
10. Verify API permission is added correctly.
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/ce013bf6e2c12b3269436887f6c8c29941ad0314/Images/macOS/IntuneGraph-Config6.png)
   
## Step 4: Execute the script and create policy through Graph API
Now you're ready to run the script and create policies via Graph API. Execute the downloaded PowrShell script (AddDefenderConfigsToIntune.ps1) in the step 1.
You will see login prompt. Enter your Intune admin account and password to proceed.

1. Launch PowerShell.
2. Navigate to the downloaded script file, AddDefenderConfigsToIntune.ps1, which you downloaded in Step 1.
3. Execute the script to begin the policy creation process.
4. Sign in when prompted: A login window will appear. Enter your Intune administrator credentials to proceed.
5. The results of the script execution will be displayed in the PowerShell window.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/Images/macOS/PS-Intune_GraphSDK.png)

## Step 5: Check Policy created in  Microsoft Intune portal

1. Open [Intune portal](https://aka.ms/memac)   
2. Go to **Devices** / **Manage devices** / **Configuration** in Microsoft Intune portal.  
3. Look for policies whose names begin with **"MDE (imported) -"** created successfully.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/4a59bfcee1ddef91783cac9e1bc2097d6e89315d/Images/macOS/Intune-DeviceConfiguration.png)

## Step 6: Assign the policy to a group

1. Open [Intune portal](https://aka.ms/memac)
2. Select the policy crated in Step 5. (In this example, I selected *MDE (imported) - sysext_restricted Configuration*)
3. Click **Edit** under the Assignments section in the policy properties.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/6f67d935dc99f6bc02938a45d7a8d2ccdfa0f3af/Images/macOS/Intune-PolicyAssign1.png)
4. On the assignments page, click **Add groups** under Included groups.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/6f67d935dc99f6bc02938a45d7a8d2ccdfa0f3af/Images/macOS/Intune-PolicyAssign2.png)
5. Search and select your target group. (For example, MDE macOS devices group)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/6f67d935dc99f6bc02938a45d7a8d2ccdfa0f3af/Images/macOS/Intune-PolicyAssign3.png)
6. Confirm that your group is selected
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/6f67d935dc99f6bc02938a45d7a8d2ccdfa0f3af/Images/macOS/Intune-PolicyAssign4.png)
7. Click **Review + save** to apply the changes

> **Repeat these steps for all other configuration profiles created by the script, except for the Kernel Extension (Kext) policy. Assigning a Kext policy is no longer necessary for currently supported macOS devices**

***
## Go to next section  
Once completed, go to next section [3: Deploy Defender onboarding Package](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/macOS/Deploy-MDE-macOS-with-Intune/3_Deploy_Defender_Onboarding_Package.md)
