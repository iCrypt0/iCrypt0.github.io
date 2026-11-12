# icrypt0.github.io
 
Portfolio and lab logbook for Chandler Kirk. IT student at Kennesaw State, A.S. in Cybersecurity from Lanier Tech, building toward SOC analyst and IT support roles in Metro Atlanta.
 
**Live site:** https://icrypt0.github.io
 
## What's here
 
| Page | Purpose |
|---|---|
| `index.html` | Home. About, skills, live network topology, and an overview of the lab. |
| `logbook.html` | Evidence. Screenshots and write-ups from the lab, organized by topic. |
 
Everything is hand-written HTML, CSS, and vanilla JavaScript. No framework, no build step. Hosted on GitHub Pages.
 
## The lab
 
A self-hosted SOC environment running on a single Beelink mini PC under Proxmox VE, segmented into five 802.1Q VLANs on a managed switch using a router-on-a-stick design.
 
| VLAN | Name | Role |
|---|---|---|
| 10 | Trusted | Wired and wireless clients |
| 20 | Honeypot | Cowrie SSH honeypot, exposed to the internet |
| 30 | Management | Proxmox and Wazuh |
| 40 | IoT | Smart home devices, isolated from everything else |
| 50 | OSINT | Isolated research segment with VPN and Tor, no path to internal networks |
 
| Component | Codename | What it does |
|---|---|---|
| OPNsense | Aegis | Virtualized firewall, NAT, inter-VLAN routing, syslog to SIEM |
| Proxmox VE | atlas | Hypervisor hosting every VM |
| Wazuh | Hermes | SIEM with custom decoders, MITRE ATT&CK mapping, SOC dashboard |
| Cowrie | Dolos | SSH honeypot capturing real attacker sessions |
| Parrot OS | Athena | OSINT workstation on VLAN 50 |
 
### Why the Greek names
 
I like a naming scheme, and I've been into Greek mythology since I was a kid, so each host is named for what it does. Aegis is the shield of Zeus and Athena, so it's the firewall. Atlas holds up the sky, so it's the hypervisor holding every VM. Hermes is the messenger between gods and mortals, so it's the SIEM carrying logs from everything. Dolos is the spirit of trickery and deception, so it's the honeypot. Athena is strategy and wisdom, so it's the intelligence workstation.
 
## Logbook sections
 
1. **Lab Infrastructure.** Proxmox VM inventory and the switch VLAN table.
2. **Network Security Architecture.** OPNsense rulesets and live firewall logs showing inbound SSH redirected to the honeypot.
3. **Threat Detection & SIEM.** Wazuh dashboards, alert volume, and MITRE tactic distribution.
4. **Incident Analysis.** A complete attacker session reconstructed from Wazuh and Cowrie's TTY playback, mapped to T1078 and T1059.
5. **OSINT & Threat Intelligence.** Isolated research VLAN used to corroborate a live Interlock ransomware incident against ransomware.live infrastructure data.
## Privacy notes
 
Public attacker IPs in firewall and honeypot logs are left visible; they are internet scanners hitting a deliberate trap. My own WAN address, internal addressing, and hardware models for home network gear are scrubbed. The organization affected by the ransomware incident in section 5 is intentionally not identified anywhere on this site.
 
## Contact
 
GitHub: [iCrypt0](https://github.com/iCrypt0)
LinkedIn: [chandlerkirk](https://www.linkedin.com/in/chandlerkirk)
