# FICHE 09 – Voyage complet d’un mail : APDU → SDU → PDU

## 1️⃣ Contexte

Cette fiche illustre concrètement **comment une donnée (mail) traverse toutes les couches réseau**, en utilisant les notions d’**APDU, SDU et PDU** vues dans la fiche 08.  

Le mail choisi :  

```mardown
From: alice@exemple.com
To: bob@exemple.com
Subject: Salut
bonjour ça va
```


Chaque couche réseau ajoute sa propre “enveloppe” (header), transmet la donnée encapsulée, et la couche réceptrice retire cette enveloppe lors de la réception.

---

## 2️⃣ Parcours couche par couche

### 🟦 1. Couche Application (SMTP)

- **Entrée** : le mail rédigé par Alice  
- **Action** : production de l’APDU (donnée compréhensible par SMTP)  
- **Sortie** : APDU


```mardown
[APDU SMTP]
From: alice@exemple.com
To: bob@exemple.com
Subject: Salut
bonjour ça va
```

---

### 🟨 2. Couche Transport (TCP)

- **Entrée** : APDU fournie par la couche supérieure  
- **Action** : encapsulation dans un **segment TCP**, ajout du header TCP (ports source/destination, numéros de séquence, contrôle de flux)  
- **Sortie** : **PDU Transport**


```mardown
[TCP HEADER]
[APDU SMTP]
```


---

### 🟥 3. Couche Réseau (IP)

- **Entrée** : segment TCP  
- **Action** : ajout du header IP (adresses source/destination, TTL, protocole)  
- **Sortie** : **Paquet IP (PDU Réseau)**


```mardown
[IP HEADER]
[TCP HEADER]
[APDU SMTP]
```


---

### 🟩 4. Couche Liaison (Ethernet)

- **Entrée** : paquet IP  
- **Action** : ajout du header Ethernet (MAC source/destination) + trailer CRC  
- **Sortie** : **Trame Ethernet (PDU Liaison)**


```mardown
[ETH HEADER]
[IP HEADER]
[TCP HEADER]
[APDU SMTP]
[CRC]
```

---

### ⚡ 5. Couche Physique

- **Entrée** : trame Ethernet  
- **Action** : conversion en bits pour transmission sur le câble ou les ondes  
- **Sortie** : flux de bits transmis

010101010101010101...


---

## 3️⃣ Schéma visuel ASCII


```text
📧 Application (SMTP)
┌─────────────────────────────┐
│          [APDU]             │
│  Contenu compréhensible     │
│  par la couche applicative  │
└─────────────────────────────┘
              │ SDU = APDU pour couche Transport
              ▼
⚡ Transport (TCP)
┌─────────────────────────────┐
│        [TCP HEADER]         │
│        [APDU]               │
│  Segment TCP → PDU transport│
└─────────────────────────────┘
              │ SDU = Segment TCP pour couche Réseau
              ▼
🌐 Réseau (IP)
┌─────────────────────────────┐
│         [IP HEADER]         │
│         [TCP HEADER]        │
│         [APDU]              │
│   Paquet IP → PDU réseau    │
└─────────────────────────────┘
              │ SDU = Paquet IP pour couche Liaison
              ▼
🔗 Liaison (Ethernet)
┌─────────────────────────────────┐
│          [ETH HEADER]           │
│          [IP HEADER]            │
│          [TCP HEADER]           │
│          [APDU]                 │
│          [CRC]                  │
│  Trame Ethernet → PDU liaison   │
└─────────────────────────────────┘
              │ SDU = Trame Ethernet pour couche Physique
              ▼
⚡ Physique
Bits transmis : 010101010101010101...
(PDU physique → signal électrique / optique / radio)
```






