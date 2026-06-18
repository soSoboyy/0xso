---
{"dg-publish":true,"permalink":"/htb/cjca/widows/sec1-windows/","dg-note-properties":{}}
---

#windows
###### Windows primary command line interfaces: `PowerShell` and `Command Prompt`
==One key difference is that you can run Command Prompt commands from a PowerShell console, but to run PowerShell commands from a Command Prompt. ==

*Command Prompt is a much more static way of interacting with the operating system, while PowerShell is a powerful scripting language that can be used for a wide variety of tasks and to create simple and very complex scripts.*

#windowscommand
Commands (*cmdlet*) to retrieve version + build number:
```powershell
PS C:\htb> Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber

Version    BuildNumber
-------    -----------
10.0.19041 19041
```
This cmdlet can be used to get instances of WMI classes or information about available WMI classes. There are a variety of ways to find the version and build number of our system. We can easily obtain this information using the `win32_OperatingSystem` class, which shows that we are on a Windows 10 host, build number 19041.

Other classes to use with *WmiObject* :
- `Get-WmiObject -Class win32_OperatingSystem` --> OS listing
- `Get-WmiObject -Class win32_Process` --> Process listing
- `Get-WmiObject -Class win32_Service` --> List of services 
- `Get-WmiObject -Class win32_BIOS` --> Basic I/O information

---
#remoteaccesswindows
On any given day, a technical professional could be accessing multiple machines locally and remotely. With that, let's discuss the concept of remote access.
*Remote Access is accessing a computer over a network. Local access to a computer is needed before one can access another computer remotely.*
Some of the most common remote access technologies include but aren't limited to:
- Virtual Private Networks (VPN)
- Secure Shell (SSH)
- File Transfer Protocol (FTP)
- Virtual Network Computing (VNC)
- Windows Remote Management (or PowerShell Remoting) (WinRM)
- Remote Desktop Protocol (RDP)

#### RDP:
RDP uses a client/server architecture where a client-side application is used to specify a computer's target IP address or hostname over a network where RDP access is enabled.

- RDP listens to port *3389* by default
- We can use RDP to connect to a Windows target from an attack host running Linux or Windows.
- remote access must already be [allowed] on the target Windows system.
- RDP creates Remote desktop files under the .rdp format

#attackpath
**Offensive PATH:**
From a Linux-based attack host we can use a tool called [xfreerdp](https://linux.die.net/man/1/xfreerdp) to remotely access Windows targets.
- Use command `xfreerdp /v:<ipaddress> /u:<username> /p:<password>` from Linux
