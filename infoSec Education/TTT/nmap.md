here is where we will write our cheat sheet for nmap.

for information on the [[Nmap scripting engine]] please follow the link

If you find nothing with normal scans MAKE SURE YOU SCAN UDP JACKASS

## Basic Scans
Basic nmap scan is as follows ^d11596
```
nmap 192.168.255.255
```

Basic UDP scans are also advisable
```
nmap -sU 192.168.255.255
```

and finally do a simple scan on all TCP ports
```
nmap -p- 192.168.255.255
```



## Advanced Scans

For advanced scans I recommend starting with a full scan of UDP just to be safe. It probably wont show much but it's still worth doing on the side
```
nmap -p- -sU 10.10.10.10
```
Better safe that sorry. P.S. The UDP scan can take a while longer so best do it on the side while you continue with your TCP scans.

Now If noise doesn't matter lets go for breadth first scan
```
nmap -A 192.168.255.255
```
feel free to target specific ports with this scan to speed it up

## Additional Info

<span class="red-text">Please note that port scanning is not representative of traditional user activity and could be considered illegal in some jurisdictions. Therefore, it should not be performed outside of laboratory environments without direct, written permission from the target network owner.</span>

Additionally please note that reckless port scanning is very easily detectable by IDS([[Intrusion Detection Systems]]) and therefor is a dead giveaway that you are planning an attack.

Information gathered from the [[Information Gathering#Passive Information Gathering|Passive]] portion of the information gathering process should be used to minimize the number of ports scanned. In addition to scanning the ports in non suspicious ways, this allows us to stay undetected.

Port scanning is a dynamic and cyclical process, the results of one scan dictate the type and scope of the following scan.

Nmap scripts are large in number but luckily have been categorized to simplify their usage, I won't be going over the categories here given how numerous they are but the Nmap website has some great documentation if more info is needed. when a script category is selected the entire library of scripts under that category will be run.

## Additional Useful Flags

#### -A
something about the -A flag that enables a service scan.
#### -O
something about the -O flag which enables OS scanning and the --osscan-guess option in order to get OS scan guesses when nmap isn't sure
#### -oG
The -oG \<filename> flag will write output in Nmap's so-called grepable format to _`<filename>`_. This tabular format fits the output of each host on a single line, making it easy to grep for open ports, certain operating systems, application names, or other data. Normal output will still be printed to stdout unless you ask for the grepable output to be directed there by specifying `-` as _`<filename>`_. While this format works well for parsing with simple grep and awk command-lines, significant scripts and programs should use the XML output instead. The XML format contains substantial information that grepable format has no place for, and extensibility makes XML easier to update with new information without breaking tools that rely on it.
#### -sn
-sn this option tells Nmap not to do a port scan after host discovery, and only print out the available hosts that responded to the host discovery probes. This is often known as a “ping scan”, but you can also request that traceroute and NSE host scripts be run. This is by default one step more intrusive than the list scan, and can often be used for the same purposes. It allows light reconnaissance of a target network without attracting much attention. Knowing how many hosts are up is more valuable to attackers than the list provided by list scan of every single IP and host name.
Systems administrators often find this option valuable as well. It can easily be used to count available machines on a network or monitor server availability. This is often called a ping sweep, and is more reliable than pinging the broadcast address because many hosts do not reply to broadcast queries.
The default host discovery done with `-sn` consists of an ICMP echo request, TCP SYN to port 443, TCP ACK to port 80, and an ICMP timestamp request by default. When executed by an unprivileged user, only SYN packets are sent (using a `connect` call) to ports 80 and 443 on the target. When a privileged user tries to scan targets on a local Ethernet network, ARP requests are used unless `--send-ip` was specified. The `-sn` option can be combined with any of the discovery probe types (the `-P*` options) for greater flexibility. If any of those probe type and port number options are used, the default probes are overridden. When strict firewalls are in place between the source host running Nmap and the target network, using those advanced techniques is recommended. Otherwise hosts could be missed when the firewall drops probes or their responses.
In previous releases of Nmap, `-sn` was known as `-sP`.
#### -sU
The -sU flag switches to scanning UDP ports instead of TCP ports, it has no additional known functionality, and can be used in conjunction with all other flags.
#### -sS
The -sS Flag is far and away the most popular scan type because it the fastest way to scan ports of the most popular protocol (TCP). It is "stealthier" than connect scan, and it works against all functional TCP stacks (unlike some special-purpose scans such as FIN scan). Additionally and very importantly it also sends fewer bytes than other scan types.
#### -sV
Write something on the -sV flag which does service detection.

## About Scripts
Post Script note, if you ever find yourself searching for Nmap scripts, there is an easier way to find them, please look at the following code block and re-purpose it to your needs.
```
ali@kali:~$ ls -1 /usr/share/nmap/scripts/smb*

/usr/share/nmap/scripts/smb2-capabilities.nse
/usr/share/nmap/scripts/smb2-security-mode.nse
/usr/share/nmap/scripts/smb2-time.nse
/usr/share/nmap/scripts/smb2-vuln-uptime.nse
/usr/share/nmap/scripts/smb-brute.nse
/usr/share/nmap/scripts/smb-double-pulsar-backdoor.nse
/usr/share/nmap/scripts/smb-enum-domains.nse
/usr/share/nmap/scripts/smb-enum-groups.nse
/usr/share/nmap/scripts/smb-enum-processes.nse
/usr/share/nmap/scripts/smb-enum-sessions.nse
/usr/share/nmap/scripts/smb-enum-shares.nse
/usr/share/nmap/scripts/smb-enum-users.nse
/usr/share/nmap/scripts/smb-os-discovery.nse
```

the -1 simply puts things in a column format making it easier to read.