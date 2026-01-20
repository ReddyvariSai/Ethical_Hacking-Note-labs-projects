# MetaSploit

<img width="772" height="742" alt="image" src="https://github.com/user-attachments/assets/bdca412b-71e9-48e7-ba3b-69d204aae10f" />

`Metasploit` (referred to in the sources as "metos plit" or "metasloit") is a comprehensive framework and toolkit designed for penetration testers to discover, exploit, and manage vulnerabilities.

It functions as a collection of reusable offensive code that includes exploits, scanners, post-exploitation modules, and payloads, allowing security professionals to perform assessments without having to write every piece of code from scratch.

According to the sources, the core concepts and components of the framework include:

## Primary Modules and Tools

* `MSFconsole`: This is the main command-line interface used to access the framework's features, load modules, and manage exploits.

* `Exploits`: These are pieces of code or steps that take advantage of a bug or misconfiguration (like a flawed input validation) to run arbitrary commands on a target.

* `Payloads`: The code that runs on the target system after an exploit succeeds. This can range from a simple command shell to an advanced interactive agent like Meterpreter, which provides built-in capabilities for file access and network sniffing.

* `Auxiliary Modules`: These perform support tasks such as scanning, fuzzing, and brute-forcing. Unlike exploits, they are not designed to deliver a payload that grants a remote shell.

* `Post-Exploitation Modules`: Tools used after gaining access to a system to escalate privileges, collect evidence, or maintain persistence.

* `MSFVenom`: A standalone payload generator and encoder used to build malicious files (like .exe or .apk) that connect back to the attacker's machine.

## Key Features for Penetration Testing

* `Database Integration`: Metasploit can use a PostgreSQL database to keep scan results and session data organized. Users can run db_nmap directly within the framework to perform network discovery and automatically save the results.

* `Workspaces`: These allow testers to keep different engagements logically isolated, preventing the mixing of scan results or credentials between different clients.

* `Search Operators`: Testers can filter the thousands of available modules by platform (e.g., Windows, Android, Linux), type, or CVE year to find the specific tool needed for a target.

* `Automation`: The framework provides predictable commands and reusable patterns, which increases the speed of an attack chain and allows testers to focus on strategy rather than manual coding.

## Usage and Persistence

Metasploit is frequently used to test well-known vulnerabilities, such as the Eternal Blue (MS17-010) exploit. It also facilitates persistence, such as using the Registry Editor feature to add malicious entries to a Windows system so that an attacker maintains access even after a reboot.

```
──(root㉿kali)-[/home/kali]
└─# msfconsole 
Metasploit tip: You can use help to view all available commands
                                                  
Call trans opt: received. 2-19-98 13:24:18 REC:Loc

     Trace program: running

           wake up, Neo...
        the matrix has you
      follow the white rabbit.

          knock, knock, Neo.

                        (`.         ,-,
                        ` `.    ,;' /
                         `.  ,'/ .'
                          `. X /.'
                .-;--''--.._` ` (
              .'            /   `
             ,           ` '   Q '
             ,         ,   `._    \
          ,.|         '     `-.;_'
          :  . `  ;    `  ` --,.._;
           ' `    ,   )   .'
              `._ ,  '   /_
                 ; ,''-,;' ``-
                  ``-..__``--`

                             https://metasploit.com


       =[ metasploit v6.4.103-dev                               ]
+ -- --=[ 2,584 exploits - 1,319 auxiliary - 1,697 payloads     ]
+ -- --=[ 434 post - 49 encoders - 14 nops - 9 evasion          ]

Metasploit Documentation: https://docs.metasploit.com/
The Metasploit Framework is a Rapid7 Open Source Project

msf > ls
[*] exec: ls                                                                                                        
                                                                                                                    
'Browse Anonymously'   Downloads   myenv          Public             shell-gpt-env   tgpt                  Videos   
 Desktop               go          Pictures       rakuten_subs.txt   Sublist3r       tor-browser.desktop            
 Documents             Music       profiles.csv   shell_gpt          Templates       venv                           
msf > expoit/unit/ftp                                                                                               
[-] Unknown command: expoit/unit/ftp. Run the help command for more details.                                        
msf > help                                                                                                          
                                                                                                                    
Core Commands                                                                                                       
=============                                                                                                       
                                                                                                                    
    Command           Description                                                                                   
    -------           -----------
    ?                 Help menu
    banner            Display an awesome metasploit banner
    cd                Change the current working directory
    color             Toggle color
    connect           Communicate with a host
    debug             Display information useful for debugging
    exit              Exit the console
    features          Display the list of not yet released features that can be opted in to
    get               Gets the value of a context-specific variable
    getg              Gets the value of a global variable
    grep              Grep the output of another command
    help              Help menu
    history           Show command history
    load              Load a framework plugin
    quit              Exit the console
    repeat            Repeat a list of commands
    route             Route traffic through a session
    save              Saves the active datastores
    sessions          Dump session listings and display information about sessions
    set               Sets a context-specific variable to a value
    setg              Sets a global variable to a value
    sleep             Do nothing for the specified number of seconds
    spool             Write console output into a file as well the screen
    threads           View and manipulate background threads
    tips              Show a list of useful productivity tips
    unload            Unload a framework plugin
    unset             Unsets one or more context-specific variables
    unsetg            Unsets one or more global variables
    version           Show the framework and console library version numbers


