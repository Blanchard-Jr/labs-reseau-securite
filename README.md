# 🛡️ Labs Réseau & Sécurité — Blanchard Koubemba

> Administrateur Réseaux & Sécurité | CCNA 200-301 | Préparation Fortinet FCP Network Security  
> Ce dépôt regroupe mes labs techniques réalisés en environnement simulé (EVE-NG, PNetLab, Packet Tracer).  
> Chaque lab documente une problématique réelle : conception, mise en œuvre, troubleshooting et résultats.

[![CCNA](https://img.shields.io/badge/Cisco-CCNA_200--301-blue?logo=cisco)](https://cp.certmetrics.com/cisco/en/public/verify/credential/328896ebc1b041579c057d945b48aff6)
[![FCP](https://img.shields.io/badge/Fortinet-FCP_Network_Security-red?logo=fortinet)](https://training.fortinet.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-blanchard--koubemba.netlify.app-green)](https://blanchard-koubemba.netlify.app)

---

## 🧭 Orientation

Mon profil évolue vers l'**ingénierie réseaux et sécurité** en environnement d'entreprise.  
Les labs de ce repo couvrent trois axes principaux :

| Axe | Technos | Objectif |
|-----|---------|----------|
| 🌐 **Routing & Switching** | Cisco IOS, OSPF, EIGRP, VLANs, STP | Maîtrise des protocoles fondamentaux |
| 🔒 **Firewall & Sécurité** | FortiGate, ACL, NAT, VPN | Sécurisation des flux et périmètre réseau |
| 📡 **SD-WAN & Architectures** | FortiGate SD-WAN, multi-WAN, SLA | Architectures réseau modernes |

---

## 📂 Labs disponibles

### 🔥 Fortinet / FCP Network Security

| Lab | Description | Niveau | Technos |
|-----|-------------|--------|---------|
| [Lab FortiGate — SD-WAN Multi-WAN](./lab-fortigate-sdwan-multiwan/) | Architecture SD-WAN avec load balancing, SLA et NAT multi-WAN sur EVE-NG | ⭐⭐⭐ | FortiGate · Cisco IOS · SD-WAN · NAT |

### 🌐 Cisco / CCNA

| Lab | Description | Niveau | Technos |
|-----|-------------|--------|---------|
| [Lab CCNA — Architecture LAN 3-Tier](./lab-ccna-3tier-vlan-hsrp-etherchannel/) | Architecture hiérarchique Core/Distribution/Access avec redondance HSRP et agrégation EtherChannel | ⭐⭐⭐ | Cisco IOS · VLAN · HSRP v2 · EtherChannel · Routage Inter-VLAN |
| [Lab CCNA — OSPF Multi-Site · DHCP · ACL](./lab-ccna-ospf-dhcp-acl/) | Routage dynamique OSPF entre deux sites, DHCP centralisé et filtrage de trafic par ACL étendues | ⭐⭐ | Cisco IOS · OSPF · DHCP · ACL étendues |

---

## 🏗️ Structure type d'un lab

```
lab-nom-du-lab/
├── README.md          ← Contexte, architecture, mise en œuvre, résultats
├── captures/          ← Screenshots de la topologie et des résultats
├── configs/           ← Fichiers de configuration exportés (anonymisés)
└── doc/               ← Notes de troubleshooting, schémas complémentaires
```

---

## 🧠 Compétences couvertes

```
Routing          Switching         VLAN / Trunking     STP / RSTP
OSPF             EIGRP             NAT / PAT           ACL étendues
Firewall Policy  SD-WAN            VPN IPsec           Troubleshooting
FortiGate        Cisco IOS         EVE-NG / PNetLab    Packet Tracer
```

---

## 🛠️ Outils utilisés

### Simulation & Lab
| Outil | Usage |
|-------|-------|
| **EVE-NG / PNetLab** | Simulation de topologies réseau complètes |
| **Cisco Packet Tracer** | Prototypage rapide de labs CCNA |

### Sécurité & Firewall
| Outil | Usage |
|-------|-------|
| **FortiGate** | Firewall, SD-WAN, VPN, IPS, Application Control |
| **Wireshark** | Analyse et capture de trames réseau |
| **Kali Linux** | Tests de sécurité, audit réseau (lab) |

### Systèmes & Infrastructure
| Outil | Usage |
|-------|-------|
| **Windows Server** | AD DS, DNS, DHCP, Hyper-V |
| **Linux (Debian/Ubuntu)** | Serveurs, routage, scripting, outils réseau |

### Monitoring & Supervision
| Outil | Usage |
|-------|-------|
| **Zabbix** | Supervision réseau et alerting |
| **FortiView / Dashboard** | Monitoring temps réel FortiGate |
| **Graylog / Syslog** | Centralisation et analyse des logs |

### Automatisation & Scripting
| Outil | Usage |
|-------|-------|
| **PowerShell** | Automatisation Windows / Active Directory |
| **Bash** | Scripts Linux, tâches réseau |
| **Python** | Automatisation réseau, parsing de configs (lab) |
| **Ansible** | Automatisation de configuration d'équipements réseau (lab) |

---

## 🗺️ Roadmap

- [x] Lab FortiGate SD-WAN Multi-WAN
- [x] Lab CCNA — Architecture LAN 3-Tier (VLAN · HSRP · EtherChannel)
- [x] Lab CCNA — OSPF Multi-Site · DHCP · ACL
- [ ] Lab FortiGate VPN IPsec Site-to-Site
- [ ] Lab FortiGate Firewall Policy & Application Control
- [ ] Lab CCNA — DHCP multi-VLAN
- [ ] Lab CCNA — WLC Wireless LAN Controller

---

## 🔗 Me retrouver

| Plateforme | Lien |
|------------|------|
| 💼 LinkedIn | [blanchard-koubemba](https://www.linkedin.com/in/blanchard-koubemba-a9524ab5/) |
| 🌐 Portfolio | [blanchard-koubemba.netlify.app](https://blanchard-koubemba.netlify.app) |
| 📁 Projets antérieurs | [projets-techniques](https://github.com/Blanchard-Jr/projets-techniques) |

---

## 👤 À propos

**Blanchard Koubemba**  
Administrateur Réseaux & Sécurité — CCNA 200-301.  
Je construis une expertise sur les solutions **Fortinet** dans le cadre de ma préparation au **FCP Network Security**.  
Je documente chaque lab pour démontrer mes compétences de manière concrète et préparer ma transition vers l'ingénierie réseaux & sécurité.
