<style>
  .centered {
    text-align: center;
  }
</style>

<h1 class="centered" >Day 4 - Windows Boot Process</h1>

Rootkit takes control after boot

Bootkit takes control prior to boot

###  1. UEFI Boot Manager
bootmgfw.efi - Windows Boot Manager

### bcdedit
Detect bios or uefi
```CMD
bcdedit | findstr /i winload
```
***winload.exe*** = BIOS, ***winload.efi*** = UEFI

### 2. System Initialization
session 0 = kernel

session 1 = user

winload.exe loads the kernel

winresume.exe reads data from *hiberfile.sys*

### 3. Initializing Kernel
ntoskrnl.exe
- loads registry
- loads drivers
- starts *'C:\pagefile.sys'*
- loads hal.dll
  - provides abstraction between hareware interfaces and *ntoskrnl.exe*

Once the kernel is done loading its spawns System, System then launches ***smss.exe*** and ***csrss.exe***

### 4. Starting Subsystems
smss.exe
- loads environment variables
- populates pagefile
- starts kernel and user mode subsystems
- starts csrss.exe
  - manages processes and thread for each user subsystem

