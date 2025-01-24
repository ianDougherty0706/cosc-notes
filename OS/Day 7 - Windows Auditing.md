# Day 7 - Windows Auditing

*CEBFF5CD-ACE2-4F4F-9178-9926F41749EA* - A list of applications, files, links, and other objects that have been accessed

*F4E57C4B-2036-45F0-A9AB-443BCFE33D9F* - Lists the Shortcut Links used to start programs

### Get Recently Opened Files
- Get-Item "REGISTRY::HKEY_USERS\*\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt" | select -Expand property | ForEach-Object {
    [System.Text.Encoding]::Default.GetString((Get-ItemProperty -Path "REGISTRY::HKEY_USERS\*\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt" -Name $_).$_)

### Browser Artifacts
- %USERPROFILE%\AppData\Local\Google\Chrome\User Data\
