Telnet (Telecommunication Network) is not secure!!! = TCP/23

SSH ( Secure SHell) is encrypted, pretty much the same thing as Tel net but it's actually secure = TCP/22

DNS (Domain Name System) converts names into IP addresses = UDP/53

SMTP ( simple mail transfer protocol) =TCP/25

SFTP (Secure File Transfer Protocol) uses the SSH port, but this protocol allows file system functionality. is encrypted = TCP/22

FTP (File Transfer Protocol), transfers files between systems, authenticates with a username and password. Is not encrypted  = TCP/20

TFTP (Trivial File Transfer Protocol), very simple file transfer application. has no authentication. is very insecure. DO NOT use on production systems = UDP/69

DHCP (Dynamic Host Configuration Protocol), Automated Configuration of IP address, subnet mask and other options. Requires a DHCP server. Dynamic/Pooled, IP addresses are assigned in real time from a pool. you can reserve certain addresses for certain MAC addresses = UDP/67, UDP/68

HTTP = TCP/80

HTTPS = TCP/443

SNMP (Simple Network Management Protocol), gather statistics from network devices. there are three distinct version. the first ones are less secure. V3 has encryption = UDP/161

RDP ( Remote Desktop Protocol), share a desktop from a remote location = TCP/3389

NTP(Network Time Protocol), used to synchronize digital clocks around the world. Very accurate, better than 1 millisecond between devices on the same network = UDP/123

SIP(Session Initiation Protocol), used for setting up calls, ringing the phone and hanging up the phone. =TCP/5060, TCP/5061

SMB( Server Message Block), used by Microsoft windows, used to share files and printer sharing also called CIFS ( Common Internet File System) = TCP/445\

POP/IMAP, used to receive and authenticate emails. POP3 (Post Office Protocol Version 3), has basic mail transfer functionality = TCP/110. IMAP4 (Internet Message Access Protocol Version 4), includes management of email inbox from multiple clients - TCP/143

LDAP (Lightweight Directory ACCESS protocol), store and retrieve information in a network directory. = TCP/389. also LDAPS which is the secure version = TCP/636

H.323, VoIP, is very old but some systems still use it = TCP/1720