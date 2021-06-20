# Vagrant

## What is It?

This guy manage and automatize a lot of specs related to a Hypervisor (VMware, Virtualbox) using a simple file called Vagranfile.

Important check the compatibility between Vegrant and the Hypervisor.

## Hypervisor

Hypervisors are softwares that execute the interactions between the virtual OS and the current OS on the machine. Generally It is responsable by create, manage communication and resources.

There are 2 types:

Type 1: It is called "bare metal", because It is executed directly in the host hardware. Examples: Hyper-V and vphere.

Type 2: It is executed above some OS, examples: VirtualBox and VMware.

## Commands

All Commands start with `vagrant`.

- `init hashicorp/precise64` - Start a vagrant file environment;
- `up` - Create the virtual machine and configure it;
- `halt` - stop the machine;
- `status` - Check status;
- `ssh` - Connect thought ssh;
- `ssh-config` - Show ssh configs;
- `reload` - shutdown and restart;
- `provision` - call the scripts to config the machine.
- `box prune,remove,list...` - manage the boxes depending of what param is being passed.
- `vagrant global-status --prune (doesnt show outdated)`  - show all the boxes in the computer

Off-topic:

- `ssh -p 2222 vagrant@127.0.0.1` - Tradicional SSH;

## VagrantFile

All the virtual machine configurations come here.

## Network

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

It is also called Configuration Management, because It is generally used to define ad keep the correct configuration in the environment.

The configuration file is called manifest. It is necessary the puppet client in the guests and a puppet server in the hosts.

#### Ansible

It is a tool for provisioning, used for prepare the environment for a task.

The configuration file, the Play Books are converted to python. So, the machine that execute them need to have the python installed.

Each configuration will have a different playbook and It will be necessary execute again.

Ansible pushes the "script configuration" from the host to the guest (VM);

#### Puppet VS Ansible

Puppet is for configuration management;
Ansible is for provisioning;

In others words, puppet is generally used for validate the configuration and make sure that all the specifications are being followed (Self-healing) and Ansible for install and prepare the environment.

## Multi-Machine

- It is possible to configure in the same Vagrantfile more than one machine.

## Containerization(Docker) VS Virtualization(Vagrant)

The main point is about flexibility, size and speed. Docker is better in all this aspecsts.

Docker reaches this because all the containers are managed and uses resources of a common linux machine, so the default libraries and others resources are shared, this decreases the size of each machine and increases the deploy speed.
In fact each container is not a tradicional OS virtualization, It works different.

In Windows and Mac is kind of different, docker uses a hypervisor and creates a linux to make up the docker environment, even so, It works well.
