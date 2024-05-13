# How to solve PTY allocation request failed on channel 0 issue for a remote server which runs Forgejo

I have been uploaded my ssh key to remote virtual machine which runs Forgejo as same as the ssh public key on my physical machine. Then I tried to ssh to this virtual machine but I see this error output below :

```
hwpplayer1@hwpplayer1-Aspire-A315-24P:~$ ssh debian@192.168.122.171
PTY allocation request failed on channel 0

Forgejo: Key check failed
Connection to 192.168.122.171 closed.
```

# Solution

I removed the SSH key by openining the GUI interface Virt-Manager. Then I added my ssh key to the remote virtual machine written below:

```
ssh-copy-id debian@192.168.122.171
```

In the meantime I configured my .ssh/config as written below for connecting remote server via 

```
ssh hostname 
```

```
Host debian
    Hostname 192.168.122.171
    User debian
    IdentityFile ~/.ssh/id.rsa
```

now this command/ssh connection works ! 

```
ssh debian
```

happy hacking !
