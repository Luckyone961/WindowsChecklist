# Optimized and debloated Windows 11 fresh install

- No more default app bloat
- Less processes running in the background of your system
- More CPU for your games and other heavy tasks
  
![Initial install state](https://i.imgur.com/0Qu6nOM.png)

## [Step 1] Creating and editing the autounattend xml file

**Why autounattend?**
- Create a local account
- Prevent device encryption (Windows 11 otherwise forces Bitlocker by default)
- Remove 55+ preinstalled default apps (You can still keep apps you use)
- Uninstall Edge (Supported by Microsoft since recent updates)

#### [Step 1.1] How to get the custom pre-configured base file
1. Click the `autounattend.xml` file in this GitHub repo
2. Click the 3 dots in the top right corner of the file page
3. Click **Download** or press `CTRL+Shift+S` to save it on your PC

#### [Step 1.2] Upload and edit the base file
1. Head over to the **[Windows Autounattend File Generator](https://schneegans.de/windows/unattend-generator/)** website
2. Select **Choose File** to upload the saved file
3. Click **Import File** next to it
4. Make changes as mentioned in the next step

#### [Step 1.3] Double check the following options and edit as needed

- Use `CTRL+F` on the site to search for and edit the following keywords

1. **Windows display language:** Base file default `English`
2. **Keyboard language:** Base file default `German (Germany)`
3. **Keyboard layout:** Base file default `German`
4. **Home location and device setup region:** Base file default `Germany`
5. **Processor architectures:** Base file default `Intel / AMD 64-bit`
6. **Time zone:** Base file default `UTC+1 (Amsterdam, Berlin, Bern, Rome, ...)`
7. **User accounts:** Change account name `Lucky` to your own
8. **Remove bloatware:** Checkbox ticked means the Microsoft app won't be installed

#### [Step 1.4] Download and save the final autounattend xml file
1. Scroll to the very bottom of the website
2. Click the button `Download .xml file`
3. Save and don't change the file name

## [Step 2] Creating a bootable USB drive

Requirements:
- A **USB drive with at least 8GB** of space - formatted in **FAT32**
- The **[Windows 11 Media Creation Tool](https://www.microsoft.com/en-us/software-download/windows11)**
- Use the second download button `Create Windows 11 Installation Media`
- Do not attempt this with Ventoy or Rufus - it can end up in bluescreens during the installation

#### [Step 2.1] Finalizing the bootable USB drive
1. Run the `MediaCreationTool.exe` and go through all steps - select the formatted USB drive
2. Wait for the tool to finish and close it
3. Copy your `autounattend.xml` file into the root of the USB drive
   - It should now appear alongside files like `bootmgr`, `bootmgr.efi`, and `setup.exe`
   - **[like in this screenshot](https://i.imgur.com/4SRkhPj.png)**

#### [Step 2.2] Prepare core drivers
1. Prepare all necessary drivers (Second USB drive or external backup)
2. Download them only from your motherboard vendor's website
3. Unzip and install all of them - then reboot your PC
4. Audio - LAN - Chipset is recommended - rest is bloat

## [Step 3] Installing Windows with the prepared USB

- Ensure your prepared bootable USB drive is connected to the PC
- Remove your Ethernet cable for the installation process to avoid telemetry and geolocation

#### [Step 3.1] Method 1: Command prompt or Powershell
1. Open either command prompt or Powershell as an admin
2. Paste `shutdown /r /fw /t 0` and hit enter

#### [Step 3.2] Method 2: Manually
1. Shut down the PC and turn it back on
2. Hold the **DEL** key (or the respective key for your motherboard) to enter BIOS/UEFI
3. Set your USB drive to **priority 1** in the boot order - save - exit

#### [Step 3.3] Installation
1. Most steps will be auto skipped with our autounattend file
2. For the disk partition step - make sure to delete all drives and partitions

## [Step 4] Initial setup steps after the installation

- Here are the recommended steps to follow for the perfect Windows installation

#### [Step 4.2] Custom NVIDIA driver without bloat
- It is highly recommended to use **[NVCleanStall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/)**

1. NVCleanStall components: **[Component Settings](https://i.imgur.com/wpFw1I5.png)**
2. NVCleanStall tweaks: **[Tweaks Settings](https://i.imgur.com/Pj97Qr5.png)**
3. NVIDIA control panel: **[Nvidia Control Panel](https://i.imgur.com/nSfYcvj.png)**

#### [Step 4.3] Privacy and DNS
- I recommend **[NextDNS](https://nextdns.io/?from=768ha46y)** to block ads and malware across all devices ($1,99/month)
- Free alternatives: **[Cloudflare DNS](https://developers.cloudflare.com/1.1.1.1/setup/windows/)** or **[AdGuard DNS](https://adguard-dns.io/en/public-dns.html)**
- In case you need a guide how to change your DNS check out **[this wiki guide](https://www.wikihow.com/Change-DNS-Windows-11)**

#### [Step 4.4] Activating the Windows license
- Search for "Activation Settings" and enter your product key (use **Pro** or **Pro N**)
- You can grab a cheap volume license OEM/Retail on eBay or g2g for less than $2

#### [Step 4.5] Noteworthy Windows options
- Enable "Hardware accelerated GPU scheduling" (Search for "Graphics settings")
- Turn off "Memory integrity" (Search for "Device security" > "Core isolation")
  - Memory integrity is roughly a 5% fps loss if enabled **[read more](https://www.reddit.com/r/Windows11/comments/16827sg/should_i_turn_on_the_memory_integrity/)**

## [Step 5] Using the chris titus windows utility

- See **[Windows Utility](https://github.com/ChrisTitusTech/winutil)** - a popular GitHub Powershell project

#### [Step 5.1] Before you use it
1. Run all **Windows updates** (Search for "Check for updates") **- MANDATORY**
2. Reboot after completing all updates **- MANDATORY**
3. Open the **Microsoft Store** **once** to trigger/fix WinGet package manager (Can be closed immediately)

#### [Step 5.2] Using the windows utility
1. Search for **"Powershell"** and right-click run it as admin
2. Type the following and hit enter:  
   `irm "https://christitus.com/win" | iex`
3. Head to the **"Tweaks"** tab and (optionally) copy my **[personal settings](https://i.imgur.com/C7mVugr.png)**
4. Click **"Run Tweaks"** and wait for it to finish (check console output)
5. I also recommend adding the **Ultimate Performance Profile** in the "Tweaks" tab and enabling **Security Settings** in the "Updates" tab
6. It is also highly recommended to run the RemoveWindowsAI which is linked in step 6.1 below

## [Step 6] Extra tools & Recommendations

- Here are a few apps and tools that I use, though they’re not recommended for everyone
- Make sure you understand their purpose and can make use of them

#### [Step 6.1] Executables (Portable - No Installation)
1. **[O&O ShutUp10++](https://www.oo-software.com/en/shutup10)** – Privacy tool to disable spying/telemetry
2. **[RemoveWindowsAI](https://github.com/zoicware/RemoveWindowsAI)** – Remove the entire Copilot and other Microsoft AI features
3. **[Sysinternals Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns)** – Clean up what's loading on Windows startup
4. **[nvidiaProfileInspector](https://github.com/Orbmu2k/nvidiaProfileInspector/releases)** – Customize your Nvidia GPU settings
  *(Here's what I do: [Example](https://i.imgur.com/lzfZd3Y.png))*

#### [Step 6.2] More apps (App installers)
1. **[Nilesoft Shell](https://nilesoft.org/)** – Personalize and skin the right-click context menu
2. **[Vencord](https://vencord.dev/)** – Modifies Discord with plugins/themes (Technically against ToS)
3. **[Brave Browser](https://brave.com/download/)** – The best browser and adblocking engine (Based on Chrome)
4. **[PowerToys](https://github.com/microsoft/PowerToys)** - Set of utilities for power users
