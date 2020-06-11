---
layout: post
title: Windows 7 ESU Patching
date: 2020-05-23 00:00:00
last_modified_at: 2020-06-10
---

With the May 2020 Windows 7 updates, I went on a mission to determine the minimum set of updates needed to enable all features within Windows 7, including optional hotfixes, and to have the most up-to-date installation possible.  After extensive testing, I concluded that 35 updates not offered through Windows Update would need to be installed to reach this objective.  The following sections describe the updates required and provide links to each.

> The base test image used for this testing was 64-bit Windows 7 Ultimate SP1.  Microsoft Update was enabled, and all updates offered through Windows Update were installed prior to starting this investigation.  All links and details within this post were only validated on 64-bit, although 32-bit should have a similar set of results.

> I highly recommend both the [KUC Update Checker](http://windows-update-checker.com/) and [WSUS Offline Update](https://www.wsusoffline.net/) utilities.  I used both during this investigation in order to get to this minimum required set.  

<br>

### Enabling ESU Updates

This first section holds a single update required for ESU updates further down the list.  A detailed analysis on this update can be found on my [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis/) post.

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB4528069 |Windows 7 SP1 ESU Verification                | This optional update will help verify that eligible Windows 7 SP1 devices can continue to get Extended Security Updates (ESUs) after the end of support date of January 14, 2020. | [Windows6.1-KB4528069-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/01_Enable_ESU/01_Windows6.1-KB4528069-x64.msu)

<br>

### Installing Optional Features

The next section of updates enables all optional features not available through Windows Update.  The notable exception from this list is the AD LDS feature, which is discussed in more detail in the next section.

> After installing the Work Folders for Windows feature (KB2891638), an update may appear as available in Windows Update (KB3081954).  However, this update is not required and is replaced with Service Pack 2 (KB3125574).  Once KB3125574 is installed, KB3081954 will no longer appear in Windows Update.

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB917607  | Windows Help 32-bit Compatibility Update     | WinHlp32.exe is required to display 32-bit Help files that have the ".hlp" file name extension. To view .hlp files on Windows 7, you need to install this application. | [Windows6.1-KB917607-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/01_Windows6.1-KB917607-x64.msu) |
| KB943790  | File Management API Extensions For BitLocker | Install this update to extend the File Management APIs to not only enable the discovery and restoration of deleted files from volumes that are not encrypted but also enable the recovery of files from BitLocker encrypted volumes. | [Windows6.1-KB943790-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/02_Windows6.1-KB943790-x64.msu) |
| KB958559  | Windows Virtual PC                           | Windows Virtual PC can be used to run more than one operating system at the same time on one computer, and to run many productivity applications on a virtual Windows environment, with a single click, directly from a computer running Windows 7. | [Windows6.1-KB958559-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/03_Windows6.1-KB958559-x64.msu) |
| KB958830  | Remote Server Administration Tools           | Remote Server Administration Tools for Windows 7 SP1 enables IT administrators to manage roles and features that are installed on computers that are running Windows Server 2008 R2, Windows Server 2008, or Windows Server 2003, from a remote computer that is running Windows 7 SP1. | Windows6.1-KB958830-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.001)  <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.002)  <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.003) |
| KB969168  | Microsoft Agent                              | Microsoft Agent is a set of software services that supports interactive characters within the Microsoft Windows display. Examples of the Microsoft Agent characters are the Office Assistants. | [Windows6.1-KB969168-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB969168-x64.msu) |
| KB970985  | Windows Activation Technologies              | Windows Activation Technologies helps you confirm that the copy of Windows 7 that is running on your computer is genuine. Additionally, Windows Activation Technologies helps protect against the risks of counterfeit software. | [Windows6.1-KB970985-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/06_Windows6.1-KB970985-x64.msu) |
| KB974150  | Windows NTBackup Utility                    | NTBackup is the legacy Windows backup application included in previous versions of Windows. Files can be backed up to tape, ZIP drives, floppy disks, and hard drives using a proprietary backup format (BKF). It also features integration with Task Scheduler and has several command line switches for scheduled automated backups. | [Windows6.1-KB974150-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/07_Windows6.1-KB974150-x64.msu) |
| KB974405  | Windows Identity Foundation                  | The Windows Identity Foundation helps simplify user access for developers by externalizing user access from applications via claims and reducing development effort with pre-built security logic and integrated .NET tools. | [Windows6.1-KB974405-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/08_Windows6.1-KB974405-x64.msu) |
| KB974674  | Windows NTBackup Restore Utility             | The Windows NTBackup Restore Utility for Windows 7 SP1 restores backups that are made on Windows XP and on Windows Server 2003 to computers that are running Windows 7 and Windows Server 2008 R2. | [Windows6.1-KB974674-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/09_Windows6.1-KB974674-x64.msu) |
| KB2666914 | DirectAccess Connectivity Assistant 2.0      | The Microsoft DirectAccess Connectivity Assistant (DCA) version 2.0 is used by DirectAccess client computers running Windows 7, to connect to Windows Server 2012 servers running DirectAccess. | [Windows6.1-KB2666914-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/10_Windows6.1-KB2666914-x64.msu) |
| KB2790621 | Windows Server Essentials Connector          | Windows Server Essentials Connector is software that helps you connect your PC or Mac client to Windows Server 2012 R2 with the Windows Server Essentials Experience server role enabled. It also enables and manages key client-side functionality of Windows Server Essentials Experience. | [Windows6.1-KB2790621-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/11_Windows6.1-KB2790621-x64.msu) |
| KB2891638 | Work Folders For Windows                     | Work Folders is a place to store your work files so that you can open them from all computers and devices, even when you are offline. | [Windows6.1-KB2891638-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/12_Windows6.1-KB2891638-x64.msu) |
| KB2959936 | Embedded Lockdown Manager Feature Set Update | Embedded Lockdown Manager uses Windows Management Instrumentation (WMI) providers to detect and change configuration settings and can export the settings to PowerShell scripts. | [Windows6.1-KB2959936-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/13_Windows6.1-KB2959936-x64.msu) |
| KB2990999 | Internet Explorer 11 Web Driver Tool         | The IE WebDriver Tool enables developers to create automated tests that simulate users interacting with webpages and report back results in Internet Explorer 11. It can also manage testing across multiple windows, tabs, and webpages in a single session. | [Windows6.1-KB2990999-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/14_Windows6.1-KB2990999-x64.msu) |
| KB3191566 | Windows Management Framework 5.1             | Windows Management Framework 5.1 includes updates to Windows PowerShell, Windows PowerShell Desired State Configuration (DSC), Windows Remote Management (WinRM), and Windows Management Instrumentation (WMI). | [Windows6.1-KB3191566-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/15_Windows6.1-KB3191566-x64.msu) |
 
