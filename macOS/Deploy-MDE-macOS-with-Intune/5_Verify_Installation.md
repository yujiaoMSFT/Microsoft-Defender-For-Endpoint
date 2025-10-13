# 5: Verify Installation

## What's covered in this section
Once all previous onboarding steps are complete, verify the setup on a macOS device.  
This section covers the following methods to check the MDE installation on macOS:
- Verifying MDE installation from the macOS UI
- Verifying MDE installation using the terminal
- Checking the device inventory in the Microsoft Defender portal

> This document was created using a Mac mini running macOS 15.5 with an Apple M4 chip.  
> Please note that the macOS user interface may differ if you are using a different version of macOS.

## Step 1: Verifying MDE installation from the macOS UI

1.  Locate the **Defender icon** in the task bar.  Click the icon, then select **Open Microsoft Defender** to launch the application.  
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/31330673aa411c6f4395a21dca8d108142661c37/Images/macOS/MDEMacOS-UI1.png)

2. You will see Defender for macOS application launch. In this interface, you can view key status details, including:  
   -   Protection History (Detected threats details)
   -   AV Scan History
   -   Protection Settings (such as real-time protection and exclusions)
   -   Signature Update Status  
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/31330673aa411c6f4395a21dca8d108142661c37/Images/macOS/MDEMacOS-UI2.png)

## Step 2: Verifying MDE installation using the terminal (mdatp health command)

1.  Open Launchpad, then search for **Terminal**. Once it's found, click to launch and start the Terminal.
2.  Type the following command and press Enter:
    ```sh
    mdatp health
    ```
3.  Review the MDE health status details. If MDE on macOS is running correctly, the healthy status should be set to true.
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/4fbe5e76c8e8128aa2a6390d6db4c0fb20af52bf/Images/macOS/MDEmacOS-CLI1.png)
       > If you'd like to learn about each returned value and its description for the *mdatp health* command, please refer to the [public documentation](https://learn.microsoft.com/en-us/defender-endpoint/mac-health-status) 
4.  Additional step (option 1):  
    To see more options for the health command, run the following command:    
    ```sh
    mdatp health --help
    ```
     ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/2b1b79e008d6081ed760683a624f7cbf7f2fd1fc/Images/macOS/MDEmacOS-CLI3.png)

5. Additional step (option 2):  
   The mdatp command offers many configuration options. To view the built-in help and a list of available command-line references, run the following command:
    ```sh
    mdatp --help
    ```
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/4fbe5e76c8e8128aa2a6390d6db4c0fb20af52bf/Images/macOS/MDEmacOS-CLI2.png)  

    Also check folloing [public documentation](https://learn.microsoft.com/en-us/defender-endpoint/mac-resources#configuring-from-the-command-line) for details    
    

## Step 3: Checking the macOS device inventory in Defender Portal

1. Open [Microsoft Defender portal](https://security.microsoft.com)
2. Navigate to **Assets** > **Devices**
3. On the **Device Inventory** page, click the **Computers & Mobile** tab.
4. Locate your macOS device in the list of devices. If nessesary use the **search box** or **filter options**:
   -   Click **filter** menu
   -   Select **macOS** under **OS platform**
   -   Click Apply button.
6. Click the device name to view its details
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/08328932b1a481db1ca843d4b3d4b2180b80c174/Images/macOS/MDEmacOS-DeviceInventory1.png)

## Enabled feature by default (Without policy assignment)

Below features are enabled by default (You can change settings via Intune, MDE-attach or command line)
- Real Time protection
- Behavior Monitoring
- Tamper Protection

I will cover security settings in other article.



