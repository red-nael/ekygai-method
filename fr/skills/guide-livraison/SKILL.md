---
name: guide-livraison
description: Rédaction du document GUIDE après la livraison d'une fonctionnalité. À déclencher quand l'utilisateur dit qu'une fonctionnalité est livrée, terminée ou déployée, ou demande de documenter ce qui vient d'être construit. Produit un relevé par couche, avec inventaire des fichiers, bugs rencontrés et dettes restantes.
---

# GUIDE de livraison

Tu écris ce que le plan ne pouvait pas savoir : **comment ça fonctionne réellement, de bout
en bout, maintenant que c'est construit.**

## Ce que ce document n'est pas

Un guide n'est pas un plan rédigé au passé. Le plan était un **engagement** — il se
discutait, se refusait, se validait. Le guide est un **relevé** : il décrit ce qui est, y
compris ce qui a mal tourné.

**Un guide qui ne mentionne aucun bug n'a pas été écrit après la construction — il a été
écrit à la place.** Si tu n'as rencontré aucune difficulté, dis-le explicitement plutôt que
de laisser la section vide.

## Avant d'écrire

Relis ce qui a réellement été fait : le diff, les commits de la période, le plan d'origine
s'il existe. N'écris aucune ligne sur la base de ce qui était prévu — seulement sur la base
de ce qui est dans le dépôt maintenant. Là encore, **la mesure prime la documentation**.

## La structure

Suis le trajet d'une donnée à travers le système, dans l'ordre du flux.

### 1. Une partie par couche traversée

Du point d'entrée jusqu'au stockage. Pour chacune : ce qu'elle reçoit, ce qu'elle fait, ce
qu'elle renvoie. **Écris les contrats d'interface entre chaque couche** — c'est là que les
erreurs se logent, et c'est ce qu'on cherche en premier six mois plus tard.

### 2. Le schéma de données

Tables, colonnes, types, contraintes, index. Ce que le code suppose de la base, écrit noir
sur blanc. Si une contrainte existe dans le code mais pas dans la base, dis-le : c'est une
panne en attente.

### 3. L'inventaire des fichiers

Tous les fichiers créés ou modifiés, avec leur rôle en une ligne. Section ingrate, et la
plus utile de toutes : elle permet de retrouver un point d'entrée sans fouiller le dépôt.

### 4. Les bugs trouvés et corrigés

Ce qui a cassé pendant la construction, et pourquoi. Pour chacun : le symptôme, la cause
réelle, la correction. C'est une base de pièges qui se lit en cinq minutes et fait gagner
des heures — la section que personne n'écrit ailleurs.

Si un bug a révélé un manque dans la grille de critères du projet, signale-le : **c'est un
critère de plus à ajouter**.

### 5. Ce qui reste

Les dettes assumées, les cas non traités, les contournements en place. C'est le point de
départ de l'état des lieux du plan suivant.

## Les règles d'écriture

- **Daté dans le nom du fichier** (`AAAA-MM-JJ-sujet.md`), rangé dans le dossier des guides
  du projet (`docs/guides/` par défaut). Deux guides successifs sur le même système
  racontent son évolution — n'écrase pas le précédent.
- **Long, c'est normal.** De plusieurs centaines à plus de mille lignes pour un système
  complet. Ce document remplace la relecture du code par quelqu'un qui n'était pas là.
- **Références vérifiables** : `fichier:ligne` partout où c'est possible.
- **Aucune complaisance.** Si une partie est mal faite, dis-le ici plutôt que de la
  découvrir en panne plus tard.

## Pour finir

Propose à l'utilisateur deux choses :

1. ajouter une ligne dans la mémoire du projet pointant vers ce guide ;
2. si un bug rencontré n'était couvert par aucun critère, **ajouter ce critère à la
   grille** — c'est ainsi qu'elle grandit, et c'est la seule façon légitime de la faire
   grandir.
