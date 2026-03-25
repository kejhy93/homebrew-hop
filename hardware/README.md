# Hardware

## Decision: Router brain + M.2 5G modem + dedicated WiFi AP

Two viable options for the router brain: **used laptop** or **used mini PC**. See comparison below.

Chosen over:
- GL.iNet Spitz AX (GL-X3000): all-in-one but less hackable, harder to upgrade parts
- Phone USB tethering: requires buying both a phone and a mini PC

## Router Brain Comparison

| | Used Laptop | Used Mini PC |
|---|---|---|
| Built-in UPS | **Yes (battery)** | No |
| WWAN M.2 slot | Yes (business models) | Yes (most Tiny/Mini PCs) |
| Pre-routed antennas | **Yes (in chassis)** | No — external antennas needed |
| Idle power draw | ~8–15W | ~15–35W |
| Price used | ~2,000–3,000 CZK | ~2,000–3,500 CZK |
| Form factor | Larger | Compact |
| Battery longevity | Needs charge threshold set | N/A |

**Laptop is the better choice** due to the built-in UPS and pre-routed antenna cables. A business ThinkPad with a WWAN slot eliminates the need for external antennas entirely.

Battery health concern: keep the battery at 80% charge threshold using TLP — it will last years and still cover short outages.

---

## Components

### Router Brain (Laptop — preferred)

Target: used business laptop with a dedicated WWAN M.2 slot.

Good candidates:
- **Lenovo ThinkPad T480** — WWAN slot on most configs, excellent Linux/TLP support, widely available
- **Lenovo ThinkPad T490 / T14 Gen 1** — slightly newer, same story
- **Lenovo ThinkPad X280** — smaller form factor, also has WWAN slot
- **HP EliteBook 840 G5/G6** — also has WWAN slot, good Linux support

Key requirements:
- Dedicated WWAN M.2 slot (separate from NVMe — verify before buying)
- Pre-routed antenna cables in chassis (most business ThinkPads have 2–4)
- At least 1x Gigabit Ethernet (built-in)
- Working battery (even degraded — just needs to cover brief outages)

Where to buy: Bazoš.cz, Aukro.cz, local refurbishers.

Estimated price: **2,000–3,000 CZK**

---

### Router Brain (Mini PC — alternative)

Target: used x86 mini PC with at least one M.2 slot (for the 5G modem).

Good candidates:
- **Lenovo ThinkCentre M720q Tiny** — widely available used, has M.2 2242/2280, low power (~35W TDP), 4x USB, 2x Ethernet possible with dock or USB adapter
- **HP EliteDesk 800 G3 Mini** — similar form factor, also has M.2 slot
- **HP EliteDesk 800 G4 Mini** — slightly newer

Key requirements:
- M.2 slot (2242 or 2280, PCIe preferred — check if WWAN slot is available separately from NVMe)
- At least 1x Gigabit Ethernet (built-in)
- Low idle power draw
- 4+ GB RAM (overkill for a router, but used mini PCs come with 8–16 GB anyway)

Where to buy: Bazoš.cz, Aukro.cz, local PC shops selling refurbished hardware.

Estimated price: **2,000–3,500 CZK**

---

### 5G Modem

Target: M.2 form factor modem supporting Czech 5G bands.

Czech operator 5G bands (all three operators: O2 CZ, T-Mobile CZ, Vodafone CZ):
- Primary: **n78 (3.5 GHz)**
- Fallback LTE: B1, B3, B7, B20, B38

Good candidates:
- **Quectel RM500Q-GL** — global band support including n78, well-supported in Linux (ModemManager), widely used in DIY builds
- **Quectel RM502Q-AE** — similar, slightly newer
- **Fibocom FM350-GL** — also n78, less common in DIY context

Linux support: ModemManager + NetworkManager or mmcli handle these well.

M.2 key: M-key or B+M-key — verify the mini PC's WWAN slot type.

Also needed (if using mini PC):
- 4x SMA antenna pigtails (most modems ship without antennas)
- 4x external 5G antennas or window-mount panel antenna

If using a ThinkPad with pre-routed WWAN antenna cables: no external antennas needed — just connect the existing pigtails to the modem.

Where to buy: AliExpress (allow 3–4 weeks), or local electronics suppliers.

Estimated price: **2,500–3,500 CZK (modem) + 300–500 CZK (antennas)**

---

### WiFi Access Point

The mini PC's built-in WiFi (if any) is not suitable for AP use under Linux — driver support for AP mode is inconsistent. Use a dedicated AP instead.

Good candidates:
- **TP-Link EAP225** — dual-band WiFi 5, works standalone (no controller needed), cheap
- **TP-Link EAP670** — WiFi 6, pricier but future-proof
- Repurposed old router flashed with OpenWrt and set to AP mode (free if you have one)

Connect via Ethernet to the mini PC.

Estimated price: **800–1,500 CZK**

---

## Total Estimate

### Laptop path (preferred)

| Component | Low | High |
|-----------|-----|------|
| Used ThinkPad (T480/T490) | 2,000 CZK | 3,000 CZK |
| 5G modem (Quectel RM500Q-GL) | 2,500 CZK | 3,500 CZK |
| Antennas | 0 CZK | 200 CZK |
| WiFi AP | 800 CZK | 1,500 CZK |
| **Total** | **5,300 CZK** | **8,200 CZK** |

### Mini PC path (alternative)

| Component | Low | High |
|-----------|-----|------|
| Used mini PC | 2,000 CZK | 3,500 CZK |
| 5G modem | 2,500 CZK | 3,500 CZK |
| Antennas | 300 CZK | 500 CZK |
| WiFi AP | 800 CZK | 1,500 CZK |
| **Total** | **5,600 CZK** | **9,000 CZK** |

---

## Open Questions

- [ ] Choose between laptop and mini PC path
- [ ] Verify WWAN M.2 slot on specific unit before buying (check exact model variant, not just model line)
- [ ] Count antenna connectors inside the laptop chassis (typically 2 or 4 — RM500Q-GL needs 4, can work with 2)
- [ ] Confirm modem compatibility with SIM carrier (check APN settings)
- [ ] If laptop: configure TLP charge threshold (e.g. 40–80%) to preserve battery health
