# 6: Verify Installation

## What's covered in this section
- Check that MDE is installed and running on your macOS device.  
- Run a detection test to confirm successful onboarding

> This document was created using a Mac mini running macOS 15.5 with an Apple M4 chip.  
> Please note that the macOS user interface may differ if you are using a different version of macOS.

Once all onboarding processes are completed, let's verify it on macOS device.

## Installation check (macOS User Interface)
In the task bar, you will see Defender icon.  Now lets click **Open Microsoft Defender** to launch Defender application.
![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/d184d056be905a9f2b8ab98055738b89483134d9/images/MDE-MacOS-macOS-UI2.png)

You will see Defender for macOS application launch.
![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/5fbcdb58ada164b6c4c14940589d55495240bd52/images/MDE-MacOS-macOS-UI4.png)

To verify policy assignment, navigate to **System Settings** > **General** > **Device Management** in the macOS user interface.

![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/8d80da4ce91666ebe0a3bde63e4f05dea7917c8a/images/MDE-MacOS-DeviceManagement.png)

Also check folloiwng location
 **System Settings** > **Privacy & Security** > **Full Disk Access**  
 **System Settings** > **Privacy & Security** > **File & Folders**

## Installation check (Command line Interface)

Run mdatp health command
  
![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/e32b2413d3130f2605127b619394dbc5dc4ea833/images/MDE-MacOS-MDATP-Health.png)

- Troubleshooting

## Defender Portal

Check device inventory
Response actions

## Enabled feature by default (Without policy assignment)

Below features are enabled by default (You can change settings via Intune, MDE-attach or command line)
- Real Time protection
- Behavior Monitoring
- Tamper Protection

I will cover security settings in other article.



