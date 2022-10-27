---
layout: post
title: Windows 7 ESU Analysis Updates
date: 2020-09-12 00:00:00
last_modified_at: 2022-10-26
---

The original Windows 7 ESU Analysis can be found [here](https://hackandpwn.com/windows-7-esu-analysis).  With the September 2020 Cumulative Update, the technique as described no longer works to install this update.  However, only slight modifications need to be made in order for this new update to also install.

Please reference the original post for the majority of the instructions.  This post will only highlight updates that need to be made.

<br>

> Important:  You must obtain an ESU license to apply ESU updates.  Details on obtaining an ESU license can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).  This research was completed for security vulnerability research purposes only following the [Microsoft Legal Safe Harbor Terms](https://www.microsoft.com/en-us/msrc/bounty-safe-harbor).  Do not try to reproduce without having the required licenses.

<br>

### Installing KB4528069

Install KB4528069 as described in [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis). 

### Installing KB5018454 (October 2022 Cumulative Update)

The October 2022 Cumulative Update includes new ESU files that bump versions past those used in KB4528069.  However, the same technique that previously applied still works.

1. Install the latest Servicing Stack Update [Windows6.1-KB5017397-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5017397-x64.msu) [Windows6.1-KB5017397-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5017397-x86.msu).  Reboot the machine.

2. If using the Manifest/Components registry key technique, perform the same installation steps as KB4528069 using the updated files below.

3. If using the failed reboot technique, try to install KB5018454 and let it fail.  Apply the updated SideBySide registry key below and retry the update.  This time it will succeed.

<br>

### References

These files can all be found on GitHub [here](https://github.com/HackAndPwn/Windows-7-ESU-Analysis).  See below for specific file links.

> [Updated Manifest File x64 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/amd64_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.26174_none_c8a07a4e3654e54a.manifest)
>
> [Updated Manifest File x86 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/x86_microsoft-windows-s..edsecurityupdatesai_31bf3856ad364e35_6.1.7602.26174_none_6c81deca7df77414.manifest)
>
> [Updated Components Registry Key x64 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/ComponentsRegistryKey_x64.reg)
>
> [Updated Components Registry Key x86 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/ComponentsRegistryKey_x86.reg)
>
> [Updated SideBySide Registry Key x64 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/SideBySideRegistryKey_x64.reg)
>
> [Updated SideBySide Registry Key x86 KB5018454](https://github.com/HackAndPwn/Windows-7-ESU-Analysis/blob/master/2022_10/SideBySideRegistryKey_x86.reg)

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

### Update 2021-08-10
* Added 32-Bit links.
* Replaced July 2021 Monthly Update (KB5004289) with August 2021 Monthly Update (KB5005088).
* Replaced July 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25661) with August 2021 (6.1.7602.25685).

### Update 2021-09-25
* Replaced August 2021 Monthly Update (KB5005088) with September 2021 Monthly Update (KB5005633).
* Replaced August 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25685) with September 2021 (6.1.7602.25712).
* Updated GitHub links.

### Update 2021-10-21
* Replaced July 2021 Servicing Stack Update (KB5004378) with October 2021 Servicing Stack Update (KB5006749).
* Replaced September 2021 Monthly Update (KB5005633) with October 2021 Monthly Update (KB5006743).
* Replaced September 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25712) with October 2021 (6.1.7602.25740).

### Update 2021-11-18
* Replaced October 2021 Monthly Update (KB5006743) with November 2021 Monthly Update (KB5007236).
* Replaced October 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25740) with November 2021 (6.1.7602.25769).

### Update 2021-12-24
* Replaced November 2021 Monthly Update (KB5007236) with December 2021 Monthly Update (KB5008244).
* Replaced November 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25769) with December 2021 (6.1.7602.25796).

### Update 2022-01-16
* Replaced December 2021 Monthly Update (KB5008244) with January 2022 Monthly Update (KB5009610).
* Replaced December 2021 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25796) with January 2022 (6.1.7602.25829).

### Update 2022-02-20
* Replaced October 2021 Servicing Stack Update (KB5006749) with February 2022 Servicing Stack Update (KB5010451).
* Replaced January 2022 Monthly Update (KB5009610) with February 2022 Monthly Update (KB5010404).
* Replaced January 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25829) with February 2022 (6.1.7602.25860).

### Update 2022-03-23
* Replaced February 2022 Servicing Stack Update (KB5010451) with March 2022 Servicing Stack Update (KB5011649).
* Replaced February 2022 Monthly Update (KB5010404) with March 2022 Monthly Update (KB5011552).
* Replaced February 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25860) with March 2022 (6.1.7602.25898).

### Update 2022-04-20
* Replaced March 2022 Monthly Update (KB5011552) with April 2022 Monthly Update (KB5012626).
* Replaced March 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25898) with April 2022 (6.1.7602.25924).

### Update 2022-05-23
* Replaced April 2022 Monthly Update (KB5012626) with May 2022 Monthly Update (KB5014012).
* Replaced April 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25924) with May 2022 (6.1.7602.25954).

### Update 2022-06-19
* Replaced May 2022 Monthly Update (KB5014012) with June 2022 Monthly Update (KB5014748).
* Replaced May 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25954) with June 2022 (6.1.7602.25984).

### Update 2022-07-18
* Replaced March 2022 Servicing Stack Update (KB5011649) with July 2022 Servicing Stack Update (KB5016057).
* Replaced June 2022 Monthly Update (KB5014748) with July 2022 Monthly Update (KB5015861).
* Replaced June 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.25984) with July 2022 (6.1.7602.26022).

### Update 2022-08-22
* Replaced July 2022 Monthly Update (KB5015861) with August 2022 Monthly Update (KB5016676).
* Replaced July 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.26022) with August 2022 (6.1.7602.26065).

### Update 2022-09-26
* Replaced July 2022 Servicing Stack Update (KB5016057) with September 2022 Servicing Stack Update (KB5017397).
* Replaced August 2022 Monthly Update (KB5016676) with September 2022 Monthly Update (KB5017361).
* Replaced August 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.26065) with September 2022 (6.1.7602.26115).

### Update 2022-10-26
* Replaced September 2022 Monthly Update (KB5017361) with October 2022 Monthly Update (KB5018454).
* Replaced September 2022 Manifest, Components Registry Key, and SideBySide Registry Key (6.1.7602.26115) with October 2022 (6.1.7602.26174).