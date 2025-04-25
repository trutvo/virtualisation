# Xen Server

XenServer is a free, open-source virtualization platform based on the Xen hypervisor. It allows you to create and manage virtual machines (VMs) on a physical server. XenServer is widely used in enterprise environments for server virtualization, cloud computing, and data center management.

## Setup a XenServer

Download the XenServer ISO and install it on a server.

https://www.xenserver.com/downloads

Install it on a PC.

You can login via ssh:

    ssh root@<IP>

### Setup a Image Repository

Login to the XenServer via ssh and run the following commands:

    mkdir -p /var/opt/ISO_IMAGES
    cd /var/opt/ISO_IMAGES
    wget http://ftp.stw-bonn.de/ubuntu-cd/24.04/ubuntu-24.04.2-live-server-amd64.iso
    cd
    export SR_UUID=$(xe sr-create name-label=LocalISO type=iso device-config:location=/var/opt/ISO_IMAGES device-config:legacy_mode=true content-type=iso)
    xe sr-scan uuid=$SR_UUID

### Setup a VM

Create a VM

    export VM_UUID=$(xe vm-install template="Ubuntu Noble Numbat 24.04" new-name-label="ubuntu-vm")
    
Add network

    xe network-list 

Select the Pool-wide network associated with eth0

    export NW_UUID=$(xe network-list bridge=xenbr0 --minimal)
    xe network-list bridge=xenbr0
    xe vif-create network-uuid=$NW_UUID vm-uuid=$VM_UUID device=0

Attach storage

    xe sr-list type=lvm
    xe vdi-create name-label="UbuntuVDI" sr-uuid=$SR_UUID virtual-size=40GiB
    xe vbd-create vm-uuid=$VM_UUID vdi-uuid=$VDI_UUID device=1

Attach CD

    xe vm-cd-add vm=ubuntu-vm cd-name="ubuntu-24.04.2-live-server-amd64.iso" device=3
    xe vm-param-set uuid=$VM_UUID HVM-boot-policy="CD"

Start the VM

    xe vm-start uuid=$VM_UUID

Futher commands

    xe vm-list name-label=ubuntu-vm params=dom-id
    xe vm-shutdown force=true uuid=$VM_UUID
    xe vm-uninstall uuid=$VM_UUID
    xe vm-list params=all
    xe cd-list
    xe template-list
    xe vif-list vm-uuid=$VM_UUID


Deactivate secure boot

    varstore-sb-state $VM_UUID setup

Console

    xl console <N>

