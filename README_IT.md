<p align="right"><a href="README.md">🇬🇧 English</a> · <strong>🇮🇹 Italiano</strong></p>

# IT Systems Administration Labs

Portfolio pratico focalizzato su **System Administration, infrastruttura IT, ambienti Microsoft, Networking e Cloud**, con una progressiva estensione verso **Cybersecurity e Security Operations**.

La repository documenta lab pratici, workflow di troubleshooting, configurazioni e lezioni apprese. La roadmap di studio attuale è basata principalmente sul corso **Ultimate System Administrator Course** di Dan Mill, mentre i progetti presenti qui sono esercizi pratici indipendenti e non copie delle lezioni del corso.

## Strategia di apprendimento

L'obiettivo non è collezionare certificati. Ogni argomento segue questo workflow:

**Learn → Build → Break → Troubleshoot → Fix → Document**

Una competenza viene considerata pronta per il portfolio solo dopo essere stata utilizzata in un lab pratico.

## Progresso attuale

| Area | Stato |
|---|---|
| Homelab & Lab Architecture | 🚧 In corso |
| Networking Foundations | ✅ Fondamenti completati |
| Windows Server & Active Directory | ⏭️ Prossimo blocco principale |
| Windows 11 / Endpoint Administration | 🚧 Lab di troubleshooting iniziato |
| PowerShell & Automation | ⏳ Pianificato |
| Linux Administration | 🟡 Fondamenti precedenti completati; lab admin avanzato pianificato |
| Microsoft 365 & Entra ID | ⏳ Pianificato |
| Virtualization | ⏳ Pianificato |
| Backup & Disaster Recovery | ⏳ Pianificato |
| Azure | ⏳ Pianificato |
| Monitoring, Hardening & Security | ⏳ Pianificato |

## Roadmap della repository

### 00 — Homelab

Costruzione dell'ambiente riutilizzabile per il resto del portfolio.

Attività pianificate:

- architettura virtualizzata del lab
- VM Windows Server e Windows 11
- VM Linux server
- pianificazione di rete
- snapshot e punti di ripristino
- documentazione della topologia

➡️ **[Apri Homelab](00-homelab/README_IT.md)**

### 01 — Networking

Fondamenti completati:

- indirizzamento IPv4 e subnetting
- VLAN
- access port
- trunking 802.1Q
- router-on-a-stick
- inter-VLAN routing
- troubleshooting ARP e ICMP
- comandi di verifica Cisco IOS

Progetti:

- [Cisco Packet Tracer Networking Capstone](01-networking/cisco-packet-tracer-capstone/README_IT.md) — ✅ Completato

### 02 — Windows Server & Active Directory

Questo sarà il principale blocco di amministrazione enterprise.

Lab pianificati:

- deployment Windows Server 2025
- configurazione IP statico e baseline server
- Active Directory Domain Services
- installazione DNS e record
- utenti, gruppi e Organizational Units
- domain join di un client Windows
- Group Policy
- DHCP
- file services e permessi
- FSMO roles
- controller di dominio aggiuntivo
- troubleshooting account lockout
- Event Viewer e auditing
- Remote Desktop Services
- basi IIS
- PowerShell amministrativo

➡️ **[Apri Windows Server & Active Directory](02-windows-server-active-directory/README_IT.md)**

### 03 — Windows 11 & Endpoint Administration

Argomenti pianificati e attivi:

- [Windows Network Troubleshooting](03-windows-11-endpoint/windows-network-troubleshooting/README_IT.md) — 🚧 In corso
- account locali, Microsoft e di dominio
- Device Manager e servizi
- troubleshooting DNS/IP
- DISM e SFC
- gestione disco
- Windows Update
- Defender e Firewall
- BitLocker
- UAC
- domain join e amministrazione endpoint

### 04 — PowerShell & Automation

Attività pratiche pianificate:

- scoperta cmdlet e help
- file, processi e servizi
- diagnostica di rete
- query dei log eventi
- import/export CSV
- amministrazione Active Directory
- creazione bulk di utenti
- health check
- error handling e logging
- script amministrativi riutilizzabili

Target portfolio: **PowerShell Admin Toolkit**.

### 05 — Linux Administration

È già stata completata una base Linux/network-security.

Il nuovo obiettivo è rafforzare le aree più utili nella vera system administration:

- utenti e gruppi
- permessi e sudo
- package management
- processi e servizi
- systemd
- journalctl e log
- amministrazione SSH
- networking e DNS
- filesystem e mount
- automazione Bash
- troubleshooting

Target portfolio: **Linux Administration & Troubleshooting Lab**.

### 06 — Microsoft 365 & Entra ID

Argomenti pianificati:

- Microsoft 365 administration
- utenti e licenze
- Exchange Online
- Teams
- SharePoint
- Microsoft Entra ID
- MFA
- Conditional Access
- identity administration
- identità cloud vs on-premises

### 07 — Virtualization

Argomenti pianificati:

- Hyper-V
- VMware / ESXi
- virtual switch
- networking VM
- storage
- snapshot
- allocazione risorse
- troubleshooting VM

### 08 — Backup & Disaster Recovery

Argomenti pianificati:

- strategia di backup
- recovery objectives
- backup file e VM
- test di restore
- disaster recovery planning
- validazione dei backup
- scenari di ripristino infrastrutturale

Dove utile, verrà usato Veeam per esercizi pratici aggiuntivi di backup e restore.

### 09 — Azure

Argomenti pianificati:

- fondamenti Azure per amministratori
- virtual machine
- virtual networking
- integrazione identità
- storage
- backup
- monitoring
- sicurezza cloud di base

### 10 — Monitoring, Hardening & Security

Argomenti pianificati:

- Event Viewer
- Performance Monitor
- infrastructure monitoring
- hardening Windows e Linux
- least privilege
- audit logging
- security baseline
- metodologia di troubleshooting

Questa area verrà poi collegata direttamente al portfolio cybersecurity tramite:

- Sysmon
- Wazuh / SIEM
- alert triage
- incident investigation
- MITRE ATT&CK
- SOC-style reporting

## Struttura della repository

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

## Focus attuale

Il progetto di networking foundation è completato.

L'**architettura homelab è documentata e in corso**. Il prossimo obiettivo principale è distribuire l'ambiente Windows Server e iniziare **Windows Server 2025 + Active Directory**, completando nel frattempo il lab di troubleshooting Windows già avviato.

L'obiettivo a lungo termine è diventare competitivo per ruoli **Junior System Administration / Infrastructure**, mantenendo una solida base tecnica per il percorso **SOC Analyst / Security Operations**.