<br>

### Installing the AD LDS Optional Feature

The next table describes the updates required to enable and patch AD LDS.

There is an issue if the AD LDS feature is installed after Windows 7 SP1.  If this situation occurs, updates included within the Convenience Rollup (SP2) do not apply correctly.  Therefore, these updates need to be installed manually to fully update the feature.  More details can be found [here](http://windows-update-checker.com/FAQ/ConvenienceRollupKB3125574-Issues.htm).

There are a dozen different updates related to AD LDS on Windows 7 SP1.  However, after careful analysis, only half of them have components not replaced by other updates.  These unnecessary updates related to AD LDS are: KB2898997, KB2922852, KB3042816, KB3160352 , KB3184471, and KB3198591.  The required updates are listed in the table below.

> After installing the first AD LDS Update (KB975541), an update may appear as available in Windows Update (KB2853587).  However, this update is not required and is replaced with KB3012660.  Once KB3012660 is installed, KB2853587 will no longer appear in Windows Update. 

> After installing the first AD LDS Update (KB975541), another update may appear as available in Windows Update (KB3184471).  However, this update is not required and is replaced with the latest ESU Windows 7 Cumulative Update.  Once that is installed, KB3184471 will no longer appear in Windows Update. 

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB975541  | AD LDS Feature                               | Active Directory Lightweight Directory Services (AD LDS) provides directory services for directory-enabled applications. | [Windows6.1-KB975541-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/01_Windows6.1-KB975541-x64.msu) |
| KB2462137 | AD MMC & ADAC Country Update                 | The Active Directory Users and Computers MMC snap-in and Active Directory Administrative Center display Serbia and Montenegro as one country instead of as two countries in Windows 7 SP1. | [Windows6.1-KB2462137-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/02_Windows6.1-KB2462137-v2-x64.msu) |
| KB2539513 | Repadmin Indefinate Query                    | The repadmin command keeps running when you try to look up the users who have their passwords stored on the RODC. | [Windows6.1-KB2539513-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/03_Windows6.1-KB2539513-x64.msu) |
| KB2589154 | AD MMC RODC Update                           | Active Directory Users and Computers MMC snap-in crashes when you try to remove an RODC in Windows 7 SP1. | [Windows6.1-KB2589154-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/04_Windows6.1-KB2589154-x64.msu) |
| KB2647644 | AD Certificate Use Issuer Update             | You cannot clear the "Use Issuer for alternate security identity" check box in Windows 7 SP1. | [Windows6.1-KB2647644-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/05_Windows6.1-KB2647644-v2-x64.msu) |
| KB3012660 | Unable to install Security Update KB2853587  | "The update is not applicable to your computer" error when you install update 2853587 in Windows 7 SP1 with AD LDS. | [Windows6.1-KB3012660-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/03_Feature_AD_LDS/06_Windows6.1-KB3012660-x64.msu) |

<br>

### Installing the Convenience Rollup (SP2) and running the System Update Readiness Tool

There are two large updates that can be applied next.  The first is the Windows 7 Convenience Rollup, which is also considered SP2 for Windows 7 and includes a collection of hotfixes and updates.  The second update is the System Update Readiness Tool.  This update will not show as installed, so this is included to be executed once (verifying SP2 installation integrity).

> After installing Service Pack 2 (KB3125574), an update may appear as available in Windows Update (KB4539601).  However, this update is not required and is replaced with the latest ESU Windows 7 Cumulative Update.  Once that is installed, KB4539601 will no longer appear in Windows Update.  

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB3125574 | Service Pack 2                               | This rollup package includes most updates that were released after the release of SP1 for Windows 7, through April 2016, intended to make it easy to integrate these fixes. | Windows6.1-KB3125574-v4-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.004) <br> [Part 5](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/01_Windows6.1-KB3125574-v4-x64.zip.005) |
| KB947821  | System Update Readiness Tool                 | This tool fixes inconsistencies found in the Windows servicing store which may prevent the successful installation of future updates, service packs, and software. | Windows6.1-KB947821-v34-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.004) <br> [Part 5](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.005) <br> [Part 6](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/04_SP2/02_Windows6.1-KB947821-v34-x64.zip.006) |

