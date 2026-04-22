# Use SpiderFoot

SpiderFoot is an automated OSINT scanner. It is included with Kali. SpiderFoot queries over 1000 open-information sources and presents the results in an easy-to-use GUI. SpiderFoot can also be run from a console. SpiderFoot seeds its scan with one of the following:

----

+ Domain names
+ IP addresses
+ Subnet addresses
+ Autonomous System Numbers (ASN)
+ Email addresses
+ Phone numbers
+ Personal names

SpiderFoot offers the option of choosing scans based on use case, required data, and by SpiderFoot module. The use cases are:

+ All – Get every possible piece of information about the target. This use case can take a very long time to complete.
+ Footprint – Understand the target’s network perimeter, associated identities and other information that is yielded by extensive web crawling and search engine use.
+ Investigate – This is or targets that you suspect of malicious behavior. Footprinting, blacklist lookups, and other sources that report on malicious sites will be returned.
+ Passive – This type of scan is used if it is undesirable for the target to suspect that it is being scanned. This is a form of passive OSINT.



```

┌──(sai㉿kalki)-[~]
└─$ spiderfoot -h
usage: sf.py [-h] [-d] [-l IP:port] [-m mod1,mod2,...] [-M] [-C scanID] [-s TARGET] [-t type1,type2,...]
             [-u {all,footprint,investigate,passive}] [-T] [-o {tab,csv,json}] [-H] [-n] [-r] [-S LENGTH]
             [-D DELIMITER] [-f] [-F type1,type2,...] [-x] [-q] [-V] [-max-threads MAX_THREADS]

SpiderFoot 4.0.0: Open Source Intelligence Automation.

options:
  -h, --help            show this help message and exit
  -d, --debug           Enable debug output.
  -l IP:port            IP and port to listen on.
  -m mod1,mod2,...      Modules to enable.
  -M, --modules         List available modules.
  -C, --correlate scanID
                        Run correlation rules against a scan ID.
  -s TARGET             Target for the scan.
  -t type1,type2,...    Event types to collect (modules selected automatically).
  -u {all,footprint,investigate,passive}
                        Select modules automatically by use case
  -T, --types           List available event types.
  -o {tab,csv,json}     Output format. Tab is default.
  -H                    Don't print field headers, just data.
  -n                    Strip newlines from data.
  -r                    Include the source data field in tab/csv output.
  -S LENGTH             Maximum data length to display. By default, all data is shown.
  -D DELIMITER          Delimiter to use for CSV output. Default is ,.
  -f                    Filter out other event types that weren't requested with -t.
  -F type1,type2,...    Show only a set of event types, comma-separated.
  -x                    STRICT MODE. Will only enable modules that can directly consume your target, and if -t was
                        specified only those events will be consumed by modules. This overrides -t and -m options.
  -q                    Disable logging. This will also hide errors!
  -V, --version         Display the version of SpiderFoot and exit.
  -max-threads MAX_THREADS
                        Max number of modules to run concurrently.


┌──(sai㉿kalki)-[~]
└─$ sudo spiderfoot -l 172.20.40.219:80
2026-04-22 13:08:31,289 [INFO] sf : Starting web server at 172.20.40.219:80 ...
2026-04-22 13:08:31,340 [WARNING] sf :
********************************************************************
Warning: passwd file contains no passwords. Authentication disabled.
Please consider adding authentication to protect this instance!
Refer to https://www.spiderfoot.net/documentation/#security.
********************************************************************


*************************************************************
 Use SpiderFoot by starting your web browser of choice and
 browse to http://172.20.40.219:80/
*************************************************************

```

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/3f2b3b36-d6e0-403c-bf3b-8e5fd6c9ae7c" />

---
<img width="1919" height="1019" alt="image" src="https://github.com/user-attachments/assets/c61a17a2-1900-4b37-8a33-85a69f430f17" />

---
<img width="1699" height="536" alt="image" src="https://github.com/user-attachments/assets/3baee175-a699-404f-bbed-8d1d271ff00b" />

---
<img width="1115" height="610" alt="Screenshot 2026-04-22 132149" src="https://github.com/user-attachments/assets/d1b81802-bda0-46f8-8b68-63fd534cdd8c" />

---
<img width="1144" height="708" alt="image" src="https://github.com/user-attachments/assets/bf050b76-1e13-4aa8-9258-717c58b7a3ea" />

---
<img width="1919" height="1017" alt="image" src="https://github.com/user-attachments/assets/a59d0069-fa46-479c-942d-b9e9a4602de5" />

---
<img width="1330" height="572" alt="image" src="https://github.com/user-attachments/assets/481a3bfe-3583-47fd-bad1-edf5cc31ead0" />

---
<img width="1919" height="879" alt="image" src="https://github.com/user-attachments/assets/ba4e9ec8-ccbe-4946-adeb-db1634492d83" />

---
<img width="1903" height="841" alt="image" src="https://github.com/user-attachments/assets/33b16417-69e7-40a6-93f6-31c9e9cdb24d" />



