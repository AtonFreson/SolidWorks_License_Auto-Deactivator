# SolidWorks_License_Auto-Deactivator
A background task/service that monitors for SolidWorks to shut down, then automatically disables the license; This allows a standalone license to be used elsewhere, effectively replicating a networked license. Be adviced that there may be a limit to the total activations per license (reportedly 999), but this can be raised.

## Description:
This VBScript is a wrapper to launch a PowerShell script that installs/is a watcher for exiting SolidWorks.
It creates a Scheduled Task that runs the watcher script at user logon, which activates once SolidWorks is closed.
The watcher script will then automatically deactivate the standalone license through the 'SOLIDWORKS Activation Wizard'.

It takes ~20 seconds to detect the shutdown.
The 'SOLIDWORKS Activation Wizard' will be left on the "Deactivation Successful" page afterwards, so the user can use this as license deactivation confirmation.

This will not run if Windows is being shut down/crashing while SolidWorks is running however!


## Usage:
1. Double-click the VBScript file to run it.
    - It will prompt for the main SOLIDWORKS Corp installation folder.
2. Navigate there via the File Explorer, and copy/paste it from the address bar.

- Edit pollSeconds and windowDelay in SWActivationWatcher.ps1 if on a slow computer or if you want to speed up the process (then reboot).
- The automation works by 'pressing' the button with the text "Next >" in the 'SOLIDWORKS Activation Wizard'. To make the script work in your language, ctrl+f replace "Next" with the word on the same button in your language.
![Image of what button that has "Next" written on it in the English language SolidWorks.](https://i.imgur.com/KPhdSvo.png)
