## ssh

### links

#### vw links

[openssh](openssh.md)  # openssh

[ssh-basis](ssh-basis.md)  # ssh basis

[ssh-server](ssh-server.md)  # ssh server

#### www links

1. https://losst.pro/kak-uznat-ip-adres-linux  # how find you ip
2. https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04-ru
3. https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview
4. https://wiki.archlinux.org/title/OpenSSH  # Open SSH
5. https://wiki.archlinux.org/title/SSH_keys#Choosing_the_key_location_and_passphrase  # SSH keys
6. https://man.archlinux.org/man/ssh_config.5  # SSH config
7. https://wiki.archlinux.org/title/SSH_keys#Generating_an_SSH_key_pair  # SSH keys
8. Project with 3 parts tutorial of [OpenSSH Key Management][001]

### commands

```sh
sudo nvim /etc/ssh/sshd_config  # config file
ip a                            # show yor ip
ip -br a                        # show you ip short list
ping -c 3 <host-ip>             # ping host
systemctl status sshd           # ssh dimom status
sudo systemctl enable sshd
sudo systemctl start sshd       # start ssh dimon
# or
systemctl restart sshd          # restart ssh dimon
ssh-copy-id -i ~/.ssh/id_ed25519.pub name@host-ip  # copy ssh key to host
ssh-copy-id root@yourdomain.com # copy your kay to root of remote machine
sudo systemctl stop sshd        # stop ssh dimon
sudo systemctl disable sshd
journalctl -fu sshd  # see logs of ssh where:
	             # -f -> follow
		     # -u -> unit (here unit is sshd)
```

The `ssh-copy-id` command will ask for your server's root password and log you in briefly. What this does is that it puts your public SSH key fingerprint on your server in a file `/root/.ssh/authorized_keys`. This file in turn allows approved SSH keys to log in without passwords.
Note that you can also replace `root` with a username of an account on the server if you had made a non-root user that you'd like to easily log into as well. For the username `user`, it will also store the key in `/home/user/.ssh/authorized_keys`.

To test if this has worked, now try logging in normally to your server with ssh:
```sh
ssh root@yourdomain.com
```

If you find that this does not work try running the following, make sure you are in the directory where the keys where created.
```sh
chmod 700 ~/.ssh/
chmod 644 ~/.ssh/id_rsa.pub
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/authorized_keys
```

[001]: https://www.funtoo.org/Funtoo:Keychain "Funtoo Keychain Project"

---

[[/index|Get Back To Index]]
