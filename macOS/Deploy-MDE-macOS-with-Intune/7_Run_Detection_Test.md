# 7: Run Detection Test

## What's covered in this section
- Perform the following detection tests to validate MDE detection capabilities on macOS:
    - Antivirus (Real-Time Protection)
    - Antivirus (Behavior Monitoring)
    - EDR (Endpint Detection & Response)

## Detection test 1: Antivirus (Real Time Pritection - aka RTP)

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

1. Open the [Microsoft Defender portal](https://security.microsoft.com)
2. Navigate to **Incidents & alerts** > **Incidents**
3. A new indident should be listed.
  ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/a2af008515d23c94ce6d090ec117654681c472fa/Images/macOS/MDEmacOS-Incident1.png)
4. Click the indident name to view full details.
  ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/a2af008515d23c94ce6d090ec117654681c472fa/Images/macOS/MDEmacOS-Incident2.png)
5. Once the investigation has completed, click **Manage Incident**.
   - Set the **status** to **Resolved**.
   - Set the **classfication** as **Security testing**
   - Click Save to close the incident.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/5dde3b3c2d5fefee019f7cd89dc16780ea891c89/Images/macOS/MDEmacOS-Incident3.png)

https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware

## Detection test 2: Anttivirus (Behavior moniroing)

### Step 1: Verify Behavior Monitoring status

Run below command in terminal to confirm Behavior Monitoirng status
```sh
mdatp health --details features
```
You will see status of Behavior Monitoirng
```sh
behavior_monitoring     :"enabled"
```

> By default configuration, Behavior Monitoirng is disabled.  
> You can run following command to enable it.
```sh
sudo mdatp config behavior-monitoring --value enabled
```
### Step 2: Create Test file for Behavior Monitoirng detection

https://learn.microsoft.com/en-us/defender-endpoint/demonstration-behavior-monitoring

## Detection test 3: EDR (
- EDR functionality
https://learn.microsoft.com/en-us/defender-endpoint/edr-detection
