# FICHE 07 – Données, bits et octets : comprendre ce qui circule réellement

## 1️⃣ Contexte

Pour comprendre les réseaux, il ne suffit pas de connaître les modèles et les protocoles. Il faut savoir **ce qui circule réellement sur les câbles et ondes**.  

Une donnée réseau est **une représentation binaire de l’information**, que ce soit du texte, une image ou un fichier. Cette donnée subit des transformations successives pour pouvoir être transmise efficacement, de la couche applicative jusqu’au support physique.

---

## 2️⃣ Donnée humaine vs donnée réseau

### 👤 Donnée humaine

Quand on écrit :

```text
bonjour ça va
```


Pour l’utilisateur, c’est :

* du texte  
* du sens  
* des mots

### 💻 Donnée réseau

Pour une machine, ce texte devient :

* une suite de symboles  
* encodés  
* transformés  
* découpés  
* transmis

> Le réseau ne comprend pas le sens, il transporte des **valeurs numériques**.

---

## 3️⃣ Le bit : unité fondamentale

### 📘 Définition

Un **bit** (binary digit) est la plus petite unité d’information :

* 0 ou 1  

### 🔹 Physique

* tension basse / haute  
* lumière éteinte / allumée  
* onde radio absente / présente

---

## 4️⃣ L’octet (byte)

### 📘 Définition

* 1 octet = 8 bits

### 🔹 Pourquoi 8 ?

* compromis historique  
* suffisant pour coder des caractères

---

## 5️⃣ Comment un caractère devient des bits : encodage

### 🧪 ASCII (simplifié)

Caractère | Bits  
----------|-----  
A         | 01000001  
B         | 01000010  
...       | ...

> Limite : pas d’accents, caractères spéciaux limités

### 🌍 UTF-8 (moderne)

* Compatible ASCII  
* Gère tous les caractères (é, €, 汉…)  

Exemple :  

```text
é = 11000011 10101001
```


---

## 6️⃣ Donnée brute vs donnée structurée

| Type | Description | Exemple |
|------|------------|---------|
| Donnée brute | Bits ou octets sans contexte | Fichier binaire inconnu |
| Donnée structurée | Bits organisés selon un protocole | Paquet TCP, trame Ethernet |

> Le réseau fonctionne **toujours avec des structures** pour transporter correctement l’information.

---

## 7️⃣ Pourquoi structurer les données ?

Sans structure :  

* impossible de savoir où commence un message  
* impossible de savoir à qui il est destiné  
* impossible de le reconstruire  

> D’où l’ajout de **headers / en-têtes** à chaque couche.

---

## 8️⃣ Les en-têtes (headers) et payload

| Élément | Rôle | Exemple |
|---------|------|--------|
| Header | Métadonnées et informations de contrôle | Adresse IP, port, numéro de séquence, type de protocole |
| Payload | Données utiles pour l’application | Texte du mail, fichier, image |

> Chaque couche considère le **PDU de la couche supérieure** comme son payload.

---

## 9️⃣ Encapsulation et décapsulation

Chaque couche réseau ajoute un **en-tête** et parfois un **footer** :

| Couche | En-tête / Footer | Rôle |
|-------|-----------------|------|
| Application | Header applicatif | Infos spécifiques au protocole (ex. HTTP, SMTP) |
| Transport | Header TCP/UDP | Numéros de ports, contrôle de flux, fiabilité |
| Réseau | Header IP | Adresses source et destination, routage |
| Liaison | Header / Footer Ethernet | Adresse MAC, détection d’erreurs |
| Physique | Signaux électriques / optiques | Transmission physique sur le support |

> 🔄 Ce processus s’appelle **encapsulation**, et la **décapsulation** inverse le processus à l’arrivée.

---

## 1️⃣0️⃣ Visualisation pédagogique : “Message dans une enveloppe”

Imagine un message envoyé par la poste :

1. Écrire le texte → couche Application  
2. Mettre le texte dans une enveloppe avec adresse → couches Transport/Réseau  
3. Choisir le transporteur et route → couches Réseau/Liaison  
4. Acheminer via camion, avion, route → couche Physique  

> Chaque couche **ignore le contenu exact des autres**, mais ajoute ce dont la couche suivante aura besoin.

---

## 1️⃣1️⃣ Points clés à retenir

1. Les données circulent **toujours sous forme binaire**.  
2. Chaque couche **structure et protège** la donnée pour le transport.  
3. L’encapsulation permet de **séparer les responsabilités** et de rendre le réseau **fiable et évolutif**.  
4. Comprendre les unités (bit / octet) et l’encodage est crucial pour **diagnostiquer et analyser le trafic réseau**.

---

## 1️⃣2️⃣ Phrase clé de la FICHE 07

> « Dans les réseaux, tout commence par le bit ; la manière dont il est structuré et encapsulé détermine si l’information arrive intacte et compréhensible. »

---

### 1️⃣3️⃣ Encadré pédagogique – Termes à retenir

| Terme | Définition |
|-------|------------|
| Bit | Unité minimale d’information : 0 ou 1 |
| Octet | Groupe de 8 bits |
| Encodage | Règles de transformation des données humaines en bits |
| En-tête / Footer | Informations ajoutées par chaque couche pour le transport |
| Encapsulation / Décapsulation | Ajout ou retrait des en-têtes pour circuler dans le réseau |


