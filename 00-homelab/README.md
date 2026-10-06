# 00 — Homelab

## Objective

Build a reusable virtual lab that supports the rest of the Systems Administration portfolio.

The homelab is designed to provide a realistic environment for Windows Server, Active Directory, endpoint administration, Linux, virtualization, backup, monitoring and later security labs.

## Current Hardware

Primary system:

- **MacBook Pro M1**
- ARM64 architecture

The Apple Silicon architecture introduces an important constraint:

- Windows 11 ARM and Linux ARM can run efficiently through virtualization.
- Windows Server 2025 is x64-only, so on the Mac it must be **emulated** rather than virtualized natively.

When an x64 PC is available, Windows Server workloads can be moved there for better performance. If only the Mac is available, UTM/QEMU can be used to emulate Windows Server 2025 x64.

## Virtualization Strategy

Planned approach on the Mac:

- **UTM / QEMU** for Windows Server 2025 x64 emulation
- ARM virtualization for Windows 11 ARM
- ARM virtualization for Linux

This allows the lab to remain usable even when only Apple Silicon hardware is available.

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
