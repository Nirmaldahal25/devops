# Ansible
### Create a Inventory file
- The inventory files holds the remote hosts to be managed by ansible. The inventory file allows dns host names or ip addresses. The ip addresses might change eventually thus using host names is better.

### Running some ansible commands.
- Ansible comes with different modules such as ping, apt etc.
- Let's check if the connection could be established with the managed hosts. 
`ansible all --key-file <private_ssh_key> -i inventory -m ping`
- But inventory and ssh key file are constants thus it can be configured in the **ansible.cfg** file.
- Now the same command works with `ansible all -m ping`. Short and sweet.

### Running more ansible commands.
- Get list of know hosts.
`ansible all --list-hosts`
- Get information about all the remote hosts. 
`ansible all -m gather_facts`
- Limit ansible command to particular remote host
`ansible all -m gather_facts --limit <host_name>`
<br>
**Running apt Commands with priviliges escalation in debian based system**
- This command is equivalent of apt update
`ansible all -m apt -a update_cache=true` This fails because update indexes required sudo permission in the remote systems. Thus the privilige can be escalated with --become or --become-user(become user who has permission for those tasks).
- Instead use `ansible all -m apt -a update_cache=true --become --ask-become-pass`
- Though there might be different passwords for different hosts. And grouping them in inventory file. For now, I escape this.
- Install gedit on all the remote systems.
`ansible all -m apt -a name=gedit --become --ask-become-pass`
- Re-running this will issue not changed message
- Remove gedit from all systems. `ansible all -m apt -a "state=absent name=gedit" -b -K` when -b and -K are --become and --ask-become-pass respectively. Use **state=latest** for upgrading the package.
 
