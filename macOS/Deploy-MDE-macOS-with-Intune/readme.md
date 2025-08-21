# Deploying Defender for Endpoint for macOS using Microsoft Intune

## Disclaimar
The information provided in this guide is for general informational purposes only and reflects the author's personal experience and understanding at the time of writing. It does not represent official guidance from Microsoft. Readers should consult official Microsoft documentation and support channels for the most accurate and up-to-date information. The author and publisher disclaim any liability for errors or omissions and shall not be held responsible for any consequences arising from the use of this content.

## Overview
Deploying Microsoft Defender for Endpoint (MDE) on macOS can be accomplished in several ways: manual installation, using management tools like Intune, Jamf, or other third-party solutions. This guide focuses on deployment via Microsoft Intune, with additional automation using the Graph API to streamline repetitive tasks. Whether you’re setting up a proof-of-concept (POC) or deploying at scale, these steps will help you simplify and accelerate the process.

Deploying Microsoft Defender for Endpoint (MDE) on macOS can be accomplished through various methods, including manual installation, Microsoft Intune or third-party tools such as Jamf. This guide focuses on deployment via **Microsoft Intune**, with optional automation using the **Microsoft Graph API** to streamline repetitive tasks. Whether you're setting up a proof-of-concept (POC) or rolling out at scale, these steps will help simplify and accelerate your deployment.

## What you will learn
- How to deploy and configure MDE for macOS devices using Microsoft Intune.
- Step-by-step instructions from device registration to app deployment and configuration.
- How to leverage the Intune Graph API to automate and simplify repetitive administrative tasks.
- Tips for quickly setting up a test environment.

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
| 1 | [Prepare your macOS device](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/21bb061f08ad452f0433a2152521e6be31ea472a/macOS/Deploy-MDE-macOS-with-Intune/1_prepare_macOS_device.md) | TBD|
| 2 | [Enroll the device with Intune](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/b761dc1254cd93a85a99bfd045d5774a5fa3c566/macOS/Deploy-MDE-macOS-with-Intune/2_Enroll_device_with_Intune.md) | TBD|
| 3 | [Deploy MDE application package](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/753734989e691e2b7818fa9c9b9a151474fd8038/macOS/Deploy-MDE-macOS-with-Intune/3_Deploy_MDE_App_Package.md) | TBD |
| 4 | [Deploy MDE configuration settings (using Graph API)](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/753734989e691e2b7818fa9c9b9a151474fd8038/macOS/Deploy-MDE-macOS-with-Intune/3_Deploy_MDE_App_Package.md) | TBD |
| 5 | Download the onboarding package and create the onboarding policy | TBD |
| 6 | Assign the application and configuration to your target group | TBD | 
| 7 | Verify installation and run a detection test | TBD | 

