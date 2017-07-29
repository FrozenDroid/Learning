# Safety
Some things to look out for when designing software, so that you don't mess everything up.
## Removing files
When removing files, be absolutely sure that you're removing the right files. What do I mean? [This](https://serverfault.com/questions/587102/monday-morning-mistake-sudo-rm-rf-no-preserve-root).  
Anyway, if you have to remove temporary files, it's best to remove those files by pattern.  
Otherwise, make sure that the path is always correct, and build in safeguards.
It's also a good idea to set up permissions correctly so that your script cannot remove things it shouldn't.
