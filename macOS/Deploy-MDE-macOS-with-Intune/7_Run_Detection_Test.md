# 7: Run detection test

## What's covered in this section
- Run detection test to verify deteciton capability (AV, EDRM, Behavior Monitoring)
- Run a detection test to confirm successful onboarding

## Detection test - Antivirus (Real Time Pritection - aka RTP)

### Step 1: Verify Real Time Protection (RTP) status
Run below command in terminal to confirm real time protection (RTP) status
```sh
mdatp health --field real_time_protection_enabled
```
If RTP is enabled, the output will be *true*.  

> By default configuration, RTP is enabled.  
> If RTP is disabled, you can run following command to enable it.
```sh
sudo mdatp config real_time_protection_enabled --value enabled
```

### Step 2: Downlaod test file (Eicar) for detection
Run below command in termina
```sh
curl -o ~/Downloads/eicar.com.txt https://secure.eicar.org/eicar.com.txt
```

### Step 3: Verify detected malicious file (Defender macOS UI)

1. Launch the ""MDE for macOS** application on your device.
2. Click **Protection History** in the app
3. Under **Quarantined threats**, confirm that the quarantined file is listed.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/1d7a74bf9fe05a45b09bd40c21226cc70fae31e7/Images/macOS/AVDetection-macOS1.png)
4. Click **See details**. (You will be promptedd to enter your **administrator credentials**)
6. Review the additional information about the quarantined file.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/1d7a74bf9fe05a45b09bd40c21226cc70fae31e7/Images/macOS/AVDetection-macOS2.png)

### Step 4: Verify detected malicious file (Terminal)
1. Open terminal on your macOS device.
2. Run the following command:
   ```sh
   mdatp threat list
   ```
3. You will see the file details displayed, similar to the example screenshot below:
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/1d7a74bf9fe05a45b09bd40c21226cc70fae31e7/Images/macOS/AVDetection-CLI1.png)

### Step 5: Verify Incident / Alert in Defender Portal

You can veriry by following.
**Defender on macOS UI**


**Terminal**  

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
