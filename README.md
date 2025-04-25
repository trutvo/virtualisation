# virtualisation

## Hypervisors

### Level 1 Hypervisor

- **Type**: Bare-metal
- **Description**: A hypervisor that runs directly on the host's hardware to control the hardware and manage guest operating systems.
- **Example**: VMware ESXi, Microsoft Hyper-V, [Xen](Xen.md)

### Level 2 Hypervisor

- **Type**: Hosted
- **Description**: A hypervisor that runs on a conventional operating system just as other computer programs do. It relies on the host OS to manage the hardware.
- **Example**: VMware Workstation, Oracle VirtualBox, Parallels Desktop

## Container Virtualisation

- **Type**: OS-level
- **Description**: A lightweight form of virtualisation that allows multiple isolated user-space instances (containers) to run on a single host OS. Containers share the host OS kernel but operate in isolated user spaces.
- **Example**: Docker, LXC (Linux Containers), OpenVZ

## Unikernel

- **Type**: Specialised VM
- **Description**: A unikernel is a specialized, single-address-space machine image constructed by using library operating systems. It is designed to run a single application and includes only the necessary components for that application.
- **Example**: [MirageOS](MirageOS.md), IncludeOS, OSv
