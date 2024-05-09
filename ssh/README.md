# SSH configuration

## Server:

- Install openssh-server.
- Configure `/etc/ssh/ssh_config` file with password login
- [Start/Restart] sshd service.

### Note

**user = server_user** <br>
**host = server_host**

# Client:

- Generate ssh private and public keys with ssh-keygen
- Eg `ssh-keygen -t rsa -b 4096 -C "comment"` It uses rsa for encrypting private key.
- Add public key to ssh server. `ssh-copy-id -i pub_rsa.pub server_user@server_host` and enter the users password.
- Add host to known hosts. `ssh-keyscan -H server_host >> ~/.ssh/known_hosts`

### Note

- When `ssh server_user@serverhost` it uses password of the user.
- Thus, the private key can be added to a key base created by ssh-agent which persist until the terminal session has ended.

## Configuring ssh-agent

- Initialize ssh-agent. `` eval `ssh-agent`  ``
- `ssh-add pub_rsa` and enter the password used when creating the keys pair.
