---
layout: post
title: Windows 7 ESU Analysis Updates
original_date: 2020-09-12
date: 2025-04-17
---

The original Windows 7 ESU Analysis can be found [here](https://hackandpwn.com/windows-7-esu-analysis).  With the September 2020 Cumulative Update, the technique as described no longer works to install this update.  However, only slight modifications need to be made in order for this new update to also install.

Please reference the original post for the majority of the instructions.  This post will only highlight updates that need to be made.

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU license can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

> Note: October 2024 was the last month Microsoft released patches for x86 versions of Windows 7.  Starting November 2024, only x64 versions of the patches will be updated in this post.

### Installing KB4528069

Install KB4528069 as described in [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis). 

### Installing KB5055561 (April 2025 Cumulative Update)

The April 2025 Cumulative Update includes new ESU files that bump versions past those used in KB4528069.  However, the same technique that previously applied still works.

1. Install the latest Servicing Stack Update [Windows6.1-KB5056456-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5056456-x64.msu) [Windows6.1-KB5039339-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5039339-x86.msu).  Rebooting the machine may be required.
2. If using the Manifest/Components registry key technique on a 64-bit system, execute the following commands:
> takeown /f C:\Windows\WinSxS\Manifests /a
>
> icacls C:\Windows\WinSxS\Manifests /grant Everyone:(F)
>
> copy amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.27670_none_c89c6bdc36588b52.manifest C:\Windows\WinSxS\Manifests
>
> icacls C:\Windows\WinSxS\Manifests /remove Everyone
>
> icacls C:\Windows\WinSxS\Manifests /setowner "NT SERVICE\TrustedInstaller"
>
> reg import ComponentsRegistryKey_x64.reg
>
> reg import SideBySideRegistryKey_x64.reg
>
> Windows6.1-KB5055561-x64.msu
3. If using the Manifest/Components registry key technique on a 32-bit system, execute the following commands:
> takeown /f C:\Windows\WinSxS\Manifests /a
>
> icacls C:\Windows\WinSxS\Manifests /grant Everyone:(F)
>
> copy x86_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.27366_none_6c8e9c4e7ded9ec0.manifest C:\Windows\WinSxS\Manifests
>
> icacls C:\Windows\WinSxS\Manifests /remove Everyone
>
> icacls C:\Windows\WinSxS\Manifests /setowner "NT SERVICE\TrustedInstaller"
>
> reg import ComponentsRegistryKey_x86.reg
>
> reg import SideBySideRegistryKey_x86.reg
>
> Windows6.1-KB5044356-x86.msu
4. If using the failed reboot technique, try to install the Cumulative Update and let it fail.  Apply the new 32-bit or 64-bit SideBySide registry key linked below and retry the update.  This time it will succeed.

### References

These files can all be found on GitHub [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific file links.

> [Updated Manifest File x64 KB5055561](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2025_04/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.27670_none_c89c6bdc36588b52.manifest)
>
> [Updated Manifest File x86 KB5044356](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2024_10/x86_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.27366_none_6c8e9c4e7ded9ec0.manifest)
>
> [Updated Components Registry Key x64 KB5055561](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2025_04/ComponentsRegistryKey_x64.reg)
>
> [Updated Components Registry Key x86 KB5044356](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2024_10/ComponentsRegistryKey_x86.reg)
>
> [Updated SideBySide Registry Key x64 KB5055561](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2025_04/SideBySideRegistryKey_x64.reg)
>
> [Updated SideBySide Registry Key x86 KB5044356](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2024_10/SideBySideRegistryKey_x86.reg)

### Update 2025-04-17
* Replaced January 2025 Servicing Stack Update (KB5050681) with April 2025 Servicing Stack Update (KB5056456) (x64 only).
* Replaced March 2025 Monthly Update (KB5053620) with April 2025 Monthly Update (KB5055561) (x64 only).
* Replaced March 2025 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.27618) with April 2025 (6.1.7602.27670) (x64 only).

For previous updates to this post, see [Windows 7 ESU Analysis Updates Changelog](https://hackandpwn.com/windows-7-esu-analysis-updates-changelog/).