<p align="right"><a href="README.md">🇬🇧 English</a> · <strong>🇮🇹 Italiano</strong></p>

# 00 — Homelab

## Obiettivo

Costruire un laboratorio virtuale riutilizzabile che supporti il resto del portfolio di Systems Administration.

L'homelab è pensato per offrire un ambiente realistico per Windows Server, Active Directory, endpoint administration, Linux, virtualizzazione, backup, monitoring e successivamente lab di sicurezza.

## Host attuale

L'homelab gira su un **PC Windows x64** usando **VMware Workstation Pro** come piattaforma di virtualizzazione.

## VM Windows Server attuale

La prima VM Windows Server 2025 è configurata con:

| Risorsa | Allocazione |
|---|---:|
| Memoria | 8 GB RAM |
| CPU | 4 processori virtuali |
| Disco virtuale | 40 GB |
| Hypervisor | VMware Workstation Pro |
| Guest OS | Windows Server 2025 x64 |

Questa VM sarà il punto di partenza per il lab Active Directory e ospiterà progressivamente servizi come AD DS, DNS, DHCP e Group Policy.

## Strategia di virtualizzazione

VMware Workstation Pro è l'hypervisor principale del lab attuale.

Verranno aggiunte altre VM quando richiesto dagli esercizi, incluso un client Windows e, successivamente, server aggiuntivi o sistemi Linux. L'allocazione delle risorse verrà adattata in base al numero di macchine eseguite contemporaneamente.

## Architettura pianificata

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

Sistemi Linux e di monitoring verranno aggiunti successivamente.

## Design Active Directory

Forest e domain pianificati:

```text
corp.mazzei.test
```

Naming convention:

- `DC01` — primo Domain Controller
- `FILE01` — file server
- `CLIENT01` — client Windows
- i sistemi futuri seguiranno la stessa convenzione basata sul ruolo

## Rete pianificata

Subnet iniziale:

```text
192.168.100.0/24
```

Esempio di piano di indirizzamento:

| Sistema | Ruolo | Indirizzo |
|---|---|---|
| DC01 | AD DS / DNS / DHCP | 192.168.100.10 |
| FILE01 | File Server | 192.168.100.20 |
| CLIENT01 | Domain Client | DHCP o indirizzo riservato |

I domain member useranno il servizio DNS interno Active Directory ospitato su `DC01`.

Esempio:

```text
FILE01
IP: 192.168.100.20
DNS: 192.168.100.10
```

I resolver DNS pubblici non vengono configurati direttamente sui domain member. La risoluzione DNS esterna verrà invece gestita tramite forwarder sul server DNS interno.

## Struttura Active Directory pianificata

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

I Security Group verranno usati per i permessi, mentre le Organizational Unit verranno usate per organizzazione logica e targeting delle Group Policy.

## Group Policy

Il lab userà GPO per esercitare l'amministrazione centralizzata.

Esempi:

- restrizioni utente
- drive mapping
- impostazioni Windows Firewall
- security policy
- configurazione endpoint

Comandi utili di troubleshooting:

```text
gpupdate /force
gpresult /r
```

## Evidenze pianificate per il portfolio

Con l'avanzamento dell'ambiente questa sezione verrà ampliata con:

- configurazione VM
- topologia di rete
- indirizzamento IP
- deployment AD DS e DNS
- struttura OU e gruppi
- GPO
- ruoli server
- domain join
- screenshot
- casi di troubleshooting
- strategia snapshot e recovery

## Stato

🚧 **In corso**

L'architettura del lab e la naming strategy sono definite. Deployment delle VM e configurazione dei servizi verranno documentati progressivamente con l'avanzamento del blocco Windows Server.
