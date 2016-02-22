# File transfer and backup methods
Including across a hop (tunnel)

## Rsync

https://stackoverflow.com/questions/16654751/rsync-through-ssh-tunnel/21787966#21787966

Rsync without a tunnel

    rsync -ave "ssh user@tunnel-server ssh" <source> <target>
    
where `<source>` or `<target>` can be on the server behind the firewall.

For example:

    rsync -ave "ssh me@acc.ohsu.edu ssh" my-directory me@exacloud.ohsu.edu:/home/users/me/some-directory
    
## Ionice

https://friedcpu.wordpress.com/2007/07/17/why-arent-you-using-ionice-yet/


## Using pipes
http://serverfault.com/a/560991/168208

    cat ginormous-file | ssh user@host1 "cat | ssh user@host2 \"cat >out\" "
    
## Article: Backing up using SSH & Rsync
http://conorcahill.blogspot.com/2006/11/backing-up-using-ssh-rsync.htmlHost family_desktops

## SSH through tunnel using config file
http://unix.stackexchange.com/questions/82269/ssh-tunnel-through-middleman-server-how-to-connect-in-one-step-using-key-pair
```
Host family_desktops
  ProxyCommand ssh debian_server_fqdn nc localhost %p
  User admin
  PasswordAuthentication no
  IdentityFile ~/.ssh/my_id_rsa
 ```