<br>

### Non-ESU SP2 Hotfixes

There are 6 hotfixes available to update components after Service Pack 2 has been installed.  These do not require an ESU license to install.

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB2818604 | AMD Microcode Update                         | A microcode update is available for Windows 7-based computers that use AMD processors. | [Windows6.1-KB2818604-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/01_Windows6.1-KB2818604-x64.msu) |
| KB3046480 | .NET Framework 1.1 Migration Check           | This update enables the system to determine whether to migrate the Microsoft .NET Framework 1.1 to a later version of Windows when you upgrade from Windows 7 to a later version of Windows. This determination is based on the usage of the .NET Framework 1.1. | [Windows6.1-KB3046480-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/02_Windows6.1-KB3046480-x64.msu) |
| KB3064209 | Intel Microcode Update                       | June 2015 Intel CPU microcode update for Windows. | [Windows6.1-KB3064209-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/03_Windows6.1-KB3064209-x64.msu) |
| KB3161102 | Windows Journal Removal                       | The file format that is used by Windows Journal (Journal Note File, or JNT) has been demonstrated to be susceptible to many security exploits. Therefore, Windows Journal will be removed from all versions of Microsoft Windows. | [Windows6.1-KB3161102-v2-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/04_Windows6.1-KB3161102-v2-x64.msu) |
| KB4016754 | Media Transfer Protocol Driver Update         | MTP driver update causes USB connected phone or portable device issue.  Note: This update will most likely not be applicable. | [Windows6.1-KB4016754-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/05_Windows6.1-KB4016754-x64.msu) |
| KB4072650 | Hyper-V Integration Components Update         | This update installs the latest integrated components for Windows 7 Guest Virtual Machines (VMs) that are running on a Windows 10-based or Windows Server 2016-based host, or a Windows Server 2012 R2-based host. | [Windows6.1-KB4072650-x64.cab](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/05_Non_ESU_Hotfixes/bin/06_Windows6.1-KB4072650-x64.cab) |

<br>

### ESU Updates

This section describes the latest ESU updates available for Windows 7.  All of these updates are cumulative containing fixes from all previous versions of the updates.  An ESU license is required to install these updates, and only the latest one needs to be installed.

