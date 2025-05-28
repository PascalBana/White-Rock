passwd files generally are filled with mostly trash, so although you should try a quick visual scan of the file with your eyes. I would also recommend a few grep statements to clean things up a bit

I recommend starting with
```
grep -v -e 'nologin'
```
 This will shorten the list by quite a bit, but still leave possible diamonds to be found

If you want to cut right to the chase you can use
```
grep '/bin/bash'
```
This will show you definite users, with the exception that it only shows users with bash, others may be missed, always be thorough.