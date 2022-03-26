# Example: Floating IP with keepalived

This Ansible Playbook configures a floating IP address
on 2 servers (master & backup) with keepalived.
If the master node becomes unreachable, the IP address will be floated to the backup node.

## Usage

Set your hosts in the file `inventory`.

    [master]
    192.168.2.51 ansible_user=root

    [backup]
    192.168.2.52 ansible_user=root

Set a authentication password in `templates/keepalived.conf`.

    auth_pass monkey

Set the floating IP address in `templates/keepalived.conf`.

    192.168.2.55/24

You might need to change the network interface name in `group_vars/`,
if it is different than `eth0`.

If you run a firewall, make sure to expose port 112 for both peers.

Run the playbook.

    $ ansible-playbook -i inventory main.yml
