# FICHE 06 – OSI vs TCP/IP : comprendre sans confondre

🧠 PARTIE 2 — ÉTAPE 6  
Comparaison OSI vs TCP/IP (claire, définitive, utile)

---

## 1️⃣ Contexte

Avec la généralisation de TCP/IP, il devient essentiel de **distinguer le modèle théorique de référence et le modèle opérationnel réel**.

Le modèle **OSI** est un cadre conceptuel structuré, conçu pour expliquer, normaliser et enseigner le fonctionnement des réseaux.  
Le modèle **TCP/IP** correspond à la **suite de protocoles réellement implémentée**, utilisée historiquement sur ARPANET puis sur Internet.

Cette distinction permet d’éviter les confusions fréquentes et de **relier les concepts abstraits aux mécanismes concrets**, notamment lors du diagnostic réseau ou de l’analyse de paquets avec des outils comme Wireshark.

---

## 2️⃣ Faux débat : « OSI vs TCP/IP »

Il est important de clarifier un point fondamental :

- ❌ OSI n’est pas en concurrence avec TCP/IP  
- ❌ TCP/IP n’a pas remplacé ou « éliminé » OSI  

👉 **Les deux modèles ont des rôles différents et complémentaires**.

- OSI sert à **penser et expliquer le réseau**
- TCP/IP sert à **faire fonctionner le réseau**

---

## 3️⃣ Philosophie des deux modèles

| Aspect | OSI | TCP/IP |
|------|-----|--------|
| Nature | Modèle conceptuel | Suite de protocoles opérationnelle |
| Finalité | Normalisation et pédagogie | Communication réelle et robuste |
| Approche | Top-down | Bottom-up |
| Niveau d’abstraction | Élevé | Pragmatique |
| Rôle principal | Compréhension | Implémentation |
| Adoption | Universelle en formation | Universelle en production |

---

## 4️⃣ Approche Top-down vs Bottom-up

### 🟦 OSI – Approche Top-down

Le modèle OSI a été conçu **en partant des besoins utilisateurs**, puis en descendant progressivement vers les aspects matériels.

- Définition des fonctions idéales de communication
- Découpage logique en couches indépendantes
- Vision pédagogique avant l’implémentation technique

👉 Cette approche favorise la **clarté conceptuelle** et la **méthodologie d’analyse**.

---

### 🟨 TCP/IP – Approche Bottom-up

TCP/IP s’est construit **à partir de contraintes réelles**, issues des premiers réseaux interconnectés.

- Résoudre des problèmes concrets de communication
- Assurer la robustesse et la tolérance aux pannes
- Adapter les protocoles à l’existant matériel

👉 Cette approche privilégie **l’efficacité et la résilience** plutôt que la pure séparation théorique.

---

## 5️⃣ Objectif initial des modèles

### 🟦 OSI
- Créer un standard universel
- Décrire comment les réseaux *doivent* fonctionner
- Être indépendant des technologies existantes

### 🟨 TCP/IP
- Faire communiquer des machines réelles
- Résister aux pannes réseau
- Fonctionner efficacement sur ARPANET

---

## 6️⃣ Structure des couches et correspondance

| OSI | TCP/IP | Fonction principale |
|-----|--------|------------------|
| Application | Application | Protocoles applicatifs (HTTP, SMTP, FTP) |
| Présentation | Application | Encodage, chiffrement, compression |
| Session | Application | Gestion des dialogues et sessions |
| Transport | Transport | TCP / UDP |
| Réseau | Internet | IP, routage |
| Liaison | Accès réseau | Ethernet, Wi-Fi |
| Physique | Accès réseau | Support physique |

👉 **OSI explique plus finement**,  
👉 **TCP/IP implémente plus efficacement**.

---

## 6️⃣ bis — SDU, PDU et encapsulation : le lien concret entre OSI et TCP/IP

Pour comprendre ce qui circule réellement sur le réseau, il faut introduire deux notions fondamentales :

### 🔹 SDU — Service Data Unit
Donnée reçue par une couche depuis la couche supérieure

### 🔹 PDU — Protocol Data Unit
Donnée produite par une couche après ajout de son en-tête (et parfois d’un trailer)

> 👉 Principe clé :  
> La SDU d’une couche devient le contenu de la PDU de la couche inférieure.


---

## 8️⃣ Schéma logique OSI ↔ TCP/IP avec SDU / PDU (référence conceptuelle)


