# 3: Deploy MDE application package

## What's covered in this section
- Create an MDE application package for macOS in the Intune portal and assign it to the target group.
- Verify MDE application package deployment status in Intune portal

## Step 1: Create MDE App package and assign it to the group

1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Apps** > **Monitor** > **Platforms** > **macOS**
3. Click **Create** button.
4. Click pull down menu in **App type** and you will see a list of apps.  
   Select **macOS** under **Microsoft Defender for Endpoint**.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage1.png)
6. You will see **Microsoft Defender for Endpoing (macOS)**.  
   Click **Select** to continue.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage2.png)
7. In **App information** page, use default value and click **Next** (Of course you can choose to change if needed)
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage3.png)
8. In **Scope tag** page, click **Next**. (You can set scope tag if you need)
9. In **Assignments** page, click **Add group** under Required
10. Select your device group. In my case "MDE macOS devices" group created in previous step and click **select** button
    ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage4.png)
11. Click **Next**
12. Click **Create**.

## Step 2: Verify MDE App package deployment

> It may take some time for the installation status to update in the Intune portal.  
> You can proceed to the next section and return later to verify the installation status.

1. In **Intune portal**, go to **Apps** > **Monitor** > **Platforms** > **macOS**
2. Click on the **MDE app** from the applications.
3. Review the **installaiton status** of MDE application.
   ![image alt](https://github.com/yujiaoMSFT/Microsoft-Defender-For-Endpoint/blob/0c640afed88d27c95f61c2e0e4ae21f58cf786ef/Images/macOS/IntuneMDEAppPackage5.png)
