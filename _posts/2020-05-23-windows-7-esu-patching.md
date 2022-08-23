---
layout: post
title: Windows 7 ESU Patching
date: 2020-05-23 00:00:00
last_modified_at: 2022-08-22
---

With the May 2020 Windows 7 updates, I went on a mission to determine the minimum set of updates needed to enable all features within Windows 7, including optional hotfixes, and to have the most up-to-date installation possible.  After extensive testing, I concluded that 42 updates not offered through Windows Update would need to be installed to reach this objective.  The following sections describe the updates required and provide links to each.

> The base test image used for this research was 64-Bit Windows 7 Ultimate SP1.  Microsoft Update was enabled, and all updates offered through Windows Update were installed prior to starting this investigation.

> I highly recommend both the [KUC Update Checker](http://windows-update-checker.com/) and [WSUS Offline Update](https://www.wsusoffline.net/) utilities.  I used both during this investigation in order to get to this minimum required set.  

<br>

### Enabling ESU Updates

This first section holds a single update required for ESU updates further down the list.  A detailed analysis on this update can be found on my [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis/) post.

| KB Number | Name                          | Description | Download |
|:---------:|:-----------------------------:|-------------|:--------:|
| KB4528069 |Windows 7 SP1 ESU Verification | This optional update will help verify that eligible Windows 7 SP1 devices can continue to get Extended Security Updates (ESUs) after the end of support date of January 14, 2020. | [Windows6.1-KB4528069-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/01_Enable_ESU/01_Windows6.1-KB4528069-x64.msu) <br>&nbsp;<br> [Windows6.1-KB4528069-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/01_Enable_ESU/01_Windows6.1-KB4528069-x86.msu) |

<br>

### Installing Optional Features

The next section of updates enables all optional features not available through Windows Update.  The notable exception from this list is the AD LDS feature, which is discussed in more detail in the next section.

> After installing the Work Folders for Windows feature (KB2891638), an update may appear as available in Windows Update (KB3081954).  However, this update is not required and is replaced with Service Pack 2 (KB3125574).  Once KB3125574 is installed, KB3081954 will no longer appear in Windows Update.

| KB Number      | Name                                                      | Description | Download |
|:--------------:|:---------------------------------------------------------:|-------------|:--------:|
| KB917607       | Windows Help 32-bit Compatibility Update                  | WinHlp32.exe is required to display 32-bit Help files that have the ".hlp" file name extension. To view .hlp files on Windows 7, you need to install this application. | [Windows6.1-KB917607-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/01_Windows6.1-KB917607-x64.msu) <br>&nbsp;<br> [Windows6.1-KB917607-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/01_Windows6.1-KB917607-x86.msu) |
| KB943790       | File Management API Extensions For BitLocker              | Install this update to extend the File Management APIs to not only enable the discovery and restoration of deleted files from volumes that are not encrypted but also enable the recovery of files from BitLocker encrypted volumes. | [Windows6.1-KB943790-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/02_Windows6.1-KB943790-x64.msu) <br>&nbsp;<br> [Windows6.1-KB943790-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/02_Windows6.1-KB943790-x86.msu) |
| KB958559       | Windows Virtual PC                                        | Windows Virtual PC can be used to run more than one operating system at the same time on one computer, and to run many productivity applications on a virtual Windows environment, with a single click, directly from a computer running Windows 7. | [Windows6.1-KB958559-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/03_Windows6.1-KB958559-x64.msu) <br>&nbsp;<br> [Windows6.1-KB958559-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/03_Windows6.1-KB958559-x86.msu) |
| 1.3.7600.16423 | Windows XP Mode                                           | Windows XP Mode provides a 32-bit virtual Windows XP Professional Service Pack 3 (SP3) environment, which makes it easy to run many of your productivity programs that run on Windows XP on Windows 7. | Windows-XP-Mode-en-us.exe <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_WindowsXPMode_en-us.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_WindowsXPMode_en-us.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_WindowsXPMode_en-us.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_WindowsXPMode_en-us.zip.004) <br> [Part 5](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_WindowsXPMode_en-us.zip.005) |
| KB958830       | Remote Server Administration Tools                        | Remote Server Administration Tools for Windows 7 SP1 enables IT administrators to manage roles and features that are installed on computers that are running Windows Server 2008 R2, Windows Server 2008, or Windows Server 2003, from a remote computer that is running Windows 7 SP1. | Windows6.1-KB958830-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x64.zip.003) <br>&nbsp;<br> Windows6.1-KB958830-x86.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x86.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x86.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB958830-x86.zip.003) |
| KB969168       | Microsoft Agent                                           | Microsoft Agent is a set of software services that supports interactive characters within the Microsoft Windows display. Examples of the Microsoft Agent characters are the Office Assistants. | [Windows6.1-KB969168-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/06_Windows6.1-KB969168-x64.msu) <br>&nbsp;<br> [Windows6.1-KB969168-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/06_Windows6.1-KB969168-x86.msu) |
| KB970985       | Remote Administration Tools For Windows Media Services    | The Remote Administration Tools for Windows Media Services update for Windows 7 SP1 enables the Windows Media Services snap-in for the Microsoft Management Console. | [Windows6.1-KB970985-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/07_Windows6.1-KB970985-x64.msu) <br>&nbsp;<br> [Windows6.1-KB970985-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/07_Windows6.1-KB970985-x86.msu) |
| KB974150       | Windows NTBackup Utility                                  | NTBackup is the legacy Windows backup application included in previous versions of Windows. Files can be backed up to tape, ZIP drives, floppy disks, and hard drives using a proprietary backup format (BKF). It also features integration with Task Scheduler and has several command line switches for scheduled automated backups. | [Windows6.1-KB974150-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/08_Windows6.1-KB974150-x64.msu) <br>&nbsp;<br> [Windows6.1-KB974150-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/08_Windows6.1-KB974150-x86.msu) |
| KB974405       | Windows Identity Foundation                               | The Windows Identity Foundation helps simplify user access for developers by externalizing user access from applications via claims and reducing development effort with pre-built security logic and integrated .NET tools. | [Windows6.1-KB974405-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/09_Windows6.1-KB974405-x64.msu) <br>&nbsp;<br> [Windows6.1-KB974405-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/09_Windows6.1-KB974405-x86.msu) |
| KB974674       | Windows NTBackup Restore Utility                          | The Windows NTBackup Restore Utility for Windows 7 SP1 restores backups that are made on Windows XP and on Windows Server 2003 to computers that are running Windows 7 and Windows Server 2008 R2. | [Windows6.1-KB974674-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/10_Windows6.1-KB974674-x64.msu) <br>&nbsp;<br> [Windows6.1-KB974674-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/10_Windows6.1-KB974674-x86.msu) |
| KB981390       | Windows Server Update Services Best Practices Analyzer    | You can use the Windows Server Update Services (WSUS) update for Best Practices Analyzer to scan a server that is running WSUS. A BPA scan of WSUS can help you determine whether WSUS was properly installed and configured on your server. Scan results are displayed as a list of issues that you can sort by severity, and results include recommendations for fixing issues and links to instructions. No configuration changes are made by running the scan. | [Windows6.1-KB981390-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/11_Windows6.1-KB981390-x64.msu) |
| KB981392       | Application Server Best Practices Analyzer                | You can use the Application Server update for Best Practices Analyzer to scan a server that is running the Application Server role. BPA can help you determine whether Application Server was installed correctly on a server. Scan results are displayed as a list of issues that you can sort by severity, and results include recommendations for fixing issues and links to instructions. No configuration changes are made by running the scan. | [Windows6.1-KB981392-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/12_Windows6.1-KB981392-x64.msu) |
| KB2386667      | Application Server Best Practices Analyzer Rules Revision | Install this update to revise the rules of the Best Practice Analyzer (BPA) for the Application Server role. | [Windows6.1-KB2386667-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/13_Windows6.1-KB2386667-x64.msu) |
| KB2666914      | DirectAccess Connectivity Assistant 2.0                   | The Microsoft DirectAccess Connectivity Assistant (DCA) version 2.0 is used by DirectAccess client computers running Windows 7, to connect to Windows Server 2012 servers running DirectAccess. | [Windows6.1-KB2666914-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/14_Windows6.1-KB2666914-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2666914-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/14_Windows6.1-KB2666914-x86.msu) |
| KB2790621      | Windows Server Essentials Connector                       | Windows Server Essentials Connector is software that helps you connect your PC or Mac client to Windows Server 2012 R2 with the Windows Server Essentials Experience server role enabled. It also enables and manages key client-side functionality of Windows Server Essentials Experience. | [Windows6.1-KB2790621-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/15_Windows6.1-KB2790621-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2790621-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/15_Windows6.1-KB2790621-x86.msu) |
| KB2891638      | Work Folders For Windows                                  | Work Folders is a place to store your work files so that you can open them from all computers and devices, even when you are offline. | [Windows6.1-KB2891638-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/16_Windows6.1-KB2891638-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2891638-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/16_Windows6.1-KB2891638-x86.msu) |
| KB2959936      | Embedded Lockdown Manager Feature Set Update              | Embedded Lockdown Manager uses Windows Management Instrumentation (WMI) providers to detect and change configuration settings and can export the settings to PowerShell scripts. | [Windows6.1-KB2959936-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/17_Windows6.1-KB2959936-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2959936-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/17_Windows6.1-KB2959936-x86.msu) |
| KB2990999      | Internet Explorer 11 Web Driver Tool                      | The IE WebDriver Tool enables developers to create automated tests that simulate users interacting with webpages and report back results in Internet Explorer 11. It can also manage testing across multiple windows, tabs, and webpages in a single session. | [Windows6.1-KB2990999-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/18_Windows6.1-KB2990999-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2990999-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/18_Windows6.1-KB2990999-x86.msu) |
| KB3191566      | Windows Management Framework 5.1                          | Windows Management Framework 5.1 includes updates to Windows PowerShell, Windows PowerShell Desired State Configuration (DSC), Windows Remote Management (WinRM), and Windows Management Instrumentation (WMI). | [Windows6.1-KB3191566-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/19_Windows6.1-KB3191566-x64.msu) <br>&nbsp;<br> [Windows6.1-KB3191566-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/19_Windows6.1-KB3191566-x86.msu) |
 
