# Clean and Debloated Windows 11 Install Guide by Luckyone

## [1] Prepare Your Autounattend XML File

The following service lets you create an autounattend file for your bootable USB installation drive:  
**[Windows Autounattend File Generator](https://schneegans.de/windows/unattend-generator/)**  
*(Note: The domain is German, but the entire website is in English.)*  
We'll manually add the final file to our bootable USB installation drive later in the guide.

This file automates most of your Windows installation process, removing unwanted Microsoft apps and services before you even get to the desktop for the first time.

### [1.1] Notable Autounattend Options
- **Create a local account**
- **Prevent device encryption** (Windows 11 otherwise forces Bitlocker by default)
- **Remove 55+ preinstalled default apps** (You can still keep apps you use)
- **Uninstall Edge** (Supported by Microsoft since recent updates)

### [1.2] My Personally Customized File
For those looking for my personal file, it's available in this repository for download.  
However, you’ll still need to upload and import the file on the website linked above and make any necessary edits.

#### [1.2.1] How to Use and Edit My Personally Customized File
1. Click the `autounattend.xml` file in this GitHub repo.
2. Click the 3 dots in the top right corner of the file page.
3. Click **Download** or press `CTRL+Shift+S` to save it on your PC.
4. Go to the website linked in step 1.
5. Select **Choose File** to upload the saved file.
6. Click **Import File** next to it.
7. Make changes as mentioned in the next step.

#### [1.2.2] Options to Double-Check When Using My Personal File
- **Windows display language:** I use English (United States).
- **Keyboard layout:** I use German.
- **Processor architectures:** I use Intel/AMD 64-bit.
- **Time zone:** I use UTC+1 (Berlin).
- **User account name:** Change it from "Lucky" to your preferred name.
- **Default apps:** I leave only Notepad, Terminal, Paint, Photos, and Calculator installed.

---

## [2] Prepare Your Bootable USB Drive

You'll need:
- A **USB drive with at least 8GB** of space, formatted to **FAT32**.
- The **[Media Creation Tool](https://www.microsoft.com/en-us/software-download/windows11)** (download the second button on the page under "Create Windows 11 Installation Media").

### [2.1] Why Not Ventoy or Rufus?
- **TL;DR:** Using either of these tools might lead to bluescreens during installation for unknown reasons.
- This could be related to turning off device encryption or disabling the new Recall feature, but this is just a guess.

### [2.2] Finishing Our Bootable USB Drive
1. Run the Media Creation Tool and select your already formatted USB drive.
2. Wait for the tool to finish and close it.
3. Copy your `autounattend.xml` file into the root of the USB drive.
   - It should now appear alongside files like `bootmgr`, `bootmgr.efi`, and `setup.exe`.

---

## [3] Actually Installing Your Modified Windows

1. Ensure your finished bootable USB drive is connected to your PC.
2. Shut down the PC and turn it back on.
3. Hold down the **DEL** key (or the respective key for your motherboard) to enter BIOS/UEFI.
4. Set your USB drive to **priority 1** in the boot order, save changes, and exit.
5. Your PC should now boot into the Windows installation process, and the `autounattend.xml` file will start doing its magic.
   - The only thing you'll need to do is format the drive where Windows will be installed.

---

## [4] Initial Steps After Entering Desktop for the First Time

Here are the personal steps I follow for perfecting the Windows installation.

### [4.1] Drivers
1. Prepare a second USB drive with all necessary drivers.
2. Download them from your motherboard vendor's website.
3. Unzip and install all of them, then reboot your PC.

#### [4.1.1] NVidia Custom Driver Without Bloat
- I recommend using **[NVCleanStall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/)** for a debloated NVidia driver.
- Example of my custom settings:  
  - **(1) - Components:** [Component Settings](https://i.imgur.com/wpFw1I5.png)
  - **(2) - Tweaks:** [Tweaks Settings](https://i.imgur.com/Pj97Qr5.png)

### [4.2] Privacy and DNS
- I always use **[NextDNS](https://nextdns.io/?from=768ha46y)** to block ads and malware in all apps.
- A free alternative is **[Cloudflare DNS](https://developers.cloudflare.com/1.1.1.1/setup/windows/)**.
- Changing DNS is easy, just search for guides online.

### [4.3] Activate Your Windows License
- Search for **"Activation Settings"**, then enter your product key (preferably **Pro**).

### [4.4] Noteworthy Things to Check Immediately
- Enable **"Hardware accelerated GPU scheduling"** (Search for "Graphics settings").
- **Highly recommend** turning off **"Memory integrity"** (Search for "Device security" > "Core isolation").

---

## [5] Using the Ultimate Tool for Tweaking

My go-to tool is the **[Windows Utility](https://github.com/ChrisTitusTech/winutil)**, a popular GitHub Powershell project.

### [5.1] Before We Can Use It
1. Run all **Windows updates** (Search for "Check for updates") **- MANDATORY**.
2. Reboot after completing all updates **- MANDATORY**.
3. Open the **Microsoft Store** **once** to trigger/fix WinGet package manager (Can be closed immediately).

### [5.2] Actually Using the Windows Utility Script
1. Search for **"Powershell"** and run it as admin.
2. Type the following and hit enter:  
   `irm "https://christitus.com/win" | iex`
3. Head to the **"Tweaks"** tab and (optionally) copy my [Settings](https://i.imgur.com/bnmsW55.png).
4. Click **"Run Tweaks"** and wait for it to finish (check console output).
5. I also recommend adding the **Ultimate Performance Profile** in the "Tweaks" tab and enabling **Security Settings** in the "Updates" tab.

---

## [6] Extras I Personally Use

Here are a few apps and tools that I use, though they’re not recommended for everyone. Make sure you understand their purpose and can make use of them.

### [6.1] Programs (Portable, No Installation)
- **[O&O ShutUp10++](https://www.oo-software.com/en/shutup10)** – Privacy tool to disable spying/telemetry.
- **[Sysinternals Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns)** – Clean up what's loading on Windows startup.
- **[nvidiaProfileInspector](https://github.com/Orbmu2k/nvidiaProfileInspector/releases)** – Customize your Nvidia GPU settings.  
  *(Here's what I do: [Example](https://i.imgur.com/lzfZd3Y.png))*

### [6.2] Apps to Modify Certain Things (Installed on Your System)
- **[Nilesoft Shell](https://nilesoft.org/)** – Personalize and skin the right-click context menu.
- **[ExplorerPatcher](https://github.com/valinet/ExplorerPatcher/releases)** – Advanced customization (Not recommended unless you know what you’re doing).
- **[Vencord](https://vencord.dev/)** – Modifies Discord with plugins/themes (Technically against ToS).
- **[Brave Browser](https://brave.com/download/)** – A great browser if you can’t move away from Chrome.
- **[Firefox Browser](https://www.mozilla.org/en-US/firefox/new/)** – What I use and recommend.