| KB Number | Name                                         | Description | Download |
|:---------:|:--------------------------------------------:|-------------|:--------:|
| KB4562030 | June 2020 Servicing Stack Update             | This update makes quality improvements to the servicing stack, which is the component that installs Windows updates. Servicing stack updates (SSU) makes sure that you have a robust and reliable servicing stack so that your devices can receive and install Microsoft updates. | [Windows6.1-KB4562030-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/01_Windows6.1-KB4562030-x64.msu)
| KB4552940 | May 2020 .NET Framework 3.5.1 Update         | Security and Quality Rollup for .NET Framework 3.5.1 for Windows 7 SP1. | [Windows6.1-KB4552940-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/02_Windows6.1-KB4552940-x64.msu)
| KB4538483 | May 2020 ESU Preparation Package             | This update provides the complete set of licensing changes to enable installation of the ESU MAK add-on key, which is one of the steps to prepare for installation of Extended Security Updates. | [Windows6.1-KB4538483-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/03_Windows6.1-KB4538483-x64.msu)
| KB4561643 | June 2020 Windows 7 Cumulative Update        | Security and Quality Rollup for Windows 7 SP1. | Windows6.1-KB4561643-x64.msu <br> [Part 1](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/04_Windows6.1-KB4561643-x64.zip.001) <br> [Part 2](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/04_Windows6.1-KB4561643-x64.zip.002) <br> [Part 3](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/04_Windows6.1-KB4561643-x64.zip.003) <br> [Part 4](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/06_ESU_Updates/04_Windows6.1-KB4561643-x64.zip.004) |
| KB4552921 | May 2020 .NET Framework 4.8 Update           | Security and Quality Rollup for .NET Framework 4.8 for Windows 7 SP1. | [ndp48-KB4552921-x64.exe](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/07_ESU_.NET_4.8/01_ndp48-KB4552921-x64.exe)

<br>

### Root Certificate Updates

Finally, the latest Microsoft Root Certificates need to be installed into the Local Computer Trusted Root Authority Certificate Store.  A batch file to automatically install all certificates and revocation lists can be found here: [Import.cmd](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Import.cmd)

| Date       | Type            | Download |
|:----------:|:---------------:|:--------:|
| 2018-08-02 | Certificate     | [MicRooCerAut2011_2011_03_22.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/MicRooCerAut2011_2011_03_22.crt)
| 2018-08-02 | Certificate     | [Microsoft ECC Product Root Certificate Authority 2018.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Product%20Root%20Certificate%20Authority%202018.crt)
| 2018-08-02 | Certificate     | [Microsoft ECC TS Root Certificate Authority 2018.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20TS%20Root%20Certificate%20Authority%202018.crt)
| 2018-08-02 | Certificate     | [Microsoft Time Stamp Root Certificate Authority 2014.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20Time%20Stamp%20Root%20Certificate%20Authority%202014.crt)
| 2020-01-22 | Certificate     | [Microsoft ECC Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt)
| 2020-01-22 | Certificate     | [Microsoft EV ECC Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20ECC%20Root%20Certificate%20Authority%202017.crt)
| 2020-01-22 | Certificate     | [Microsoft RSA Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt)
| 2020-01-22 | Certificate     | [Microsoft EV RSA Root Certificate Authority 2017.crt](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20RSA%20Root%20Certificate%20Authority%202017.crt)
| 2020-03-29 | Revocation List | [Microsoft ECC Product Root Certificate Authority 2018.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Product%20Root%20Certificate%20Authority%202018.crl)
| 2020-03-29 | Revocation List | [Microsoft ECC TS Root Certificate Authority 2018.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20TS%20Root%20Certificate%20Authority%202018.crl)
| 2020-04-08 | Revocation List | [Microsoft ECC Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crl)
| 2020-04-08 | Revocation List | [Microsoft EV ECC Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20ECC%20Root%20Certificate%20Authority%202017.crl)
| 2020-04-08 | Revocation List | [Microsoft RSA Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crl)
| 2020-04-08 | Revocation List | [Microsoft EV RSA Root Certificate Authority 2017.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20EV%20RSA%20Root%20Certificate%20Authority%202017.crl)
| 2020-06-05 | Revocation List | [MicRooCerAut_2010-06-23.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/MicRooCerAut_2010-06-23.crl)
| 2020-06-06 | Revocation List | [Microsoft Time Stamp Root Certificate Authority 2014.crl](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/08_Certs/Microsoft%20Time%20Stamp%20Root%20Certificate%20Authority%202014.crl)

<br>

### Conclusion

Once these updates are installed on top of an up-to-date Windows 7 SP1 installation, the OS has been completely updated with hotfixes and optional features.  All of these updates can be found on this Github repository: [Windows 7 Patching](https://github.com/HackAndPwn/Windows-7-Patching)

The goal is to keep this list updated as changes are introduced.  Please reach out to me via [Twitter](https://twitter.com/HackAndPwn) or [Github](https://github.com/HackAndPwn) if there is an update that is missing, if there is an update in this list that you feel may not be needed, or if there are any other questions or feedback.

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