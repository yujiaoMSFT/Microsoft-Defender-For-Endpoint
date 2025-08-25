# 7: Run detection test

## What's covered in this section
- Run detection test to verify deteciton capability (AV, EDRM, Behavior Monitoring)
- Run a detection test to confirm successful onboarding


## Run detection test

## Detection test - Antivirus (Real Time Pritection - aka RTP)

### Step 1: Verify Real Time Protection (RTP) status
Run below command in terminal to confirm real time protection status
```sh
mdatp health --field real_time_protection_enabled
```
If real-time protection is enabled, the output will be *true*.  

> By default configuration, Real time protection is enabled.  
> If RTP is disabled, you can run following command to enable it.
enable
```sh
sudo mdatp config real_time_protection_enabled --value enabled
```

### Step 1: Downlaod test file (Eicar) for detection
Run below command in termina
```sh
curl -o ~/Downloads/eicar.com.txt https://secure.eicar.org/eicar.com.txt
```


You can veriry detected malicious file by following.
**Defender on macOS UI**


**Terminal**  
```sh
mdatp threat list
```
**Defender Portal**
Incident page

https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware

## Detection test -  Anttivirus (Behavior moniroing)

### How to verify BM is enabled
Before testing of Behavior Monitoring, make sure the feature is enabled on the device.

You can run below command in terminal to verify the status.
```sh
mdatp health --details features
```
You will see status of Behavior Monitoirng
```sh
behavior_monitoring     :"enabled"
```
Enabling / disabling Behavior monitoing  
enable
```sh
sudo mdatp config behavior-monitoring --value enabled
```
disable
```sh
sudo mdatp config behavior-monitoring --value disabled
```

https://learn.microsoft.com/en-us/defender-endpoint/demonstration-behavior-monitoring

## Detection test - EDR
- EDR functionality
https://learn.microsoft.com/en-us/defender-endpoint/edr-detection
