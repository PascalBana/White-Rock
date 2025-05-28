hash cat can be used in debug mode to output a list of passwords with rule sets attached
```
hashcat -r demo.rule --stdout demo.txt
```
or to output directly into another file
```
hashcat -r demo.rule --stdout demo.txt >> passwords.txt
```