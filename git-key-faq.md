# Git Key FAQ
### Create Key Pair
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
> user@local:~$ ssh-keygen -t rsa -b 4096 -C "user@host:person@domain.com"

### Create Public Key from Existing Private Key
http://askubuntu.com/questions/53553/how-do-i-retrieve-the-public-key-from-a-ssh-private-key
> user@local:~$ ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub

### Append Public Key to Authorized Keys on Remote Server
https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2
**Option 1**
> user@local:~$ ssh-copy-id -i ~/.ssh/id_rsa user@host

**Option 2**
> user@local:~$ cat ~/.ssh/id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"

### Restrict Root Login on Remote Server
https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2
> root@host:~# vim /etc/ssh/sshd_config

**Option 1: Disable Root Login**

    PermitRootLogin no

**Option 2: Restrict Root Login to SSH Keys**

    PermitRootLogin without-password

**Reload SSH Service on Remote Host**
> root@host:~# service ssh reload
