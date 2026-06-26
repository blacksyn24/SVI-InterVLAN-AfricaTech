<img width="1920" height="1080" alt="Capture d’écran du 2026-06-26 21-26-44" src="https://github.com/user-attachments/assets/f21d923b-3e54-46b9-811b-666c488536d1" />
# 🌐 CCNA2 — Inter-VLAN Routing SVI | AfricaTech

![Cisco](https://img.shields.io/badge/Cisco-CCNA2-blue?style=for-the-badge&logo=cisco&logoColor=white)
![PacketTracer](https://img.shields.io/badge/Packet%20Tracer-8.x-orange?style=for-the-badge&logo=cisco)
![Status](https://img.shields.io/badge/Status-✅%20Completed-brightgreen?style=for-the-badge)
![VLANs](https://img.shields.io/badge/VLANs-6-purple?style=for-the-badge)
![Switches](https://img.shields.io/badge/Switches-4-red?style=for-the-badge)
![PCs](https://img.shields.io/badge/PCs-36-yellow?style=for-the-badge)
![Method](https://img.shields.io/badge/Method-SVI%20Switch%20L3-lightblue?style=for-the-badge)

---

## 📋 Description

Ce TP simule le réseau de l'entreprise **AfricaTech** basée à
Cotonou, Bénin 🇧🇯. Le réseau est composé de **6 départements**
répartis sur **3 switches d'accès** reliés à un **switch L3**
qui assure le routage inter-VLAN via des **SVI**.

### Objectifs
- ✅ Créer et configurer **6 VLANs**
- ✅ Configurer le routage inter-VLAN via **SVI**
- ✅ Relier 3 switches L2 au switch L3 via **trunks**
- ✅ Tester la connectivité entre **36 PC**
- ✅ Résoudre un **scénario de panne réelle**

---

## 🖥️ Équipements

| Équipement | Modèle | Nom | Quantité |
|-----------|--------|-----|----------|
| 🔀 Switch L3 | Cisco 3560-24PS | SW-CORE | 1 |
| 🔌 Switch L2 | Cisco 2960-24TT | SW-A | 1 |
| 🔌 Switch L2 | Cisco 2960-24TT | SW-B | 1 |
| 🔌 Switch L2 | Cisco 2960-24TT | SW-C | 1 |
| 💻 PC | PC-PT | PC0 à PC35 | 36 |

---

## 🗺️ Topologie

```
              [SW-CORE L3 - 3560]
             /          |         \
         Gig0/1       Gig0/2     Fa0/24
           |             |           |
        [SW-A]        [SW-B]      [SW-C]
       /      \       /      \    /      \
   Fa0/1-6  Fa0/7-12 Fa0/1-6 Fa0/7-12 Fa0/1-6 Fa0/7-12
     |          |       |        |       |          |
  VLAN10     VLAN20  VLAN30   VLAN40  VLAN50    VLAN60
  PC0-5      PC6-11  PC12-17  PC18-23 PC24-29   PC30-35
```

---

## 🔌 Câblage

| De | Port | Vers | Port |
|----|------|------|------|
| SW-CORE | Gig0/1 | SW-A | Gig0/1 |
| SW-CORE | Gig0/2 | SW-B | Gig0/1 |
| SW-CORE | Fa0/24 | SW-C | Fa0/24 |
| SW-A | Fa0/1-6 | PC0-5 | Fa0 |
| SW-A | Fa0/7-12 | PC6-11 | Fa0 |
| SW-B | Fa0/1-6 | PC12-17 | Fa0 |
| SW-B | Fa0/7-12 | PC18-23 | Fa0 |
| SW-C | Fa0/1-6 | PC24-29 | Fa0 |
| SW-C | Fa0/7-12 | PC30-35 | Fa0 |

---

## 📊 Plan d'adressage

| VLAN | 🏷️ Nom | Réseau | Passerelle (SVI) | PCs | Switch |
|------|--------|--------|-----------------|-----|--------|
| 10 | 👔 DIRECTION | 10.10.10.0/24 | 10.10.10.1 | PC0-5 | SW-A |
| 20 | 💰 FINANCE | 10.10.20.0/24 | 10.10.20.1 | PC6-11 | SW-A |
| 30 | 👥 RH | 10.10.30.0/24 | 10.10.30.1 | PC12-17 | SW-B |
| 40 | 💻 IT | 10.10.40.0/24 | 10.10.40.1 | PC18-23 | SW-B |
| 50 | 🛒 VENTES | 10.10.50.0/24 | 10.10.50.1 | PC24-29 | SW-C |
| 60 | 📦 LOGISTIQUE | 10.10.60.0/24 | 10.10.60.1 | PC30-35 | SW-C |

---

## 🖥️ Adresses IP des PC

### VLAN 10 — 👔 DIRECTION
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC0 | 10.10.10.10 | 255.255.255.0 | 10.10.10.1 |
| PC1 | 10.10.10.11 | 255.255.255.0 | 10.10.10.1 |
| PC2 | 10.10.10.12 | 255.255.255.0 | 10.10.10.1 |
| PC3 | 10.10.10.13 | 255.255.255.0 | 10.10.10.1 |
| PC4 | 10.10.10.14 | 255.255.255.0 | 10.10.10.1 |
| PC5 | 10.10.10.15 | 255.255.255.0 | 10.10.10.1 |

### VLAN 20 — 💰 FINANCE
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC6 | 10.10.20.10 | 255.255.255.0 | 10.10.20.1 |
| PC7 | 10.10.20.11 | 255.255.255.0 | 10.10.20.1 |
| PC8 | 10.10.20.12 | 255.255.255.0 | 10.10.20.1 |
| PC9 | 10.10.20.13 | 255.255.255.0 | 10.10.20.1 |
| PC10 | 10.10.20.14 | 255.255.255.0 | 10.10.20.1 |
| PC11 | 10.10.20.15 | 255.255.255.0 | 10.10.20.1 |

### VLAN 30 — 👥 RH
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC12 | 10.10.30.10 | 255.255.255.0 | 10.10.30.1 |
| PC13 | 10.10.30.11 | 255.255.255.0 | 10.10.30.1 |
| PC14 | 10.10.30.12 | 255.255.255.0 | 10.10.30.1 |
| PC15 | 10.10.30.13 | 255.255.255.0 | 10.10.30.1 |
| PC16 | 10.10.30.14 | 255.255.255.0 | 10.10.30.1 |
| PC17 | 10.10.30.15 | 255.255.255.0 | 10.10.30.1 |

### VLAN 40 — 💻 IT
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC18 | 10.10.40.10 | 255.255.255.0 | 10.10.40.1 |
| PC19 | 10.10.40.11 | 255.255.255.0 | 10.10.40.1 |
| PC20 | 10.10.40.12 | 255.255.255.0 | 10.10.40.1 |
| PC21 | 10.10.40.13 | 255.255.255.0 | 10.10.40.1 |
| PC22 | 10.10.40.14 | 255.255.255.0 | 10.10.40.1 |
| PC23 | 10.10.40.15 | 255.255.255.0 | 10.10.40.1 |

### VLAN 50 — 🛒 VENTES
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC24 | 10.10.50.10 | 255.255.255.0 | 10.10.50.1 |
| PC25 | 10.10.50.11 | 255.255.255.0 | 10.10.50.1 |
| PC26 | 10.10.50.12 | 255.255.255.0 | 10.10.50.1 |
| PC27 | 10.10.50.13 | 255.255.255.0 | 10.10.50.1 |
| PC28 | 10.10.50.14 | 255.255.255.0 | 10.10.50.1 |
| PC29 | 10.10.50.15 | 255.255.255.0 | 10.10.50.1 |

### VLAN 60 — 📦 LOGISTIQUE
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC30 | 10.10.60.10 | 255.255.255.0 | 10.10.60.1 |
| PC31 | 10.10.60.11 | 255.255.255.0 | 10.10.60.1 |
| PC32 | 10.10.60.12 | 255.255.255.0 | 10.10.60.1 |
| PC33 | 10.10.60.13 | 255.255.255.0 | 10.10.60.1 |
| PC34 | 10.10.60.14 | 255.255.255.0 | 10.10.60.1 |
| PC35 | 10.10.60.15 | 255.255.255.0 | 10.10.60.1 |

---

## ⚙️ Configuration complète

### 🔧 SW-CORE — Switch L3

```cisco
enable
configure terminal
hostname SW-CORE

vlan 10
name DIRECTION
exit
vlan 20
name FINANCE
exit
vlan 30
name RH
exit
vlan 40
name IT
exit
vlan 50
name VENTES
exit
vlan 60
name LOGISTIQUE
exit

ip routing

interface vlan 10
ip address 10.10.10.1 255.255.255.0
no shutdown
exit

interface vlan 20
ip address 10.10.20.1 255.255.255.0
no shutdown
exit

interface vlan 30
ip address 10.10.30.1 255.255.255.0
no shutdown
exit

interface vlan 40
ip address 10.10.40.1 255.255.255.0
no shutdown
exit

interface vlan 50
ip address 10.10.50.1 255.255.255.0
no shutdown
exit

interface vlan 60
ip address 10.10.60.1 255.255.255.0
no shutdown
exit

interface gig0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan 10,20
exit

interface gig0/2
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan 30,40
exit

interface fa0/24
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan 50,60
exit

end
write
```

---

### 🔧 SW-A — Switch L2

```cisco
enable
configure terminal
hostname SW-A

vlan 10
name DIRECTION
exit
vlan 20
name FINANCE
exit

interface range fa0/1-6
switchport mode access
switchport access vlan 10
exit

interface range fa0/7-12
switchport mode access
switchport access vlan 20
exit

interface gig0/1
switchport mode trunk
switchport trunk allowed vlan 10,20
exit

end
write
```

---

### 🔧 SW-B — Switch L2

```cisco
enable
configure terminal
hostname SW-B

vlan 30
name RH
exit
vlan 40
name IT
exit

interface range fa0/1-6
switchport mode access
switchport access vlan 30
exit

interface range fa0/7-12
switchport mode access
switchport access vlan 40
exit

interface gig0/1
switchport mode trunk
switchport trunk allowed vlan 30,40
exit

end
write
```

---

### 🔧 SW-C — Switch L2

```cisco
enable
configure terminal
hostname SW-C

vlan 50
name VENTES
exit
vlan 60
name LOGISTIQUE
exit

interface range fa0/1-6
switchport mode access
switchport access vlan 50
exit

interface range fa0/7-12
switchport mode access
switchport access vlan 60
exit

interface fa0/24
switchport mode trunk
switchport trunk allowed vlan 50,60
exit

end
write
```

---

## 🔍 Vérifications

```cisco
SW-CORE# show vlan brief
SW-CORE# show interfaces trunk
SW-CORE# show ip interface brief
SW-CORE# show ip route
```

### Résultat attendu show ip interface brief
```
Vlan10   10.10.10.1   up   up
Vlan20   10.10.20.1   up   up
Vlan30   10.10.30.1   up   up
Vlan40   10.10.40.1   up   up
Vlan50   10.10.50.1   up   up
Vlan60   10.10.60.1   up   up
```

### Résultat attendu show ip route
```
C  10.10.10.0/24 via Vlan10
C  10.10.20.0/24 via Vlan20
C  10.10.30.0/24 via Vlan30
C  10.10.40.0/24 via Vlan40
C  10.10.50.0/24 via Vlan50
C  10.10.60.0/24 via Vlan60
```

---

## 🧪 Tests de connectivité

```
✅ PC0  → ping 10.10.10.1   (passerelle VLAN10)
✅ PC0  → ping 10.10.20.10  (VLAN10 → VLAN20)
✅ PC0  → ping 10.10.30.10  (VLAN10 → VLAN30 SW-B)
✅ PC0  → ping 10.10.40.10  (VLAN10 → VLAN40 SW-B)
✅ PC0  → ping 10.10.50.10  (VLAN10 → VLAN50 SW-C)
✅ PC0  → ping 10.10.60.10  (VLAN10 → VLAN60 SW-C)
✅ PC30 → ping 10.10.10.10  (VLAN60 → VLAN10)
✅ PC18 → ping 10.10.50.10  (VLAN40 → VLAN50)
```

---

## 🎭 Scénario — Ticket d'incident

```
Entreprise : AfricaTech
Ville      : Cotonou, Bénin 🇧🇯
Rôle       : Technicien réseau junior
```

> Madame KOFFI (DG) appelle :
> "Les PC de Direction, Finance, RH et IT
> ne communiquent plus ce matin !"

### Simulation de la panne
```cisco
configure terminal
no interface vlan 10
no interface vlan 20
no interface vlan 30
no interface vlan 40
end
```

### Correction
```cisco
configure terminal
interface vlan 10
ip address 10.10.10.1 255.255.255.0
no shutdown
exit
interface vlan 20
ip address 10.10.20.1 255.255.255.0
no shutdown
exit
interface vlan 30
ip address 10.10.30.1 255.255.255.0
no shutdown
exit
interface vlan 40
ip address 10.10.40.1 255.255.255.0
no shutdown
exit
end
write
```

---

## 💡 Différence SVI vs Router-on-a-Stick

| | 🏆 SVI (ce TP) | Router-on-a-Stick |
|---|---|---|
| Routeur externe | ❌ Non | ✅ Obligatoire |
| Commande clé | `ip routing` | `encapsulation dot1Q` |
| Performance | 🚀 Rapide (ASIC) | 🐢 Plus lent |
| Interface | `interface vlan X` | `interface gig0/0.X` |
| Passerelle PC | IP de la SVI | IP sous-interface |

---

## 🛠️ Outils

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-8.x-orange?style=flat-square&logo=cisco)
![Cisco IOS](https://img.shields.io/badge/Cisco%20IOS-15.x-blue?style=flat-square)
![GitHub](https://img.shields.io/badge/GitHub-black?style=flat-square&logo=github)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=flat-square&logo=ubuntu)

---

## 👨‍💻 Auteur

**Urbain Sedami Landjidé**
🎓 Étudiant en 2ème année — Licence Professionnelle
📡 Réseaux Informatique Mobilité Sécurité (RMS)
🏫 Cisco Networking Academy
📍 Cotonou, Bénin 🇧🇯

---

## 📄 Licence

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Libre d'utilisation pour l'apprentissage et la formation réseau.
