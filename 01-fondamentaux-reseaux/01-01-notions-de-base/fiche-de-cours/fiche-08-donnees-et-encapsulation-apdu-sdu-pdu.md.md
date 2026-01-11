# FICHE 08 – APDU, SDU, PDU : comprendre l’encapsulation couche par couche

## 1️⃣ Contexte

Dans un réseau, les données ne circulent pas “à l’état brut”. Chaque couche réseau **emballe et transforme** les informations selon des règles précises. Pour décrire ces transformations, on utilise trois termes clés : **APDU, SDU et PDU**.  

Cette fiche explique ces notions de manière claire et progressive, afin de comprendre **comment une donnée traverse le réseau** et comment chaque couche l’interface.

---

## 2️⃣ Pourquoi ces termes existent

Avant tout :  
APDU / SDU / PDU ne sont **pas des protocoles**.  
Ce sont des termes génériques pour décrire :  

* ce que transporte une couche  
* comment elle le voit  

👉 Ils servent à penser proprement l’encapsulation.

---

## 3️⃣ Le mot clé : Data Unit

**DU = Data Unit → unité de données**  

Le préfixe indique **à quelle couche on se place** :

| Terme | Couche concernée | Description courte |
|-------|-----------------|-----------------|
| APDU | Application | Donnée produite et comprise par l’application |
| SDU | Service | Donnée transmise par la couche supérieure à la couche suivante |
| PDU | Protocol | Donnée transportée par la couche avec en-têtes ajoutés |

---

## 4️⃣ APDU — Application Protocol Data Unit

📘 **Définition**  
L’APDU est l’unité de données de la couche Application.  
👉 C’est :  

* ce que produit l’application  
* ce qu’elle comprend  
* ce qu’elle veut transmettre

🧠 **Exemple concret (SMTP)**  

Mail écrit par Alice :

```mardown
From: alice@exemple.com
To: bob@exemple.com
Subject: Salut
bonjour ça va
```


👉 Cela constitue une **APDU** :  

* Lisible  
* Structurée  
* Compréhensible uniquement par SMTP

---

## 5️⃣ SDU — Service Data Unit

📘 **Définition**  
La SDU est ce qu’une couche reçoit de la **couche supérieure**.  

⚠️ Important : une même donnée est **SDU pour une couche**, et **PDU pour la couche inférieure**.  

🔁 **Exemple** :  

- Couche Transport reçoit l’APDU  
- L’APDU devient la SDU pour la couche Transport  
- La couche ajoute son **header** et produit le PDU

👉 La **SDU est un point de vue**, pas une structure spécifique.

---

## 6️⃣ PDU — Protocol Data Unit

📘 **Définition**  
La PDU est l’unité de données **complète produite par une couche**, incluant le header ajouté pour le transport.

📦 **Structure générique d’une PDU** :

```mardown
[Header de la couche]
[Payload = SDU]
```

---

## 7️⃣ Exemple couche par couche (SMTP → TCP → IP → Ethernet)

| Couche      | SDU reçue       | Header ajouté        | PDU produit               |
|------------|----------------|-------------------|--------------------------|
| Application | —              | —                  | APDU                      |
| Transport  | APDU           | TCP Header         | Segment TCP (PDU transport) |
| Réseau     | Segment TCP    | IP Header          | Paquet IP                 |
| Liaison    | Paquet IP      | Ethernet Header + Trailer | Trame Ethernet         |
| Physique   | Trame Ethernet | —                  | Bits transmis             |

```text
🟦 Application
[SMTP DATA]

🟨 Transport (TCP)
[TCP HEADER][APDU SMTP]

🟥 Réseau (IP)
[IP HEADER][TCP HEADER][APDU]

🟩 Liaison (Ethernet)
[ETH HEADER][IP HEADER][TCP HEADER][APDU][CRC]

⚡ Physique
010101010101...
```

## 8️⃣ À la réception (désencapsulation)

Chaque couche :

- Lit son **header**
- Interprète les champs
- Retire le **header**
- Transmet le reste vers la couche supérieure

👉 Jusqu’à retrouver l’**APDU originale**.

---

## 9️⃣ Visualisation pédagogique : “Chaîne de production alimentaire”

Imagine une usine alimentaire :

- **Ingrédients bruts** → APDU  
- **Préparation et transformation** → SDU  
- **Emballage final avec étiquettes** → PDU  

| Étape de la chaîne      | Correspondance réseau | Action                                |
|-------------------------|--------------------|--------------------------------------|
| Ingrédients bruts       | APDU               | Contenu original                     |
| Préparation / cuisson   | SDU                | Service fourni par la couche supérieure |
| Emballage / étiquetage  | PDU                | Encapsulation pour transport         |

> Chaque poste transforme uniquement sa partie, ignore les autres étapes, et respecte les interfaces (services).

---

## 🔟 Erreurs classiques à éviter

❌ “L’APDU devient un segment”  
❌ “La SDU est une structure spécifique”  

✅ En réalité :  

- L’**APDU** reste intacte  
- Elle est **transportée**, jamais modifiée par les couches basses  

---

## 1️⃣1️⃣ Points clés à retenir

- **APDU** : ce que l’application veut transmettre  
- **SDU** : ce que la couche supérieure fournit à la couche suivante  
- **PDU** : la donnée transportée par la couche, avec ses en-têtes  
- **Encapsulation / décapsulation** : mécanismes fondamentaux pour la modularité et l’interopérabilité  
- Cette approche est au **cœur du fonctionnement réseau moderne**

---

## 1️⃣2️⃣ Phrase clé de la FICHE 08

> « APDU, SDU et PDU : la même donnée, vue et transformée par chaque couche pour voyager efficacement dans le réseau. »

---

### Encadré pédagogique – Termes à retenir

| Terme         | Définition                                         |
|---------------|--------------------------------------------------|
| APDU          | Donnée vue par la couche applicative            |
| SDU           | Donnée fournie à la couche suivante            |
| PDU           | Donnée transportée par la couche, incluant les en-têtes |
| Encapsulation | Ajout d’en-têtes par une couche pour le transport |
| Décapsulation | Retrait des en-têtes pour restituer la donnée  |

---


 