<br>

### Installing the AD LDS Optional Feature

The next table describes the updates required to enable and patch AD LDS.

There is an issue if the AD LDS feature is installed after Windows 7 SP1.  If this situation occurs, updates included within the Convenience Rollup (SP2) do not apply correctly.  Therefore, these updates need to be installed manually to fully update the feature.  More details can be found [here](http://windows-update-checker.com/FAQ/ConvenienceRollupKB3125574-Issues.htm).

There are a dozen different updates related to AD LDS on Windows 7 SP1.  However, after careful analysis, only half of them have components not replaced by other updates.  These unnecessary updates related to AD LDS are: KB2898997, KB2922852, KB3042816, KB3160352 , KB3184471, and KB3198591.  The required updates are listed in the table below.

> After installing the first AD LDS Update (KB975541), an update may appear as available in Windows Update (KB2853587).  However, this update is not required and is replaced with KB3012660.  Once KB3012660 is installed, KB2853587 will no longer appear in Windows Update. 

> After installing the first AD LDS Update (KB975541), another update may appear as available in Windows Update (KB3184471).  However, this update is not required and is replaced with the latest ESU Windows 7 Cumulative Update.  Once that is installed, KB3184471 will no longer appear in Windows Update. 

| KB Number | Name                                        | Description | Download |
|:---------:|:-------------------------------------------:|-------------|:--------:|
| KB975541  | AD LDS Feature                              | Active Directory Lightweight Directory Services (AD LDS) provides directory services for directory-enabled applications. | [Windows6.1-KB975541-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/01_Windows6.1-KB975541-x64.msu) <br>&nbsp;<br> [Windows6.1-KB975541-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/01_Windows6.1-KB975541-x86.msu) |
| KB2462137 | AD MMC & ADAC Country Update                | The Active Directory Users and Computers MMC snap-in and Active Directory Administrative Center display Serbia and Montenegro as one country instead of as two countries in Windows 7 SP1. | [Windows6.1-KB2462137-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/02_Windows6.1-KB2462137-v2-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2462137-v2-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/02_Windows6.1-KB2462137-v2-x86.msu) |
| KB2539513 | Repadmin Indefinate Query                   | The repadmin command keeps running when you try to look up the users who have their passwords stored on the RODC. | [Windows6.1-KB2539513-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/03_Windows6.1-KB2539513-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2539513-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/03_Windows6.1-KB2539513-x86.msu) |
| KB2589154 | AD MMC RODC Update                          | Active Directory Users and Computers MMC snap-in crashes when you try to remove an RODC in Windows 7 SP1. | [Windows6.1-KB2589154-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/04_Windows6.1-KB2589154-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2589154-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/04_Windows6.1-KB2589154-x86.msu) |
| KB2647644 | AD Certificate Use Issuer Update            | You cannot clear the "Use Issuer for alternate security identity" check box in Windows 7 SP1. | [Windows6.1-KB2647644-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/05_Windows6.1-KB2647644-v2-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2647644-v2-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/05_Windows6.1-KB2647644-v2-x86.msu) |
| KB2790338 | AD FS Update Rollup 3                       | Update Rollup 3 for Active Directory Federation Services (AD FS) 2.0. | [Windows6.1-KB2790338-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/06_Windows6.1-KB2790338-v2-x64.msu) |
| KB3012660 | Unable to install Security Update KB2853587 | "The update is not applicable to your computer" error when you install update 2853587 in Windows 7 SP1 with AD LDS. | [Windows6.1-KB3012660-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/07_Windows6.1-KB3012660-x64.msu) <br>&nbsp;<br> [Windows6.1-KB3012660-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/07_Windows6.1-KB3012660-x86.msu) |

<br>

### Installing the Convenience Rollup (SP2) and running the System Update Readiness Tool

There are two large updates that can be applied next.  The first is the Windows 7 Convenience Rollup, which is also considered SP2 for Windows 7 and includes a collection of hotfixes and updates.  The second update is the System Update Readiness Tool.  This update will not show as installed, so this is included to be executed once (verifying SP2 installation integrity).

> After installing Service Pack 2 (KB3125574), an update may appear as available in Windows Update (KB4539601).  However, this update is not required and is replaced with the latest ESU Windows 7 Cumulative Update.  Once that is installed, KB4539601 will no longer appear in Windows Update.  

| KB Number | Name                         | Description | Download |
|:---------:|:----------------------------:|-------------|:--------:|
| KB3125574 | Service Pack 2               | This rollup package includes most updates that were released after the release of SP1 for Windows 7, through April 2016, intended to make it easy to integrate these fixes. | Windows6.1-KB3125574-v4-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.004) <br> [Part 5](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.005) <br>&nbsp;<br> Windows6.1-KB3125574-v4-x86.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x86.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x86.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x86.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x86.zip.004) |
| KB947821  | System Update Readiness Tool | This tool fixes inconsistencies found in the Windows servicing store which may prevent the successful installation of future updates, service packs, and software. | Windows6.1-KB947821-v34-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.004) <br> [Part 5](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.005) <br> [Part 6](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.006) <br>&nbsp;<br> Windows6.1-KB947821-v34-x86.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x86.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x86.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x86.zip.003) |

