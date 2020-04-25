---
layout: post
title: Windows 7 ESU Analysis
date: 2020-04-25 00:00:00
tags: draft
---

The Windows 7 security update window closed to consumers in January of 2020.  However, due to the overwhelming popularity of the Operating System, Microsoft began offering Extended Security Updates (ESU) for the Operating System.  The original update behind enabling these additional updates is [KB4528069](https://support.microsoft.com/en-us/help/4528069).  This post dissects this update in order to understand how ESUs works.

> Dislaimer:  You must obtain an ESU license in order to apply ESU updates.  Details on obtaining an ESU update can be found [here](https://support.microsoft.com/en-us/help/4497181/lifecycle-faq-extended-security-updates).

### Preparing The Computer

To start, I deployed a brand new VM of 64-Bit Windows 7 SP1, resulting in the build from November 19th, 2010 (101119).

<img src="/assets/2020-04-25-windows-7-esu-analysis/1.jpg">

Next, I started checking for updates.  This resulted in 181 updates on the first scan.

<img src="/assets/2020-04-25-windows-7-esu-analysis/2.jpg">

After many update cycles and reboots, almost 10 years of updates have been applied.  Some of the updates wouldn't install without manually installing KB4474419 first (the SHA2 update).

Finally, no more updates are available, bringing the build to January 2nd, 2020 (200102).

<img src="/assets/2020-04-25-windows-7-esu-analysis/3.jpg">

### Installing KB4528069

sdf