Module Commands
===============

    Command           Description
    -------           -----------
    advanced          Displays advanced options for one or more modules
    back              Move back from the current context
    clearm            Clear the module stack
    favorite          Add module(s) to the list of favorite modules
    favorites         Print the list of favorite modules (alias for `show favorites`)
    info              Displays information about one or more modules
    listm             List the module stack
    loadpath          Searches for and loads modules from a path
    options           Displays global options or for one or more modules
    popm              Pops the latest module off the stack and makes it active
    previous          Sets the previously loaded module as the current module
    pushm             Pushes the active or list of modules onto the module stack
    reload_all        Reloads all modules from all defined module paths
    search            Searches module names and descriptions
    show              Displays modules of a given type, or all modules
    use               Interact with a module by name or search term/index


Job Commands
============

    Command           Description
    -------           -----------
    handler           Start a payload handler as job
    jobs              Displays and manages jobs
    kill              Kill a job
    rename_job        Rename a job


Resource Script Commands
========================

    Command           Description
    -------           -----------
    makerc            Save commands entered since start to a file
    resource          Run the commands stored in a file


Database Backend Commands
=========================

    Command           Description
    -------           -----------
    analyze           Analyze database information about a specific address or address range
    certs             List Pkcs12 certificate bundles in the database
    db_connect        Connect to an existing data service
    db_disconnect     Disconnect from the current data service
    db_export         Export a file containing the contents of the database
    db_import         Import a scan result file (filetype will be auto-detected)
    db_nmap           Executes nmap and records the output automatically
    db_rebuild_cache  Rebuilds the database-stored module cache (deprecated)
    db_remove         Remove the saved data service entry
    db_save           Save the current data service connection as the default to reconnect on startup
    db_stats          Show statistics for the database
    db_status         Show the current data service status
    hosts             List all hosts in the database
    klist             List Kerberos tickets in the database
    loot              List all loot in the database
    notes             List all notes in the database
    services          List all services in the database
    vulns             List all vulnerabilities in the database
    workspace         Switch between database workspaces


Credentials Backend Commands
============================

    Command           Description
    -------           -----------
    creds             List all credentials in the database


Developer Commands
==================

    Command           Description
    -------           -----------
    edit              Edit the current module or a file with the preferred editor
    irb               Open an interactive Ruby shell in the current context
    log               Display framework.log paged to the end if possible
    pry               Open the Pry debugger on the current module or Framework
    reload_lib        Reload Ruby library files from specified paths
    time              Time how long it takes to run a particular command


DNS Commands
============

    Command           Description
    -------           -----------
    dns               Manage Metasploit's DNS resolving behaviour

For more info on a specific command, use <command> -h or help <command>.


msfconsole
==========

`msfconsole` is the primary interface to Metasploit Framework. There is quite a
lot that needs go here, please be patient and keep an eye on this space!

Building ranges and lists
-------------------------

Many commands and options that take a list of things can use ranges to avoid
having to manually list each desired thing. All ranges are inclusive.

### Ranges of IDs

Commands that take a list of IDs can use ranges to help. Individual IDs must be
separated by a `,` (no space allowed) and ranges can be expressed with either
`-` or `..`.

### Ranges of IPs

There are several ways to specify ranges of IP addresses that can be mixed
together. The first way is a list of IPs separated by just a ` ` (ASCII space),
with an optional `,`. The next way is two complete IP addresses in the form of
`BEGINNING_ADDRESS-END_ADDRESS` like `127.0.1.44-127.0.2.33`. CIDR
specifications may also be used, however the whole address must be given to
Metasploit like `127.0.0.0/8` and not `127/8`, contrary to the RFC.
Additionally, a netmask can be used in conjunction with a domain name to
dynamically resolve which block to target. All these methods work for both IPv4
and IPv6 addresses. IPv4 addresses can also be specified with special octet
ranges from the [NMAP target
specification](https://nmap.org/book/man-target-specification.html)

### Examples

Terminate the first sessions:

    sessions -k 1

Stop some extra running jobs:

    jobs -k 2-6,7,8,11..15

Check a set of IP addresses:

    check 127.168.0.0/16, 127.0.0-2.1-4,15 127.0.0.255

Target a set of IPv6 hosts:

    set RHOSTS fe80::3990:0000/110, ::1-::f0f0

Target a block from a resolved domain name:

 set RHOSTS www.example.test/24



```



