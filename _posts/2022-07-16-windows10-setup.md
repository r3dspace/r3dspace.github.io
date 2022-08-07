---
title: Windows 10 fresh install & setup
date: 2022-07-16 17:00:00 +0100
categories: [os, windows]
tags: [install, setup]     # TAG names should always be lowercase
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed ornare sapien sed nulla ornare, in aliquam lectus porta. Aenean bibendum porttitor aliquam. Phasellus sed pretium nisl. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Etiam ultrices sem enim. Etiam felis tellus, scelerisque vel nisl et, dictum aliquam eros. Sed nec efficitur nisi. Quisque accumsan, lectus et interdum tincidunt, tortor nunc rhoncus tortor, sit amet finibus justo ex sed ipsum. Suspendisse sem enim, lacinia in elit eu, mattis blandit ante. Donec vitae diam lacus.


## **Depemdemcies**

For everything to work out you will need to make sure that you have the following requirements:

* USB-drive with atleast 8 GB of space
* Recomended to have Windows 10 Pro lizen
* ...

If this is the case we can carrie on creating a bootable Windows installation drive.


## **Creat installation media**

Download the Windows [media creation tool](https://www.microsoft.com/de-de/software-download/windows10) from Microsoft. After completing the download run the `MediaCreationToolXXXX.exe`.

1. Click on `Accept`

![media creation tool](/assets/img/win-setup/media-creation-tool-1.png){: .shadow w="500" h="200" }

2. Select `Create installation media (USB flash drive, DVD or ISO file) for another PC` and the click on `Next`

![media creation tool](/assets/img/win-setup/media-creation-tool-2.png){: .shadow w="500" h="200" }

3. The tool will by default select the host language. If you want to change this just deselect the `Use the recommended options for this PC` and select your prefered Language from the dropdown. Afterwards you can click on `Next`

![media creation tool](/assets/img/win-setup/media-creation-tool-3.png){: .shadow w="500" h="200" }

4. Leave the option `USB flash drive` selected and click on `Next`

![media creation tool](/assets/img/win-setup/media-creation-tool-4.png){: .shadow w="500" h="200" }

5. Select your USB flash drive, in my case it is the drive with the letter `G` and the name `YOUR USB`. Then click `Next`
> If you are unsure on what the right usb drive is, remove all other USB drives and press on the `Refresh drive list` text. Only external USB drives will be shown in the list NO internal drives
{: .prompt-tip }

![media creation tool](/assets/img/win-setup/media-creation-tool-5.png){: .shadow w="500" h="200" }

6. Now we need to wait. This make several minutes, depending on your internet connection and the speed of your computer

![media creation tool](/assets/img/win-setup/media-creation-tool-6.png){: .shadow w="500" h="200" }

7. To finish up press the `Finish` button and then remove your USB drive

![media creation tool](/assets/img/win-setup/media-creation-tool-7.png){: .shadow w="500" h="200" }


## **Installing Windows**

To boot from your USB drive turn on your computer and enter the boot menu by spamming one of the following keys `ESC, F1, F8 ,F9, F10, F11, F12 or Delete`

> If you are unsure on what the right button for the boot menu is, visit your motherboard vendors FAQ
{: .prompt-tip }

1. Select the USB drive from the boot menu and press the `Enter key`

![windows install](/assets/img/win-setup/windows-install-1.png){: .shadow w="500" h="200" }

2. Click on `Next` to start

![windows install](/assets/img/win-setup/windows-install-2.png){: .shadow w="500" h="200" }

3. Click on `Install now`

![windows install](/assets/img/win-setup/windows-install-3.png){: .shadow w="500" h="200" }

4. Enter your Windows lizenz key and click on `Next`. If you do not own a lizenz goto point `4.2`

![windows install](/assets/img/win-setup/windows-install-4.png){: .shadow w="500" h="200" }

4.2 If you do not have a lizenz at this time just click on `I don't have a product key` and select `Windows 10 Pro`

![windows install](/assets/img/win-setup/windows-install-5.png){: .shadow w="500" h="200" }

6. Select `Custom: Install Windows only (advanced)`

![windows install](/assets/img/win-setup/windows-install-6.png){: .shadow w="500" h="200" }

7. If you want to do a fresh install of an already setup system select and delete all partitions of the drive on which windows is installed (example `Drive 2 Partion 3` and so on). If this is a fresh install for example on a new drive select that drive and click on `Next`

![windows install](/assets/img/win-setup/windows-install-7.png){: .shadow w="500" h="200" }

8. Let the install run. This may take a couple of minutes

![windows install](/assets/img/win-setup/windows-install-8.png){: .shadow w="500" h="200" }

9. The system will automaticly reboot after 10 seconds

![windows install](/assets/img/win-setup/windows-install-9.png){: .shadow w="500" h="200" }


## **Setup of Windows**

1. Select your region, then confirme it with `Yes`

![windows install setup](/assets/img/win-setup/windows-install-setup-1.png){: .shadow w="500" h="200" }

2. Select your keyboard, then confirme it with `Yes`

![windows install setup](/assets/img/win-setup/windows-install-setup-2.png){: .shadow w="500" h="200" }

3. Click on `Skip`, even if you want other keyboard layouts. These can be added later

![windows install setup](/assets/img/win-setup/windows-install-setup-3.png){: .shadow w="500" h="200" }

4. Select `Set up for personal use`

![windows install setup](/assets/img/win-setup/windows-install-setup-4.png){: .shadow w="500" h="200" }

5. Do NOT use your Microsoft account. Use the `Offline account` button in the bottom left hand corner

> If you do not see that text disconect your internet and retriger the page by returning one step or rebooting your system.
{: .prompt-tip }


![windows install setup](/assets/img/win-setup/windows-install-setup-5.png){: .shadow w="500" h="200" }

6. Click on `Limited experience`

![windows install setup](/assets/img/win-setup/windows-install-setup-6.png){: .shadow w="500" h="200" }

7. Enter your username

![windows install setup](/assets/img/win-setup/windows-install-setup-7.png){: .shadow w="500" h="200" }

8. Enter your password and confirm it afterwards

> It is recomended to have a password with atleast 12 characters. It should incloude upper and lowercase letters, numbers and symbols.
{: .prompt-tip }

![windows install setup](/assets/img/win-setup/windows-install-setup-8.png){: .shadow w="500" h="200" }

9. Enter your security questions

![windows install setup](/assets/img/win-setup/windows-install-setup-9.png){: .shadow w="500" h="200" }

10. Always select the bottom option

![windows install setup](/assets/img/win-setup/windows-install-setup-10.png){: .shadow w="500" h="200" }

11. Press the `Skip` button

![windows install setup](/assets/img/win-setup/windows-install-setup-11.png){: .shadow w="500" h="200" }

12. Select `Not now`

![windows install setup](/assets/img/win-setup/windows-install-setup-12.png){: .shadow w="500" h="200" }

### **Installing drivers**

Text coming soon!


### **Installing firmware**

Text coming soon!


### **Removing junk**

Run the following commands in powershell as an administrator, if you want to make these changes to your system.

**Nav:** Press the `Windows key` > type `powershell` > select `Run as Administrator`

**Always aktivated num lock**
```powershell
Set-ItemProperty -Path 'HKCU:\Control Panel\Keyboard' -Name InitialKeyboardIndicators -Value '2'
Set-ItemProperty -Path 'Registry::\HKEY_USERS\.DEFAULT\Control Panel\Keyboard' -Name InitialKeyboardIndicators -Value '2147483650'
```

**Deaktivation of Cortana**
```powershell
New-Item -Path 'HKLM:\SOFTWARE\Microsoft\PolicyManager\current\device\Experience' -Force | Out-Null
New-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\PolicyManager\current\device\Experience' -Name AllowCortana -Value 0 -PropertyType DWORD -Force | Out-Null
```

**Deaktivation of OneDrive**
```powershell
New-Item -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\OneDrive' -Force | Out-Null
New-ItemProperty -Path 'HKLM:\SOFTWARE\Policies\Microsoft\Windows\OneDrive' -Name DisableFileSyncNGSC -Value 1 -PropertyType DWORD -Force | Out-Null
```

**Uninstall spam software**
```powershell
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Xbox*'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Office*'} | Remove-AppxProvisionedPackage -Online
Get-AppxProvisionedPackage -Online | ? { $_.DisplayName -like "*windowscommunicationsapps*"} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Solitair*'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Skypeapp*'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like 'Office'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Note*'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like 'Tips'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like 'Spotify'} | Remove-AppxProvisionedPackage -Online
Get-AppXProvisionedPackage -Online | ? { $_.DisplayName -like '*Reality*'} | Remove-AppxProvisionedPackage -Online

Get-AppxPackage *Xbox* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Office* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Solitair* -AllUsers | Remove-AppxPackage
Get-AppxPackage *king.com* -AllUsers | Remove-AppxPackage
Get-AppxPackage *skypeapp* -AllUsers | Remove-AppxPackage
Get-AppxPackage *windowscommunicationsapps* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Office* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Note* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Tips* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Spotify* -AllUsers | Remove-AppxPackage
Get-AppxPackage *Reality* -AllUsers | Remove-AppxPackage
```

### **Setting defaults**

To create the best and clean expierence to new users on the system we need to edit the default user layouts under `C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml`. Copy the following code into the file and after that save it

> If you are the only user on the system you do not need to do this. 
{: .prompt-tip }

```xml
<?xml version="1.0" encoding="utf-8"?>
<LayoutModificationTemplate
    xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
    xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
    xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
    xmlns:taskbar="http://schemas.microsoft.com/Start/2014/TaskbarLayout"
    Version="1">
	<LayoutOptions StartTileGroupCellWidth="6" />
	<DefaultLayoutOverride>
		<StartLayoutCollection>
			<defaultlayout:StartLayout GroupCellWidth="6" />
		</StartLayoutCollection>
	</DefaultLayoutOverride>
	<CustomTaskbarLayoutCollection>
		<defaultlayout:TaskbarLayout>
			<taskbar:TaskbarPinList>
			</taskbar:TaskbarPinList>
		</defaultlayout:TaskbarLayout>
	</CustomTaskbarLayoutCollection>
</LayoutModificationTemplate>
```

<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)