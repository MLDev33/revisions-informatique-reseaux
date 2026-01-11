# FICHE 01 – LES FONDATIONS DES RÉSEAUX

## 1️⃣ Pourquoi les réseaux existent-ils ?

Il était une fois, dans les années 1950 et 1960, un monde informatique très différent du nôtre. Chaque ordinateur était **une île isolée** : énorme, coûteux, réservé à quelques organisations, et incapable de communiquer avec un autre. Si l’on voulait transférer un programme ou des données, il fallait passer par des moyens physiques : disquettes, bandes magnétiques… ou ce que l’on appelait humoristiquement le **“sneakernet”**, le réseau à pied.  

Mais très vite, les ingénieurs et scientifiques ont rencontré un vrai problème : **comment faire communiquer des machines différentes**, construites par des fabricants distincts, situées à des endroits éloignés, **sans intervention humaine** ?  

En réalité, ce problème se décompose en plusieurs défis :

1. **Compréhension** : IBM ne parlait pas le même langage que DEC, et les formats de données étaient incompatibles.  
2. **Transmission** : comment envoyer des données à distance ? Électrique, optique, radio…  
3. **Fiabilité** : que se passe-t-il si un message est perdu, dupliqué, ou arrive dans le désordre ?  
4. **Évolutivité** : communiquer entre deux machines est simple, mais entre 10, 100, voire un million ?  

Face à ces défis, la solution fondamentale s’est imposée : **standardiser et découper le problème**. Les ingénieurs ont compris qu’on ne pouvait pas tout résoudre d’un coup. Il fallait **découper la communication en couches**, chaque couche ayant une **fonction précise**, et ne s’occupant que de ce qui la concernait.  

---

## 2️⃣ Qu’est-ce qu’une couche réseau ?

Une couche réseau n’est **pas un logiciel ni un matériel**. C’est une **abstraction fonctionnelle** : elle fournit un service à la couche supérieure, utilise celui de la couche inférieure, et communique logiquement avec sa couche équivalente distante.  

**Analogie : une usine de livraison**  

Pour comprendre le concept de couches réseau, imagine une usine de livraison. Chaque étape de l’acheminement d’un colis correspond à une couche réseau, avec un rôle précis.


| Étape                   | Rôle         |
| ----------------------- | ------------ |
| Écriture du message     | Contenu      |
| Mise en enveloppe       | Présentation |
| Choix du transporteur   | Transport    |
| Adresse du destinataire | Routage      |
| Camion / avion          | Liaison      |
| Route / câble           | Physique     |

> 👉 Chaque acteur fait son travail et ne se préoccupe pas du reste.

## 💡 Avantages des couches

* 🔧 Maintenance facile  
* 🔄 Interopérabilité  
* 🧠 Compréhension humaine  
* 🕵️ Debug réseau possible  

### ⚠️ Sans couches

* Tout est mélangé  
* Impossible à analyser  
* Impossible à faire évoluer


**sans connaître les détails des autres étapes**.  

Cette méthode présente de nombreux avantages : maintenance simplifiée, interopérabilité, compréhension humaine et facilité de debug.  

---

## 3️⃣ Pourquoi les réseaux ont explosé

Dans les années 1960–70, universités, armée et laboratoires de recherche ont commencé à **partager des ordinateurs et des données**. Le besoin était clair : communiquer rapidement, partager la puissance de calcul et les informations.  

C’est ainsi qu’est né **ARPANET**, le premier réseau expérimental financé par le **DoD américain (Département de la Défense)**. ARPANET avait un objectif ambitieux : créer un réseau résilient capable de **survivre à la perte de nœuds**, donnant naissance à deux concepts fondamentaux : **la commutation de paquets** et le **routage dynamique**.  

---

## 4️⃣ Deux visions apparaissent

À partir d’ARPANET, deux visions complémentaires ont émergé :

1. **La vision académique / théorique** → **modèle OSI**  
   - Organisation : **ISO (International Organization for Standardization)**  
   - Objectif : créer un modèle universel, structuré et pédagogique  
   - Approche : **top-down** (du concept vers l’implémentation)

2. **La vision pragmatique / terrain** → **TCP/IP**  
   - Créateurs : **Vint Cerf et Bob Kahn** à la **DARPA**  
   - Objectif : que ça fonctionne rapidement sur ARPANET  
   - Approche : **bottom-up** (expérimentation et itération)

⚠️ À ce stade, il est crucial de comprendre :  
- OSI n’est pas un protocole, c’est une **carte conceptuelle**.  
- TCP/IP n’est pas qu’un modèle, c’est un **réseau opérationnel réel**.

---

## 5️⃣ Histoire détaillée : OSI vs TCP/IP

### Contexte historique
À la fin des années 1970, les ordinateurs se multiplient, mais chaque constructeur invente son propre réseau : IBM → SNA, DEC → DECnet, Xerox → XNS, et d’autres encore. Résultat : réseaux fermés, incompatibles, impossibles à faire communiquer.  

### Le besoin mondial
États, universités et entreprises comprennent que **sans standards ouverts, un réseau mondial est impossible**. L’ISO crée alors le **modèle OSI (Open Systems Interconnection)**, publié officiellement en 1984. Son objectif : fournir un **cadre théorique universel**, indépendant des technologies, découpé en **7 couches logiques**.  

Pourquoi 7 couches ? L’ISO a cherché un découpage **ni trop fin, ni trop grossier**, chaque couche rendant service à la couche supérieure et utilisant celle du dessous.  

**Mais OSI avait un problème** : trop théorique, complexe et lent à implémenter. Pendant ce temps, TCP/IP fonctionne déjà sur ARPANET et s’impose naturellement comme le réseau de terrain.  

---

## 6️⃣ Concepts clés à retenir

- **Couche** : abstraction fonctionnelle qui remplit un rôle précis.  
- **Encapsulation / Décapsulation** : mécanisme par lequel chaque couche ajoute ou retire des en-têtes pour transporter une donnée.  
- **SDU (Service Data Unit) / PDU (Protocol Data Unit) / APDU (Application Protocol Data Unit)** : termes pour décrire comment une donnée est vue et transformée à chaque couche.  
- **Protocole** : ensemble de règles qui définissent le format, l’ordre et la signification des échanges.  

---

## 7️⃣ Phrase clé de la FICHE 01

> « OSI est une **grille de lecture**, TCP/IP est le **moteur réel**. »  

Cette phrase résume toute la philosophie des réseaux : **OSI explique, TCP/IP fait fonctionner**.

---

### Encadré pédagogique – Acteurs et noms à retenir

| Acteur / Organisme | Rôle |
|------------------|------|
| ISO | Normalisation, modèle OSI |
| DARPA | Recherche, développement ARPANET, TCP/IP |
| Vint Cerf & Bob Kahn | Créateurs TCP/IP |
| Universités & laboratoires | Expérimentation, adoption et amélioration des protocoles |
| IBM / DEC / Xerox | Constructeurs de réseaux propriétaires |

---
