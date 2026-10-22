<p align="right"><a href="README.md">🇬🇧 English</a> · <strong>🇮🇹 Italiano</strong></p>

# Lab 01 - Windows Network Troubleshooting

## Obiettivo

Diagnosticare problemi comuni di connettività di rete in Windows usando una metodologia di troubleshooting strutturata invece di procedere per tentativi.

## Scenario

Un utente segnala:

> "Il computer è connesso alla rete, ma non riesco ad accedere ai siti web."

L'obiettivo è determinare se il problema riguarda:

- configurazione di rete locale
- indirizzamento IP
- default gateway
- risoluzione DNS
- routing
- raggiungibilità del servizio remoto

## Ambiente

- workstation Windows 10/11
- rete TCP/IP locale
- connettività Internet
- Command Prompt
- PowerShell

## Strumenti

### Command Prompt

- `ipconfig /all`
- `ping`
- `tracert`
- `nslookup`
- `arp -a`
- `route print`

### PowerShell

- `Test-NetConnection`
- `Get-NetIPConfiguration`
- `Get-DnsClientServerAddress`

## Workflow di troubleshooting

L'investigation segue questo ordine:

```text
Network adapter
      ↓
IP configuration
      ↓
Local TCP/IP stack
      ↓
Default gateway
      ↓
Remote IP connectivity
      ↓
DNS resolution
      ↓
Route/path analysis
      ↓
Application or service
```

Questo approccio permette di isolare il livello guasto prima di modificare la configurazione.

## Scenario 1 - Verifica baseline

### Obiettivo

Verificare la configurazione attuale e definire una baseline funzionante.

### Controlli

1. identificare l'adapter attivo
2. registrare indirizzo IPv4 e subnet mask
3. identificare il default gateway
4. identificare i DNS configurati
5. testare lo stack TCP/IP locale
6. testare la connettività verso il gateway
7. testare la connettività verso un IP esterno
8. testare la risoluzione DNS
9. analizzare il percorso verso un host remoto

### Risultati

Da completare durante il lab.

## Scenario 2 - Errore DNS

La workstation ha connettività IP ma non riesce a risolvere nomi di dominio.

L'investigation confronterà:

- `ping <IP address>`
- `ping <hostname>`
- `nslookup <hostname>`
- server DNS configurati

### Risultati

Da completare durante il lab.

## Scenario 3 - IP o gateway errato

Verrà introdotta intenzionalmente una configurazione di rete errata.

L'obiettivo è identificare l'errore seguendo il workflow di troubleshooting e ripristinare la connettività.

### Risultati

Da completare durante il lab.

## Scenario 4 - Test con PowerShell

Usare `Test-NetConnection` per verificare:

- raggiungibilità ICMP
- raggiungibilità porta TCP
- risoluzione DNS
- informazioni sul percorso

### Risultati

Da completare durante il lab.

## Analisi del troubleshooting

Per ogni scenario documentare:

- sintomo iniziale
- comandi usati
- output rilevante
- root cause
- azione correttiva
- verifica dopo il fix

## Screenshot

Gli screenshot verranno aggiunti solo quando forniscono evidenze utili, ad esempio:

- configurazione di rete
- test di connettività fallito
- errore DNS
- configurazione corretta
- verifica riuscita

Le informazioni sensibili verranno rimosse o anonimizzate.

## Cosa ho imparato

Da completare al termine del lab.

Punti su cui riflettere:

- differenza tra connettività IP e risoluzione DNS
- ruolo del default gateway
- troubleshooting strutturato per livello di rete
- quando usare `ping`, `tracert`, `nslookup` e `Test-NetConnection`
- importanza della verifica dopo il fix
