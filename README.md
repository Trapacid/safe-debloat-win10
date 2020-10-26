# safe-debloat-win10
Safest way to debloat Windows 10 for low end computers without destroying your system with powershell "debloat" scripts.

<hr>

# Step 0: Reset Windows and use Windows 10 Home.
I cannot stress this enough, resetting always helps. OEMs are known to bloat up your system with their crapware. (Looking at you, Dell, HP, and Lenovo. Especially Lenovo.)
OEM bloatware is always the first culprit to a laggy system rather than Windows 10 itself.

`Search "Recovery options" > Reset this PC > Remove Everything > Only the drive where windows is installed`

# Step 0.5: Do *not* use OEM drivers.
Drivers provided by Windows Update go through major testing via [Windows Hardware Quality Labs (WHQL)](https://wikipedia.org/wiki/WHQL_Testing). Latest OEM drivers do not go through such testing immediately. Windows Update drivers are found to be largely much more stable, but may be a few versions behind. If you for some reason absolutely need some sort of functionality your OEM provides that Windows Update drivers don't provide at the moment, go right ahead. 

**AND DO NOT USE DRIVER UTILITIES. EVEN INTEL DRIVER UPDATE UTILITIES.**

<hr>

## Disabling and deleting in Settings

### 1. Don't use an external anti malware software
External anti malware/virus software is often the main resource eater. Stick to default Windows 10 Security Center.<br>
Disable `cloud-based protection` and `automatic sample submission` in Security Center. Utilize common sense to decide and decipher between good and bad.

### 2. Delete unnecessary applications using Settings.
Please for the love of what ever god exists, do NOT use powershell "debloat" scripts. Often times they are not recoverable and if they are, the system is still tainted.<br>
Search `Apps & features` in the Search bar, or `Settings > System > Apps & features > Click an app > Uninstall`

### 3. Disable apps from starting up and background usage.
Self explanatory. Speeds up boot time and reduces memory usage.<br>
`Ctrl + Shift + Esc > More details > Startup > Right click > Disable`<br>
This is a huge memory saver:<br>
`Settings > Privacy > Background apps > OFF all except "Settings"`

### 4. Disable visual effects.
Disables some visual effects to free up memory.<br>
`Search "advanced system settings" > Performance Settings > Adjust for best performance`<br>
Disable everything **except** for smooth font. Unless you're fine with ugly fonts.<br>
`Settings > Ease of Access > Other options > OFF "Play animation" and OFF "Show background"`<br>
`Settings > Personalization > Colors > OFF "Make Start, taskbar... transparent" and OFF others of your choice`<br>
`Settings > Personalization > Start > Show more tiles OFF, Occasionaly show suggestions OFF`<br>
Use a static wallpaper, preferably a simple color.<br>
Unpin all tiles from Start Menu.

### 5. Disable some Microsoft things.
`Settings > Personalization > Lock screen > Get fun facts, tips, tricks > OFF (after previous point)`<br>
`Settings > System > Notifications & actions > Get tips, tricks, and suggestions OFF, Get notifications from apps OFF`<br>
`Settings > System > Notifications & actions > Show me tips about Windows > OFF`<br>
`Settings > System > Offline maps > Automatically update maps > OFF`<br>
`Settings > Gaming > Xbox Game Bar > OFF` (There are discussions and debates about whether Game Mode actually helps. Honestly, if you intend on playing games, leave it enabled. Otherwise, disable it.)<br>
`Settings > Devices > AutoPlay > Use AutoPlay for all media and devices > OFF`

### 6. Opt-out of personalized telemetry.
Again, please for crying out loud, there is no need to run a debloat script to add unnecessary registry keys or group policy edits.

Settings > Privacy:
- `General > OFF "Send Microsoft info about how I write..." and OFF others of your choice`
- `Speech, inking and typing > Stop getting to know me`
- `Location > Change > OFF`
- `Feedback and diagnostics > Windows should ask for my feedback: NEVER`
- `Send your device data to Microsoft: Basic`

### 7. Disable automatic Microsoft Store app updates.
`Store > user icon > Settings > Update apps automatically > OFF`<br>
`Store > user icon > Settings > Show products on tile > OFF`

<hr>

## Cleaning up

### 1. Defragment your hard drive/TRIM your SSD.
No, you absolutely do not need to do anything in the command prompt to TRIM your SSD. Windows 10 natively detects SSDs.

Search: "Defragment and Optimize Drives". Defrag or TRIM any drives, especially your C: drive.<br>
Set the schedule to run this weekly for **TRIM** on SSDs, or Monthly for defragmentation of HDDs.

### 2. Free up storage using Disk Cleanup.
Always make sure to leave 10GB of storage minimum on your C: drive available to avoid lag and storage issues.

Search up "Disk Cleanup". <sup>or `Win + R > cleanmgr`</sup> Let it search. Then select "Clean up system files". Let it search. Tick all the boxes then let it Clean.

### 3. Check for system corruption and disk errors.
Search for "Command Prompt". Right click it and Run it as an Administrator. Then run the following in the order they're displayed:
- `CHKDSK C: /F`
- `DISM /Online /Cleanup-image /Restorehealth`
- `sfc /scannow`

Reboot your PC afterwards. See [here](https://docs.microsoft.com/en-us/troubleshoot/windows-server/deployment/fix-windows-update-errors) for more details.

### 4. Enable high performance power profile in Power settings.
If you don't mind the extra power usage, you should enable High Performance power profile in Battery Settings (bottom right). Move the slider to the far right for high performance.

## Hardware Upgrades
Ultimately, for a stable and pretty responsive system, you're going to want 8GB of DDR3 1600MHz or DDR4 2400MHz minimum of memory. You'll want a SATA3 SSD that is 100GB minimum as well. These are enough for simple games like Minecraft and Terraria, Office 365 Usage, and medium-high JavaScript loading for browsers like Google Chrome and Firefox.

## Browser Extensions

You'll normally not want to use any, but because the Web is plagued with crazy amounts of JavaScript and advertisements, a simple adblocker will save loads of JavaScript loading.<br>
Use [uBlock Origin](https://github.com/gorhill/uBlock). **NOT uBlock.org**