```text
════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════

│ Couche OSI         │ Données (SDU / PDU)                                                      │ Couche TCP/IP        │
─────────────────────┼──────────────────────────────────────────────────────────────────────────┼───────────────────────
│ Application (7)    │ 📦 SDU reçu = Message / APDU "bonjour ça va"                              │ Application         │
│ Présentation (6)   │ 🔲 Header Application                                                     │ Application         │
│ Session (5)        │ 🔵 PDU Application = Header Application + SDU reçu  (unité : APDU)        │ Application         │
│                    │ 🟢 SDU envoyé à Transport = PDU Application = APDU                        │                     │

════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════

│ Transport (4)       │ 📦 SDU reçu = APDU                                                       │ Transport           │
│                     │ 🔲 Header Transport (Ports, Num Séquence, contrôle)                      │ Transport           │
│                     │ 🔵 PDU Transport = Header Transport + SDU reçu (unité : Segment)         │                     │
│                     │ 🟢 SDU envoyé à Réseau = PDU Transport = Segment TCP                     │                     │

════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════

│ Réseau (3)          │ 📦 SDU reçu = Segment TCP                                                │ Internet            │
│                     │ 🔲 Header Réseau (IP : adresses, TTL, protocole)                         │ Internet            │
│                     │ 🔵 PDU Réseau = Header Réseau + SDU reçu (unité : Paquet)                │                     │
│                     │ 🟢 SDU envoyé à Liaison = PDU Réseau = Paquet IP                         │                     │

════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════

│ Liaison (2)         │ 📦 SDU reçu = Paquet IP                                                  │ Accès réseau        │
│                     │ 🔲 Header + Trailer CRC                                                  │ Accès réseau        │
│                     │ 🔵 PDU Liaison = Header + SDU reçu (unité : Trame)                       │                     │
│                     │ 🟢 SDU envoyé à Physique = PDU Liaison = Trame Ethernet                  │                     │

════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════

│ Physique (1)        │ 📦 SDU reçu = Trame Ethernet                                             │ Physique            │
│                     │ ⚡ Bits transmis : 010101010101…                                          │ Physique            │
│                     │ 🔵 PDU Physique = Signal électrique / optique / radio (unité : Bits)     │                     │
│                     │ 🟢 SDU transmis = mêmes bits → support physique                          │                     │

════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
```

💡 Explications :
- 🟢 SDU = ce que la couche reçoit de la couche supérieure
- 🔵 PDU = donnée encapsulée par la couche
- 🔲 Header / Trailer = info ajoutée pour le transport et le contrôle
- ⚡ Payload / Bits = données utiles transportées

--- 
## 9️⃣ Exemple concret : dépannage réseau

### Problème
> Impossible d’accéder à un site web

### Réflexe OSI – Méthode de raisonnement

1. Couche 1 : câble, signal, interface physique -> OK ?  
2. Couche 2 : carte réseau, trames -> OK ?  
3. Couche 3 : adresse IP, routage -> valide ?
4. Couche 4 : ports TCP 80 / 443 -> ouvert ?
5. Couche 7 : service HTTP -> actif ?

👉 OSI fournit une **méthodologie structurée de diagnostic**.

---

### Réflexe TCP/IP – Outils réels

- `ping`
- `traceroute`
- `netstat`
- `wireshark`

👉 TCP/IP fournit les **outils concrets d’analyse**.

---

## 8️⃣ Pourquoi OSI est toujours enseigné

### 🎓 En formation
- Structure mentale claire
- Vocabulaire universel
- Base solide pour l’apprentissage réseau

### 🛠 En entreprise
- Analyse d’incidents
- Documentation technique
- Communication entre équipes

---

## 🔟 Pourquoi TCP/IP est incontournable

- Internet repose entièrement sur TCP/IP
- Implémenté par tous les systèmes d’exploitation
- Performant et robuste
- Évolutif
- Stable depuis plusieurs décennies

---

## 1️⃣1️⃣ Cas réel : analyse avec Wireshark

Lors de l’analyse d’un paquet réseau :

- Ethernet → couche 2
- IP → couche 3
- TCP → couche 4
- HTTP → couche 7

👉 Le **modèle OSI est utilisé pour lire et comprendre**  
👉 Les **protocoles TCP/IP sont observés dans les paquets réels**

---

## 1️⃣3️⃣ Résumé essentiel

- OSI structure la compréhension
- TCP/IP assure le fonctionnement
- Les deux modèles sont complémentaires

---

## 1️⃣4️⃣ Phrase clé à retenir

❝ OSI est une méthode de pensée,  
TCP/IP est une réalité technique ❞
