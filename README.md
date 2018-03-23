# ssh-create

1. Creates an ssh keypair for you and puts it in ~/.ssh.

2. Starts ssh agent.

3. Adds keypair to keyring via ssh-add.

## Example:

```
$> ssh-create derp
YOUR_EMAIL.com
creating keypair for derp
Generating public/private rsa key pair.
Your identification has been saved in /home/USER/.ssh/derp.
Your public key has been saved in /home/USER/.ssh/derp.pub.
The key fingerprint is:
SHA256:OMITTED YOUR_EMAIL.com
The key's randomart image is:
+---[RSA 4096]----+
|    OMITTED      |
+----[SHA256]-----+
Agent pid 2XXXX
Identity added: /home/USER/.ssh/derp (/home/USER/.ssh/derp)
```

## Install:

```
$> install
```
copies `ssh-create` to `~/.local/bin`

if `~/.local/bin` is not in your path, add the following to the end of your .zshrc, or .bashrc, or whatever rc file you use.

```
echo 'PATH=~/.local/bin:$PATH' >> YOUR_RC_FILE_NAME && source YOUR_RC_FILE_NAME

echo 'PATH=~/.local/bin:$PATH' >> ~/.zshrc && source ~/.zshrc
```


