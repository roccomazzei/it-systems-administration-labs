<p align="right"><a href="README.md">🇬🇧 English</a> · <strong>🇮🇹 Italiano</strong></p>

# Networking Foundation Capstone - Cisco Packet Tracer

## Obiettivo

Progettare, configurare e verificare una piccola rete aziendale in Cisco Packet Tracer usando i concetti di networking affrontati durante il percorso.

Il progetto consolida i fondamenti di rete prima di passare ai lab Windows Server, Active Directory e amministrazione infrastrutturale.

## Scenario

Una piccola azienda ha tre reparti che devono essere separati logicamente mantenendo la possibilità di comunicare tramite inter-VLAN routing.

La rete prevede:

- VLAN separate per IT, Administration e Sales
- subnetting IPv4 con reti /27
- access port per gli endpoint
- trunking 802.1Q
- router-on-a-stick
- default gateway per ogni VLAN
- verifica della connettività

## Tecnologie

- Cisco Packet Tracer
- Cisco IOS
- IPv4
- Subnetting
- VLAN
- 802.1Q Trunking
- Router-on-a-stick
- Inter-VLAN Routing
- ICMP
- ARP

## Piano di indirizzamento

| VLAN | Reparto | Rete | Gateway |
|---|---|---|---|
| 10 | IT | 192.168.50.0/27 | 192.168.50.1 |
| 20 | ADMIN | 192.168.50.32/27 | 192.168.50.33 |
| 30 | SALES | 192.168.50.64/27 | 192.168.50.65 |

Subnet mask: `255.255.255.224`

## Topologia

![Topologia Packet Tracer](screenshots/topology.png)

```text
                    Router
                      |
                    TRUNK
                      |
                    Switch
            __________|__________
           |          |          |
        VLAN 10    VLAN 20    VLAN 30
           IT       ADMIN       SALES
         PC0/PC1    PC2/PC3    PC4/PC5
```

## File della repository

```text
cisco-packet-tracer-capstone/
│
├── README.md
├── README_IT.md
├── packet-tracer/
│   └── small-business-network.pkt
├── configs/
│   ├── Router-running-config.txt
│   └── Switch-running-config.txt
└── screenshots/
    ├── topology.png
    └── ping.png
```

## Implementazione

- [x] definizione requisiti di rete
- [x] piano di indirizzamento IP
- [x] costruzione topologia Packet Tracer
- [x] configurazione VLAN
- [x] configurazione access port
- [x] configurazione trunk
- [x] configurazione router-on-a-stick
- [x] configurazione inter-VLAN routing
- [x] configurazione IP e default gateway degli endpoint
- [x] verifica connettività tra VLAN
- [x] esportazione configurazioni router e switch
- [x] screenshot
- [x] file Packet Tracer
- [x] esercizio di troubleshooting
- [x] documentazione finale

## Comandi di verifica

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show running-config
ping
```

## Verifica

![Ping inter-VLAN riuscito](screenshots/ping.png)

La connettività inter-VLAN è stata testata con successo da un host nella subnet `192.168.50.0/27` verso host nelle subnet `192.168.50.32/27` e `192.168.50.64/27`, con 0% packet loss.

La verifica finale ha confermato che:

- i dispositivi nella stessa VLAN comunicano
- dispositivi in VLAN diverse comunicano tramite router
- ogni PC usa il default gateway corretto
- lo switch ha le corrette assegnazioni delle access port per VLAN 10, 20 e 30
- il link switch-router opera come trunk 802.1Q
- il router ha tre subinterface attive per le tre reti /27

## Esercizio di troubleshooting

È stato introdotto intenzionalmente un errore Layer 2 sulla porta di una workstation SALES.

### Sintomo

La workstation non riusciva più a raggiungere il default gateway né host al di fuori della VLAN prevista.

### Errore introdotto

L'access port collegata alla workstation SALES è stata assegnata intenzionalmente alla VLAN 20 invece della VLAN 30.

### Investigation

Il troubleshooting ha seguito un approccio per livelli:

1. test della connettività dalla workstation interessata
2. verifica che un altro host in VLAN 30 raggiungesse il gateway
3. verifica comunicazione same-VLAN
4. controllo membership VLAN con:

```text
show vlan brief
```

Questo ha isolato il problema all'assegnazione VLAN dell'access port, escludendo router e trunk.

### Root cause

La porta switch della workstation era assegnata alla VLAN sbagliata.

L'host manteneva IP e default gateway appartenenti alla subnet SALES `192.168.50.64/27`, ma il traffico Layer 2 veniva inserito nella VLAN 20.

### Correzione

La porta switch interessata è stata riassegnata alla VLAN 30.

Dopo il ripristino della corretta membership VLAN, la connettività è stata nuovamente verificata. Packet Tracer ha richiesto brevemente traffico/tempo aggiuntivo prima di ripristinare la raggiungibilità del gateway; successivamente sia la comunicazione same-VLAN sia quella inter-VLAN hanno funzionato.

### Verifica finale

- PC4 -> PC5: riuscito
- PC5 -> gateway VLAN 30: riuscito
- PC4 -> gateway VLAN 30: riuscito dopo il ripristino
- comunicazione inter-VLAN: riuscita

## Cosa ho imparato

- una VLAN separa un broadcast domain Layer 2 anche su uno stesso switch fisico
- le access port devono appartenere alla VLAN coerente con la subnet IP dell'host
- un trunk 802.1Q trasporta più VLAN su un singolo link fisico
- router-on-a-stick usa una sola interfaccia fisica con più subinterface logiche
- l'interfaccia fisica del router non necessita di IP quando l'indirizzamento Layer 3 è sulle subinterface
- ogni subinterface agisce come default gateway della propria VLAN
- `show vlan brief`, `show interfaces trunk`, `show ip interface brief` e `show ip route` aiutano a isolare errori Layer 2 e Layer 3
- testare la connettività per fasi aiuta a capire se il problema è sull'host, nella VLAN, sul trunk o sul router
- dopo una modifica correttiva bisogna sempre verificare il risultato
