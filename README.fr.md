# Méthode EKYGAI

**[English](README.md)** · Français

> Une méthode de travail avec un agent de code : une mémoire qui survit à la fin de
> session, et un protocole qui interdit d'écrire du code avant d'avoir lu l'existant.

Rodée sur plusieurs années de développement réel, d'abord sur [EKYGAI](https://ekygai.com).
Ce dépôt n'en publie que la méthode — jamais le produit.

---

## Le problème

Un agent de code comprend une architecture en deux heures de conversation, puis la session
se termine et tout part. Et si on ne lui impose rien, il commence à écrire dès qu'il croit
avoir compris — ce qui arrive très vite. Le résultat compile, a l'air juste, ignore la
moitié des conventions du dépôt. Il passe le sprint. Il casse au trimestre.

Deux réponses, qui ne tiennent pas l'une sans l'autre.

## Les deux parties

| | |
|---|---|
| **[Partie I — Deux couches de mémoire](fr/01-memoire.md)** | Une capture automatique par hooks, un index écrit à la main. Où vivent les faits, ce qui les périme, ce que ça coûte — y compris ce que ça envoie hors de votre machine. |
| **[Partie II — Avant le code, après le code](fr/02-methode.md)** | Le protocole `ULTRA PLAN` avant d'écrire, le document `GUIDE` après avoir livré. Et la grille de critères que chacun doit construire pour soi. |

## Ce qu'il y a dans le dépôt

```
fr/
├── 01-memoire.md          les deux couches de mémoire, avec les schémas
├── 02-methode.md          le protocole et les deux documents
├── demarrage.md           le prompt qui met tout en place en une conversation
├── skills/
│   ├── ultra-plan/        protocole de planification, exécutable
│   └── guide-livraison/   rédaction du guide après livraison
└── gabarits/              index de mémoire, fiche de fait, plan, guide
```

## Installation

Rien à installer pour la couche essentielle. Copiez les skills, donnez les deux documents à
votre agent, puis lancez le prompt de [`fr/demarrage.md`](fr/demarrage.md).

```bash
git clone https://github.com/red-nael/ekygai-method.git
cp -r ekygai-method/fr/skills/* ~/.claude/skills/
```

Le skill `ultra-plan` cherche la grille de critères de votre projet. S'il n'en trouve
aucune, **il ne l'invente pas** : il propose de la dériver avec vous, à partir des pannes
que vous avez réellement vécues.

## Ce que ce dépôt n'est pas

- **Pas un outil.** Aucun service à faire tourner, aucune dépendance obligatoire.
- **Pas une grille de critères prête à l'emploi.** Elle a été volontairement retirée : un
  critère qu'on n'a jamais payé n'est jamais défendu, il est coché. La méthode explique
  comment dériver la vôtre en cinq étapes.
- **Pas une garantie.** La méthode garantit un niveau de résultat, pas le résultat. Elle
  empêche le travail d'être bâclé ; elle ne décide pas quoi construire.

## Licences

| Ce que c'est | Licence |
|---|---|
| Documents (`fr/*.md`, `en/*.md`) | [CC BY 4.0](LICENSE-DOCS.md) — réutilisation libre, y compris commerciale, **avec citation de la source** |
| Skills et gabarits | [MIT](LICENSE) — copiez, modifiez, adaptez : c'est fait pour ça |

Une méthode de travail n'est pas protégeable par le droit d'auteur — seule son expression
l'est. Ces licences encadrent la reproduction du texte, pas l'usage des idées.

## Auteur

**Redouane El Bakkouch** — [EKYGAI](https://ekygai.com)

Les contributions sont bienvenues, en particulier les retours de terrain : quelle grille de
critères votre projet a-t-il produite, et quelle panne l'a fait naître.
