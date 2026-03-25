# Homebrew 5G Router

Replacing a weak commercial router with a custom-built Linux box using a 5G uplink.

## Goals

- Use an existing 5G SIM as the WAN uplink
- Handle ~10 devices (mostly WiFi, some Ethernet)
- Full Linux control — no locked-down firmware
- Budget: ~5,000–8,000 CZK

## Architecture

```
5G network (n78 / 3.5 GHz)
        |
  [M.2 5G modem]
        |
  [Mini PC - router brain]
  - nftables firewall
  - dnsmasq (DHCP + DNS)
  - ModemManager (5G link)
        |
   +----+----+
   |         |
[Ethernet] [WiFi AP]
 devices    devices
```

## Hardware (decided)

See [docs/hardware.md](docs/hardware.md)

## Progress

See [docs/progress.md](docs/progress.md)

## Docs

- [Hardware research & decisions](docs/hardware.md)
- [Software stack](docs/software.md)
- [Progress log](docs/progress.md)
# homebrew-hop