<br>

### Optional Software Updates

There are seven Windows 7 optional software updates that do not require an ESU license to install.

| Version     | Name                                                        | Description | Download |
|:-----------:|:-----------------------------------------------------------:|-------------|:--------:|
| 5.3.0.0     | Attack Surface Analyzer                                     | Attack Surface Analyzer takes a snapshot of your system state before and after the installation of product(s) and displays the changes to a number of key elements of the Windows attack surface. | [Attack-Surface-Analyzer-x64.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/01_Attack_Surface_Analyzer_x64.msi) <br>&nbsp;<br> [Attack-Surface-Analyzer-x86.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/01_Attack_Surface_Analyzer_x86.msi) | 
| 5.52        | Enhanced Mitigation Experience Toolkit                      | The Enhanced Mitigation Experience Toolkit (EMET) helps raise the bar against attackers gaining access to computer systems. EMET anticipates the most common actions and techniques adversaries might use in compromising a computer, and helps protect by diverting, terminating, blocking, and invalidating those actions and techniques. EMET helps protect your computer systems even before new and undiscovered threats are formally addressed by security updates and antimalware software. EMET benefits enterprises and all computer users by helping to protect against security threats and breaches that can disrupt businesses and daily lives. | [EMET-Setup.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/02_EMET_Setup.msi) |
| 12.0.0.0    | Enterprise Mode Internet Explorer Site List Manager         | This tool lets IT Professionals create and update the Enterprise Mode Site List in the version 2.0 (v.2) XML schema. The Enterprise Mode schema has been updated to v.2 to be easier to read and to provide a better foundation for future capabilities. | [EM-IE-Site-List-Manager.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/03_EMIESiteListManager.msi) |
| 10.0.237.0  | Windows Journal                                             | Windows Journal has been removed from certain versions of the Windows Operating System.  This update allows users to install Windows Journal on versions of Windows where it has been removed. | [Journal-en-us-x64.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/04_Journal_en-us_x64.msi) <br>&nbsp;<br> [Journal-en-us-x86.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/04_Journal_en-us_x86.msi) |
| 2.3.2208    | Microsoft Baseline Security Analyzer                        | The Microsoft Baseline Security Analyzer provides a streamlined method to identify missing security updates and common security misconfigurations. | [MBSA-Setup-x64-EN.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/05_MBSASetup-x64-EN.msi) <br>&nbsp;<br> [MBSA-Setup-x86-EN.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/05_MBSASetup-x86-EN.msi) |
| 6.3.9723.0  | Microsoft Camera Codec Pack                                 | The Microsoft Camera Codec Pack enables the viewing of a variety of device-specific file formats in Windows Live Photo Gallery as well as other software that is based in Windows Imaging Codecs (WIC).  Installing this package will allow supported RAW camera files to be viewable in Windows Explorer.  | [Microsoft-Camera-Codec-Pack-x64.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/06_MicrosoftCameraCodecPack-x64.msi) <br>&nbsp;<br> [Microsoft-Camera-Codec-Pack-x86.msi](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/06_MicrosoftCameraCodecPack-x86.msi) |
| 10.0.7063.0 | Utilities and SDK for Subsystem for UNIX-based Applications | Utilities and SDK for Subsystem for UNIX-based Applications (SUA) includes the following base utilities, software development kits (SDKs), and shells for use with Subsystem for UNIX-based Applications: Base subsystem commands and utilities, SVR-5 commands and utilities, Base subsystem SDK, GNU SDK, GNU commands and utilities, SCO commands and utilities, UNIX-based Perl, Microsoft Visual Studio® Debugger Extension for debugging POSIX applications, Korn and C shells, and Subsystem for UNIX-based Applications HTML Help files (\*.chm). This release allows you to develop x64-based applications by using SUA, and develop and port custom UNIX-based applications to Windows by using the Windows OCI (Oracle Call Interface) and Windows ODBC libraries. | Utilities-and-SDK-for-Subsystem-for-UNIX-based-Applications-AMD64.exe <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_AMD64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_AMD64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_AMD64.zip.003) <br>&nbsp;<br> Utilities-and-SDK-for-Subsystem-for-UNIX-based-Applications-X86.exe <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_X86.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_X86.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Optional_Software_Updates/07_Utilities_and_SDK_for_Subsystem_for_UNIX-based_Applications_X86.zip.003) |

