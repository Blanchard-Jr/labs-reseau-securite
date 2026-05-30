# 🌐 Lab CCNA — OSPF Multi-Site · DHCP · ACL
### Routage dynamique · Attribution automatique d'adresses · Filtrage de trafic

> **Contexte** : Lab réalisé durant la préparation au **CCNA 200-301**  
> **Plateforme** : Cisco Packet Tracer  
> **Niveau** : Intermédiaire — Routing & Security

---

## 🎯 Objectifs

- Mettre en place le **routage dynamique OSPF** entre deux sites distants
- Configurer le **DHCP** sur chaque routeur pour distribuer les adresses aux clients
- Implémenter des **ACL étendues** pour filtrer le trafic entre les réseaux
- Vérifier la connectivité et valider les règles de filtrage

---

## 🏗️ Architecture

```
        Site A                                    Site B
        ──────                                    ──────

      ┌────────┐                              ┌────────┐
      │  2911  │─────── 192.168.255.0/24 ─────│  2911  │
      │   R1   │  .1                      .2  │   R2   │
      └──┬──┬──┘                              └──┬──┬──┘
         │  │                                    │  │
    ┌────┘  └────┐                          ┌────┘  └────┐
    │            │                          │            │
┌───┴──┐     ┌───┴──┐                  ┌───┴──┐     ┌───┴──┐
│ ASW1 │     │ ASW2 │                  │ ASW3 │     │ ASW4 │
│ 2960 │     │ 2960 │                  │ 2960 │     │ 2960 │
└──┬───┘     └──┬───┘                  └──┬───┘     └──┬───┘
   │             │                        │             │
L0  L1         L2  L3                  L4  L5        L6  L7

DHCP pool       DHCP pool              DHCP pool    DHCP pool
192.168.10.0/24 192.168.20.0/24        192.168.30.0/24 192.168.40.0/24
```

### Tableau d'adressage

| Équipement | Interface | Réseau | Rôle |
|------------|-----------|--------|------|
| R1 | Gi0/0 | 192.168.10.0/24 | LAN Site A — ASW1 |
| R1 | Gi0/1 | 192.168.20.0/24 | LAN Site A — ASW2 |
| R1 | Se0/0/0 | 192.168.255.0/24 (.1) | Lien WAN inter-sites |
| R2 | Gi0/0 | 192.168.30.0/24 | LAN Site B — ASW3 |
| R2 | Gi0/1 | 192.168.40.0/24 | LAN Site B — ASW4 |
| R2 | Se0/0/0 | 192.168.255.0/24 (.2) | Lien WAN inter-sites |

---

## ⚙️ Mise en œuvre

### 1. OSPF — Routage dynamique inter-sites

- Protocole **OSPF area 0** configuré sur R1 et R2
- Tous les réseaux LAN et WAN annoncés via OSPF
- Vérification avec `show ip ospf neighbor` et `show ip route ospf`

```
router ospf 1
 network 192.168.10.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 192.168.255.0 0.0.0.255 area 0
```

### 2. DHCP — Distribution automatique d'adresses

- 4 pools DHCP configurés (un par sous-réseau LAN)
- Gateway et DNS poussés automatiquement aux clients

```
ip dhcp pool LAN-10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8

ip dhcp excluded-address 192.168.10.1 192.168.10.10
```

### 3. ACL étendue — Filtrage de trafic

- **ACL bloquant** les pings de `192.168.10.0/24` vers `192.168.30.0/24`
- Appliquée en **inbound** sur l'interface LAN de R1
- Le reste du trafic reste autorisé (permit ip any any)

```
ip access-list extended BLOC-PING
 deny icmp 192.168.10.0 0.0.0.255 192.168.30.0 0.0.0.255
 permit ip any any

interface GigabitEthernet0/0
 ip access-group BLOC-PING in
```

---

## ⚠️ Problématiques typiques rencontrées

| Problème | Cause | Solution |
|----------|-------|----------|
| OSPF neighbor stuck en INIT | Lien WAN série mal configuré | Vérification encapsulation HDLC/PPP |
| DHCP ne distribue pas d'IP | `excluded-address` trop large | Réduction de la plage exclue |
| ACL bloque tout le trafic | `permit ip any any` manquant | Ajout de la règle permit en fin d'ACL |
| ACL sans effet | Appliquée sur la mauvaise interface ou mauvais sens | Vérification `in` vs `out` et bonne interface |

---

## ✅ Résultats

- ✔️ Routage OSPF opérationnel — tous les réseaux joignables entre les deux sites
- ✔️ DHCP fonctionnel — les 8 laptops obtiennent une adresse automatiquement
- ✔️ ACL validée — ping bloqué de 192.168.10.x vers 192.168.30.x uniquement
- ✔️ Reste du trafic non affecté par l'ACL

---

## 🧠 Compétences travaillées

`OSPF` `Routage dynamique` `DHCP` `ACL étendues` `Filtrage de trafic` `Multi-site` `Cisco IOS` `Packet Tracer`

---

## 📁 Structure du dossier

```
lab-ccna-ospf-dhcp-acl/
├── README.md                  ← Ce fichier
├── captures/
│   └── topologie-ospf-acl.png ← Schéma topologie Packet Tracer
└── configs/
    └── modele-etude-acl-etendue.pkt  ← Fichier Packet Tracer
```

---

## 🔗 Liens utiles

- [Cisco — OSPF Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_ospf/configuration/xe-16/iro-xe-16-book.html)
- [Cisco — ACL Configuration Guide](https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html)
- [CCNA 200-301 — Exam Topics](https://learningnetwork.cisco.com/s/ccna-exam-topics)

---

## 👤 Auteur

**Blanchard Koubemba** — Ingénieur Réseaux & Sécurité  
🏅 CCNA 200-301 | En cours : Fortinet NSE4  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Blanchard_Koubemba-blue?logo=linkedin)](https://www.linkedin.com/in/blanchard-koubemba-a9524ab5/)
