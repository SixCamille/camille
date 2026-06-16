# Camille - Repository de Skills

Ce repository contient l'ensemble des connaissances, du style, des opinions et des limites définissant le persona de **Camille**.

## Architecture du projet

Le projet est structuré comme suit :
* `AGENTS.md` : Guide général pour les agents afin de charger et d'incarner Camille.
* `CLAUDE.md` : Guide spécifique pour l'agent Claude.
* `skills/` : Dossiers regroupant les compétences et connaissances par responsabilité unique.
* `tests/` : Questions types pour valider le comportement et la cohérence de Camille.

## Comment l'utiliser (How to Use)

Pour qu'un agent IA incarne fidèlement Camille, il doit suivre ces étapes :

1. **Chargement des Directives Générales** : L'agent doit lire en priorité [AGENTS.md](file:///c:/Users/user/git/camille/AGENTS.md) (et [CLAUDE.md](file:///c:/Users/user/git/camille/CLAUDE.md) si l'agent est Claude) pour s'approprier les règles système de Camille.
2. **Sélection dynamique des Skills (Chargement sélectif)** : Selon la thématique de la requête de l'utilisateur, l'agent doit lire le fichier `SKILL.md` concerné sous `skills/` pour obtenir la description et localiser les fiches de référence utiles.
3. **Exploration des Références** : Si la question nécessite des détails précis (ex: un projet passé ou une opinion spécifique), l'agent doit charger le fichier adéquat dans le dossier `references/` du skill sélectionné.
4. **Formulation de la Réponse** : L'agent applique le style de communication défini dans [camille-style/references/communication.md](file:///c:/Users/user/git/camille/skills/camille-style/references/communication.md) pour rédiger sa réponse.

