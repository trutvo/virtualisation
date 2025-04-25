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

## Operation System

- **Type**: General-purpose
- **Description**: A general-purpose operating system that can run multiple applications and services. It provides a wide range of functionalities and is designed for various use cases.
- **Example**: Linux, Windows, macOS

### Kernel Space

- **Type**: Privileged
- **Description**: The part of the operating system that interacts directly with the hardware. It has full access to the system's resources and can execute any CPU instruction.
- **Example**: Linux kernel, Windows NT kernel

### User Space

- **Type**: Unprivileged
- **Description**: The memory area where user applications and processes run. It is isolated from the kernel space, providing a layer of security and stability.
- **Example**: User applications, libraries, and services that run on top of the kernel.

### Multitasking

The ability of an operating system to execute multiple tasks or processes simultaneously. It can be achieved through time-sharing or multiprocessing.

Types of multitasking include:

- **Preemptive Multitasking**: The operating system allocates CPU time to each process and can interrupt a running process to switch to another.
- **Example**: Linux, Windows NT

- **Cooperative Multitasking**: Each process is responsible for yielding control to other processes, allowing them to run. If a process does not yield, it can monopolize the CPU.
- **Example**: Older versions of Mac OS, Windows 3.x
