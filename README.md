READ THIS README.MD FIRST BEFORE DOWNLOAD THE EFI.

Don't clone the repository. Just click [here](https://github.com/log1cs/OpenCore-0.6.4-STABLE-Vostro3568/releases) and after that you can find the download sections.
I'll upload the issue in [here](https://github.com/log1cs/OpenCore-STABLE-Vostro3568/issues)

![Alt text](https://user-images.githubusercontent.com/60842977/147896099-d8449ccf-ed32-42b1-bbf1-b00fc25627ca.png)

OpenCore for Monterey on Vostro 3568 (Stable version)

Just copy the EFI folder and paste it in your EFI partition.

About the specs:
 
| Specs | Info |
|----------|----------|
| **RAM** | 4GB DDR4 2133 x1 + 1x 4GB DDR4 2400 x1 |
| **CPU** | Intel Core i3-7020u (2 cores 4 threads) 2.3 GHz |
| **Audio** | Realtek ALC256 Audio Controller |
| **Ethernet** | Realtek RTL8111 |
| **Wi-Fi Card** | Intel Dual Band AC-3165 |
| **GPU** | Intel(R) HD Graphics 620 |
| **SMBIOS** | MacBookPro14,1 |



| Feature | Status | Notes |
| ------------- | ------------- | ------------- |
| **Intel iGPU** | ✅ Working | Intel HD 620 is detected as Intel HD Graphics KBL CRB but nevermind, it's not an error |
| **Trackpad I2C** |  ✅ Working | Full gesture support.| 
| **iMessages and App Store** | ✅ Working | Just follow the OpenCore Guide (#ℹ️-changing-serial-number,-board-serial-number-and-smuuid) |
| **Speakers and Headphones** | ✅ Working | To permanently fix headphones follow this [link](https://github.com/hackintosh-stuff/ComboJack) below |
| **Built-in Microphone** | ✅ Working |
| **Webcam** | ✅ Working | Fully working, is detected as Integrated Webcam |
| **Wi-Fi/BT** | ✅ Working | The stock AC3165 Wi-Fi card is working perfectly fine with newest kext Airportitlwm from zxystd. But I recommend using another card like DW1560 or DW1820A for better experiences. |
| **Fingerprint reader** | ❌ Not working | Probably will never work, because proprietary Synaptics drivers that only exist for Windows are needed. Will patch to disable it. |
| **SD Reader** | ❌ Not working | The USB2.0 SDCard Reader from Realtek will never work on Mac because drivers is only for Windows. Will patch to disable it. |
| **Ethernet** | ✅ Working perfectly |


FOR BATTERY OPTIMIZATION USE THIS GUIDE: ~~(I've added this kext but you can edit with yours, whatever)~~. I REMOVED THIS KEXT SINCE IT CAUSES PERFORMANCE ISSUES ON MONTEREY, HUGE PERFORMANCE DROP. YOU CAN ADD THIS KEXT MANUALLY, THAT DEPENDS ON YOU.
https://github.com/stevezhengshiqi/one-key-cpufriend 

+ Guide :

1. Run this command in Terminal:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/stevezhengshiqi/one-key-cpufriend/master/one-key-cpufriend.sh)"
```

**Cause we're using OpenCore, install using this guide:**

  - Copy `CPUFriend.kext` and `CPUFriendDataProvider.kext` from desktop to `/OC/Kexts/`.
  - Open `/OC/config.plist` and add the following code:
```xml
<dict>
    <key>Arch</key>
    <string>x86_64</string>
    <key>BundlePath</key>
    <string>CPUFriend.kext</string>
    <key>Comment</key>
    <string>Power management data injector</string>
    <key>Enabled</key>
    <true/>
    <key>ExecutablePath</key>
    <string>Contents/MacOS/CPUFriend</string>
    <key>MaxKernel</key>
    <string></string>
    <key>MinKernel</key>
    <string>12.0.0</string>
    <key>PlistPath</key>
    <string>Contents/Info.plist</string>
</dict>
<dict>
    <key>Arch</key>
    <string>x86_64</string>
    <key>BundlePath</key>
    <string>CPUFriendDataProvider.kext</string>
    <key>Comment</key>
    <string>Power management data</string>
    <key>Enabled</key>
    <true/>
    <key>ExecutablePath</key>
    <string></string>
    <key>MaxKernel</key>
    <string></string>
    <key>MinKernel</key>
    <string>12.0.0</string>
    <key>PlistPath</key>
    <string>Contents/Info.plist</string>
</dict>
```


FOR AUDIO FIXING USE THIS GITHUB REPO AND FOLLOW THE INSTRUCTIONS: 
https://github.com/hackintosh-stuff/ComboJack

Cause I've added this kext in EFI folder so you don't need to add it anymore.

+ Guide :
1. Run ComboJack_Installer/install.sh in terminal and reboot
2. Done. When you attach a headphone there will be a popup asking about headphone type.

## Credits:

- Thanks to [Acidanthera](https://github.com/acidanthera) and [PMHeart](https://github.com/PMHeart) for providing [CPUFriend](https://github.com/acidanthera/CPUFriend).

- Thanks to [stevezhengshiqi](https://github.com/stevezhengshiqi) for providing CPUFriend script.

- Thanks to ComboJack cause this providing headphones script to fix "reeeee" sounds when you connect the headphones in ALC256.
