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

```


---

[[/index|Get Back To Index]]
