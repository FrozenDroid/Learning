# Docker
## IPTABLES
By default, Docker interferes directly with [IPTABLES](http://ipset.netfilter.org/iptables.man.html) which may not always be preferred, as in my case.  
Instead, you can make rules manually using [UFW](https://wiki.ubuntu.com/UncomplicatedFirewall).  

To do this, you first have to disable Docker's intefering with IPTABLES.
1. Create the file `/etc/docker/daemon.json` if it doesn't already exist.
2. Add `{ "iptables": false }` to the file, or add the key-value pair to the JSON if it is already present.

Now you can manually create rules!
