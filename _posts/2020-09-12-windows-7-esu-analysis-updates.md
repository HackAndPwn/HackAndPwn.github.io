---
layout: post
title: Windows 7 ESU Analysis Updates
date: 2020-09-12 00:00:00
last_modified_at: 2021-07-14
---

The original Windows 7 ESU Analysis can be found [here](https://hackandpwn.com/windows-7-esu-analysis).  With the September 2020 Cumulative Update, the technique as described no longer works to install this update.  However, only slight modifications need to be made in order for this new update to also install.

Please reference the original post for the majority of the instructions.  This post will only highlight updates that need to be made.

<br>

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU license can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

<br>

### Installing KB4528069

Install KB4528069 as described in [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis). 

### Installing KB5004289 (July 2021 Cumulative Update)

The July 2021 Cumulative Update includes new ESU files that bump versions past those used in KB4528069.  However, the same technique that previously applied still works.

1. Install the latest Servicing Stack Update [Windows6.1-KB5004378-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/01_Windows6.1-KB5004378-x64.msu).  Reboot the machine.

2. If using the Manifest/Components registry key technique, perform the same installation steps as KB4528069 using the updated files below.

3. If using the failed reboot technique, try to install KB5004289 and let it fail.  Apply the updated SideBySide registry key below and retry the update.  This time it will succeed.

<br>

### References

These files can all be found on Github [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific file links.

> [Updated Manifest File X64 KB5004289](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2021_07/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.25661_none_c8a869a2364f5576.manifest)
>
> [Updated Components Registry Key KB5004289](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2021_07/ComponentsRegistryKey.reg)
>
> [Updated SideBySide Registry Key KB5004289](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/raw/master/2021_07/SideBySideRegistryKey.reg)

<br>

### Update 2020-10-17
* Replaced September 2020 Servicing Stack Update (KB4570673) with October 2020 Servicing Stack Update (KB4580970).
* Replaced September 2020 Monthly Update (KB4577051) with October 2020 Monthly Update (KB4580345).
* Replaced September 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24560) with October 2020 (6.1.7602.24561).

### Update 2020-11-22
* Replaced October 2020 Monthly Update (KB4580345) with November 2020 Monthly Update (KB4586827).
* Replaced October 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24561) with November 2020 (6.1.7602.24562).

### Update 2020-12-15
* Replaced October 2020 Servicing Stack Update (KB4580970) with December 2020 Servicing Stack Update (KB4592510).
* Replaced November 2020 Monthly Update (KB4586827) with December 2020 Monthly Update (KB4592471).
* Replaced November 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24562) with December 2020 (6.1.7602.24563).
* Added a note that a reboot is required after installing the SSU.

### Update 2021-01-17
* Replaced December 2020 Monthly Update (KB4592471) with January 2021 Monthly Update (KB4598279).
* Replaced December 2020 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24563) with January 2021 (6.1.7602.24564).

### Update 2021-02-17
* Replaced January 2021 Monthly Update (KB4598279) with February 2021 Monthly Update (KB4601347).
* Replaced January 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24564) with February 2021 (6.1.7602.24565).

### Update 2021-04-03
* Replaced February 2021 Monthly Update (KB4601347) with March 2021 Monthly Update (KB5000841).
* Replaced February 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24565) with March 2021 (6.1.7602.24566).

### Update 2021-04-15
* Replaced March 2021 Monthly Update (KB5000841) with April 2021 Monthly Update (KB5001335).
* Replaced March 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24566) with April 2021 (6.1.7602.24576).

### Update 2021-05-13
* Replaced April 2021 Monthly Update (KB5001335) with May 2021 Monthly Update (KB5003233).
* Replaced April 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24576) with May 2021 (6.1.7602.24600).

### Update 2021-06-13
* Replaced May 2021 Monthly Update (KB5003233) with June 2021 Monthly Update (KB5003667).
* Replaced May 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.24600) with June 2021 (6.1.7602.25632).

### Update 2021-07-14
* Replaced December 2020 Servicing Stack Update (KB4592510) with July 2021 Servicing Stack Update (KB5004378).
* Replaced June 2021 Monthly Update (KB5003667) with July 2021 Monthly Update (KB5004289).
* Replaced June 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25632) with July 2021 (6.1.7602.25661).