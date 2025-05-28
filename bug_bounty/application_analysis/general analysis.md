Never assume that an application has been hacked through and through, there's always something more to be found.

Also always wait for new features to be launch, every time a new feature launches a ton of new bugs are just waiting to be found.

patience is your friend.

if you feel lost and overwhelmed, so does everybody else. if you keep going you will find the things people never had the will power to find.

Always make an account and look past the authentication barrier. profile and customer information is a gold mine. Maybe paid features can get hacked for free usage.


## Pre manual testing and automation

### Testing Layers

#### Open Ports and Services

#### Web Hosting Software

#### Application Framework

#### Custom Code or COTS
Lots of good stuff here

#### Application Libraries (usually JavaScript)

#### integrations


## Tech profiling
webanalyze terminal tool


## Finding CVE's and Misconfigs
This is mostly against non custom code

There are plenty of automated tools that help you do this. One of which is Nuclei

Scans are most succesful on domains you think no one else has scanned or found. This requires extremely good recon.

## Port scanning

If you haven't done port scanning yet now would be the time to do it.

# Content Discovery
## Tools 
[[FerroxBuster]] -> replacement for gobuster... use it lol
## Lists
### IISS/MSF
httparchive_aspx_asp_cfm_svc_ashx_asmx_ -> This is from wordlists.assetnote.com
OOS Shortname Scanner

### PHP + CGI
httparchive_cgi_pl -> This is from wordlists.assetnote.com
httparcheve_php -> This is from wordlists.assetnote.com

### General API
httparchive_apiroutes_ -> This is from wordlists.assetnote.com
swagger-wordlist.txt -> This is from wordlists.assetnote.com
SECLISTS/blob/master/Discovery/web-content/api/api-endpoints.txt

### Java
httparchive_jsp_lspa_do_action -> This is from wordlists.assetnote.com

### Generic
httparchive_directories-im -> This is from wordlists.assetnote.com
RAFT
Robots Dissalowed
github/six2dez/OneListForAll
jhaddix/content_discovery_all.txt