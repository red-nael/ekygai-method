# Contribuer — et la grille que ce dépôt s'applique à lui-même

[English](CONTRIBUTING.md) · Français

Ce dépôt décrit une méthode. Il serait malhonnête de la publier sans l'appliquer ici. Ce
fichier contient donc **la grille de critères du dépôt lui-même**, dérivée comme la méthode
le prescrit : à partir de ce qui a réellement cassé, pas de bonnes intentions.

Chaque critère ci-dessous est né d'une panne réelle survenue pendant la construction,
datée. Aucun n'a été inventé pour faire complet.

## La grille

| # | Critère | Né de |
|---|---|---|
| 1 | **Rien ici ne permet de déduire l'activité ou la taille des projets d'où vient la méthode.** Les chiffres des exemples sont illustratifs et ne doivent pas être réels. | 2026-09-19 — le tableau d'exemple d'audit portait les vrais nombres d'un audit de production (`216 lignes / 48 humains`). Repéré avant le premier push. |
| 2 | **Rien que la machine génère toute seule n'entre dans le dépôt sans décision.** | 2026-09-19 — la couche de capture automatique a créé un `CLAUDE.md` et un `.memory/` dans ce dossier pendant la session d'écriture. Un `git add -A` distrait aurait poussé des mémoires de session dans un dépôt public. |
| 3 | **Tout fichier écrit est relu tel qu'il est sur le disque, pas tel qu'on croit l'avoir écrit.** | 2026-09-19 — un heredoc shell a interprété des accents graves comme une substitution de commande et supprimé silencieusement un mot d'une page publiée. Trouvé par grep, pas en relisant la source. |
| 4 | **Tout ce qui se rend — schémas, liens — est vérifié par exécution, jamais par lecture.** | 2026-09-19 — les schémas Mermaid ont été validés en les parsant dans un navigateur headless ; les liens internes en résolvant chaque chemin. Aucun des deux n'aurait été vu à la relecture. |
| 5 | **Toute modification d'un document a son miroir dans l'autre langue, dans le même commit.** | Structurel : un dépôt bilingue dérive en silence. Les versions française et anglaise ne sont pas des traductions l'une de l'autre, ce sont deux faces du même document. |

## Les deux garde-fous

Un critère qui ne peut pas être tenu se **déclare dans la pull request**, avec sa raison.
Une PR qui coche les cinq par politesse ne vaut rien — la valeur est dans l'aveu.

Les critères s'appliquent **au périmètre du changement**, pas au-delà. Corriger une faute
de frappe n'oblige pas à auditer tout le dépôt.

## À quoi ressemble une contribution utile

Les retours de terrain d'abord : **quelle grille de critères votre projet a-t-il produite,
et quelle panne l'a fait naître ?** C'est la seule partie de cette méthode qui ne peut pas
s'écrire à l'avance, et la plus utile à collecter.

Traductions, corrections et clarifications bienvenues. Les grilles de critères toutes
faites, non : en publier une contredirait la méthode.

## Trace

Le guide de la construction de ce dépôt, bugs compris, est dans
[`docs/guides/`](docs/guides/). Il n'y a pas de document de plan pour la construction
initiale — elle s'est faite sans, et en écrire un après coup serait exactement le faux
relevé que cette méthode interdit.