<br>

### Non-ESU SP2 Hotfixes

There are six hotfixes available to update components after Service Pack 2 has been installed.  These do not require an ESU license to install.

| KB Number | Name                                            | Description | Download |
|:---------:|:-----------------------------------------------:|-------------|:--------:|
| KB2818604 | AMD Microcode Update                            | A microcode update is available for Windows 7-based computers that use AMD processors. | [Windows6.1-KB2818604-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/01_Windows6.1-KB2818604-x64.msu) <br>&nbsp;<br> [Windows6.1-KB2818604-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/01_Windows6.1-KB2818604-x86.msu) |
| KB3046480 | .NET Framework 1.1 Migration Check              | This update enables the system to determine whether to migrate the Microsoft .NET Framework 1.1 to a later version of Windows when you upgrade from Windows 7 to a later version of Windows. This determination is based on the usage of the .NET Framework 1.1. | [Windows6.1-KB3046480-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/02_Windows6.1-KB3046480-x64.msu) <br>&nbsp;<br> [Windows6.1-KB3046480-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/02_Windows6.1-KB3046480-x86.msu) |
| KB3064209 | Intel Microcode Update                          | June 2015 Intel CPU microcode update for Windows. | [Windows6.1-KB3064209-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/03_Windows6.1-KB3064209-x64.msu) <br>&nbsp;<br> [Windows6.1-KB3064209-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/03_Windows6.1-KB3064209-x86.msu) |
| KB4072650 | Hyper-V Integration Components Update           | This update installs the latest integrated components for Windows 7 Guest Virtual Machines (VMs) that are running on a Windows 10-based or Windows Server 2016-based host, or a Windows Server 2012 R2-based host. | [Windows6.1-KB4072650-x64.cab](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/bin/04_Windows6.1-KB4072650-x64.cab) <br>&nbsp;<br> [Windows6.1-KB4072650-x86.cab](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/bin/04_Windows6.1-KB4072650-x86.cab) |
| KB4524752 | Windows 7 SP1 Support Notification              | After 10 years of servicing, January 14, 2020 is the last day Microsoft will offer security updates for computers that run Windows 7 Service Pack 1 (SP1). This update enables reminders about Windows 7 end of support. | [Windows6.1-KB4524752-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/05_Windows6.1-KB4524752-x64.msu) <br>&nbsp;<br> [Windows6.1-KB4524752-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/05_Windows6.1-KB4524752-x86.msu) |
| KB4578847 | Update for Application and Device Compatibility | Adds functionality for evaluating the compatibility status of the Windows ecosystem to help ensure application and device compatibility for all updates to Windows. | [Windows6.1-KB4578847-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/06_Windows6.1-KB4578847-x64.msu) <br>&nbsp;<br> [Windows6.1-KB4578847-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_Non_ESU_Hotfixes/06_Windows6.1-KB4578847-x86.msu) |

