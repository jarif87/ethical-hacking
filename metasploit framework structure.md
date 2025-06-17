# Metasploit Framework Navigation Commands

## Overview
Commands for navigating the Metasploit Framework's `modules` directory on Kali Linux to explore its structure for cybersecurity tasks.

## Commands
### Change to Metasploit Directory
```
cd /usr/share/metasploit-framework
```
### List Directory Contents


8 **Purpose: Display files and folders in the current directory. Executed in:**
- /usr/share/metasploit-framework (shows modules, msfconsole, etc.)

- /usr/share/metasploit-framework/modules (shows auxiliary, exploits, etc.)

- /usr/share/metasploit-framework/modules/exploits (shows windows, linux, etc.)

- /usr/share/metasploit-framework/modules/auxiliary (shows scanner, spoof, etc.)

- /usr/share/metasploit-framework/modules/auxiliary/spoof (shows arp, dns, etc.)

- /usr/share/metasploit-framework/modules/post (shows windows, linux, etc.)

- /usr/share/metasploit-framework/modules/payloads (shows stagers, singles, etc.)

- /usr/share/metasploit-framework/modules/payloads/stagers (shows windows, android, etc.)

- /usr/share/metasploit-framework/modules/payloads/stagers/windows (shows reverse_tcp.rb, etc.)

- /usr/share/metasploit-framework/modules/encoders (shows x86, cmd, etc.)

- /usr/share/metasploit-framework/modules/evasion (shows windows)

- /usr/share/metasploit-framework/modules/evasion/windows (shows applocker_evasion_msbuild.rb, etc.)

### Navigate to Modules

```
cd modules
```
### Typo Attempt
```
cd modulues
```
### Navigate to Exploits
```
cd exploits
```
### Move Up Directory

```
cd ..
```

* **Purpose: Navigate up one directory level. Used to return from:**
- exploits to modules

- auxiliary to modules

- spoof to auxiliary

- post to modules

- payloads to modules

- stagers to payloads

- windows to stagers

- evasion to modules

- windows to evasion

### Navigate to Auxiliary

```
cd auxiliary
```
### Navigate to Spoof

```
cd spoof
```
### Navigate to Post
```
cd post
```
### Navigate to Payloads
```
cd payloads
```

### Navigate to Stagers
```
cd stagers
```

### Navigate to Windows Stagers

```
cd windows

Purpose: Enter the windows directory for Windows-specific stager payloads.
```
### Navigate to Encoders
```
cd encoders

Purpose: Enter the encoders directory for payload encoding modules.
```
### Navigate to Evasion

```
cd evasion

Purpose: Enter the evasion directory for modules that bypass security mechanisms.
```

### Navigate to Windows Evasion

```
cd windows

Purpose: Enter the windows directory for Windows-specific evasion modules.
```
