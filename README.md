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

## Installation

Here is how to install these scripts on your computer.

```shell
$> install
```

copies `ssh-create` to `~/.local/bin/ssh-create`

if `~/.local/bin/ssh-create` is not in your path, add the following to the end of your .zshrc, or .bashrc, or whatever rc file you use.

```shell
echo 'PATH=~/.local/bin/ssh-create:$PATH' >> YOUR_RC_FILE_NAME && source YOUR_RC_FILE_NAME

echo 'PATH=~/.local/bin/ssh-create:$PATH' >> ~/.zshrc && source ~/.zshrc
```

## Creating a key

```shell
ssh-create mykey
```

## Deleting a key

```shell
ssh-remove mykey
```

## Adding a key to an SSH config

Add the following to the `~/.ssh/config` file.

```shell
Host SERVER_NAME       <-- Insert your server name here (whatever you want to call it.)
    HostName SERVER_IP <-- Insert your server IP here
    User root
    IdentityFile ~/.ssh/mykey
```

## Adding a key to a server

```shell
ssh-copy-id -i ~/.ssh/config/mykey SERVER_NAME
```

The server can now be SSH'ed into by name.

```shell
ssh SERVER_NAME
```

No key, username, or password necessary.

## Starting an SSH Agent

The agent is a background process that possesses a keyring used to hold keys. These keys are used when SSHing into Servers soley by the servers name.

There are many ways to start an agent. A rudimentary way:

```shell
eval "$(ssh-agent -s)" &> /dev/null
```

## Adding a key to an SSH Agent

In order for SSH to use a key when authenticating to a server, the key must exist on the SSH Agents keyring.

Add the following to `~/.zshrc`, `~/.zshenv`, or whichever shell specific file sourced in your terminal.

```shell
# After starting the agent, add the key to the agent's keyring.
ssh-add -q ~/.ssh/mykey
```
