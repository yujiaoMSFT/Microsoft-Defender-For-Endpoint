# 1: Prepare macOS device for Defender for Endpoint (MDE)

## What's covered in this section
This section outlines the prerequisites for deploying MDE for macOS, including:
- Supported macOS versions
- Network prerequisites and connectivity validation
- Licensing prerequisites
- Portal access and required roles

## System requirements
Microsoft Defender for Endpoint (MDE) on macOS is supported on the three most recent major release versions for both Intel and ARM chip:
- macOS 26 (Tahoe)
- macOS 15.0.1 (Sequoia)
- macOS 14 (Sonoma)
  
> This document was tested using following devcies  
> - a Mac mini running macOS Sequoia 15.5 with an Apple M4 chip.  
> - a MacBook Air running macOS Tahoe 26.0.1 with an Apple M4 chip.  
> The user interface may vary depending on your macOS version.  
> Please note that the macOS user interface may differ if you are using a different version of macOS.*  
> MDE does not support beta version of MacOS. The new macOS version will be supported on Day 1 of its General Availability (GA) release.*

## Network requirements
To ensure proper connectivity for MDE on macOS, review the official documentation:  
 https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#network-connectivity  
 https://learn.microsoft.com/en-us/defender-endpoint/configure-environment  
 
You can test connectivity using either a browser or the command line.

**Test from browser.**  
Access the following URLs:
>  https://x.cp.wd.microsoft.com/api/report  
>  https://cdn.x.cp.wd.microsoft.com/ping

If successful, you will see an OK message.
![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/475f6b6767a0e4b75a419374000bceb22b81872c/Images/macOS/NetworkAccessTest-Browser.png)

**Test from command line.**  
Run the following command in Terminal:

 ```sh
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
 ```
A successful test will return an OK message..
![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/640d73e0452a31e36b7e39a3d048a10d71a25f59/Images/macOS/NetworkAccessTest-Terminal.png)

## License requirements
To follow the deployment method described in this guide, you will need licenses for both **Microsoft Intune** and **Microsoft Defender for Endpoint**.
Supported license options include:
- Microsoft 365 E5 (*Includes Microsoft Intune and Defender for Endpoint Plan 2*)
- Microsoft 365 E3 (*Includes Microsoft Intune and Defender for Endpoint Plan 1*)
- Microsoft Defender for Endpoint Plan 2 or Plan 1
- Microsoft intune 

To assign license to the user, refer to the official guide:  
https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide

> *Defender for Endpoint Plan 1 provides antivirus (AV) functionality but does not include capabilities such as endpoint detection and response (EDR), Threat & Vulnarability management and Advanced Hunting.*  
> *For more details about MDE Plan 1, please refer to the [Overview of Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1).*

## Device Entolled to Intune
Your macOS device must be enrolled to **Microsoft Intune**.  
You can refer to the [Microsoft Intune enrollment documentation](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/macos-enroll).


## Access permissions to portal & API
To complete the setup, ensure access to both **Microsoft Intune** and **Microsoft Defender Portal**.
In this guide, an Entra ID account was created and assigned the following roles:

**Microsoft Intune portal & Grahp API**  
Assigned the account to the Intune Administrator role under Entra ID built-in roles.  
This account is designated for accessing the Intune portal and utilizing the Microsoft Graph API.  
See : [Microsoft Entra built-in roles - Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)

**Microsoft Defender portal**  
Use [Microsoft Defender XDR Unified role-based access control (RBAC)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) and assign following permissions.  
-  Security operators (All read and manage permissions)
-  Security posture  (All read and manage permissions)
-  Authorization and settings (All read and manage permissions)

See: [Permissions in Microsoft Defender XDR Unified role-based access control (RBAC)](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details)

***
## Go to next section
Once completed, go to next section [2. Deploy MDE configuration settings (using Graph API)](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/main/macOS/Deploy-MDE-macOS-with-Intune/2_Deploy_MDE_Configuration_Files.md)
