---
layout: post
title: Windows 7 ESU Patching
date: 2020-05-23 00:00:00
tags: draft
---

With the May 2020 Windows Updates, I went on a mission to determine exactly what the minimum set of updates are required to enable all options within Windows 7 (and all optional hotfixes).  After extensive testing on both VMs and a laptop, I concluded that 35 updates not offered through Windows Update would reach this objective.  The following sections describe the updates required and provide links to each.

Note 1: The base test image used for this testing was 64-bit Windows 7 Ultimate SP1.  Microsoft Update was enabled, and all updates offered through Windows Update were installed.  All links and details within this post were only validated on 64-bit, although 32-bit should have a similar set of results.

Note2: I highly recommend both the [KUC Update Checker](https://windows-update-checker.com/) and [WSUS Offline Update](https://www.wsusoffline.net/) utlities.  I used both during this investigation in order to get to the minimum required set.  

<br>

### Enabling ESU

This first section only contains a single update required for ESU updates.  A detailed analysis on this update can be found on my other blog post [Windows 7 ESU Analysis](https://hackandpwn.com/windows-7-esu-analysis/).

| KB Number | Name                                         | Description | Download |
|:---------:|----------------------------------------------|-------------|----------|
| KB4528069 |Windows 7 SP1 Verification                    | This optional nonsecurity update will help you verify that your eligible Windows 7 Service Pack 1 (SP1) and Server 2008 R2 SP1 devices can continue to get Extended Security Updates (ESUs) after the end of support date of January 14, 2020. | [Windows6.1-KB4528069-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/01_Enable_ESU/01_Windows6.1-KB4528069-x64.msu)

<br>

### Installing Optional Features

The next section of updates enables all optional features not available through Windows Update.  The notable exception is the AD LDS feature, as that will be discussed in more detail in the next section.

| KB Number | Name                                         | Description | Download |
|:---------:|----------------------------------------------|-------------|----------|
| KB917607  | Windows Help 32-bit Compatability Update     | WinHlp32.exe is required to display 32-bit Help files that have the ".hlp" file name extension. To view .hlp files on Windows 7, you need to install this application. | [Windows6.1-KB917607-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/01_Windows6.1-KB917607-x64.msu) |
| KB943790  | File Management API extensions for BitLocker | Install this update to extend the File Management APIs to not only enable the discovery and restoration of deleted files from volumes that are not encrypted but also enable the recovery of files from Bitlocker encrypted volumes. | [Windows6.1-KB943790-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/02_Windows6.1-KB943790-x64.msu) |
| KB958559  | Windows Virtual PC                           | Windows Virtual PC is the latest Microsoft virtualization technology. You can use it to run more than one operating system at the same time on one computer, and to run many productivity applications on a virtual Windows environment, with a single click, directly from a computer running Windows 7. | [Windows6.1-KB958559-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/03_Windows6.1-KB958559-x64.msu) |
| KB958830  | Remote Server Administration Tools           | Remote Server Administration Tools for Windows® 7 with SP1 enables IT administrators to manage roles and features that are installed on computers that are running Windows Server® 2008 R2, Windows Server® 2008, or Windows Server® 2003, from a remote computer that is running Windows 7 or Windows 7 with SP1. | [Windows6.1-KB958830-x64.zip.001](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.001)  [Windows6.1-KB958830-x64.zip.002](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.002)  [Windows6.1-KB958830-x64.zip.003](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/04_Windows6.1-KB958830-x64.zip.003) |
| KB969168  | Microsoft Agent                              | Microsoft Agent is a set of software services that supports interactive characters within the Microsoft Windows display. Some examples of the Microsoft Agent characters are the Office Assistants.  Microsoft Agent is not included in Windows 7, and it will not be included in any later versions of the Windows operating system. However, you can download Microsoft Agent as a hotfix for your Windows 7 computer. | [Windows6.1-KB969168-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/05_Windows6.1-KB969168-x64.msu) |
| KB970985  | Windows Activation Technologies              | Windows Activation Technologies helps you confirm that the copy of Windows 7 that is running on your computer is genuine. Additionally, Windows Activation Technologies helps protect against the risks of counterfeit software. Windows Activation Technologies in Windows 7 consists of activation and validation components that contain anti-piracy features. | [Windows6.1-KB970985-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/06_Windows6.1-KB970985-x64.msu) |
| KB974150  | Windows NTBackup Utility                    | NTBackup is the legacy Windows backup application included in previous versions of Windows. Files can be backed up to tape, ZIP drives, floppy disks, and hard drives using a proprietary backup format (BKF). It also features integration with Task Scheduler and has several command line switches for scheduled automated backups. | [Windows6.1-KB974150-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/07_Windows6.1-KB974150-x64.msu) |
| KB974405  | Windows Identity Foundation                  | The Windows Identity Foundation helps simplify user access for developers by externalizing user access from applications via claims and reducing development effort with pre-built security logic and integrated .NET tools. | [Windows6.1-KB974405-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/08_Windows6.1-KB974405-x64.msu) |
| KB974674  | Windows NTBackup Restore Utility             | The Windows NTBackup Restore Utility for Windows 7 and for Windows Server 2008 R2 restores backups that are made on Windows XP and on Windows Server 2003 to computers that are running Windows 7 and Windows Server 2008 R2. | [Windows6.1-KB974674-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/09_Windows6.1-KB974674-x64.msu) |
| KB2666914 | DirectAccess Connectivity Assistant 2.0      | The Microsoft DirectAccess Connectivity Assistant (DCA) version 2.0 is used by DirectAccess client computers running Windows 7, to connect to Windows Server 2012 servers running DirectAccess. | [Windows6.1-KB2666914-x64.msu](https://github.com/HackAndPwn/Windows-7-Patching/raw/master/02_Features/10_Windows6.1-KB2666914-x64.msu) |
| KB2790621 | d                          | d          | link |
| KB2891638 | d                          | d          | link |
| KB2959936 | d                          | d          | link |
| KB2990999 | d                          | d          | link |
| KB3191566 | d                          | d          | link |
















