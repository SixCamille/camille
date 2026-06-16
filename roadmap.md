# Roadmap de création d'un repository de skills pour un persona

## 🎯 Objectif

Créer un repository permettant à un agent (Claude, Codex ou autre) d'incarner un personnage nommé **Camille** de manière cohérente, en utilisant une architecture modulaire basée sur des skills.

Le projet doit être facilement maintenable, extensible et optimisé pour ne charger que les informations nécessaires à chaque requête.

---

# Étape 1 – Initialisation du projet

Créer l'arborescence suivante :

```
camille-skills/
├── AGENTS.md
├── CLAUDE.md
├── README.md
├── skills/
└── tests/
```

Créer également un `.gitignore` adapté et initialiser le dépôt Git.

---

# Étape 2 – Créer les skills principaux

Créer un dossier par responsabilité.

```
skills/
├── camille-identite/
├── camille-style/
├── camille-connaissances/
├── camille-opinions/
├── camille-limites/
├── camille-maniere-de-repondre/
└── camille-faq/
```

Chaque dossier contient au minimum :

```
SKILL.md
```

---

# Étape 3 – Définir les métadonnées des skills

Chaque `SKILL.md` doit commencer par :

```yaml
---
name: camille-identite
description: Utiliser ce skill lorsqu'une question concerne l'identité, le parcours ou le contexte général de Camille.
---
```

La description doit être suffisamment précise pour permettre à l'agent de déterminer quand charger le skill.

---

# Étape 4 – Déplacer les contenus volumineux

Ne jamais mettre plusieurs centaines de lignes dans `SKILL.md`.

Créer un dossier `references/` lorsque nécessaire.

Exemple :

```
camille-connaissances/
├── SKILL.md
└── references/
    ├── biographie.md
    ├── parcours.md
    ├── valeurs.md
    ├── passions.md
    └── anecdotes.md
```

Le `SKILL.md` sert uniquement de guide et renvoie vers ces documents.

---

# Étape 5 – Rédiger AGENTS.md

Le fichier doit être court.

Il doit :

* expliquer que le persona est Camille ;
* indiquer que les connaissances sont réparties dans `skills/` ;
* demander à l'agent de ne charger que les skills utiles ;
* rappeler qu'il ne doit jamais inventer une information absente.

Éviter d'y recopier tout le persona.

---

# Étape 6 – Rédiger CLAUDE.md

Même philosophie que `AGENTS.md`.

Ce fichier adapte uniquement le comportement au fonctionnement de Claude mais ne contient pas les connaissances elles-mêmes.

---

# Étape 7 – Séparer les responsabilités

Vérifier qu'aucune information n'est présente à plusieurs endroits.

Par exemple :

* le ton appartient à `camille-style` ;
* les préférences personnelles appartiennent à `camille-opinions` ;
* la biographie appartient à `camille-connaissances` ;
* les refus et limites appartiennent à `camille-limites`.

Chaque information doit avoir une seule source de vérité.

---

# Étape 8 – Optimiser les noms

Tous les dossiers et fichiers doivent être explicites.

Préférer :

```
biographie.md
valeurs.md
passions.md
questions-frequentes.md
```

à

```
infos.md
divers.md
notes.md
```

Le nom doit permettre de comprendre immédiatement le contenu.

---

# Étape 9 – Ajouter des exemples

Créer un fichier :

```
tests/questions.md
```

contenant des questions telles que :

* Qui es-tu ?
* Quel est ton métier ?
* Quelle est ta philosophie ?
* Quelle est ta plus grande qualité ?
* Quel est ton plat préféré ?
* Comment réponds-tu lorsqu'une information est inconnue ?

Ces questions serviront à valider le comportement du persona.

---

# Étape 10 – Vérifier la non-redondance

Parcourir tout le dépôt et supprimer les duplications.

Objectif :

* une information = un seul emplacement ;
* un style = un seul skill ;
* une biographie = un seul document.

Le repository doit rester simple à maintenir même après plusieurs années.

---

# Étape 11 – Tester le chargement sélectif

Pour chaque question de test, identifier les skills réellement nécessaires.

Exemple :

Question :

> « Quel est ton plat préféré ? »

Skills attendus :

* ✅ camille-opinions

Skills inutiles :

* ❌ camille-connaissances
* ❌ camille-faq
* ❌ camille-style (sauf pour la formulation)

L'objectif est de minimiser les lectures inutiles.

---

# Étape 12 – Vérification finale

Le projet est considéré terminé si :

* chaque skill possède une responsabilité unique ;
* aucune connaissance n'est dupliquée ;
* AGENTS.md et CLAUDE.md restent courts ;
* les documents volumineux sont externalisés ;
* les noms sont explicites ;
* le persona répond de manière cohérente et stable ;
* les tests couvrent les principaux cas d'usage ;
* l'ajout d'une nouvelle information ne nécessite de modifier qu'un seul fichier.
