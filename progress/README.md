# Progress Log

## Status: Planning / Hardware sourcing

---

## 2026-03-25 — Project started

### Decisions made

- **Architecture:** Router brain (laptop or mini PC) + M.2 5G modem + dedicated WiFi AP
- **OS:** Debian 12
- **Location:** Prague, Czech Republic (5G band n78)
- **SIM:** Already available

### Rejected alternatives

- GL.iNet Spitz AX (GL-X3000): viable but less control, harder to upgrade
- Phone USB tethering: requires buying a phone AND a mini PC
- Raspberry Pi + 5G HAT: limited HAT options, weaker CPU

### Under consideration

- **Laptop vs mini PC** — laptop preferred due to built-in battery (UPS) and pre-routed WWAN antenna cables inside chassis. Leading candidate: ThinkPad T480/T490.

### Next steps

- [ ] Decide: laptop (ThinkPad T480/T490) or mini PC (Lenovo M720q)
- [ ] Verify WWAN M.2 slot on the specific unit before buying
- [ ] Source router brain (Bazoš, Aukro)
- [ ] Source 5G modem (Quectel RM500Q-GL via AliExpress or local)
- [ ] Source WiFi AP (TP-Link EAP225 or similar)
- [ ] If laptop: check antenna cable count inside chassis
- [ ] If mini PC: source antennas + SMA pigtails
- [ ] Install Debian 12
- [ ] Configure TLP battery threshold (laptop only)
- [ ] Set up ModemManager + NetworkManager
- [ ] Configure nftables NAT
- [ ] Configure dnsmasq
- [ ] Connect WiFi AP
- [ ] Test with all ~10 devices
