# 3: Create the MDE application package

## What's covered in this section
- Create Defender for Endtpoint (MDE) applicatino package for macOS in Intune portal

## Prerequistie
- Access permission to Intune portal

## Step 1: Create MDE App package

1. Open [Intune portal](https://aka.ms/memac)
2. Go to **Apps** > **Monitor** > **Platforms** > **macOS**
3. Click **Create** button.
4. Click pull down menu in **App type** and you will see a list of apps. Select **macOS** under **Microsoft Defender for Endpoint**.
   ![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/53df410b8f67843b24d025c6f4075d352d98d77d/images/macOS/Create-MDE-App-Package1.png)
6. You will see **Microsoft Defender for Endpoing (macOS)**. Click **Select** to continue.
   ![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/3f72e06889878c0cff0494bb7c8bef0fc17aaee4/images/macOS/Create-MDE-App-Package2.png)
7. In **App information** page, use default value and click **Next** (Of course you can choose to change if needed)
   ![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/c830698dd1b9235f4d9edc6f4e0ef8948dab29ce/images/macOS/Create-MDE-App-Package3.png)
8. In **Scope tag** page, click **Next**. (You can set scope tag if you need)
9. In **Assignments** page, click **Add group** under Required
10. Select your device group. In my case "MDE macOS devices" group created in previous step and click **select** button
    ![image alt](https://github.com/yujiaoMSFT/mde-temp/blob/77970cbd2eb62c38a1e0096f0bf1dc93e3d714b9/images/macOS/Create-MDE-App-Package4.png)
11. Click **Next**
12. Click **Create**.
13. Go to **Apps** > **Monitor** > **Platforms** > **macOS** and confirm MDE app is created.


## Note
use below if we skip assignment
9. In **Assignments** page, click **Next** at this moment. (We will app assignments to the device group later, so fo now, let's skip this process)
