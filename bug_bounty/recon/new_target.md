# Getting Started


## ASN's
Autonomous system number
for company's large enough to require them, most medium to large company's have an ASN.
Most big buisnesses have some of their own infra and then a fair bit in the cloud as well.

Do not automate finding the ASN. automation will always either under or overscope. best to do it manually.

Hurricane Electric site. easy free form search for a website, great place to start looking for ASN

You'll want to check for Prefixes, especially IPv4.

You then want to scan all the IP's you've found and check two things
1. first check for open web servers 80/443
2. then check for any other open ports you can find
Notes: 
You can use a Terminal tool calles asnmap in order to not copy all the ip's manually

Use naabu or rustscan for initial port scan then use nmap for fingerprinting

you can also use smap, for passive scan, it uses shodan in order to check nmap databases. it'll check the last port scan that shodan did on your target.

doing smap scans help you not get banned lol. just in case the team bans people for being to agressive with scans.

## Cloud Recon

Most small companies and some medium sized companies tend to be completly cloud based. Even big companies have a tendency to use a fair bit of cloud based computing.

Look for SSL certificates. It can give you possible DNS or subdomain data for the company your doing recon on.

Cloud Recon, is a great option for scanning the ENTIRE INTERNET every day for its SSL certs. giving you an up to date scan which can get you ahead of compition


## Shodan
why do we use shodan... It's passive, its a giant spider that scans the entire internet for tons of info.
It is a paid Infrastructure spider

Tips an Tricks:
look for cheat sheets
Learn to use operators to specify your search
Learn to use shodan in terminal
use a tool called karma_v2p
also shosubgo for finding subdomains
there's also some great youtube video's about asset descovery with shodan