```text

## 3️⃣ Schéma visuel ASCII

🧑‍💻 Couche APPLICATION
(regroupe OSI couche 7 • 6 • 5 dans TCP/IP couche Application )
┌─────────────────────────────────────────────┐
│                 APDU                        │
│  SMTP / HTTP / FTP / DNS                    │
│  - Donnée compréhensible par l’application  │
│  - Encodage, session, format                │
└─────────────────────────────────────────────┘
                │ SDU = APDU pour couche Transport
                ▼

🚚 Couche TRANSPORT 
(OSI couche 4 dans TCP/IP couche Transport)
┌─────────────────────────────────────────────┐
│              TCP HEADER                     │
│---------------------------------------------│
│                 APDU                        │
│        Segment TCP = PDU Transport          │
└─────────────────────────────────────────────┘
                │ SDU = Segment TCP pour couche Réseau
                ▼

🌐 Couche RÉSEAU
(OSI couche 3 dans TCP/IP couche Réseau)
┌─────────────────────────────────────────────┐
│               IP HEADER                     │
│---------------------------------------------│
│             TCP HEADER                      │
│---------------------------------------------│
│                 APDU                        │
│          Paquet IP = PDU Réseau             │
└─────────────────────────────────────────────┘
                │ SDU = Paquet IP pour couche Liaison
                ▼

🔗 Couche LIAISON
(OSI couche 2 dans TCP/IP couche Réseau)
┌───────────────────────────────────────────────────┐
│              ETHERNET HEADER                      │
│---------------------------------------------------│
│                 IP HEADER                         │
│---------------------------------------------------│
│                TCP HEADER                         │
│---------------------------------------------------│
│                    APDU                           │
│---------------------------------------------------│
│                     CRC                           │
│           Trame Ethernet = PDU Liaison            │
└───────────────────────────────────────────────────┘
                │ SDU = Trame Ethernet pour couche Physique
                ▼

⚡ Couche PHYSIQUE
(OSI couche 1 dans TCP/IP couche Physique)
┌─────────────────────────────────────────────┐
│        010101010011010101010101...          │
│   Signal électrique / optique / radio       │
└─────────────────────────────────────────────┘
```

✅ Chaque bloc représente :

- L’**APDU** originale au départ  
- La **SDU**, qui est la donnée vue par la couche suivante  
- La **PDU**, qui inclut l’APDU et le header spécifique de la couche  

---

## 4️⃣ À la réception (désencapsulation)

Chaque couche, du bas vers le haut, effectue :

1. Lecture du header  
2. Interprétation des champs  
3. Retrait du header  
4. Transmission de la donnée vers la couche supérieure  

Physique -> Liaison -> Réseau -> Transport -> Application


> Jusqu’à retrouver l’**APDU originale** produite par l’application.

---

## 5️⃣ Points clés à retenir

- **Chaque couche ajoute / retire sa propre enveloppe**, la donnée originale ne change pas.  
- **APDU** : ce que produit et comprend l’application  
- **SDU** : ce que reçoit la couche suivante (point de vue d’une couche)  
- **PDU** : unité transportée, avec en-têtes spécifiques à la couche  
- L’**encapsulation / décapsulation** est au cœur de la modularité et de l’interopérabilité réseau  
- Cette approche permet un **diagnostic précis** et une **maintenance simplifiée**

---

## 6️⃣ Phrase clé de la FICHE 09

> « Une donnée traverse le réseau intacte, seule son enveloppe change à chaque couche. »

---

### Encadré pédagogique – Termes à retenir

| Terme | Définition |
|-------|------------|
| APDU | Donnée vue par la couche applicative |
| SDU | Donnée fournie à la couche suivante |
| PDU | Donnée transportée par la couche, incluant les en-têtes |
| Encapsulation | Ajout d’en-têtes par une couche pour le transport |
| Décapsulation | Retrait des en-têtes pour restituer la donnée |



> Jusqu’à retrouver l’**APDU originale** produite par l’application.

---

## 5️⃣ Points clés à retenir

- **Chaque couche ajoute / retire sa propre enveloppe**, la donnée originale ne change pas.  
- **APDU** : ce que produit et comprend l’application  
- **SDU** : ce que reçoit la couche suivante (point de vue d’une couche)  
- **PDU** : unité transportée, avec en-têtes spécifiques à la couche  
- L’**encapsulation / décapsulation** est au cœur de la modularité et de l’interopérabilité réseau  
- Cette approche permet un **diagnostic précis** et une **maintenance simplifiée**

---

## 6️⃣ Phrase clé de la FICHE 09

> « Une donnée traverse le réseau intacte, seule son enveloppe change à chaque couche. »

---

### Encadré pédagogique – Termes à retenir

| Terme | Définition |
|-------|------------|
| APDU | Donnée vue par la couche applicative |
| SDU | Donnée fournie à la couche suivante |
| PDU | Donnée transportée par la couche, incluant les en-têtes |
| Encapsulation | Ajout d’en-têtes par une couche pour le transport |
| Décapsulation | Retrait des en-têtes pour restituer la donnée |




