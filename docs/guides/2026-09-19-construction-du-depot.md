# GUIDE — construction du dépôt

_Date : 2026-09-19 · Plan d'origine : **aucun** (voir §6)_

Ce guide documente la construction du dépôt qui publie la méthode. Il sert deux fins : la
trace habituelle, et un exemple réel de ce à quoi ressemble un guide — bugs compris.

## 1. Le trajet, étape par étape

### Source
Deux notes publiées en pages web lors d'une session antérieure. Les fichiers HTML d'origine
vivaient dans un dossier temporaire de session, **effacé depuis**. Récupération faite depuis
les pages publiées, pas depuis une copie locale.

Contrat vers l'étape suivante : HTML complet, texte + SVG inline.

### Conversion
Extraction du texte par suppression des balises, puis réécriture en Markdown. Les trois
schémas SVG ont été **réécrits en Mermaid**, pas convertis : GitHub rend Mermaid nativement
en clair comme en sombre, un SVG aux couleurs figées n'aurait tenu que dans un thème.

### Traduction
Les documents anglais ne sont pas une traduction automatique du français. Termes fixés :
*relevé de cicatrices* → *record of scars* ; *zéro complaisance* → *zero flattery* ;
*la mesure prime la documentation* → *measurement beats documentation* ;
*minimum viable durable* → *durable minimum viable*.

### Skills
Écrits de zéro, pas dérivés des documents. Un document explique à un lecteur ; un skill
donne des instructions à un agent. Le passage de l'un à l'autre est une réécriture complète,
à l'impératif.

## 2. Structure des fichiers

Langue au premier niveau (`fr/`, `en/`), structure miroir en dessous. Alternative écartée :
un niveau `docs/` avec suffixes de langue — plus difficile à parcourir, et rend le miroir
invisible.

## 3. Inventaire

| Fichier | Rôle |
|---|---|
| `README.md` / `README.fr.md` | porte d'entrée bilingue |
| `CONTRIBUTING.md` / `.fr.md` | la grille de critères que le dépôt s'applique |
| `LICENSE` | MIT — skills et gabarits |
| `LICENSE-DOCS.md` | CC BY 4.0 — documents, avec la limite du droit d'auteur sur une méthode |
| `{fr,en}/01-*.md` | partie I, 2 schémas Mermaid chacune |
| `{fr,en}/02-*.md` | partie II, 1 schéma chacune |
| `{fr,en}/demarrage.md`, `getting-started.md` | le prompt d'installation |
| `{fr,en}/skills/*/SKILL.md` | 2 skills × 2 langues |
| `{fr,en}/{gabarits,templates}/*.md` | 4 gabarits × 2 langues |

## 4. Bugs trouvés et corrigés

### Des accents graves supprimés en silence
- **Symptôme** : une phrase publiée disait « Le skill  cherche la grille » — un mot manquant.
- **Cause réelle** : un heredoc shell non protégé a interprété `` `ultra-plan` `` comme une
  substitution de commande. Le shell a exécuté `ultra-plan`, échoué, et inséré une chaîne vide.
- **Correction** : remplacement par un script Python opérant sur le fichier.
- **Critère manquant ?** Oui → critère 3 de la grille.

### Les vrais chiffres d'un audit de production dans un exemple
- **Symptôme** : le tableau d'exemple portait `216 lignes / 48 humains`.
- **Cause réelle** : l'exemple avait été genericisé pour les noms, pas pour les nombres.
  Le dépôt indiquant l'origine du projet, ces chiffres laissaient déduire une base
  d'utilisateurs.
- **Correction** : valeurs illustratives. Commit `7f5a069`.
- **Critère manquant ?** Oui → critère 1.

### La couche de capture s'est installée dans le dépôt
- **Symptôme** : un `CLAUDE.md` et un `.memory/` apparus dans le dossier après le premier
  commit, non créés par nous.
- **Cause réelle** : les hooks de capture automatique décrits en partie I tournent sur la
  machine et s'accrochent à tout dossier de travail — y compris celui-ci.
- **Correction** : les deux ajoutés au `.gitignore`.
- **Critère manquant ?** Oui → critère 2. À noter : la panne décrite en partie I est
  survenue sur le dépôt qui la décrit.

### Schémas et liens non vérifiables à la lecture
- **Symptôme** : aucun — rien n'a cassé.
- **Pourquoi c'est ici quand même** : la syntaxe Mermaid (`classDef stroke-dasharray:6 4`)
  et les 60+ liens relatifs ne se valident pas à l'œil. Vérifiés par exécution :
  `mermaid.parse()` dans un navigateur headless, et résolution de chaque chemin. Les 6
  schémas passent ; les 10 liens signalés cassés sont des emplacements de gabarit.
- **Critère manquant ?** Oui → critère 4.

## 5. Ce qui reste

- **Le miroir bilingue n'a aucune vérification automatique.** Rien n'empêche aujourd'hui de
  modifier `fr/02-methode.md` en oubliant `en/02-method.md`. Le critère 5 existe, l'outil
  qui le contrôle non.
- **Aucun exemple de plan rempli.** Les gabarits sont vides ; le dépôt ne montre pas à quoi
  ressemble un ULTRA PLAN réel. Fournir le sien reviendrait à publier l'audit d'un projet.
- **Le dépôt n'a pas de couche mémoire à lui.** Cohérent — il n'est pas un projet de code —
  mais c'est une asymétrie assumée, pas un oubli.

## 6. Ce qui n'a pas été fait, et pourquoi c'est écrit ici

**Il n'y a pas eu d'ULTRA PLAN pour cette construction.** Trois questions de cadrage, puis
l'écriture des fichiers. Ni état des lieux daté, ni découpage en phases, ni grille à
laquelle répondre — elle n'existait pas encore.

Écrire ce plan après coup aurait produit un document daté d'aujourd'hui décrivant des
décisions prises sans lui : un faux relevé, exactement ce que la partie II interdit. Le
manque est donc consigné ici plutôt que comblé.

La grille du dépôt ([`CONTRIBUTING.md`](../../CONTRIBUTING.md)) a été dérivée *après*, à
partir des pannes ci-dessus. C'est l'ordre normal : une grille est un relevé de cicatrices.
Les changements suivants, eux, passeront par elle.
