# SolidWorks License Auto-Deactivator
A background task/service that monitors for SolidWorks to shut down, then automatically disables the license; This allows a standalone license to be used elsewhere, effectively replicating a networked license. Be adviced that there may be a limit to the total activations per license (reportedly 999), but this can be raised.

## Description:
This VBScript is a wrapper to launch a PowerShell script that installs/is a watcher for when SolidWorks turns off.
Specifically, it creates a Scheduled Task that runs the watcher script at user logon which activates once SolidWorks is closed. The watcher script will then automatically deactivate the standalone license through the *'SOLIDWORKS Product Activation'* Wizard.

It takes ~20 seconds to detect the shutdown and step through the Wizard.
The Wizard will be left on the **"Deactivation Successful"** page afterwards, so the user can use this as license deactivation confirmation.

**The script will not run if Windows is being shut down/crashing while SolidWorks is running however!**


## Usage:
1. Click on the VBScript file (*ends with .vbs*) in https://github.com/AtonFreson/SolidWorks_License_Auto-Deactivator/releases to download it.
2. Double-click the VBScript file to run it.
    - Accept any admin privilege requests, etc. 
    - It will prompt for the main SOLIDWORKS Corp installation folder.
3. Navigate to the *"SOLIDWORKS Corp"* folder via the *File Explorer*, and *copy/paste* from the address bar.
    - The default folder is: `C:\Program Files\SOLIDWORKS Corp`

### Additional information:
Changes while running the script are possible. Do this by editing `<SOLIDWORKS Corp>/Scripts/SWActivationWatcher.ps1`. Edits take effect after a PC reboot.
- Afther it has been initiated, **holding down the Spacebar key will stop the deactivation process**.
    - This is a feature that stops the deactivation in-case accidental deactivation was initiated, e.g. if SolidWorks crashed or the user plans to continue using the software. The *'SOLIDWORKS Product Activation'* Wizard will still open.
- Change *pollSeconds* and *windowDelay* if you're on a slow computer or if you want to speed up the process.
- To make the script work in your language, *ctrl+f* replace *"Next >"* with what's written on the same button in your language, as well as the *"Select All"* button. See the image below.
    - The automation works by 'pressing' the button with the text *"Next >"* in the 'SOLIDWORKS Product Activation' Wizard, then *"Select All"*, and lastly *"Next >"* again.
- Errors are logged in `C:\ProgramData\SWActivationWatcher.txt`.

![Image of what button that has "Next" written on it in the English language SolidWorks.](https://i.imgur.com/KPhdSvo.png)
