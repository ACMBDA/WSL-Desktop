# WSL-Desktop (WiP - Come back later :-)
Aeolus Standard XFCE deployment on Windows Subsystem for Linux

Script to NetInstall **Ubuntu 20.04**, **xRDP**, and **XFCE 4.16** on WSL (Version 1 or 2).  

**INSTRUCTIONS:  From an elevated prompt, change to your desired install directory and type/paste the following command:**

     PowerShell -executionpolicy bypass -command "wget https://raw.githubusercontent.com/ACMBDA/WSL-Desktop/main/xWSL.CMD -UseBasicParsing -OutFile xWSL.cmd ; .\xWSL.cmd"

You will be asked a few questions.  The installer script finds the current DPI scaling in Windows, you can set your own value if preferred:

     [xWSL Installer 20210601]

     Enter a unique name for your xWSL distro or hit Enter to use default.
     Keep this name simple, no space or underscore characters [xWSL]: XFCE416
     Port number for xRDP traffic or hit Enter to use default [3399]: 13399
     Port number for SSHd traffic or hit Enter to use default [3322]: 13322
     Set a custom DPI scale, or hit Enter for Windows default [1.5]: 1.25
     [Not recommended!] Type X to eXclude from Windows Defender:

     Installing xWSL Distro [XFCE416] to "C:\WSL Distros\XFCE416"
     This will take a few minutes, please wait...

The installer will download and install the [LxRunOffline](https://github.com/DDoSolitary/LxRunOffline) distro manager and [Windows Store Ubuntu image](https://www.microsoft.com/en-bm/p/ubuntu/9nblggh4msv6?).  Reference times will vary depending on system performance and the presence of antivirus software.  A fast system with good Internet can finish in under 10 minutes. 

     [11:14:57] Installing Ubuntu 20.04 LTS (~1m00s)
     [11:15:43] Git clone and update repositories (~1m15s)
     [11:16:37] Remove un-needed packages (~1m00s)
     [11:17:13] Configure apt-fast Downloader (~0m15s)
     [11:17:24] Remote Desktop Components (~4m45s)
     [11:21:43] XFCE 4.16 (~2m00s)
     [11:23:06] Install Mozilla Seamonkey and media playback (~1m30s)
     [11:23:53] Post-install clean-up (~0m45s)
   
At the end of the script you will be prompted to create a non-root user which will automatically be added to sudo'ers.

     Enter name of primary user for XFCE416: zero
     Enter password for zero: ********

     Open Windows Firewall Ports for xRDP, SSH, mDNS...
     Building RDP Connection file, Console link, Init system...
     Building Scheduled Task...
     SUCCESS: The scheduled task "XFCE416" has successfully been created.
     
           Start: Mon 06/01/2021 @ 11:14
             End: Mon 06/01/2021 @ 11:24
        Packages: 1100

       - xRDP Server listening on port 13399 and SSHd on port 13322.

       - Links for GUI and Console sessions have been placed on your desktop.

       - (Re)launch init from the Task Scheduler or by running the following command:
         schtasks /run /tn XFCE416
     
      XFCE416 Installation Complete!  GUI will start in a few seconds...

A fullscreen XFCE session will launch using your stored credentials. 

**Configure xWSL to start at boot (like a service, no console window)**

* Right-click the task in Task Scheduler, click properties
* Click the checkbox for **Run whether user is logged on or not** and click **OK**
* Enter your Windows credentials when prompted
 
Reboot your PC when complete and xWSL will startup automatically.

**Start/Stop Operation**

* Reboot the instance (example with default distro name of 'xWSL'): ````schtasks /run /tn xWSL```` 
* Terminate the instance: ````wslconfig /t xWSL````

