# FICHE 04 – La naissance du modèle OSI

## 1️⃣ Contexte : prolifération des réseaux propriétaires

À la fin des années 1970, l’informatique se développe rapidement. Les entreprises et universités utilisent des réseaux fermés créés par chaque constructeur :  

- IBM → SNA  
- DEC → DECnet  
- Xerox → XNS  

Résultat : ces réseaux ne communiquent pas entre eux. Chaque organisation doit gérer **des systèmes incompatibles**, limitant le partage d’informations et la collaboration.  

---

## 2️⃣ Le besoin de normalisation

Face à cette situation, les États, universités et entreprises constatent qu’un **réseau mondial ouvert** est impossible sans **standards universels**.  

La **ISO (International Organization for Standardization)** prend l’initiative de créer un cadre conceptuel indépendant des technologies et des constructeurs : le **modèle OSI (Open Systems Interconnection)**, publié officiellement en 1984.  

Objectifs principaux :  

- Fournir un **cadre théorique universel**  
- Décomposer la communication en **unités logiques et compréhensibles**  
- Faciliter la **normalisation et l’enseignement des réseaux**  

---

## 3️⃣ Le découpage en 7 couches

L’ISO choisit un découpage **ni trop fin, ni trop grossier**, afin que chaque couche :  

- Rende un **service à la couche supérieure**  
- Utilise le **service de la couche inférieure**  
- Ne se préoccupe **que de sa fonction spécifique**  

Les 7 couches OSI sont :  

1. **Physique** → transmission des bits sur un support  
2. **Liaison** → fiabilité de la transmission entre deux nœuds adjacents  
3. **Réseau** → routage des paquets vers la destination  
4. **Transport** → fiabilité de bout en bout et contrôle de flux  
5. **Session** → gestion des échanges et dialogues  
6. **Présentation** → traduction des formats, chiffrement, compression  
7. **Application** → interface utilisateur et applications réseau  

---

## 4️⃣ Avantages du modèle OSI

- **Abstraction claire** : chaque couche a un rôle précis  
- **Interopérabilité** : facilite la compatibilité entre technologies différentes  
- **Pédagogie** : outil idéal pour enseigner et comprendre les réseaux  
- **Maintenance et debug** : plus simple de localiser les problèmes  

⚠️ À noter : OSI est **un modèle théorique**, pas un protocole à implémenter. Il sert de **grille de lecture**, tandis que TCP/IP reste le **réseau opérationnel réel**.

---

## 5️⃣ Limites et adoption

- Trop **complexe pour être implémenté intégralement**  
- **Déploiement lent** dans les environnements réels  
- Mais reste une **référence universelle pour la compréhension des réseaux**, utilisée dans la formation et la conception de protocoles.  

---

### Encadré pédagogique – Acteurs et concepts à retenir

| Acteur / Organisme | Rôle |
|-------------------|------|
| ISO               | Normalisation et création du modèle OSI |
| Constructeurs (IBM, DEC, Xerox…) | Réseaux propriétaires ayant motivé la standardisation |
| Universités & laboratoires | Adoption et expérimentation des concepts de couche |

---

Le modèle OSI fournit une grille théorique pour comprendre la communication en couches, concept qui sera mis en pratique par TCP/IP dans les réseaux opérationnels.
