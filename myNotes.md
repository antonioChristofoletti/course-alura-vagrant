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
- `reload` - shutdown and restart;
- `provision` - call the scripts to config the machine.

Off-topic:

- `ssh -p 2222 vagrant@127.0.0.1` - Tradicional SSH;


## VagrantFile

All the virtual machine configurations come here.

There are 3 network types: 

- Forwarded Port: It uses the IP and a port from host; 
- Private Network: It uses a private address that It is not visible in the public network;
- Public Network: It uses a public IP from a public network, It can use DHCP.

## SSH

- It uses public/private key to connect;
- `vagrant ssh` uses localhost;
- SSH uses private/public hash keys. Useful commands:
    - `ssh-keygen -t rsa` - Creates a pair of public and private keys;
    - `ssh-keyscan virtual-machine-ip` - Check a booked key on linux;
    - `ssh-keygen -R virtual-machine-ip` - Delete a booked key on linux;
    - `ssh -i path_private_key_file your_user@virtual-machine-ip`: SSH command line connection using a has key;
    - Registring a new key on virtual-machine:
        1 - Create the pair: `ssh-keygen -t rsa`;
        2 - Then just put in the this folder: `cat id_bionic.pub >> .ssh/authorized_keys`;
        3 - Use the private key in order to connect in this machine.

## Provisioning

- Vagrant don't provide configuration of machines, however, It allows integration with others tools.

#### Shell

It allows to create shell scripts to configure the machine right after be made up.

#### Puppet

It is possible use and integrate with Puppet. 

Puppet is a open-source utility software that can be used to define, manage and automatize machines configuration, It has a friendly and clean syntax, making this process and less painful and increasing the idea of IaC (Infrastructure as Code).

#### Ansible

The Ansible idea is the same of Puppet, but there are 2 main differences:

1 - Ansible pushes the "script configuration" from the host to the guest (VM);
2 - Ansible does not need a client in order to be executed, just python and most part of the linux distributions already have python pre-installed

## Multi-Machine

- It is possible to configure in the same Vagrantfile more than one machine.