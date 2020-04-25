---
layout: post
title: Windows 7 ESU Analysis
date: 2020-04-25 00:00:00
tags: draft
---

The Windows 7 security update window closed to consumers in January of 2020.  However, due to the overwhelming popularity of the Operating System, Microsoft began offering Extended Security Updates (ESU) for the Operating System.  The driving update behind enabling these additional updates is KB4528069.  This post dissects this update in order to understand how it works.

> Dislaimer:  You must obtain an ESU license in order to apply ESU updates.  Details can be found here:

To start, I deployed a brand new VM of 64-Bit Windows 7 SP1, resulting in the build from November 19th, 2010 (101119).

<img src="/assets/2020-04-25-windows-7-esu-analysis/1.jpg">

Next, I started checking for updates.  This  resulted in a huge number of updates.