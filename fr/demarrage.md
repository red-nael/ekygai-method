# Démarrage — tout mettre en place en une conversation

Colle le prompt ci-dessous dans ton agent de code, **à la racine de ton projet** —
pas dans un dossier vide : l'interrogatoire ne vaut rien sans code à regarder.

Donne-lui aussi les deux documents ([partie I](01-memoire.md), [partie II](02-methode.md))
avant de lancer le prompt.

---

````markdown
Tu vas mettre en place sur ce projet la méthode décrite dans le document que je t'ai
donné. Lis-le en entier d'abord ; si je ne te l'ai pas fourni, demande-le-moi avant de
commencer quoi que ce soit.

Le travail se fait en trois temps, dans cet ordre. Ne saute pas le premier.

---

## 1. Tu m'interroges avant d'écrire le moindre fichier

Pose tes questions UNE PAR UNE et attends ma réponse avant la suivante. Pas de
questionnaire en bloc. Tu n'écris aucun fichier pendant cette phase.

Ce que tu dois apprendre sur le projet :

- ce qu'il fait, pour qui, depuis combien de temps
- la pile technique, et comment il est déployé
- si je travaille seul ou à plusieurs
- s'il tourne en production avec de vrais utilisateurs, ou s'il est encore en construction
- les contraintes qui ne se négocient pas : réglementaires, données personnelles,
  fonctionnement hors ligne, coût d'exécution, compatibilité imposée…
- mes habitudes de travail : ce que je veux que tu fasses toujours, ce que je ne veux jamais

Puis la partie qui compte le plus, celle qui sert à dériver ma grille de critères :

- qu'est-ce qui a **réellement** cassé, sur ce projet ou sur le précédent ? Demande des
  incidents précis et datés, pas des craintes générales
- combien de temps chaque panne m'a coûté
- ce que j'ai déjà dû refaire deux fois
- ce qui me réveillerait la nuit si ça tombait

Si une réponse est vague, relance. Si je n'ai aucune panne à raconter parce que le projet
est neuf, dis-le-moi franchement plutôt que de meubler : ma grille sera provisoire, et à
réviser dès la première vraie casse.

---

## 2. Tu construis ma grille avec moi — tu ne me la livres pas

À partir de mes réponses, et d'elles seules :

- regroupe mes pannes par cause, pas par symptôme
- traduis chaque groupe en une question vérifiable, jamais en nom de vertu
  (pas « observable » mais « si ça casse à trois heures du matin, qu'est-ce qui me permet
  de savoir où ? »)
- propose entre cinq et dix critères, chacun accompagné de la panne qui l'a fait naître
- dis-moi lesquels tu as écartés, et pourquoi

**Interdit : recopier les critères qui servent d'exemple dans le document.** Si un critère
que tu veux proposer ne correspond à rien de ce que j'ai vécu, soit tu ne le proposes pas,
soit tu le présentes explicitement comme ta suggestion à toi — pas comme quelque chose que
j'aurais dit.

Je valide, je corrige. Tu n'écris qu'ensuite.

---

## 3. Tu mets en place la mémoire

Si tu disposes d'un mécanisme de mémoire persistante entre sessions, utilise-le. Sinon,
crée un dossier `.claude/memoire/` à la racine du projet, et ajoute dans le `CLAUDE.md` du
projet une consigne qui t'impose de lire son index au démarrage de chaque session.

La forme, dans les deux cas :

- **un fichier d'index** qui liste les mémoires — une ligne chacune : titre, lien,
  accroche. Jamais de contenu dedans, c'est un sommaire
- **un fichier par fait**, nommé d'après son sujet, avec en en-tête un identifiant, une
  description d'une ligne, et un type parmi : `user` (qui je suis), `feedback` (comment
  travailler avec moi), `projet` (le travail en cours), `reference` (liens externes)
- pour les types `feedback` et `projet` : la **raison** de la règle, puis l'action concrète
  attendue. Une règle sans sa raison est appliquée de travers dès que le contexte bouge
- toute date relative convertie en date absolue
- ne consigne pas ce que le dépôt raconte déjà — structure du code, historique git,
  correctifs passés. La mémoire sert à ce qui n'est écrit nulle part

Les fichiers à créer à l'issue de notre échange :

1. **Le protocole.** Type `feedback`. Il dit : quand j'écris ULTRA PLAN — ou le mot-clé que
   j'aurai choisi — dans un message, tu passes en mode plan, tu ne modifies aucun fichier,
   tu lis d'abord l'arborescence du module concerné, l'architecture en place et ses
   conventions, puis tu proposes un plan qui répond à MA grille. Écris la grille dedans,
   avec la raison de chaque critère. Précise aussi les deux garde-fous : un critère qui ne
   peut pas être tenu se déclare dans le plan au lieu d'être coché, et les critères
   s'appliquent au périmètre du plan, pas aux modules voisins.
2. **Mes règles de travail.** Type `feedback` : ce que j'ai répondu sur mes habitudes.
3. **L'état du projet.** Type `projet`, quelques lignes, daté.

Crée enfin deux dossiers, `docs/plans/` et `docs/guides/`, chacun avec un README d'une
ligne disant ce qu'on y range : les plans avant le code, les guides après.

---

## Comment tu me parles pendant tout ça

- Une question à la fois.
- Aucune complaisance. Si une de mes réponses est floue, contradictoire ou irréaliste,
  dis-le tout de suite.
- « Je ne sais pas » et « ça ne marchera pas » sont des réponses valides de ta part.
- Ne me félicite pas, ne commente pas la qualité de mes idées. Travaille.
- À la fin, montre-moi la liste des fichiers créés avec leur contenu, et demande-moi ce
  qui est faux.

---

## Une dernière question, à la toute fin

Quand tout est en place, demande-moi si je veux ajouter la couche de capture automatique
décrite dans la première partie du document. Explique-moi d'abord ce qu'elle implique :
un paquet à installer, une clé API à moi, un coût par extraction, et surtout le fait que
mes transcripts de session partent se faire résumer par un modèle distant.

Ne l'installe pas sans mon accord explicite.
````

---

## Ce qui va se passer

La phase de questions prend une vingtaine de minutes. C'est la partie qu'on est tenté
de bâcler, et exactement celle qui détermine si la grille vaut quelque chose : elle se
dérive de pannes réelles, pas de bonnes intentions.

À la fin, tu auras une mémoire de projet remplie, un protocole déclenché par mot-clé,
ta propre grille de critères, et deux dossiers pour les plans et les guides.

## Installer les skills

Les deux skills de ce dépôt sont directement utilisables. Copie le dossier voulu dans
les skills de ton projet ou de ton compte :

```bash
# pour un seul projet
cp -r fr/skills/ultra-plan       <ton-projet>/.claude/skills/
cp -r fr/skills/guide-livraison  <ton-projet>/.claude/skills/

# ou pour tous tes projets
cp -r fr/skills/*  ~/.claude/skills/
```

Le skill `ultra-plan` cherche la grille de critères du projet au démarrage. S'il n'en
trouve aucune, il ne l'invente pas : il propose de la dériver avec toi.

---

[← Sommaire](../README.fr.md)