<br>

### ESU Updates

This section describes the latest ESU updates available for Windows 7.  All of these updates are cumulative containing fixes from all previous versions of the updates.  An ESU license is required to install these updates, and only the latest one needs to be installed.

| KB Number   | Name                                    | Description | Download |
|:-----------:|:---------------------------------------:|-------------|:--------:|
| KB5016057   | July 2022 Servicing Stack Update        | This update makes quality improvements to the servicing stack, which is the component that installs Windows updates. Servicing stack updates (SSU) makes sure that you have a robust and reliable servicing stack so that your devices can receive and install Microsoft updates. | [Windows6.1-KB5016057-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5016057-x64.msu) <br>&nbsp;<br> [Windows6.1-KB5016057-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/01_Windows6.1-KB5016057-x86.msu) |
| KB5016676\* | August 2022 Windows 7 Cumulative Update | Security and Quality Rollup for Windows 7 SP1. | Windows6.1-KB5016676-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x64.zip.004) <br>&nbsp;<br> Windows6.1-KB5016676-x86.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x86.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x86.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/02_Windows6.1-KB5016676-x86.zip.003) |
| KB5013637   | May 2022 .NET Framework 3.5.1 Update    | Security and Quality Rollup for .NET Framework 3.5.1 for Windows 7 SP1. | [Windows6.1-KB5013637-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/03_Windows6.1-KB5013637-x64.msu) <br>&nbsp;<br> [Windows6.1-KB5013637-x86.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/03_Windows6.1-KB5013637-x86.msu) |
| KB5016367   | August 2022 .NET Framework 4.8 Update   | Security and Quality Rollup for .NET Framework 4.8 for Windows 7 SP1. | [ndp48-KB5016367-x64.exe](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/04_ndp48-KB5016367-x64.exe) <br>&nbsp;<br> [ndp48-KB5016367-x86.exe](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_Updates/04_ndp48-KB5016367-x86.exe) |

