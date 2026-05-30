# 🛡️ Labs Réseau & Sécurité — Blanchard Koubemba

> Administrateur systèmes & réseaux | CCNA 200-301 | Préparation Fortinet NSE4  
> Ce dépôt regroupe mes labs techniques réalisés en environnement simulé (EVE-NG, PNETLab, Packet Tracer).  
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

> *Labs CCNA à venir — en cours de documentation*

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

## 🗺️ Roadmap

- [x] Lab FortiGate SD-WAN Multi-WAN
- [ ] Lab FortiGate VPN IPsec Site-to-Site
- [ ] Lab FortiGate Firewall Policy & Application Control
- [ ] Lab OSPF multi-area
- [ ] Lab VLAN / Inter-VLAN Routing
- [ ] Lab ACL avancées

---

## 🛠️ Outils & Environnement technique

Les labs sont réalisés dans des environnements simulés proches de la production, avec les outils suivants :

### 🔬 Plateformes de virtualisation réseau
- **EVE-NG** — Simulation avancée de topologies multi-constructeurs
- **PNETLab** — Alternative performante pour les labs complexes

### 🔥 Équipements & systèmes
- **FortiGate (Fortinet)** — Firewall, SD-WAN, NAT, VPN
- **Cisco IOS** — Routing & Switching (CCNA level)
- **Windows / Linux** — Machines clientes, serveurs et tests réseau

### ⚙️ Automatisation & scripting
- **Python** — Scripts d’automatisation réseau
- **Ansible** — Déploiement et configuration automatisée d’équipements

### 📊 Outils d’analyse
- **Wireshark** — Analyse de trafic réseau (troubleshooting)
- **CLI (SSH / Console)** — Configuration et diagnostic bas niveau
  
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
