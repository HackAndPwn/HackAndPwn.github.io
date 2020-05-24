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

| KB Number | Description                | Notes                                                      | Download |
|:---------:|----------------------------|------------------------------------------------------------|----------|
| KB4528069 |Windows 7 SP1 Verification  | Update is no longer available through Microsoft's website. | [KB4528069](https://github.com/HackAndPwn/Windows-7-Patching/blob/master/01_Enable_ESU/01_Windows6.1-KB4528069-x64.msu)

<br>

### Installing Optional Features

The next section of updates enables all optional features not available through Windows Update.  The notable exception is the AD LDS feature, as that will be discussed in more detail in the next section.

| KB Number | Description                                  | Notes      | Download |
|:---------:|----------------------------------------------|------------|------------|
| KB917607  | Windows Help 32-bit Compatability Update     |            | [KB917607](https://github.com/HackAndPwn/Windows-7-Patching/blob/master/02_Features/01_Windows6.1-KB917607-x64.msu)
| KB943790  | File Management API extensions for BitLocker | Install this update to extend the File Management APIs to not only enable the discovery and restoration of deleted files from volumes that are not encrypted but also enable the recovery of files from Bitlocker encrypted volumes.           | [KB943790](https://github.com/HackAndPwn/Windows-7-Patching/blob/master/02_Features/02_Windows6.1-KB943790-x64.msu)
| KB958559  | d                          | d          | link |
| KB958830  | d                          | d          | link |
| KB969168  | d                          | d          | link |
| KB970985  | d                          | d          | link |
| KB974150  | d                          | d          | link |
| KB974405  | d                          | d          | link |
| KB974674  | d                          | d          | link |
| KB2666914 | d                          | d          | link |
| KB2790621 | d                          | d          | link |
| KB2891638 | d                          | d          | link |
| KB2959936 | d                          | d          | link |
| KB2990999 | d                          | d          | link |
| KB3191566 | d                          | d          | link |
