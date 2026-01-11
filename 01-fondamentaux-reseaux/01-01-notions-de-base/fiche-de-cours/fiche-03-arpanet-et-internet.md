# FICHE 03 – ARPANET et la naissance d’Internet

## 1️⃣ Contexte historique

À la fin des années 1960, la multiplication des ordinateurs dans les universités, les laboratoires et l’armée américaine créait un besoin urgent : **partager rapidement des informations et des ressources de calcul**.  

Chaque réseau était isolé, propriétaire et incompatible. Les chercheurs et ingénieurs avaient donc besoin d’une **infrastructure capable de relier différents types d’ordinateurs sur de longues distances**, tout en résistant aux pannes et aux interruptions.

---

## 2️⃣ Naissance d’ARPANET

Pour répondre à ce besoin, la **DARPA (Defense Advanced Research Projects Agency)**, branche du Département de la Défense américain, finance un projet expérimental : **ARPANET**.  

Objectifs principaux :  

- Créer un **réseau résilient**, capable de survivre à la perte de nœuds ou de liens  
- Tester des **méthodes de communication innovantes**, indépendantes du constructeur ou de la technologie  
- Fournir un **laboratoire vivant** pour le développement de protocoles  

ARPANET constitue ainsi le premier réseau à commutation de paquets, où **les données sont découpées en petits blocs** et envoyées indépendamment vers leur destination. Ce mécanisme permet une meilleure utilisation des lignes de communication et une **résilience naturelle aux pannes**.

---

## 3️⃣ Commutation de paquets et routage dynamique

Deux concepts fondamentaux émergent de l’expérience ARPANET :  

1. **Commutation de paquets**  
   - Les messages sont découpés en paquets  
   - Chaque paquet peut emprunter un chemin différent pour atteindre sa destination  
   - Les paquets sont réassemblés à l’arrivée  

2. **Routage dynamique**  
   - Les nœuds du réseau choisissent le meilleur chemin en fonction de la congestion et des pannes  
   - Le réseau s’adapte en temps réel, garantissant la livraison même en cas de défaillance partielle  

Ces innovations posent les bases de **l’Internet moderne**, où fiabilité, performance et adaptabilité sont assurées par des mécanismes intelligents plutôt que par un contrôle centralisé.

---

## 4️⃣ Du projet militaire au réseau mondial

ARPANET commence comme un projet limité à quelques universités et centres de recherche, mais son succès conduit rapidement à une adoption plus large :  

- Les laboratoires universitaires utilisent le réseau pour **partager données et logiciels**  
- Les ingénieurs expérimentent de nouveaux protocoles pour **augmenter la compatibilité et l’efficacité**  
- L’expérience démontre qu’un **réseau universel, ouvert et standardisé est possible**  

Ce passage du réseau expérimental à un réseau opérationnel constitue la **transition clé vers TCP/IP et l’Internet tel que connu aujourd’hui**.

---

## 5️⃣ Points clés à retenir

- **ARPANET = laboratoire vivant** pour tester communication et protocoles  
- **Résilience et adaptabilité** = principes centraux  
- **Commutation de paquets + routage dynamique** = fondations techniques de l’Internet  
- **Passage du militaire au civil** = démonstration du potentiel universel des réseaux  

---

### Encadré pédagogique – Acteurs à retenir

| Acteur / Organisme | Rôle |
|-------------------|------|
| DARPA             | Financement et supervision du projet ARPANET |
| Universités       | Expérimentation, adoption et amélioration des protocoles |
| Centres de recherche | Développement des premiers protocoles de communication |
| Ingénieurs réseau | Conception du routage dynamique et de la commutation de paquets |  

---

Cette étape illustre comment la genèse des réseaux a conduit naturellement à la structuration en couches et à la normalisation des standards, préparant le terrain pour comprendre OSI et TCP/IP.