\* Note: a new ESU package has been integrated into this update.  For details please see this post: [Windows 7 ESU Analysis Updates](https://hackandpwn.com/windows-7-esu-analysis-updates/).

<br>

### Root Certificate Updates

Finally, the latest Microsoft Root Certificates need to be installed into the Local Computer Trusted Root Authority Certificate Store.  A batch file to automatically install all certificates and revocation lists can be found here: [Import.cmd](https://github.com/HackAndPwn/Windows-7-Patching/blob/master/08_Certs/Import.cmd)

| Date       | Type            | Download |
|:----------:|:---------------:|:--------:|
| 2018-08-02 | Certificate     | [MicRooCerAut2011_2011_03_22.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/MicRooCerAut2011_2011_03_22.crt) |
| 2018-08-02 | Certificate     | [Microsoft ECC Product Root Certificate Authority 2018.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Product%20Root%20Certificate%20Authority%202018.crt) |
| 2018-08-02 | Certificate     | [Microsoft ECC TS Root Certificate Authority 2018.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20TS%20Root%20Certificate%20Authority%202018.crt) |
| 2018-08-02 | Certificate     | [Microsoft Time Stamp Root Certificate Authority 2014.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20Time%20Stamp%20Root%20Certificate%20Authority%202014.crt) |
| 2020-01-22 | Certificate     | [Microsoft ECC Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) |
| 2020-01-22 | Certificate     | [Microsoft EV ECC Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20ECC%20Root%20Certificate%20Authority%202017.crt) |
| 2020-01-22 | Certificate     | [Microsoft RSA Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) |
| 2020-01-22 | Certificate     | [Microsoft EV RSA Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20RSA%20Root%20Certificate%20Authority%202017.crt) |
| 2022-06-01 | Revocation List | [Microsoft ECC Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crl) |
| 2022-07-05 | Revocation List | [MicRooCerAut_2010-06-23.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/MicRooCerAut_2010-06-23.crl) |
| 2022-07-06 | Revocation List | [Microsoft RSA Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crl) |
| 2022-07-13 | Revocation List | [Microsoft ECC Product Root Certificate Authority 2018.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Product%20Root%20Certificate%20Authority%202018.crl) |
| 2022-07-13 | Revocation List | [Microsoft ECC TS Root Certificate Authority 2018.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20TS%20Root%20Certificate%20Authority%202018.crl) |
| 2022-07-23 | Revocation List | [Microsoft EV ECC Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20ECC%20Root%20Certificate%20Authority%202017.crl) |
| 2022-07-23 | Revocation List | [Microsoft EV RSA Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20RSA%20Root%20Certificate%20Authority%202017.crl) |
| 2022-07-27 | Revocation List | [Microsoft Time Stamp Root Certificate Authority 2014.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20Time%20Stamp%20Root%20Certificate%20Authority%202014.crl) |

<br>

### Conclusion

Once these updates are installed on top of an up-to-date Windows 7 SP1 installation, the OS has been completely updated with hotfixes and optional features.  All of these updates can be found on this GitHub repository: [Windows 7 Patching](https://github.com/HackAndPwn/Windows-7-Patching).

The goal is to keep this list updated as changes are introduced.  Please reach out to me via [Twitter](https://twitter.com/HackAndPwn) or [GitHub](https://github.com/HackAndPwn) if there is an update that is missing, if there is an update in this list that you feel may not be needed, or if there are any other questions or feedback.

<br>

### Update 2020-05-25
* Internet Explorer 11 Cumulative Update (KB4556798) is included with the generic Windows 7 Monthly Update.  Therefore, this update is no longer required.

### Update 2020-05-26
* Added information about unnecessary updates showing up in Windows Update (KB2853587, KB3081954, KB3184471, KB4539601) and which updates replace them.  
* Removed link to IE 11 Cumulative Update.

### Update 2020-06-10
* Replaced May 2020 Servicing Stack Update (KB4555449) with June 2020 Servicing Stack Update (KB4562030).
* Replaced May 2020 Monthly Update (KB4556836) with June 2020 Monthly Update (KB4561643).
* Updated MicRooCerAut_2010-06-23.crl
* Updated Microsoft Time Stamp Root Certificate Authority 2014
* Sorted Certificates By Date

### Update 2020-07-15
* Replaced June 2020 Servicing Stack Update (KB4562030) with July 2020 Servicing Stack Update (KB4565354).
* Replaced May 2020 .NET Framework 3.5.1 Update (KB4552940) with July 2020 .NET Framework 3.5.1 Update (KB4565612).
* Replaced June 2020 Monthly Update (KB4561643) with July 2020 Monthly Update (KB4565524).
* Replaced May 2020 .NET Framework 4.8 Update (KB4552921) with July 2020 .NET Framework 4.8 Update (KB4565636).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.

### Update 2020-08-11
* Replaced July 2020 Servicing Stack Update (KB4565354) with August 2020 Servicing Stack Update (KB4570673).
* Replaced July 2020 .NET Framework 3.5.1 Update (KB4565612 v1 & v2) with August 2020 .NET Framework 3.5.1 Update (KB4569767).
* Replaced July 2020 Monthly Update (KB4565524) with August 2020 Monthly Update (KB4571729).
* Replaced July 2020 .NET Framework 4.8 Updates (KB4565636 v1 & v2) with August 2020 .NET Framework 4.8 Update (KB4569754).
* Removed May 2020 ESU Preparation Package (KB4538483) and July 2020 ESU Preparation Package (KB4575903).  This has been replaced with the August 2020 Monthly Update (KB4571729).

### Update 2020-09-14
* Replaced August 2020 Monthly Update (KB4571729) with September 2020 Monthly Update (KB4577051).
* Replaced August 2020 .NET Framework 4.8 Update (KB4569754) with September 2020 .NET Framework 4.8 Update (KB4576487).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2020-10-17
* Replaced August 2020 Servicing Stack Update (KB4570673) with October 2020 Servicing Stack Update (KB4580970).
* Replaced September 2020 Monthly Update (KB4577051) with October 2020 Monthly Update (KB4580345).
* Replaced August 2020 .NET Framework 3.5.1 Update (KB4569767) with October 2020 .NET Framework 3.5.1 Update (KB4578952).
* Replaced September 2020 .NET Framework 4.8 Update (KB4576487) with October 2020 .NET Framework 4.8 Update (KB4578977).
* Changed the order of ESU updates (Monthly Update needs to be installed prior to installing .NET Framework 3.5.1 Update).

### Update 2020-10-22
* Updated the description for KB970985 - Thanks <a href="https://twitter.com/FrankLesniak">FrankLesniak</a>!

### Update 2020-11-22
* Replaced October 2020 Monthly Update (KB4580345) with November 2020 Monthly Update (KB4586827).
* Replaced October 2020 .NET Framework 4.8 Update (KB4578977) with November 2020 .NET Framework 4.8 Update (KB4585205).
* Updated MicRooCerAut_2010-06-23.crl
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl

### Update 2020-12-15
* Replaced October 2020 Servicing Stack Update (KB4580970) with December 2020 Servicing Stack Update (KB4592510).
* Replaced November 2020 Monthly Update (KB4586827) with December 2020 Monthly Update (KB4592471).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.

### Update 2021-01-17
* Replaced December 2020 Monthly Update (KB4592471) with January 2021 Monthly Update (KB4598279).
* Replaced December 2020 .NET Framework 4.8 Update (KB4585205) with January 2021 .NET Framework 4.8 Update (KB4597254).

### Update 2021-02-17
* Replaced January 2021 Monthly Update (KB4598279) with February 2021 Monthly Update (KB4601347).
* Replaced January 2021 .NET Framework 4.8 Update (KB4597254) with February 2021 .NET Framework 4.8 Update (KB4600944).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2021-04-04
* Replaced February 2021 Monthly Update (KB4601347) with March 2021 Monthly Update (KB5000841).
* Replaced February 2021 .NET Framework 4.8 Update (KB4600944) with March 2021 .NET Framework 4.8 Update (KB4600944-v2).

### Update 2021-04-15
* Replaced March 2021 Monthly Update (KB5000841) with April 2021 Monthly Update (KB5001335).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.
* Excluded Graphical Update (KB4601275) - included in April 2021 Monthly Update (KB5001335).
* Excluded DST Update (KB5001639) - included in April 2021 Monthly Update (KB5001335).

### Update 2021-05-13
* Replaced April 2021 Monthly Update (KB5001335) with May 2021 Monthly Update (KB5003233).
* Replaced March 2021 .NET Framework 4.8 Update (KB4600944) with May 2021 .NET Framework 4.8 Update (KB5001843).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.

### Update 2021-06-13
* Replaced May 2021 Monthly Update (KB5003233) with June 2021 Monthly Update (KB5003667).
* Replaced May 2021 .NET Framework 4.8 Update (KB5001843) with June 2021 .NET Framework 4.8 Update (KB5003543).

### Update 2021-07-14
* Replaced December 2020 Servicing Stack Update (KB4592510) with July 2021 Servicing Stack Update (KB5004378).
* Replaced June 2021 Monthly Update (KB5003667) with July 2021 Monthly Update (KB5004289).
* Replaced June 2021 .NET Framework 4.8 Update (KB5003543) with July 2021 .NET Framework 4.8 Update (KB5004116).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2021-08-11
* Added 32-bit Updates
* Replaced July 2021 Monthly Update (KB5004289) with August 2021 Monthly Update (KB5005088).
* Replaced July 2021 .NET Framework 4.8 Update (KB5004116) with August 2021 .NET Framework 4.8 Update (KB5004755).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.

### Update 2021-09-25
* Updated GitHub links.
* Added Windows XP Mode - (32-bit / 64-bit).
* Added KB981390 - (64-bit).
* Added KB981392 - (64-bit).
* Added KB2386667 - (64-bit).
* Added KB2790338 - (64-bit).
* Added Optional Software Updates Section.
* Added Attack Surface Analyzer (32-bit / 64-bit).
* Added Enhanced Mitigation Experience Toolkit (32-bit / 64-bit).
* Added Enterprise Mode Internet Explorer Site List Manager (32-bit / 64-bit).
* Added Windows Journal (32-bit / 64-bit).
* Added Microsoft Baseline Security Analyzer (32-bit / 64-bit).
* Added Microsoft Camera Codec Pack  (32-bit / 64-bit).
* Added Utilities and SDK for Subsystem for UNIX-based Applications (32-bit / 64-bit).
* Removed KB3161102 (Windows Journal Removal).
* Removed KB4016754 (Media Transfer Protocol Driver Update).
* Added KB4524752 - (32-bit / 64-bit).
* Added KB4578847 - (32-bit / 64-bit).
* Replaced August 2021 Monthly Update (KB5005088) with September 2021 Monthly Update (KB5005633).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2021-10-22
* Replaced July 2021 Servicing Stack Update (KB5004378) with October 2021 Servicing Stack Update (KB5006749).
* Replaced September 2021 Monthly Update (KB5005633) with October 2021 Monthly Update (KB5006743).
* Replaced August 2021 .NET Framework 4.8 Update (KB5004755) with October 2021 .NET Framework 4.8 Update (KB5006060).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.

### Update 2021-11-18
* Replaced October 2021 Monthly Update (KB5006743) with November 2021 Monthly Update (KB5007236).
* Replaced October 2021 .NET Framework 4.8 Update (KB5006060) with November 2021 .NET Framework 4.8 Update (KB5007149).
* Updated Microsoft RSA Root Certificate Authority 2017.crl.

### Update 2021-12-24
* Replaced November 2021 Monthly Update (KB5007236) with December 2021 Monthly Update (KB5008244).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2022-01-16
* Replaced December 2021 Monthly Update (KB5008244) with January 2022 Monthly Update (KB5009610).
* Replaced October 2020 .NET Framework 3.5.1 Update (KB4578952) with January 2022 .NET Framework 3.5.1 Update (KB5008867).
* Replaced November 2021 .NET Framework 4.8 Update (KB5007149) with January 2022 .NET Framework 4.8 Update (KB5008858).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.

### Update 2022-02-20
* Replaced October 2021 Servicing Stack Update (KB5006749) with February 2022 Servicing Stack Update (KB5010451).
* Replaced January 2022 Monthly Update (KB5009610) with February 2022 Monthly Update (KB5010404).
* Replaced January 2022 .NET Framework 4.8 Update (KB5008858) with February 2022 .NET Framework 4.8 Update (KB5010457).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2022-03-23
* Replaced February 2022 Servicing Stack Update (KB5010451) with March 2022 Servicing Stack Update (KB5011649).
* Replaced February 2022 Monthly Update (KB5010404) with March 2022 Monthly Update (KB5011552).
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.

### Update 2022-04-20
* Replaced March 2022 Monthly Update (KB5011552) with April 2022 Monthly Update (KB5012626).
* Replaced February 2022 .NET Framework 4.8 Update (KB5010457) with April 2022 .NET Framework 4.8 Update (KB5012125).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2022-05-23
* Replaced April 2022 Monthly Update (KB5012626) with May 2022 Monthly Update (KB5014012).
* Replaced January 2022 .NET Framework 3.5.1 Update (KB5008867) with May 2022 .NET Framework 3.5.1 Update (KB5013637).
* Replaced April 2022 .NET Framework 4.8 Update (KB5012125) with May 2022 .NET Framework 4.8 Update (KB5013632).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.

### Update 2022-06-19
* Replaced May 2022 Monthly Update (KB5014012) with June 2022 Monthly Update (KB5014748).
* Replaced May 2022 .NET Framework 4.8 Update (KB5013632) with June 2022 .NET Framework 4.8 Update (KB5014631).
* Updated Microsoft ECC Root Certificate Authority 2017.crl.

### Update 2022-07-18
* Replaced March 2022 Servicing Stack Update (KB5011649) with July 2022 Servicing Stack Update (KB5016057).
* Replaced June 2022 Monthly Update (KB5014748) with July 2022 Monthly Update (KB5015861).
* Updated Microsoft ECC Product Root Certificate Authority 2018.crl.
* Updated Microsoft ECC TS Root Certificate Authority 2018.crl.
* Updated Microsoft RSA Root Certificate Authority 2017.crl.
* Updated MicRooCerAut_2010-06-23.crl.

### Update 2022-08-22
* Replaced July 2022 Monthly Update (KB5015861) with August 2022 Monthly Update (KB5016676).
* Replaced June 2022 .NET Framework 4.8 Update (KB5014631) with August 2022 .NET Framework 4.8 Update (KB5016367).
* Updated Microsoft EV ECC Root Certificate Authority 2017.crl.
* Updated Microsoft EV RSA Root Certificate Authority 2017.crl.
* Updated Microsoft Time Stamp Root Certificate Authority 2014.crl.