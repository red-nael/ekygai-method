---
name: identifiant-en-kebab-case
description: Une ligne qui permet de juger de la pertinence au moment du rappel.
type: user | feedback | projet | reference
---

Un fichier = un seul fait. Le nom du fichier reprend le champ `name`.

**Les quatre types :**

- `user` — qui je suis : métier, expertise, préférences durables
- `feedback` — comment travailler avec moi : corrections données, approches validées
- `projet` — travail en cours, objectifs, contraintes non déductibles du code
- `reference` — pointeurs externes : URL, tableaux de bord, tickets

Pour `feedback` et `projet`, ajouter les deux lignes suivantes :

**Pourquoi :** la raison derrière la règle — sans elle, la règle est appliquée de travers
dès que le contexte change.

**Comment l'appliquer :** l'action concrète attendue la prochaine fois.

Liens vers d'autres mémoires : `[[nom-de-l-autre-memoire]]`. Un lien vers une mémoire qui
n'existe pas encore est acceptable — il marque ce qui reste à écrire.

Toute date relative est convertie en date absolue à l'écriture.

Ne pas consigner ce que le dépôt raconte déjà : structure du code, historique git,
correctifs passés. La mémoire sert à ce qui n'est écrit nulle part.
