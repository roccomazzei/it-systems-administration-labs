# 00 — Homelab

## Objective

Build a reusable virtual lab that supports the rest of the Systems Administration portfolio.

The homelab is designed to provide a realistic environment for Windows Server, Active Directory, endpoint administration, Linux, virtualization, backup, monitoring and later security labs.

## Current Lab Host

The homelab is currently running on a **Windows x64 PC** using **VMware Workstation Pro** as the virtualization platform.

## Current Windows Server VM

The first Windows Server 2025 virtual machine is configured with:

| Resource | Allocation |
|---|---:|
| Memory | 8 GB RAM |
| CPU | 4 virtual processors |
| Virtual disk | 40 GB |
| Hypervisor | VMware Workstation Pro |
| Guest OS | Windows Server 2025 x64 |

This VM will be used as the starting point for the Active Directory lab and will progressively host services such as AD DS, DNS, DHCP and Group Policy.

## Virtualization Strategy

VMware Workstation Pro is the primary hypervisor for the current lab.

Additional virtual machines will be added as required by the exercises, including a Windows client and, later, additional servers or Linux systems. Resource allocation will be adjusted based on the number of machines running simultaneously.

## Planned Lab Architecture

```text
                         Homelab
                            │
                    Virtual Network
                            │
           ┌────────────────┼────────────────┐
           │                │                │
         DC01             FILE01          CLIENT01
   Windows Server 2025  Windows Server    Windows 11
           │                │                │
        AD DS            File Server      Domain Client
        DNS              SMB / NTFS
        DHCP
        GPO
```

Additional Linux and monitoring systems will be added later.

## Active Directory Design

Planned forest and domain:

```text
corp.mazzei.test
```

Planned naming convention:

- `DC01` — first Domain Controller
- `FILE01` — file server
- `CLIENT01` — Windows client
- Future systems will continue the same role-based naming scheme.

## Planned Network

Initial lab subnet:

```text
192.168.100.0/24
```

Example addressing plan:

| System | Role | Address |
|---|---|---|
| DC01 | AD DS / DNS / DHCP | 192.168.100.10 |
| FILE01 | File Server | 192.168.100.20 |
| CLIENT01 | Domain Client | DHCP or reserved address |

Domain members will use the internal Active Directory DNS service hosted on `DC01`.

Example:

```text
FILE01
IP: 192.168.100.20
DNS: 192.168.100.10
```

Public DNS resolvers are not configured directly on domain members. External DNS resolution can instead be handled through DNS forwarders on the internal DNS server.

## Planned Active Directory Structure

Example organizational structure:

```text
corp.mazzei.test
│
├── OU=IT
│   ├── Users
│   └── Computers
│
├── OU=Administration
│   ├── Users
│   └── Computers
│
└── OU=Servers
    ├── DC01
    └── FILE01
```

Security Groups will be used for permissions, while Organizational Units will be used for logical organization and Group Policy targeting.

## Group Policy

The lab will use GPOs to practise centralized administration.

Examples include:

- User restrictions
- Drive mapping
- Windows Firewall settings
- Security policies
- Endpoint configuration

Useful troubleshooting commands will include:

```text
gpupdate /force
gpresult /r
```

## Planned Portfolio Evidence

As the environment is built, this section will be expanded with:

- VM configuration
- Network topology
- IP addressing
- AD DS and DNS deployment
- OU and group structure
- GPOs
- Server roles
- Domain join
- Screenshots
- Troubleshooting cases
- Recovery and snapshot strategy

## Status

🚧 **In Progress**

The lab architecture and naming strategy are defined. VM deployment and service configuration will be documented progressively as the Windows Server course blocks are completed.
