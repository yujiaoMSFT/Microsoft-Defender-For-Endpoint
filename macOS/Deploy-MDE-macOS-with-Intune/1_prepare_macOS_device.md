# 1: Prepare macOS device for Defender for Endpoint (MDE)

## System requirements
Microsoft Defender for Endpoint (MDE) on macOS is supported on the three most recent major release versions for both Intel and ARM chipsets:
- macOS 15.0.1 (Sequoia)
- macOS 14 (Sonoma)
- macOS 13 (Ventura)
  
> *This document was created using a Mac mini running macOS 15.5 with an Apple M4 chip.  The user interface may vary depending on your macOS version.*
> *Please note that the macOS user interface may differ if you are using a different version of macOS.*

## Network requirements
To ensure proper connectivity for MDE on macOS, review the official documentation:  
 https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#network-connectivity  
 https://learn.microsoft.com/en-us/defender-endpoint/configure-environment  
 
You can test connectivity using either a browser or the command line.

**Test from browser.**  
Access the following URLs:
>  https://x.cp.wd.microsoft.com/api/report  
>  https://cdn.x.cp.wd.microsoft.com/ping

If successful, you’ll see an OK message.
![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/475f6b6767a0e4b75a419374000bceb22b81872c/Images/macOS/NetworkAccessTest-Browser.png)

**Test from command line.**  
Run the following command in Terminal:

 ```sh
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
 ```
A successful test will return an OK message..
![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/640d73e0452a31e36b7e39a3d048a10d71a25f59/Images/macOS/NetworkAccessTest-Terminal.png)

## License requirements
To follow the deployment method described in this guide, you’ll need licenses for both **Microsoft Intune** and **Microsoft Defender for Endpoint**.
Supported license options include:
- Microsoft 365 E5 (*Includes Microsoft Intune and Defender for Endpoint P2*)
- Microsoft 365 E3 (*Includes Microsoft Intune and Defender for Endpoint P1*)
- Defender for Endpoint Plan 2 or Plan 1
- MIcrosoft intune 

To assign license to the user, refer to the official guide:  
https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide

## Portal access
To complete the setup, ensure access to both **Microsoft Intune** and **Microsoft Defender Portal**.
In this guide, an Entra ID account was created and assigned the following roles:

**Microsoft Intune**
Added the account to Endpoint Security Manager role (Intune built-in role)  
See: [Role-based access control with Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/role-based-access-control)

**Microsoft Defender for Endpoint**  
Use [Microsoft Defender XDR Unified role-based access control (RBAC)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) and assign following permissions.  
-  Security operators (All read and manage permissions)
-  Security posture  (All read and manage permissions)
-  Authorization and settings (All read and manage permissions)

See:[Permissions in Microsoft Defender XDR Unified role-based access control (RBAC)](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details)

