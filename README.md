# 🛡️ Labs Réseau & Sécurité — Blanchard Koubemba

> Administrateur systèmes & réseaux | CCNA 200-301 | Préparation Fortinet NSE4  
> Ce dépôt regroupe mes labs techniques réalisés en environnement simulé (EVE-NG, GNS3, Packet Tracer).  
> Chaque lab documente une problématique réelle : conception, mise en œuvre, troubleshooting et résultats.

[![CCNA](https://img.shields.io/badge/Cisco-CCNA_200--301-blue?logo=cisco)](https://cp.certmetrics.com/cisco/en/public/verify/credential/328896ebc1b041579c057d945b48aff6)
[![NSE4](https://img.shields.io/badge/Fortinet-NSE4_en_cours-red?logo=fortinet)](https://training.fortinet.com)
[![EVE-NG](https://img.shields.io/badge/Plateforme-EVE--NG-orange)](https://www.eve-ng.net/)

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

### 🔥 Fortinet / NSE4

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

Chaque lab suit la même organisation pour faciliter la lecture :

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
OSPF             EIGRP             BGP (notions)       NAT / PAT
Firewall Policy  SD-WAN            VPN IPsec           ACL
FortiGate        Cisco IOS         EVE-NG              Troubleshooting
```

---

## 🛠️ Outils utilisés

### Simulation & Lab
| Outil | Usage |
|-------|-------|
| **EVE-NG / PNetLab** | Simulation de topologies réseau complètes |
| **GNS3** | Émulation d'équipements Cisco et réseau |
| **Cisco Packet Tracer** | Prototypage rapide de labs CCNA |

### Sécurité & Firewall
| Outil | Usage |
|-------|-------|
| **FortiGate** | Firewall, SD-WAN, VPN, IPS, Application Control |
| **Wireshark** | Analyse et capture de trames réseau |
| **Kali Linux** | Tests de sécurité, audit réseau, outils offensifs (lab) |

### Systèmes & Infrastructure
| Outil | Usage |
|-------|-------|
| **Windows Server** | AD DS, DNS, DHCP, Hyper-V |
| **Linux (Debian/Ubuntu)** | Serveurs, routage, scripting, outils réseau |
| **Windows** | Administration postes, GPO, outils réseau |

### Monitoring & Supervision
| Outil | Usage |
|-------|-------|
| **PRTG / Zabbix** | Supervision réseau et alerting |
| **FortiView / Dashboard** | Monitoring temps réel FortiGate |
| **Syslog** | Centralisation des logs équipements |

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
| 🌐 Portfolio | [velvety-lolly-6d76ef.netlify.app](https://velvety-lolly-6d76ef.netlify.app/) |
| 📁 Projets antérieurs | [projets-techniques](https://github.com/Blanchard-Jr/projets-techniques) |

---

## 👤 À propos

**Blanchard Koubemba**  
Administrateur systèmes & réseaux en transition vers l'ingénierie réseaux & sécurité.  
Après l'obtention du **CCNA 200-301**, je construis une expertise sur les solutions **Fortinet** dans le cadre de ma préparation au **NSE4**.  
Je documente chaque lab pour partager ma progression et démontrer mes compétences de manière concrète.
