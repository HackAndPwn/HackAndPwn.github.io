---
layout: post
title: Windows 7 ESU Analysis
date: 2020-04-28 00:00:00
tags: draft
---

The Windows 7 free security update window closed to consumers in January of 2020.  However, due to the overwhelming popularity of the OS, Microsoft began offering Extended Security Updates (ESU) for the Operating System.  The first update preparing a Windows 7 system for this next phase of patches is [KB4528069](https://support.microsoft.com/en-us/help/4528069).  This post dissects the KB4528069 update to understand how ESUs differ from standard Windows 7 updates.

<br>

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU update can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

<br>

### Preparing The Computer

To start, I deployed a brand new VM of 64-Bit Windows 7 SP1, resulting in a build from November 19th, 2010 (101119).

<img src="/assets/2020-04-28-windows-7-esu-analysis/01.jpg">

Next, I started checking for updates.  This resulted in 181 updates on the first scan.

<img src="/assets/2020-04-28-windows-7-esu-analysis/02.jpg">

Some of the updates would not install without manually installing KB4474419 first (the SHA2 update).

After many update cycles and reboots, 10 years of updates have been applied.  

Finally, no more updates are available, bringing the build to January 2nd, 2020 (200102).

<img src="/assets/2020-04-28-windows-7-esu-analysis/03.jpg">

For good measure I also ran disk cleanup to remove 8 GB of excess files.

<img src="/assets/2020-04-28-windows-7-esu-analysis/04.jpg">

<br>

### Installing KB4528069

Next, I downloaded and tried to install KB4528069 (Verify Computer Is Ready To Receive Extended Updates).  But this fails.

<img src="/assets/2020-04-28-windows-7-esu-analysis/05.jpg">

So, I reverted the VM, started up ProcMon, and traced the installation of this update.

<br> 

### Manifest File

The first thing that I discovered within the trace was a manifest file that was being created, specifically:

> C:\Windows\WinSXS\Manifests\amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.20587_none_c8993b883659a816.manifest

<img src="/assets/2020-04-28-windows-7-esu-analysis/06.jpg">

The content of this file shows that it is an important file to keep on the system.

<img src="/assets/2020-04-28-windows-7-esu-analysis/07.jpg">

A final note on this file.  If you re-examine the ProcMon capture, this file is added but NOT DELETED when the update failed.  This will be important later.

<br> 

### Components Registry Keys

The next thing that I noticed was a couple of registry keys being created, specifically:

> [HKEY_LOCAL_MACHINE\Components\DerivedData\Components\amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.20587_none_c8993b883659a816]
> "identity"=hex:4d,69,63,72,6f,73,6f,66,74,2d,57,69,6e,64,6f,77,73,2d,53,4c,43,2d,43,\
6f,6d,70,6f,6e,65,6e,74,2d,45,78,74,65,6e,64,65,64,53,65,63,75,72,69,74,79,55,70,64,61,\
74,65,73,41,49,2c,20,43,75,6c,74,75,72,65,3d,6e,65,75,74,72,61,6c,2c,20,56,65,72,73,69,\
6f,6e,3d,36,2e,31,2e,37,36,30,32,2e,32,30,35,38,37,2c,20,50,75,62,6c,69,63,4b,65,79,54,\
6f,6b,65,6e,3d,33,31,62,66,33,38,35,36,61,64,33,36,34,65,33,35,2c,20,50,72,6f,63,65,73,\
73,6f,72,41,72,63,68,69,74,65,63,74,75,72,65,3d,61,6d,64,36,34,2c,20,76,65,72,73,69,6f,\
6e,53,63,6f,70,65,3d,4e,6f,6e,53,78,53
> "S256H"=hex:e8,4b,2d,35,da,c9,da,c4,7c,70,94,05,e4,e6,4b,00,7d,3e,9d,93,f6,b9,c4,e2,ee,79,bf,b4,cd,c0,7f,f8
> "c!1208dabb65a..2207abac32f_31bf3856ad364e35_6.1.7602.20587_85098b546dfae448"=hex:

<img src="/assets/2020-04-28-windows-7-esu-analysis/08.jpg">

The COMPONENTS registry hive is hidden by default, so I manually mounted it to view the referenced registry key.

<img src="/assets/2020-04-28-windows-7-esu-analysis/09.jpg">

Navigating to the registry key shows that again, the installation step is not reverted, and the registry keys persist.  Checking the ProcMon trace again reconfirms this discovery that the registry key is created, but not removed when the update fails.

<img src="/assets/2020-04-28-windows-7-esu-analysis/10.jpg">

This will also be important later.

<br>

### SideBySide Registry Keys

Finally, the last important activity I noticed was the modification of registry keys in the Local Machine registry hive.  Specifically:

> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners\amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_none_0e8b36cfce2fb332\6.1]

