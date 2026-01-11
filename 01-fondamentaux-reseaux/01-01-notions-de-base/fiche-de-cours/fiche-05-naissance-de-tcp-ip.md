# FICHE 05 – naissance de TCP/IP : le modèle qui marche

## 1️⃣ Contexte historique

Au début des années 1970, ARPANET, le réseau expérimental financé par le **DoD américain**, fonctionne déjà avec succès pour relier quelques universités et laboratoires. Cependant, la multiplication des machines et des types de réseaux impose un défi majeur : **faire communiquer des systèmes hétérogènes de manière fiable et évolutive**.  

Les réseaux propriétaires (IBM → SNA, DEC → DECnet, Xerox → XNS) sont fermés et incompatibles. L’ISO propose le **modèle OSI** pour normaliser et conceptualiser les échanges, mais ce modèle reste théorique et complexe à implémenter.  

Dans ce contexte, **Vint Cerf et Bob Kahn** à la **DARPA** développent TCP/IP, un ensemble de protocoles pragmatique et fonctionnel, pensé pour l’**Internet réel** plutôt que pour un cadre conceptuel.

---

## 2️⃣ Philosophie et principes clés

TCP/IP repose sur quelques principes fondamentaux :

1. **Intelligence aux extrémités**  
   - Les ordinateurs (hosts) gèrent la majorité de la logique et des décisions.  
   - Le réseau lui-même reste simple et ne fait que transmettre des paquets.

2. **Robustesse et fiabilité**  
   - Les messages sont découpés en **paquets** indépendants, pouvant suivre des chemins différents.  
   - Chaque paquet contient l’adresse de destination, permettant un routage dynamique.

3. **Interopérabilité**  
   - TCP/IP fonctionne sur différents types de supports physiques et systèmes d’exploitation.  
   - Chaque réseau local ou longue distance peut se connecter sans adapter le protocole fondamental.

4. **Pragmatisme**  
   - L’objectif principal est que **ça marche**, même si la théorie est imparfaite.  
   - L’itération et l’expérimentation priment sur la perfection conceptuelle.

---

## 3️⃣ Les composants du protocole

TCP/IP est en réalité un **ensemble de protocoles complémentaires**. Les deux plus importants sont :

| Protocole | Fonction principale |
|-----------|------------------|
| **TCP** (Transmission Control Protocol) | Assure la fiabilité, le contrôle d’ordre, la gestion des erreurs et le flux de données entre deux machines |
| **IP** (Internet Protocol) | Assure le routage des paquets sur le réseau, en se basant sur les adresses IP |

D’autres protocoles viennent compléter le système, par exemple **UDP** pour les communications rapides mais non fiables, **ICMP** pour le diagnostic réseau, ou **ARP** pour la résolution d’adresses.

---

## 4️⃣ Flag Day 1983

Le **1er janvier 1983**, connu sous le nom de **Flag Day**, marque la transition officielle d’ARPANET vers TCP/IP.  

Tous les nœuds du réseau doivent désormais utiliser TCP/IP pour communiquer. Cette date symbolise **l’adoption globale d’un protocole pragmatique et opérationnel**, qui permet l’expansion rapide d’Internet.

---

## 5️⃣ Analogie “Chaîne de poste pragmatique”

Pour comprendre TCP/IP, on peut utiliser une analogie différente de celle de l’usine de livraison (OSI) : **une chaîne postale moderne**.

| Étape                     | Rôle dans TCP/IP |
|---------------------------|-----------------|
| Découpage du message       | TCP : fragmentation et numérotation des paquets |
| Adresse sur chaque paquet  | IP : routage à travers le réseau |
| Transport par camion/avion | IP : acheminement vers le réseau suivant |
| Réassemblage à l’arrivée   | TCP : reconstruction du message complet |

> Chaque étape se concentre sur sa tâche, sans connaître la logique interne des autres étapes. L’interface entre les étapes garantit que l’ensemble fonctionne, même si l’un des composants change.

---

## 6️⃣ Adoption et impact

TCP/IP a rapidement dépassé ARPANET pour devenir la norme mondiale, en raison de sa **simplicité, robustesse et interopérabilité**.  

- Universités, entreprises et opérateurs l’adoptent.  
- Il permet l’expansion d’Internet à l’échelle mondiale.  
- La philosophie “intelligence aux extrémités” influence encore les réseaux modernes et les applications distribuées.

---

## 7️⃣ Concepts à retenir

- **TCP/IP = moteur opérationnel** qui fait fonctionner le réseau.  
- **OSI = grille de lecture** conceptuelle pour comprendre les échanges.  
- **Paquets indépendants** et **adresses IP** = fondation du routage dynamique.  
- **Fiabilité et contrôle** sont assurés par TCP au-dessus d’un réseau IP simple.

---

## 8️⃣ Phrase clé de la FICHE 05

> « TCP/IP est le moteur réel qui a permis à ARPANET de devenir Internet, tandis qu’OSI reste le cadre de lecture universel. »

---

### Encadré pédagogique – Acteurs et organismes

| Acteur / Organisme | Rôle |
|------------------|------|
| DARPA | Financement et coordination d’ARPANET |
| Vint Cerf & Bob Kahn | Créateurs de TCP/IP |
| Universités & laboratoires | Adoption et expérimentation sur ARPANET |
| IBM / DEC / Xerox | Constructeurs de réseaux hétérogènes intégrant TCP/IP |

