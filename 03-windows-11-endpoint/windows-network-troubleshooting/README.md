# Lab 01 - Windows Network Troubleshooting

## Objective

Diagnose common Windows network connectivity problems using a structured troubleshooting methodology instead of trial-and-error fixes.

## Scenario

A user reports:

> "My computer is connected to the network, but I cannot access websites."

The objective is to determine whether the problem is related to:

- Local network configuration
- IP addressing
- Default gateway
- DNS resolution
- Routing
- Remote service reachability

## Environment

- Windows 10/11 workstation
- Local TCP/IP network
- Internet connectivity
- Command Prompt
- PowerShell

## Tools

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

## Troubleshooting Workflow

The investigation follows this order:

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

This helps isolate the faulty layer before making configuration changes.

## Scenario 1 - Baseline Network Verification

### Goal

Verify the current network configuration and establish a known-good baseline.

### Checks

1. Identify the active adapter.
2. Record the IPv4 address and subnet mask.
3. Identify the default gateway.
4. Identify the configured DNS servers.
5. Test the local TCP/IP stack.
6. Test connectivity to the gateway.
7. Test connectivity to an external IP address.
8. Test DNS name resolution.
9. Inspect the path to a remote host.

### Results

To be completed during the lab.

## Scenario 2 - DNS Failure

A workstation has IP connectivity but cannot resolve domain names.

The investigation will compare:

- `ping <IP address>`
- `ping <hostname>`
- `nslookup <hostname>`
- Configured DNS servers

### Results

To be completed during the lab.

## Scenario 3 - Incorrect IP or Gateway

A deliberately incorrect network configuration will be introduced.

The objective is to identify the configuration error using the troubleshooting workflow and restore connectivity.

### Results

To be completed during the lab.

## Scenario 4 - PowerShell Connectivity Testing

Use `Test-NetConnection` to verify:

- ICMP reachability
- TCP port reachability
- DNS resolution
- Route information

### Results

To be completed during the lab.

## Troubleshooting Analysis

For each scenario, document:

- Initial symptom
- Commands used
- Relevant output
- Root cause
- Corrective action
- Verification after the fix

## Screenshots

Screenshots will be added only when they provide useful evidence, such as:

- Network configuration
- Failed connectivity test
- DNS failure
- Corrected configuration
- Successful verification

Sensitive information will be removed or anonymized.

## What I Learned

To be completed after the lab.

Topics to reflect on:

- Difference between IP connectivity and DNS resolution
- Role of the default gateway
- Structured troubleshooting by network layer
- When to use `ping`, `tracert`, `nslookup`, and `Test-NetConnection`
- Importance of verifying the fix after troubleshooting
