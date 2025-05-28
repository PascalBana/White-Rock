# Passive Information Gathering 
This is the first step due to it being undetectable by your target. It often includes OSINT(Open Source Intelligence) as well as gathering information from web servers and DNS.

It is important to understand that during Passive Information Gathering you may access the targets website as a normal user would, but you would want to avoid doing anything suspicious such as trying to log into an administrator page. The goal is to remain completely undetected.

Our ultimate goal with Passive Information Gathering is to obtain information that clarifies or expands an attack surface, helps us conduct a successful phishing campaign, or supplements other penetration testing steps such as password guessing, which can ultimately lead to account compromise.

It is important to remember even seemingly useless information can be critical, such as employee email addresses being used to start a client-side attack.

## Tactics and Tools
Now that we've covered the basics it's time to go over some common tactics and tools used in Passive Information gathering.

### Whois Enumeration
Whois is a TCP service, tool, and type of database that can provide information about a domain name. The information provided is often public, since registrars charge a fee for private registration. Whois is a command line tool, here is some example commands.
```
whois megacorpone.com -h 192.168.50.251
```
The structure of the command is as such... first the domain name "megacorpone.com" followed by the "-h" flag which stands for host. the "-h" flag takes an argument of an IP address.
This is often not that useful, but on occasion gives us information about the owner of the domain, which gives us a jumping off point for other types of research such as googling people or companies associated with the domain.

> [!info] 
> whois info changes based on host ip, I don't know why but understanding this is very important, please research when available


### Google Hacking
essentially this is googling with the help of advanced operators, please google "google search operators" if you have forgotten what they are.

> [!todo]
> We should create a page specifically filled with google operators and examples for future reference

for advanced research please reference the Google Hacking Database for crazy uses of google hacking

### Netcraft
Kill Myself, this is getting boring raaaaaaaaaaaaa
It's a website that lets you enter a URL and it gives you info, reeeeeeeee
The website is hard to navigate and they say they will shut down their DNS services soon so it would be wise to look into alternatives.

### Open-Source Code
This is just Github and stuff, make sure to check all Git based remote Repo services but really it's just looking for the company name in Github and trying to see if they have any open-source code, this is useful for two major reasons. One you may find Coding practices, languages, or common dependencies that you can prepare to encounter later. Secondly you may find user information from contributors like company emails, and perhaps they left some naughty API keys or something like that in their code, you never know.

### Shodan
Okay, the short of it is, it searches IOT devices, checks what has an external internet connection, very useful in the real world, but useless in the course. Check it out later.

### Security Headers and SSL/TLS
again extra info... check securityheaders.com for more information. not quite sure how it's useful but info is info.

# Active Information Gathering
Remember that active information gathering is detectable by the owners of the servers your collecting info on. That's not to say that everyone is going to be analyzing traffic, but if they are you will stick out like a soar thumb.

The goal here is to strike a balance between gathering info and being detected, most of the time it is better to stay undetected than it is to gather extra info, you should be using info gathered during the passive phase in order to limit the amount of probing you have to do.

For tools used in this section please reference [[Enumeration Tools]]
### DNS Enumeration
using tools you can scan the DNS records of a given IP address or URL, or both. This can give you important configuration information about the targets DNS records

### TCP/UDP Scanning
other wise known as port scanning.

<span class="red-text">Please note that port scanning is not representative of traditional user activity and could be considered illegal in some jurisdictions. Therefore, it should not be performed outside of laboratory environments without direct, written permission from the target network owner.</span>

Additionally please note that reckless port scanning is very easily detectable by IDS([[Intrusion Detection Systems]]) and therefor is a dead giveaway that you are planning an attack.

Information gathered from the [[Information Gathering#Passive Information Gathering|Passive]] portion of the information gathering process should be used to minimize the number of ports scanned. In addition to scanning the ports in non suspicious ways, this allows us to stay undetected.

Port scanning is a dynamic and cyclical process, the results of one scan dictate the type and scope of the following scan.

Nmap scripts are large in number but luckily have been categorized to simplify their usage, I won't be going over the categories here given how numerous they are but the Nmap website has some great documentation if more info is needed. when a script category is selected the entire library of scripts under that category will be run.

something about the -A flag that enables a service scan.

something about the -O flag which enables os scanning and the --osscan-guess option in order to get os scan guesses when nmap isn't sure

The -oG \<filename> flag will write output in Nmap's so-called grepable format to _`<filename>`_. This tabular format fits the output of each host on a single line, making it easy to grep for open ports, certain operating systems, application names, or other data. Normal output will still be printed to stdout unless you ask for the grepable output to be directed there by specifying `-` as _`<filename>`_. While this format works well for parsing with simple grep and awk command-lines, significant scripts and programs should use the XML output instead. The XML format contains substantial information that grepable format has no place for, and extensibility makes XML easier to update with new information without breaking tools that rely on it.

-sn this option tells Nmap not to do a port scan after host discovery, and only print out the available hosts that responded to the host discovery probes. This is often known as a “ping scan”, but you can also request that traceroute and NSE host scripts be run. This is by default one step more intrusive than the list scan, and can often be used for the same purposes. It allows light reconnaissance of a target network without attracting much attention. Knowing how many hosts are up is more valuable to attackers than the list provided by list scan of every single IP and host name.
Systems administrators often find this option valuable as well. It can easily be used to count available machines on a network or monitor server availability. This is often called a ping sweep, and is more reliable than pinging the broadcast address because many hosts do not reply to broadcast queries.
The default host discovery done with `-sn` consists of an ICMP echo request, TCP SYN to port 443, TCP ACK to port 80, and an ICMP timestamp request by default. When executed by an unprivileged user, only SYN packets are sent (using a `connect` call) to ports 80 and 443 on the target. When a privileged user tries to scan targets on a local ethernet network, ARP requests are used unless `--send-ip` was specified. The `-sn` option can be combined with any of the discovery probe types (the `-P*` options) for greater flexibility. If any of those probe type and port number options are used, the default probes are overridden. When strict firewalls are in place between the source host running Nmap and the target network, using those advanced techniques is recommended. Otherwise hosts could be missed when the firewall drops probes or their responses.
In previous releases of Nmap, `-sn` was known as `-sP`.

The -sU flag switches to scanning UDP ports instead of TCP ports, it has no additional known functionality, and can be used in conjunction with all other flags.

The -sS Flag is far and away the most popular scan type because it the fastest way to scan ports of the most popular protocol (TCP). It is "stealthier" than connect scan, and it works against all functional TCP stacks (unlike some special-purpose scans such as FIN scan). Additionally and very importantly it also sends fewer bytes than other scan types.

Write something on the -sV flag which does service detection.

This concludes the general section of port scanning we will now move on to more specific cases

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
#### SMB enumeration

#### SMTP enumeration


