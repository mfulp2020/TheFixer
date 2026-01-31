---
title: "Windows Update Error 0x80070002: Fixed (2026)"
date: 2026-01-31T14:35:00Z
draft: false
tags: ["windows", "microsoft", "error 0x80070002"]
description: "Windows Update failing with 0x80070002? Here is how to delete corrupted update files and force the install."
---

# Fixing Windows Update Error 0x80070002

The error **0x80070002** translates to "The system cannot find the file specified." Essentially, Windows Update downloaded a file, but it got corrupted or lost before it could install it.

## The Nuclear Fix: Delete SoftwareDistribution
This is the most effective fix. We will stop the update service, delete the old files, and force a fresh download.

### Step 1: Stop Services
1.  Open **Command Prompt** (Run as Admin).
2.  Type: `net stop wuauserv` and hit Enter.
3.  Type: `net stop bits` and hit Enter.

### Step 2: Delete Files
1.  Press `Win + R` and paste: `C:\Windows\SoftwareDistribution`.
2.  Open the **DataStore** folder and delete everything.
3.  Open the **Download** folder and delete everything.

### Step 3: Restart Services
1.  Go back to Command Prompt.
2.  Type: `net start wuauserv`.
3.  Type: `net start bits`.

### Step 4: Update
Go to Settings -> Windows Update and click **Check for Updates**. It will take longer this time (as it re-downloads everything), but it should work!

## Alternative: Time Sync
Believe it or not, if your Date/Time is wrong, Windows Update fails. Right-click your clock -> **Adjust Date/Time** -> **Sync Now**.
