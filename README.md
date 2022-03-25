# Example: Floating IP with keepalived

This Ansible Playbook configures a floating IP address
on 2 servers (master & backup) with keepalived.
If the master node becomes unreachable, the IP address will be floated to the backup node.

## Usage

Set your hosts in the file `inventory`.

    ansible-playbook -i inventory main.yml
