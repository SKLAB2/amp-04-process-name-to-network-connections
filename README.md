[![Gitter chat](https://img.shields.io/badge/gitter-join%20chat-brightgreen.svg)](https://gitter.im/CiscoSecurity/AMP-for-Endpoints "Gitter chat")

### AMP for Endpoints Process Name to Network Connections:

Takes a process name as a command line argument and searches the environment for computers that have seen a seen a process or file with that name. It then fetches the trajectory for those computers and parses it to collect the SHA256s for the associated process. The the trajectory is parsed on more time looking at for network connections generated by the relevant SHA256s.

NOTE: This script will process hits from a maximum of 500 endpoints (there is no pagination). If you search for something and it hits on more than 500 endpoints you will not get a complete view of the environment

### Before using you must update the following:
The authentictaion parameters are set in the ```api.cfg``` :
- client_id 
- api_key

### Usage:
```
python process_name_to_network_connections.py powershell.exe
```

### Example script output:

This script has multiple outputs:
* Prints connection information to the console
* Writes a CSV containing connection the IPs, ports, direction, hostname, and GUID
* Writes a log containing basic information about progress
```
Computers Found: 5
Processing: Demo_AMP_Exploit_Prevention_Audit - 13de840a-3577-41b3-8930-1917ca87ceda
  TCP 172.16.175.136:49349 -> 52.148.86.91:7777
  TCP 172.16.175.136:49347 -> 52.148.86.91:7777
  TCP 172.16.175.136:49346 -> 52.148.86.91:7777
  TCP 172.16.175.136:49340 -> 52.148.86.91:7777
  TCP 172.16.175.136:49338 -> 52.148.86.91:7777
  TCP 172.16.175.136:49336 -> 52.148.86.91:7777
  TCP 172.16.175.136:49336 -> 52.148.86.91:7777
Processing: Demo_AMP_Intel - 14dcfce3-9663-434d-9beb-c8836de035ce
  TCP 192.168.68.138:49311 -> 50.225.30.41:80
  TCP 192.168.68.138:49311 -> 50.225.30.41:80
Processing: Demo_AMP - 43ea5bb6-a4ec-48fa-876c-59cc304fda17
  TCP 172.16.175.143:49180 -> 52.168.18.255:8080
  TCP 172.16.175.143:49180 -> 52.168.18.255:8080
Processing: Demo_AMP_MAP_FriedEx - 93252a58-6d27-4687-b5a5-4e32e54cc166
  No communication observed
Processing: Demo_Command_Line_Arguments_Meterpreter - d2721a44-3795-4138-a73a-f36e6d8b0201
  No communication observed
Computers with powershell.exe: 5
Unique SHA256s for powershell.exe: 4
IPs powershell.exe has been observed communicating with: 38
```
