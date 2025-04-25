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

Build one example

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
