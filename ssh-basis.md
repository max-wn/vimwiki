## ssh cheatsheet

### Basis

#### Generate ssh keys used for authentication, password-less logins, and other things.

```sh
ssh-keygen                            # Generate a key interactively
ssh-keygen -f ~/.ssh/filename         # Specify file in which to save the key
ssh-keygen -t ed25519 -a 100          # Generate an ed25519 key with 100 key derivation function rounds
ssh-keygen -t rsa -b 4096 -C "email"  # Generate an RSA 4096 bit key with email as a comment
ssh-keygen -lf .ssh/id_ed25519.pub    # show key fingerprint
```

#### Remove and retrieve keys

```sh
ssh-keygen -l -F remote_host             # Retrieve the key fingerprint
                                         # from a host (useful for confirming
                                         # the authenticity of the host
                                         # when first connecting to it via SSH)
ssh-keygen -R remote_host                # Remove the keys of a host from the known\_hosts file (useful when a known host has a new key)
ssh-keygen -l -E md5 -f ~/.ssh/filename  # Retrieve the fingerprint of a key in MD5 Hex
```

#### Change the password of a key:

```sh
ssh-keygen -p -f ~/.ssh/filename
```

#### Transfer files

To transfer a file to a remote computer in the terminal run:

```sh
scp /path/to/local/file remoteuser@remote-ip-address:/path/to/remote/file
```

And to transfer a file from a remote computer to your local computer simply
type first the remote address and then local.

```sh
scp remoteuser@remote-ip-address:/path/to/remote/file  /path/to/local/file
```

#### Installation

Debian/Ubuntu you install on local machine `sudo apt install openssh-client`
and on remote `sudo apt install openssh-server`
on Archlinux you install on local and remote `sudo pacman -S openssh`

### Add SSH to Github [LINK][002]

Generate key

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"  # generate key
eval "$(ssh-agent -s)"  # Start the ssh-agent in the background
ssh-add ~/.ssh/id_ed25519  # Add your SSH ***private*** key to the ssh-agent
```

Adding a new  ***public*** SSH key to your GitHub account and test connection

```sh
pbcopy < ~/.ssh/id_ed25519.pub  # Copy the SSH public key to your clipboard and paste it to SSH settings on github site
# or via github cli
gh ssh-key add ~/.ssh/id_ed25519.pub --type signing
ssh -T git@github.com           # testing your SSH connection
```

Verify that the fingerprint in the message you see matches [GitHub's RSA public key fingerprint][001]. If it does, then type `yes`


### ssh without password for one session only

```sh
eval "$(ssh-agent)"        # Start the ssh-agent in the background
ssh-add ~/.ssh/id_ed25519  # add key to ssh agent memory, agent stops when you close a terminal
# но учше добавлять ключ лишь на указанный промежуток времени:
ssh-add -t 600s ~/.ssh/id_ed25519  # time format: '600' or '600s' or '1h30m'
ssh-add -l  # list fingerprints of currently loaded keys
```

[001]: https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints "github fingerprint"
[002]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account "Adding a new SSH key to your GitHub account"
[003]: https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh "Managing remote repositories"
[004]: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-ssh-keys "Reviewing your SSH keys"
[005]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection "Testing your SSH connection"

---

[[/index|Get Back To Index]]
