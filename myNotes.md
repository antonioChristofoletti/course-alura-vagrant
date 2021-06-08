# Vagrant

## What is It?

This guy manage and automatize a lot of specs related to a Hypervisor (VMware, Virtualbox) using a simple file called Vagranfile.

Import to check the compatibility between Vegrant and the Hypervisor.

## Hypervisor

Hypervisor are software that execute the interactions between the virtual OS and the current OS on the machine. Generally It is responsable by creating, manage communication and resources.

There are 2 types:

Type 1: It is called "bare metal", because It is executed directly in the host hardware. Examples: Hyper-V and vphere.

Type 2: It is executed above some OS, examples: VirtualBox and VMware.

## Commands

All Commands start with `vagrant`.

- `init hashicorp/precise64` - Start a vagrant file environment;
- `up` - Create de virtual machine and configure it;
- `halt` - stop the machine;
- `status` - Check status;
- `ssh` - Connect thought ssh:;
- `ssh-config` - Show ssh configs;
- `reload` - shutdown and restart.

Off-topic:

- `ssh -p 2222 vagrant@127.0.0.1` - Tradicional SSH;


## VagrantFile

All the virtual machine configurations come here.

There are 3 network types: 

- Forwarded Port: It uses the IP and a port from host; 
- Private Network: It uses a private address that It is not visible in the public network;
- Public Network: It uses a public IP from a public network, It can use DHCP.