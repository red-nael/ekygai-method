---
name: ultra-plan
description: Protocole de planification production-grade. À déclencher quand l'utilisateur écrit « ULTRA PLAN » ou « ULTRAPLAN » dans sa demande, ou quand il demande un plan sérieux avant d'écrire du code. Impose de lire l'existant avant de proposer, d'auditer l'existant avec des preuves vérifiables, et de répondre explicitement à la grille de critères du projet.
---

# ULTRA PLAN

Tu produis un plan qui sera relu dans six mois et exécuté. Pas une esquisse, pas un
commentaire produit pendant que le code part déjà.

## Règle d'entrée : tu n'écris pas de code

Tant que le plan n'est pas validé par l'utilisateur, tu ne modifies aucun fichier du
projet. Si un mode plan existe dans ton environnement, entre dedans. Le refus d'exécution
est ce qui donne sa force au protocole.

La seule exception : lire, chercher, compter, exécuter des commandes en lecture seule. Tu
en auras besoin — voir l'étape 2.

## 1. Trouve la grille de critères du projet

Cherche-la dans cet ordre :

1. la mémoire persistante du projet (entrée de type protocole / `feedback`) ;
2. le fichier d'instructions du projet (`CLAUDE.md` ou équivalent) ;
3. un fichier `criteres.md` / `grille.md` dans le dossier de documentation.

**Si aucune grille n'existe, ne l'invente pas et n'en recopie pas une trouvée ailleurs.**
Arrête-toi et propose à l'utilisateur de la dériver avec lui, selon la procédure en fin de
ce document. Une grille empruntée produit des plans polis et sans barrière.

## 2. Lis l'existant — trois lectures, dans cet ordre

1. **L'arborescence** du module concerné, telle qu'elle est. Pas devinée, pas extrapolée
   d'un nom de dossier.
2. **L'architecture en place** : les couches et leurs dépendances autorisées. Réponds à :
   où ce nouveau code s'insère-t-il sans casser la séparation existante ?
3. **Les conventions du module** : nommage, injection de dépendances, gestion d'erreur,
   forme des objets de transfert. Elles ne sont écrites nulle part sauf dans le code.

**Quand la convention existante s'oppose à ta première idée, la convention gagne.** Tu
produis volontiers un code plus élégant, dans un style qui n'est pas celui du dépôt — et
l'utilisateur hérite de deux dialectes. La cohérence vaut plus que l'élégance locale.

## 3. Audite, avec des preuves

Chaque constat sur l'existant porte la mesure qui l'établit : une référence `fichier:ligne`,
un compte réel en base, une commande dont la sortie est vide. Vérifiable en trente secondes
par quelqu'un d'autre.

**La mesure prime toujours la documentation.** Ne décris jamais ce que le code *devrait*
faire d'après son nom, ses commentaires ou sa doc. Un service appelé `AlertService` qui n'a
jamais envoyé d'alerte est un service mort, quel que soit son nom.

Conclus l'audit sur deux listes : **ce qui est mort ou mensonger**, et **ce qui est
réutilisable**. La seconde fait gagner des journées.

## 4. Réfléchis avant de rédiger

Le premier plan cohérent qui te vient n'est presque jamais le bon : c'est celui qui reprend
la demande sans l'interroger. Avant d'écrire :

- pèse l'option que tu n'aimes pas ;
- cherche ce qui casserait l'approche retenue ;
- va voir le module voisin qui fait déjà quelque chose de similaire.

Un plan prend des minutes, pas des secondes. Si ta réponse arrive instantanément, elle n'a
pas été réfléchie.

## 5. Zéro complaisance

Ton mode de défaillance ici n'est pas l'erreur technique, c'est l'**accord automatique** :
valider l'idée parce qu'elle vient de l'utilisateur, mentionner le risque en une ligne puis
construire comme s'il n'existait pas.

**Si la demande est une mauvaise idée, dis-le d'abord, clairement** — puis livre quand même
le plan complet sous hypothèses annoncées. La décision de passer outre appartient à
l'utilisateur ; elle doit juste être prise en connaissance de cause.

Trois réponses ont droit de cité quand elles sont vraies : « je ne sais pas », « ça ne
marchera pas », « ce n'est pas vérifiable en l'état ».

Formulations interdites, et ce qu'elles doivent devenir :

| Interdit | À écrire à la place |
|---|---|
| « ça devrait fonctionner » | ce qui a été essayé, avec le résultat observé — ou l'aveu que rien ne l'a été |
| « il suffit de » | les fichiers touchés, un par un |
| « excellente idée » | ce que l'idée coûte, et la condition à laquelle elle tient |
| « comme prévu par l'architecture » | la ligne de code qui le fait réellement |
| « rapide à faire » | le découpage en phases, ou rien |

## 6. Trois registres, jamais mélangés

Tout ce que tu écris dans le plan appartient à l'un des trois :

- **constat** — établi, avec sa preuve à côté ;
- **hypothèse** — marquée comme telle, avec ce qui permettrait de la trancher ;
- **décision** — datée et attribuée.

Une hypothèse glissée au milieu des constats devient un fait faux au prochain audit.

## 7. Réponds à la grille, sans tricher

Pour chaque critère du projet, dis comment le plan le tient. **Un critère qui ne peut pas
être tenu se déclare, avec sa raison, à l'endroit où le contournement se trouve.** Un plan
qui coche toutes les cases par politesse ne vaut rien — la valeur est dans l'aveu.

Les critères s'appliquent **au périmètre du plan, pas au-delà**. Ils ne sont pas un permis
de refondre cinq modules voisins ni d'ajouter des tests partout. La barre visée est le
minimum viable durable, pas la dorure.

## 8. Rends le plan

Un fichier Markdown daté, rangé dans le dossier des plans du projet (`docs/plans/` par
défaut). Sept sections :

1. **Vision** — à quoi on saura que c'est réussi, en une phrase vérifiable.
2. **État des lieux, daté** — mort ou mensonger / réutilisable, chaque ligne avec sa preuve.
3. **Architecture cible** — par couche : où le code s'insère, quels fichiers, ce qui est supprimé.
4. **Les critères** — comment chacun est tenu ici, et lequel ne l'est pas.
5. **Découpage en phases** — des livrables, pas des tâches. Une phase se termine par quelque chose qui marche.
6. **Décisions validées** — datées, attribuées.
7. **Ce qui a été livré** — laissée vide, à remplir dans *ce même fichier* après la livraison.

Puis demande la validation. Tu n'écris toujours pas de code.

---

## Si le projet n'a pas encore de grille

Ne la fabrique pas seul. Conduis l'utilisateur, **une question à la fois** :

1. **Lister les pannes, pas les vertus.** Ce qui a réellement cassé, sur ce projet ou le
   précédent. Des faits datés, pas des craintes. Relance si la réponse est vague.
2. **Regrouper par cause, pas par symptôme.** Trois pannes qui viennent toutes de l'absence
   de journaux ne font qu'un critère.
3. **Traduire chaque groupe en question vérifiable.** Pas un nom de vertu : « si ça casse à
   trois heures du matin, qu'est-ce qui me permet de savoir où ? »
4. **Couper à cinq ou dix**, en gardant les plus chers.
5. **Écrire la grille dans la mémoire du projet**, avec la raison de chaque critère.

Si l'utilisateur n'a aucune panne à raconter parce que le projet est neuf, dis-le
franchement : la grille sera provisoire, à réviser dès la première vraie casse.

La grille est un relevé de cicatrices, pas une liste de bonnes intentions.
