# Docker
## IPTABLES
By default, Docker interferes directly with [IPTABLES](http://ipset.netfilter.org/iptables.man.html), so that exposed ports are allowed automatically, which may not always be preferred.  
I found the need to disable this when I wanted to expose a HTTP/HTTPS service through a reverse-proxy with Caddy.  
Because I did not want to let users access the service without going through Caddy, I made rules manually using [UFW](https://wiki.ubuntu.com/UncomplicatedFirewall).  

To do this, you first have to disable Docker's intefering with IPTABLES.
1. Create the file `/etc/docker/daemon.json` if it doesn't already exist.
2. Add `{ "iptables": false }` to the file, or add the key-value pair to the JSON if it is already present.

Now you can manually create rules!
## Inside container or not?
Once, I needed to determine whether a script was running inside of a container.  
A good way of doing this is by checking if there is a file called `.dockerenv` inside the root. If it is there, it means the script is running inside a Docker container.