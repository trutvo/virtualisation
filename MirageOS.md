# MirageOS

MirageOS is a library operating system that constructs unikernels for secure, high-performance network applications. It is designed to run on various hypervisors and cloud platforms, providing a minimalistic and efficient environment for applications.

## Install Ocaml and Mirage

Install the OCaml package manager `opam`

    sudo apt install opam
    opam init
    eval $(opam env)
    opam update
    opam install mirage

## Create a Unikernel

Checkout the MIrage skeleton project

    git clone https://github.com/mirage/mirage-skeleton.git

Build hello example

    cd mirage-skeleton/tutorial/hello
    mirage configure -t xen
    make

Copy the generated unikernel to the Xen hypervisor

    scp hello.xen hello.xl root@<IP>:

## Run the Unikernel

Login to the Xen hypervisor

    ssh root@<IP>

Run the unikernel

    xl create hello.xl -c

## Build and run minipaf webserver

Build minipaf app

    cd mirage-skeleton/applications/http
    mirage configure -t xen --net=direct --dhcp=true
    make

Copy `.xen` and `.xl` files to the hypervisor.

Login to the Xen hypervisor

    ssh root@<IP>

Check and fix the network configuration in `minipaf.xl`

    # if your system uses openvswitch then either edit /etc/xen/xl.conf and set
    #     vif.default.script="vif-openvswitch"
    # or add "script=vif-openvswitch," before the "bridge=" below:
    vif = [ 'bridge=xenbr0' ]

Run the unikernel

    xl create minipaf.xl -c
