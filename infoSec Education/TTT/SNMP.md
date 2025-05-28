basic check:
nmap -sU -p 161 --script snmp-info 192.168.1.100

attempt to retrieve sensitive data:
snmpwalk -v 2c -c public 192.168.1.100 1.3.6.1.2.1.1

in order to gather extra info and attempt a basic brute force
nmap --script "snmp*" 10.10.11.48 -sU -p 161
