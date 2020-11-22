---
layout: post
title: Windows 7 ESU Analysis Updates
date: 2020-09-12 00:00:00
last_modified_at: 2020-11-22
---

The original Windows 7 ESU Analysis can be found [here](https://hackandpwn.com/windows-7-esu-analysis).  With the September 2020 Cumulative Update, the technique as described no longer works to install this update.  However, only slight modifications need to be made in order for this new update to also install.

Please reference the original post for the majority of the instructions.  This post will only highlight updates that need to be made.

<br>

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU license can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

<br>

### Installing KB4528069

Install KB4528069 as described in [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis). 

### Installing KB4586827 (November 2020 Cumulative Update)

The November 2020 Cumulative Update includes new ESU files that bump versions past those used in KB4528069.  However, the same technique that previously applied still works.

1. Install the latest Servicing Stack Update [Windows6.1-KB4580970-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/01_Windows6.1-KB4580970-x64.msu)

2. If using the Manifest/Components registry key technique, perform the same installation steps as KB4528069 using the updated files below.

3. If using the failed reboot technique, try to install KB4586827 and let it fail.  Apply the updated SideBySide registry key below and retry the update.  This time it will succeed.

<br>

### References

These files can all be found on Github [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific file links.

> [Updated Manifest File X64 KB4586827](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2020_11/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.24562_none_c8a97ece364e5805.manifest)
>
> [Updated Components Registry Key KB4586827](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2020_11/ComponentsRegistryKey.reg)
>
> [Updated SideBySide Registry Key KB4586827](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2020_11/SideBySideRegistryKey.reg)

<br>

### Update 2020-10-17
* Replaced September 2020 Servicing Stack Update (KB4570673) with October 2020 Servicing Stack Update (KB4580970).
* Replaced September 2020 Monthly Update (KB4577051) with October 2020 Monthly Update (KB4580345).
* Replaced September 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24560) with October 2020 (6.1.7602.24561).

### Update 2020-11-22
* Replaced October 2020 Monthly Update (KB4580345) with November 2020 Monthly Update (KB4586827).
* Replaced October 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24561) with November 2020 (6.1.7602.24562).