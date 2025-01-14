<h1 style="text-align: center">Windows Registry</h1>

Servers as the backbone of configuration for the system.

Separeted into Keys, Subkeys, Values, and Hives

## 1. Hives
- HKLM
- HKU
- HKCU
- HKCC
- HKCR

### HKLM - Configuration for the entire computer
- HARDWARE
- SAM
- Security
- System

### HKU - User profile settings
- Environment Settigns
- Shortcuts
- File associations
- SID
  - 500 - Administrator
  - 501 - Guest
  - 1000+ - User Accounts

### HKCU - Current logged in user
- A dynamic link of the key in HKU\SID

### HKCC - Current config
- Dynamic link to harware subkey - **HLKM\SYSTEM\CurrentControlSet\Harware Profiles\Current**

### HKCR - Classes root
- Dynamic link to classes subkey - **HKLM\Software\Classes**
- Contains extension associations (intended for compatibility with the 16-bit registry)


## 2. Manipulation
- regedit.exe - GUI app
- reg.exe - Commandline
  - /?
  - query /?
- Powershell
  - Get-ChildItem
  - Get-ItemProperty
  - Get-Item

- sethc.exe

- net use * http://live.sysinternals.com

## 3. Pwershell Drives
- Creates a way for PowerShell to navigate the registry the same way you could navigate the file system
- Get-PSDrive - find current drives

## 4. Important Registry Locations
- Just use google bro
- HKLM\Software\Microsoft\Windows\CurrentVersion\Run
- HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKLM\<sid>\Software\Microsoft\Windows\CurrentVersion\Run
- HKLM\<sid>\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKLM\SYSTEM\CurrentControlSet\Services

### Critical Locations
- HKLM\BCD00000000 - for replacement of old boot.ini
- HKLM\SAM\SAM - using sysinternals to make a regedit instance with system permissions
- HKU\<sid>\Software\Policies\Microsoft\Windows\System\Scripts - group policy modification
