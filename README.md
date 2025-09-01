# App Protection Policies (Outlook + OneDrive) — Microsoft Intune + Entra ID

**Platform note:** This lab was performed on iOS. The same concepts apply to Android and other mobile platforms.

---

## Overview

This project demonstrates how **Microsoft Intune App Protection Policies (MAM)** can enforce **Data Loss Prevention (DLP)** on mobile apps, even in a **BYOD (Bring Your Own Device)** scenario without full device enrollment.  

- Targeted corporate apps: **Microsoft Outlook** and **OneDrive**  
- Enforced DLP restrictions: **PIN requirement, encryption, copy/paste restrictions, save/download restrictions, and screenshot blocking**  
- Confirmed policies applied dynamically to a previously enrolled iOS test device  

---

## What I built

- **App Protection Policy (iOS)**: Targeted Outlook + OneDrive, scoped to my iOS test user  
- **DLP settings enforced**:  
  - Blocked copy/paste into unmanaged apps  
  - Blocked saving files to unmanaged locations  
  - Blocked screenshots inside managed apps  
  - Required app-level PIN for access  
  - Required encryption of corporate data at rest  
- **Validated results**: Demonstrated each protection in action on my iPhone  

---

## Step-by-step

### 1) Confirm User & Device Scope
I reused my existing **iOS test user** and enrolled iPhone from the previous MDM lab. This user was already licensed for Intune and placed in a dedicated iOS user group for policy scoping.

<p align="center">
User & Device Scope (Existing iOS Test User + Device)<br/>
<img src="https://i.imgur.com/Mzb0klY.png" width="800" style="height:auto;" alt="iOS test user and device listed in Entra ID / Intune"/>
<br /><br />
</p>

___

### 2) Create iOS App Protection Policy
In Intune, I created an **App Protection policy** for Outlook and OneDrive on iOS.  
This policy enforces DLP by encrypting organizational data, blocking copy/paste into unmanaged apps, preventing local saves, and requiring an app-level PIN.  

<p align="center">
App Protection Policy — Review<br/>
<img src="https://i.imgur.com/9VqvtJf.png" width="800" style="height:auto;" alt="Intune app protection policy review screen for Outlook and OneDrive"/>
<br /><br />
</p>

___

### 3) Apply Policy on iOS Device
On my iPhone, I installed the Intune **management profile** for FALSOTECH through the Company Portal app, confirming the device was successfully enrolled.  
Immediately after sign-in, the App Protection policy was applied. Outlook displayed a message confirming organizational data was now protected under Intune DLP controls.

<p align="center">
Device Enrolled + DLP Enforcement<br/>
<img src="https://i.imgur.com/QEHFzAD.png" width="800" style="height:auto;" alt="iOS device enrolled and Outlook showing organization data protection applied"/>
<br /><br />
</p>

___

### 4) Validate App Protection & DLP Controls
I tested the applied policy on my iPhone to confirm that DLP settings were enforced:

- **PIN requirement**: Outlook forced me to set and enter a PIN before accessing corporate data.  
- **Copy/Paste restriction**: Copying text from Outlook into Notes or other unmanaged apps was blocked.  
- **Save/Open restrictions**: OneDrive blocked downloading or saving files into unmanaged locations.  
- **Screenshot restriction**: Attempting to take a screenshot inside Outlook was blocked by the policy.  

These behaviors confirm that Intune App Protection successfully secured organizational data on a BYOD device.

<p align="center">
App Protection Enforced (PIN, Copy/Paste, Save, Screenshot Controls)<br/>
<img src="https://i.imgur.com/1uqm9Fw.png" width="800" style="height:auto;" alt="PIN requirement, copy/paste blocked, OneDrive save restricted, screenshot blocked"/>
<br /><br />
</p>

<p align="center">

<img src="https://i.imgur.com/H9RqNxF.png" width="800" style="height:auto;" alt="PIN requirement, copy/paste blocked, OneDrive save restricted, screenshot blocked"/>
<br /><br />
</p>

---

## What I learned

- How to build and assign **App Protection (MAM) policies** in Intune for iOS.  
- How **DLP controls** work at the app level: encryption, PIN, copy/paste restrictions, save restrictions, and screenshot blocking.  
- That these protections can apply **without full device enrollment** — enabling secure BYOD scenarios.  
- How to test DLP effectiveness directly on mobile apps (Outlook + OneDrive).  
- How mobile app governance ties into a broader **Zero Trust strategy** by ensuring corporate data remains in managed apps, even on personal devices.  
