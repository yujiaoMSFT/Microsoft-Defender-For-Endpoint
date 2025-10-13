# 7: Run Detection Test

## What's covered in this section
- Perform the following detection tests to validate MDE detection capabilities on macOS:
    - Antivirus (Real-Time Protection)
    - Antivirus (Behavior Monitoring)
    - EDR (Endpint Detection & Response)

## Detection test 1: Antivirus (Real Time Pritection - aka RTP)

### Step 1: Verify Real Time Protection (RTP) status
Open **Terminal** and run the following command to check the status of Real-Time Protectin (RTP).
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
Run below command in terminal
```sh
curl -o ~/Downloads/eicar.com.txt https://secure.eicar.org/eicar.com.txt
```

### Step 3: Verify detected malicious file (Defender macOS UI)

1. Launch the **MDE for macOS** application on your device.
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

**Reference:**  
[Antivirus detection test for verifying device's onboarding and reporting services](https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware)

## Detection test 2: Anttivirus (Behavior moniroing)
> **Behavior Monitoring for MDE on macOS is reached General Availability (GA) in June 2025**.  
> For more details, Please refer to official [blog announcement](https://techcommunity.microsoft.com/blog/microsoftdefenderatpblog/behavior-monitoring-is-now-generally-available-for-microsoft-defender-for-endpoi/4415697) and [public document](https://learn.microsoft.com/en-us/defender-endpoint/behavior-monitor-macos)

### Step 1: Verify Behavior Monitoring status
Open **Terminal** and run the following command to check the status of Behavior Monitoirng.
```sh
mdatp health --details features
```
You will see status of Behavior Monitoirng
```sh
behavior_monitoring     :"disabled"
```

By default, Behavior Monitoirng is **disabled**.  To enable it run the following command
```sh
sudo mdatp config behavior-monitoring --value enabled
```
### Step 2: Create a Test file for Behavior Monitoirng Detection

1. Open **Terminal** on your macOS device.
2. Run the following command to create a test script file:
   ```sh
   touch BM_test.sh
   ```
3. Open a file in **nano editor**.
   ```sh
   nano BM_test.sh
   ```
4. Paste the following text to the editor.
    ```sh
   #! /usr/bin/bash
   echo " " >> /tmp/9a74c69a-acdc-4c6d-84a2-0410df8ee480.txt
   echo " " >> /tmp/f918b422-751c-423e-bfe1-dbbb2ab4385a.txt
   sleep 5
    ```
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/e03beaf8c890116d2e603651f3506752222ce57b/Images/macOS/CreateBMTestFile1.png))
6. Press **control + X** to exit, then press **Y** and **Enter** to save the file.
7. Run following command to verify script content.
   ```sh
   cat BM_test.sh
   ```
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/e03beaf8c890116d2e603651f3506752222ce57b/Images/macOS/CreateBMTestFile3.png)
8. Run following command to make the script executable
   ```sh
   sudo chmod u+x BM_test.sh
   ```
9. Run the script
    ```sh
    sudo bash BM_test.sh
    ```
### Step 3: Verify detected malicious file (Defender macOS UI)

1. Launch the **MDE for macOS** application on your device.
2. Click **Protection History** in the app
3. Under **Quarantined threats**, confirm that the quarantined file is listed. (Category is *Suspicious Behavior*)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/c2cb350ce611d0c6edcead1e575874c86d515b1b/Images/macOS/AVDetection-macOS3.png)
4. Click **See details**. (You will be promptedd to enter your **administrator credentials**)
6. Review the additional information about the quarantined file. (Type is *Process*)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/c2cb350ce611d0c6edcead1e575874c86d515b1b/Images/macOS/AVDetection-macOS4.png)

### Step 4: Verify detected malicious file (Terminal)
1. Open terminal on your macOS device.
2. Run the following command:
   ```sh
   mdatp threat list
   ```
3. You will see the file details displayed, similar to the example screenshot below:
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/d8e83f916ebc0dda5b171632a22a990d8703422b/Images/macOS/AVDetection-CLI2.png)
   
### Step 5: Verify Incident / Alert in Defender Portal

1. Open the [Microsoft Defender portal](https://security.microsoft.com)
2. Navigate to **Incidents & alerts** > **Incidents**
4. Click the indident name to view full details.
  ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/d8e83f916ebc0dda5b171632a22a990d8703422b/Images/macOS/MDEmacOS-Incident5.png)

 
**Reference:**  
[Behavior Monitoring demonstration](https://learn.microsoft.com/en-us/defender-endpoint/demonstration-behavior-monitoring)

## Detection test 3: EDR (Endpoint Detection and Response)
> EDR functionality is available only with a **Defender for Endpoint Plan 2 (P2)** or **Defender for Business (MDB)** license.  
> If you are using **Defender for Endpoint Plan 1 (P1)**, EDR capabilities are **not included**.

1. Open your browser and go to https://aka.ms/mdatpmacosdiy.
2. The **MDATP MacOS DIY** file will be downloaded.
3. Right click click the downloaded file, and select **open**.
   >  If your macOS device uses an Apple M-series chipset, you may be prompted to install Rosetta. Click Install (you will need to enter your administrator credentials).
4. After Rosetta is installed, right-click the file again and select Open to proceed.
5. Open [Defender portal](https://security.microsoft.com) and verify that an incident titled **macOS EDR Test Alert** has been created. 
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/6aa2b122c8d783c577e193bb536e29d3ec4d3c2f/Images/macOS/MDEmacOS-Incident4.png)
6. Review at the alert details and the device timeline, and perform the regular investigation steps.
   
**Reference:**  
[EDR detection test for verifying device's onboarding and reporting services](https://learn.microsoft.com/en-us/defender-endpoint/edr-detection)
