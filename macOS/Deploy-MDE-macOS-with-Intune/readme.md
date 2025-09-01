# Deploying Defender for Endpoint for macOS using Microsoft Intune

## Disclaimar
The information provided in this guide is for general informational purposes only and reflects the author's personal experience and understanding at the time of writing. It does not represent official guidance from Microsoft. Readers should consult official Microsoft documentation and support channels for the most accurate and up-to-date information. The author and publisher disclaim any liability for errors or omissions and shall not be held responsible for any consequences arising from the use of this content.

## Overview
Deploying **Microsoft Defender for Endpoint (MDE) for macOS** can be accomplished in several ways: manual installation, using management tools like Intune, Jamf, or other third-party solutions. This guide focuses on deployment via **Microsoft Intune**, with additional automation using the **Microsoft Graph API** to streamline repetitive tasks. Whether you’re setting up a proof-of-concept (POC) or deploying at scale, these steps will help you simplify and accelerate the process.

## What you will learn
- How to deploy and configure MDE for macOS devices using Microsoft Intune.
- Step-by-step instructions from device registration to app deployment and configuration.
- How to leverage the Intune Graph API to automate and simplify repetitive administrative tasks.
- How to validate AV (Antivirus) and EDR (Endpoint Detection & Response) capablities by using simulation files.

## Who should read this?
- IT administrators managing macOS devices with Intune and planning to deploy MDE.
- Anyone looking to reduce manual configuration in Intune by using the Graph API.

## Prerequisties
- Appropriate Microsoft licenses for Intune and MDE.
- A macOS device meeting the minimum OS requirements.
- Network connectivity as required by Intune and MDE.
- Access to the Intune portal and Defender portal.

## High level steps
The table below outlines the key steps for deploying MDE on macOS using Intune. Click each link for detailed instructions:

| No | Section | Desctiption | 
| ------ | ------ | ------ |
| 1 | [Prepare your macOS device](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/21bb061f08ad452f0433a2152521e6be31ea472a/macOS/Deploy-MDE-macOS-with-Intune/1_prepare_macOS_device.md) | Prepare your macOS device by ensuring OS compatibility, network connectivity, proper licensing, and portal access with required roles for Defender for Endpoint deployment via Intune.|
| 2 | [Enroll the device with Intune](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/b761dc1254cd93a85a99bfd045d5774a5fa3c566/macOS/Deploy-MDE-macOS-with-Intune/2_Enroll_device_with_Intune.md) | Enroll macOS in Intune (BYOD), install Company Portal, sign in, and create a device group for deploying Defender for Endpoint and managing policies.|
| 3 | [Deploy MDE application package](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/753734989e691e2b7818fa9c9b9a151474fd8038/macOS/Deploy-MDE-macOS-with-Intune/3_Deploy_MDE_App_Package.md) | Create and assign the MDE app package to your macOS device group in Intune, then verify deployment status in the portal to ensure successful installation. |
| 4 | [Deploy MDE configuration settings (using Graph API)](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/753734989e691e2b7818fa9c9b9a151474fd8038/macOS/Deploy-MDE-macOS-with-Intune/3_Deploy_MDE_App_Package.md) | Use a PowerShell script with Graph API to automate deployment of MDE macOS configuration profiles in Intune, saving time over manual setup. |
| 5 | [Deploy MDE onboarding package](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/a4a36628529268238f43020ee1a619e3baaf7046/macOS/Deploy-MDE-macOS-with-Intune/5_Deploy_MDE_Onboarding_Package.md) | Download and deploy the MDE onboarding package via Intune to complete macOS setup. Without it, devices show license errors and MDE won’t function properly. |
| 6 | [Verify installaton](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/4dbedf239c2769502ff9f41b052b9ef6f88434ab/macOS/Deploy-MDE-macOS-with-Intune/6_Verify_Installation.md) | Verify MDE installation via macOS UI, terminal commands, and Defender portal device inventory to ensure successful onboarding and active protection. | 
| 7 | [Run a detection test](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/46001444f000f2161777b315e92a05841b4c0455/macOS/Deploy-MDE-macOS-with-Intune/7_Run_Detection_Test.md) | Run antivirus, behavior monitoring, and EDR tests to validate MDE detection on macOS via UI, terminal, and Defender portal. EDR requires P2 or MDB license. | 

