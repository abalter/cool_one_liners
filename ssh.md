Rsync without a tunnel

    rsync -ave "ssh -A user@tunnel-server ssh" <source> <target>
    
where `<source>` or `<target>` can be on the server behind the firewall.

For example:

    rsync -ave "ssh -A me@acc.ohsu.edu ssh" my-directory me@exacloud.ohsu.edu:/home/users/me/some-directory
    
    
