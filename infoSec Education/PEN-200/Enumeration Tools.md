# DNS Enumeration

Host -> host allows you to check dns records, usefull tip is that the -t flag allows you to define types of records
Examples:
```
~ 
❯ host megacorpone.com
megacorpone.com mail is handled by 10 fb.mail.gandi.net.
megacorpone.com mail is handled by 50 mail.megacorpone.com.
megacorpone.com mail is handled by 20 spool.mail.gandi.net.
megacorpone.com mail is handled by 60 mail2.megacorpone.com.

~ 
❯ host costa-rica-refined.com
costa-rica-refined.com has address 76.76.21.21
costa-rica-refined.com mail is handled by 15 f2e4sgogy2wegxbzruj22fhdgcjtmbty5kpbymwvtq7hr6xji2ta.mx-verification.google.com.
costa-rica-refined.com mail is handled by 1 smtp.google.com.

~ 
❯ host -t a megacorpone.com
megacorpone.com has no A record

~ 
❯ host -t txt megacorpone.com
megacorpone.com descriptive text "Try Harder"
megacorpone.com descriptive text "google-site-verification=U7B_b0HNeBtY4qYGQZNsEYXfCJ32hMNV3GtC0wWq5pA"
```

while this is a useful tool when used manually it can quite easily become automated. No scripts are even necessary in order to automate it, just some simple Bash scripting. 

### Walk-through
Step 1:
Create a file of the host names you want checked for example
```
www
ftp
mail
owa
proxy
router
```

lets call this hosts.txt

Step 2:
now with a quick bash one liner we can automate this process.
```
for ip in $(cat hosts.txt); do host $ip.megacorpone.com; done
```

Step 3:
for more comprehensive word lists that would be useful in real world attacks please reference this external resource [SecLists](https://github.com/danielmiessler/SecLists)

Step 4: 
There are also advanced tools written just fo this purpose, two available on kali linux are _DNSRecon_ and _DNSenum_, It should be noted there are probably more tools out there that are worth discovering.

# TCP/UDP Port Scanning
Nmap is the tool of choice for port scanning, here we will go over some useful flags and options that Nmap provides out of the box as well as showing a few examples along the way.

