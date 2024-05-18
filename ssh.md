## ssh

### links
#### vw links
[openssh](openssh.md)  --> openssh
[ssh-basis](ssh-basis.md)  --> ssh basis
[ssh-server](ssh-server.md)  --> ssh server

#### www links
https://losst.pro/kak-uznat-ip-adres-linux  # how find you ip
https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04-ru
https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview
https://wiki.archlinux.org/title/OpenSSH

### commands
```bash
ip a                            # show yor ip
ip -br a                        # show you ip short list
ping -c 3 <host-ip>             # ping host
systemctl status sshd           # ssh dimom status
sudo nvim /etc/ssh/sshd_config  # config file
sudo systemctl start sshd       # start ssh dimon
systemctl restart sshd          # restart ssh dimon
ssh-copy-id -i ~/.ssh/id_ed25519.pub name@host-ip  # copy ssh key to host
sudo systemctl stop sshd        # stop ssh dimon
sudo systemctl disable sshd
sudo systemctl enable sshd
journalctl -fu sshd  # see logs of ssh where:
	             # -f -> follow
		     # -u -> unit (here unit is sshd)
```

```bash
ssh-copy-id root@yourdomain.com
```
The above command will ask for your server's root password and log you in briefly. What this does is that it puts your public SSH key fingerprint on your server in a file `/root/.ssh/authorized_keys`. This file in turn allows approved SSH keys to log in without passwords.
Note that you can also replace `root` with a username of an account on the server if you had made a non-root user that you'd like to easily log into as well. For the username `user`, it will also store the key in `/home/user/.ssh/authorized_keys`.

To test if this has worked, now try logging in normally to your server with ssh:
```bash
ssh root@yourdomain.com
```

If you find that this does not work try running the following, make sure you are in the directory where the keys where created.
```bash
chmod 700 ~/.ssh/
chmod 644 ~/.ssh/id_rsa.pub
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/authorized_keys
```


---

[[/index|Get Back To Index]]
