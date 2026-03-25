# Software Stack

## OS

**Debian 12 (Bookworm)** — stable, minimal, well-documented for router use cases.

Alternative: Ubuntu Server 24.04 LTS (also fine, slightly heavier).

Reasoning: full control over every component, no router-specific abstractions to work around, extensive community knowledge for networking on Debian.

## Components

### 5G Modem Management

**ModemManager** — handles the modem lifecycle (detect, unlock SIM, connect, reconnect on drop).

```
ModemManager
    └── mmcli (CLI tool for interacting with modems)
```

Works out of the box with Quectel RM500Q-GL on Debian 12.

### Network Management

Two options — pick one:

**Option A: NetworkManager** (recommended for getting started)
- Integrates with ModemManager automatically
- Handles failover, reconnect, DHCP on interfaces
- `nmcli` for scripting

**Option B: systemd-networkd + manual ModemManager integration**
- More lightweight, better for understanding what's happening
- More setup work

Start with NetworkManager; switch later if needed.

### Firewall

**nftables** — modern Linux firewall, replaces iptables.

Ruleset will handle:
- NAT/masquerade on the 5G interface (WWAN → LAN)
- Basic stateful firewall (drop unsolicited inbound)
- Optional: port forwarding

### DHCP + DNS

**dnsmasq** — handles both DHCP for LAN clients and local DNS caching/resolution.

Configuration:
- DHCP range on LAN interface
- Upstream DNS: use a privacy-respecting resolver (Cloudflare 1.1.1.1, Quad9 9.9.9.9, or run Unbound locally)
- Optional: local hostname resolution for devices

### Optional Add-ons (later)

| Feature | Tool |
|---------|------|
| Ad blocking | dnsmasq + blocklists, or Pi-hole |
| VPN server | WireGuard |
| Traffic monitoring | vnstat, ntopng |
| Remote access | WireGuard or Tailscale |
| IPv6 | ModemManager + radvd or dhcpcd |

## Boot / Service Management

systemd units for:
- ModemManager
- NetworkManager
- dnsmasq
- nftables

All start automatically on boot.

## Open Questions

- [ ] Does carrier require specific APN settings?
- [ ] IPv6 support on the SIM — check with carrier
- [ ] DNS strategy: upstream resolver vs local Unbound
