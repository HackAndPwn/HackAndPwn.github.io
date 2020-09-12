---
layout: post
title: Windows 7 ESU Analysis Updates
date: 2020-09-12 00:00:00
tags: draft
---

The original Windows 7 ESU Analysis can be found [here](https://hackandpwn.com/2020-04-28-windows-7-esu-analysis).  With the September 2020 Cumulative Update, the technique as described no longer works to install this update.  However, only slight modifications need to be made in order for this new update to also install.

Please reference the original post for the majority of the instructions.  This post will only highlight updates that need to be made.

<br>

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU license can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

<br>

### Installing KB4528069

Install KB4528069 as described in [Windows 7 ESU Analysis](https://hackandpwn.com/2020-04-28-windows-7-esu-analysis). 

### Installing KB4577051 (September 2020 Cumulative Update)

The September 2020 Cumulative Update includes new ESU files that bump versions past those used in KB4528069.  However, the same technique that previously applied still works.

1. Install the latest Servicing Stack Update [Windows6.1-KB4570673-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/01_Windows6.1-KB4570673-x64.msu)

2. If using the Manifest/Components registry key technique, perform the same installation steps as KB4528069 using the updated files below.

3. If using the failed reboot technique, try to install KB4577051 and let it fail.  Apply the update SideBySide registry key below and retry the update.  This time it will succeed.

<br>

### References

These files can all be found on Github [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific file links.

> [Updated Manifest File X64 KB4577051](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2020_09/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.24560_none_c8a77e3a36502557.manifest)
>
> [Updated Components Registry Key KB4577051](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2020_09/ComponentsRegistryKey.reg)
>
> [Updated SideBySide Registry Key KB4577051](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2020_09/SideBySideRegistryKey.reg)