<img src="/assets/2020-04-28-windows-7-esu-analysis/11.jpg">

Checking the registry again after the failed update, there is something different about this registry entry.  It is missing.

<img src="/assets/2020-04-28-windows-7-esu-analysis/12.jpg">

Re-examining the ProcMon trace, we see that this key is created, and then deleted as part of the failed update.

> [ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners\amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_none_0e8b36cfce2fb332\6.1]
> "6.1.7602.20587"=hex:01

<img src="/assets/2020-04-28-windows-7-esu-analysis/13.jpg">

The other key that is being set during the patch installation is the Default @ value, which temporarily switches to the new build number and then reverts to the old value.

<img src="/assets/2020-04-28-windows-7-esu-analysis/14.jpg">

<br>

### Manually Flipping SideBySide Registry Keys

So now that we know the SideBySide registry key switch gets reverted, I manually switch it back to the value KB4528069 is trying to set it to.

> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners\amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_none_0e8b36cfce2fb332\6.1]
> @="6.1.7602.20587"
> "6.1.7602.20587"=hex:01

<img src="/assets/2020-04-28-windows-7-esu-analysis/15.jpg">

And now if I try to install KB4528069 again...

<img src="/assets/2020-04-28-windows-7-esu-analysis/16.jpg">

The update completes successfully!

<br>

### Bringing Windows 7 Up To Date

It is one thing to install a silly update that verifies eligibility.  It is another to get additional updates to install.  First, I grab the latest SSU from April and try to install it.

<img src="/assets/2020-04-28-windows-7-esu-analysis/17.jpg">

This installs successfully.   Next, I to install the latest cumulative update from April.  

<img src="/assets/2020-04-28-windows-7-esu-analysis/18.jpg">

This appears to install successfully.  However, we will not know if it works until after the reboot.  From Microsoft's Known Issues section in the [February Cumulative Update](https://support.microsoft.com/en-us/help/4537820/windows-7-update-kb4537820):

> After installing this update and restarting your device, you might receive the error, “Failure to configure Windows updates.  Reverting Changes.  Do not turn off your computer,” and the update might show as Failed in Update History.  

This is a sign that there are issues with the current ESU configuration.  However, when we reboot, there are no errors, and the OS build date has successfully increased to March 30th, 2020

<img src="/assets/2020-04-28-windows-7-esu-analysis/19.jpg">

<br>

### Summary

What I learned from dissecting this update was that there are 3 important parts to the install: The manifest file, the Components registry keys, and the SideBySide registry keys.  However, 2 of the 3 required parts do not revert upon a failed update.  Therefore, to get the update to install properly:

1. Attempt to install KB4528069 and let it fail.
2. Flip the SideBySide registry key to use the newer SideBySide version.
3. Attempt to install KB4528069 and it should succeed.

After this, the latest servicing stack update and the latest cumulative update can be installed without issue.

Windows Update will still not detect updates though, as the machine has not been properly licensed.  But once a valid key has been activated, the Windows Update client will begin detecting updates again.

<br>

### References

The various files and registry keys used as part of this analysis have been uploaded to GitHub [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific files and links referenced.

> [KB4528069 X64](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/windows6.1-kb4528069-x64_b00bef3c3a13b8bc65bfaea63426386dbb54c336.msu)
>
> [Manifest File X64](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.20587_none_c8993b883659a816.manifest)
>
> [Components Registry Key](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/ComponentsRegistryKey.reg)
>
> [SideBySide Registry Key](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/SideBySideRegistryKey.reg)