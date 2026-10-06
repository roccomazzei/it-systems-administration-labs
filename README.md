# IT Systems Administration Labs

Hands-on portfolio focused on **System Administration, IT Infrastructure, Microsoft environments, Networking and Cloud**, with a progressive extension toward **Cybersecurity and Security Operations**.

The repository documents practical labs, troubleshooting workflows, configurations and lessons learned. The current learning roadmap is primarily based on Dan Mill's **Ultimate System Administrator Course**, while the projects here are designed as independent hands-on exercises rather than copies of course lessons.

## Learning Strategy

The goal is not to collect certificates. Each topic follows this workflow:

**Learn → Build → Break → Troubleshoot → Fix → Document**

A skill is considered portfolio-ready only after it has been used in a practical lab.

## Current Progress

| Area | Status |
|---|---|
| Homelab & Lab Architecture | 🚧 In Progress |
| Networking Foundations | ✅ Foundation completed |
| Windows Server & Active Directory | ⏭️ Next major block |
| Windows 11 / Endpoint Administration | 🚧 Troubleshooting lab started |
| PowerShell & Automation | ⏳ Planned |
| Linux Administration | 🟡 Previous foundation completed; deeper admin lab planned |
| Microsoft 365 & Entra ID | ⏳ Planned |
| Virtualization | ⏳ Planned |
| Backup & Disaster Recovery | ⏳ Planned |
| Azure | ⏳ Planned |
| Monitoring, Hardening & Security | ⏳ Planned |

## Repository Roadmap

### 00 — Homelab

Build the reusable environment for the rest of the portfolio.

Planned work:

- Virtualized lab architecture
- Windows Server and Windows 11 VMs
- Linux server VM
- Network planning
- Snapshots and recovery points
- Documentation of the lab topology

### 01 — Networking

Completed foundations include:

- IPv4 addressing and subnetting
- VLANs
- Access ports
- 802.1Q trunking
- Router-on-a-stick
- Inter-VLAN routing
- ARP and ICMP troubleshooting
- Cisco IOS verification commands

Projects:

- [Cisco Packet Tracer Networking Capstone](01-networking/cisco-packet-tracer-capstone/) — ✅ Completed

### 02 — Windows Server & Active Directory

This will be the main enterprise administration block.

Planned labs:

- Windows Server 2025 deployment
- Static IP and server baseline configuration
- Active Directory Domain Services
- DNS installation and records
- Users, groups and Organizational Units
- Windows client domain join
- Group Policy
- DHCP
- File services and permissions
- FSMO roles
- Additional domain controller
- Account lockout troubleshooting
- Event Viewer and auditing
- Remote Desktop Services
- IIS basics
- Administrative PowerShell

### 03 — Windows 11 & Endpoint Administration

Planned and active topics:

- [Windows Network Troubleshooting](03-windows-11-endpoint/windows-network-troubleshooting/) — 🚧 In Progress
- Local vs domain accounts
- Device Manager and services
- DNS/IP troubleshooting
- DISM and SFC
- Disk management
- Windows Update
- Defender and Firewall
- BitLocker
- UAC
- Domain join and endpoint administration

### 04 — PowerShell & Automation

Planned hands-on work:

- Cmdlet discovery and help
- Files, processes and services
- Network diagnostics
- Event log queries
- CSV import/export
- Active Directory administration
- Bulk user creation
- Health checks
- Error handling and logging
- Reusable administration scripts

Portfolio target: **PowerShell Admin Toolkit**.

### 05 — Linux Administration

Previous Linux/network-security training has already been completed.

The new goal is to strengthen the areas most relevant to real system administration:

- Users and groups
- Permissions and sudo
- Package management
- Processes and services
- systemd
- journalctl and logs
- SSH administration
- Networking and DNS
- Filesystems and mounts
- Bash automation
- Troubleshooting

Portfolio target: **Linux Administration & Troubleshooting Lab**.

### 06 — Microsoft 365 & Entra ID

Planned topics:

- Microsoft 365 administration
- Users and licenses
- Exchange Online
- Teams
- SharePoint
- Microsoft Entra ID
- MFA
- Conditional Access
- Identity administration
- Cloud vs on-premises identity

### 07 — Virtualization

Planned topics:

- Hyper-V
- VMware / ESXi
- Virtual switches
- VM networking
- Storage
- Snapshots
- Resource allocation
- Troubleshooting virtual machines

### 08 — Backup & Disaster Recovery

Planned topics:

- Backup strategy
- Recovery objectives
- File and VM backup
- Restore testing
- Disaster recovery planning
- Backup validation
- Infrastructure recovery scenarios

Where useful, Veeam will be used for additional practical backup exercises.

### 09 — Azure

Planned topics:

- Azure fundamentals for administrators
- Virtual machines
- Virtual networking
- Identity integration
- Storage
- Backup
- Monitoring
- Basic cloud security

### 10 — Monitoring, Hardening & Security

Planned topics:

- Event Viewer
- Performance Monitor
- Infrastructure monitoring
- Windows and Linux hardening
- Least privilege
- Audit logging
- Security baselines
- Troubleshooting methodology

This area will later connect directly to the cybersecurity portfolio through:

- Sysmon
- Wazuh / SIEM
- Alert triage
- Incident investigation
- MITRE ATT&CK
- SOC-style reporting

## Repository Structure

```text
it-systems-administration-labs/
│
├── 00-homelab/
├── 01-networking/
├── 02-windows-server-active-directory/
├── 03-windows-11-endpoint/
├── 04-powershell-automation/
├── 05-linux-administration/
├── 06-microsoft-365-entra/
├── 07-virtualization/
├── 08-backup-disaster-recovery/
├── 09-azure/
└── 10-monitoring-security-hardening/
```

## Current Focus

The networking foundation project is complete.

The **homelab architecture is now documented and in progress**. The next major objective is to deploy the Windows Server environment and begin **Windows Server 2025 + Active Directory**, while completing the existing Windows troubleshooting lab.

The long-term objective is to become employable in **Junior System Administration / Infrastructure** roles while building a strong technical foundation for a future **SOC Analyst / Security Operations** path.
