# 🌐 Lab CCNA — Architecture LAN 3 Niveaux (3-Tier)
### VLAN · HSRP · EtherChannel · Routage Inter-VLAN

> **Contexte** : Lab réalisé durant la préparation au **CCNA 200-301**  
> **Plateforme** : Cisco Packet Tracer  
> **Niveau** : Intermédiaire — Switching & Routing

---

## 🎯 Objectifs

- Concevoir et déployer une **architecture LAN hiérarchique 3 niveaux** (Core / Distribution / Access)
- Configurer la **redondance de passerelle** avec HSRP v2
- Mettre en place l'**agrégation de liens** avec EtherChannel
- Assurer le **routage inter-VLAN** via un routeur en périphérie
- Segmenter le réseau en **VLANs** et vérifier la connectivité end-to-end

---

## 🏗️ Architecture

```
                         ┌─────────────────┐
                         │   2911 - R1      │
                         │  (Routeur Core)  │
                         └────┬────────┬───┘
                    172.15.0.0/16   172.16.0.0/16
                              │        │
               ┌──────────────┘        └──────────────┐
               │                                       │
       ┌───────┴────────┐   172.19.0.0/16   ┌──────────┴──────┐
       │  3650 - CSW1   │───────────────────│  3650 - CSW2    │
       │  (Distribution)│                   │  (Distribution) │
       └───────┬────────┘                   └──────────┬──────┘
               │  Port-channel1               Port-channel2  │
          172.17.0.0/16                         172.18.0.0/16
               │                                       │
       ┌───────┴────────┐   172.20.0.0/16   ┌──────────┴──────┐
       │  3650 - DSW1   │───────────────────│  3650 - DSW2    │
       │  (Distribution)│                   │  (Distribution) │
       └──┬──────────┬──┘                   └──┬──────────┬───┘
          │          │         172.21.0.0/16    │          │
     ┌────┘     ┌────┘                     ┌───┘     ┌────┘
     │          │                          │         │
 ┌───┴──┐   ┌───┴──┐                  ┌────┴─┐   ┌───┴──┐
 │ ASW1 │   │ ASW2 │                  │ ASW2 │   │ ASW3 │
 │2960  │   │2960  │                  │2960  │   │2960  │
 └──┬───┘   └──┬───┘                  └──┬───┘   └──┬───┘
    │           │                        │           │
 PC0 PC1    PC2 PC3                   PC4 PC5    (clients)
 v22  v23   v22  v23                  v22  v23
```

### Tableau d'adressage

| Équipement | Interface | Réseau | Rôle |
|------------|-----------|--------|------|
| R1 | Gi0/0 | 172.15.0.0/16 | Lien vers CSW1 |
| R1 | Gi0/1 | 172.16.0.0/16 | Lien vers CSW2 |
| CSW1 ↔ CSW2 | L3 | 172.19.0.0/16 | Lien inter-distribution |
| DSW1 ↔ DSW2 | L3 | 172.20.0.0/16 | Lien inter-distribution |
| CSW1 ↔ DSW1 | Port-channel1 | 172.17.0.0/16 | EtherChannel |
| CSW2 ↔ DSW2 | Port-channel2 | 172.18.0.0/16 | EtherChannel |
| DSW1/DSW2 | Vlan22 | 172.22.0.0/16 | Gateway HSRP VLAN 22 |
| DSW1/DSW2 | Vlan23 | 172.23.0.0/16 | Gateway HSRP VLAN 23 |

---

## ⚙️ Mise en œuvre

### 1. VLANs & Trunking
- Création des VLANs 22 et 23 sur tous les switches
- Configuration des ports en mode **trunk** entre les couches
- Ports clients en mode **access** sur les ASW

### 2. EtherChannel (LACP)
- Agrégation de 2 liens physiques entre CSW et DSW
- Protocole **LACP (802.3ad)**
- Port-channel1 : CSW1 ↔ DSW1
- Port-channel2 : CSW2 ↔ DSW2

### 3. HSRP v2 — Redondance de passerelle

Configuration sur **DSW1** (actif pour VLAN 22 et 23) :

```
interface Vlan22
 mac-address 00e0.f98d.6901
 ip address 172.22.0.2 255.255.0.0
 standby version 2
 standby 1 ip 172.22.0.1
 standby 1 priority 105
 standby 1 preempt

interface Vlan23
 mac-address 00e0.f98d.6902
 ip address 172.23.0.2 255.255.0.0
 standby version 2
 standby 1 ip 172.23.0.1
 standby 1 priority 105
 standby 1 preempt
```

- **IP virtuelle VLAN 22** : `172.22.0.1` (gateway des clients)
- **IP virtuelle VLAN 23** : `172.23.0.1` (gateway des clients)
- DSW1 actif (priority 105 > défaut 100) avec **preempt**
- DSW2 en standby — prend le relais automatiquement si DSW1 tombe

### 4. Routage Inter-VLAN
- Routage assuré par **R1** en périphérie
- Les DSW remontent le trafic inter-VLAN vers les CSW puis vers R1
- Routes statiques / dynamiques configurées pour joindre tous les réseaux

---

## ⚠️ Problématiques typiques rencontrées

| Problème | Cause | Solution |
|----------|-------|----------|
| HSRP ne bascule pas | `preempt` absent sur le switch actif | Ajout de `standby 1 preempt` |
| EtherChannel en err-disabled | Modes LACP/PAgP incompatibles entre les deux extrémités | Alignement des modes (`active`/`active`) |
| Pas de routage inter-VLAN | Interface SVI non activée (`no shutdown`) | `no shutdown` sur chaque interface VLAN |
| Trunk ne passe pas les VLANs | VLANs non autorisés sur le trunk | `switchport trunk allowed vlan add 22,23` |

---

## ✅ Résultats

- ✔️ Connectivité end-to-end entre tous les PCs (VLAN 22 ↔ VLAN 23)
- ✔️ Basculement HSRP fonctionnel — la gateway virtuelle reste joignable si DSW1 tombe
- ✔️ EtherChannel opérationnel — agrégation de bande passante vérifiée
- ✔️ Routage inter-VLAN fonctionnel via R1

---

## 🧠 Compétences travaillées

`VLAN` `Trunking 802.1Q` `EtherChannel LACP` `HSRP v2` `Routage Inter-VLAN` `Architecture 3-Tier` `STP / RSTP` `Cisco IOS` `Packet Tracer`

---

## 📁 Structure du dossier

```
lab-ccna-3tier-vlan-hsrp-etherchannel/
├── README.md                        ← Ce fichier
├── captures/
│   └── topologie-3tier.png          ← Schéma topologie Packet Tracer
└── configs/
    └── Architecture LAN à 3 Niveaux.pkt  ← Fichier Packet Tracer
```

---

## 🔗 Liens utiles

- [Cisco — HSRP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios/12_2/ipaddr/configuration/guide/fipr_c/fcfhsrp.html)
- [Cisco — EtherChannel Configuration](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/12023-4.html)
- [CCNA 200-301 — Exam Topics](https://learningnetwork.cisco.com/s/ccna-exam-topics)

---

## 👤 Auteur

**Blanchard Koubemba** — Ingénieur Réseaux & Sécurité  
🏅 CCNA 200-301 | En cours : Fortinet NSE4  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Blanchard_Koubemba-blue?logo=linkedin)](https://www.linkedin.com/in/blanchard-koubemba-a9524ab5/)
