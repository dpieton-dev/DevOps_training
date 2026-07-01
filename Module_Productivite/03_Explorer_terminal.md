Le Terminal expliqué de A à Z

"Le terminal est la porte d'entrée vers le système d'exploitation."

🎯 Objectifs

À la fin de ce chapitre, tu comprendras :

Ce qu'est réellement un terminal.
La différence entre Terminal, Console, TTY, Shell et Bash.
Ce que signifient stdin, stdout et stderr.
Pourquoi Linux considère un terminal comme un fichier.
Comment les programmes communiquent entre eux.
Pourquoi le pipe (|) est une invention géniale.
⚠️ Le plus gros malentendu de Linux

Je vais commencer par une phrase que j'entends très souvent.

"J'ouvre Bash."

En réalité...

Tu n'ouvres presque jamais Bash.

Tu ouvres :

GNOME Terminal

qui lance ensuite :

Bash

Ce n'est pas du tout la même chose.

Une analogie

Imagine un théâtre.

Le bâtiment est :

👉 Le terminal.

L'acteur est :

👉 Le shell.

Le public parle avec l'acteur grâce au théâtre.

Le théâtre ne joue pas la pièce.

Le shell, oui.

Décomposition

Quand tu fais :

Ctrl + Alt + T

Il se passe ceci :

Toi
 │
 ▼
GNOME Terminal
 │
 ▼
Pseudo Terminal (PTY)
 │
 ▼
Bash
 │
 ▼
Kernel
 │
 ▼
CPU

Le terminal est simplement une interface graphique.

Petit retour dans les années 1970

À l'époque...

Pas d'écran.

Pas de souris.

Les utilisateurs avaient ceci :

██████████████████████
█                    █
█      TERMINAL      █
█                    █
██████████████████████

Un écran.

Un clavier.

Rien d'autre.

Le terminal était une machine physique.

Aujourd'hui...

Le terminal est un logiciel qui imite ces anciennes machines.

C'est pour cela qu'on parle encore de :

Terminal Emulator
Le Shell

Le Shell est un programme.

Chez toi :

echo $SHELL

donne probablement :

/bin/bash

Il pourrait aussi être :

zsh
fish
dash
sh
ksh

Tous sont des shells.

Pourquoi "Shell" ?

Shell signifie :

Coquille

Pourquoi ?

Parce qu'il entoure le noyau.

Utilisateur

↓

Shell

↓

Kernel

↓

Matériel

Le Shell protège l'utilisateur de la complexité du noyau.

Le TTY

Voici un mot que tu verras très souvent.

TTY

Cela signifie :

Teletype

Encore un héritage historique.

Aujourd'hui un TTY est :

Un terminal texte.

Tu peux en voir plusieurs.

Essaie :

tty

Tu obtiendras quelque chose comme :

/dev/pts/0

Nous reviendrons sur ce résultat dans quelques minutes.

Pourquoi /dev/pts/0 ?

Souviens-toi du Module 01.

Linux dit :

Tout est un fichier.

Ton terminal est lui aussi représenté comme un fichier.

Regarde :

ls -l /dev/pts

Tu verras probablement :

0

1

2

Chaque terminal ouvert possède son propre fichier.

L'expérience

Ouvre deux terminaux.

Dans le premier :

tty

Exemple :

/dev/pts/0

Dans le deuxième :

tty

Tu verras :

/dev/pts/1

Chaque terminal possède son propre canal de communication.

Les trois flux magiques

Chaque programme Linux possède automatiquement trois canaux de communication.

stdin

Standard Input

Numéro :

0

C'est l'entrée.

Exemple :

Le clavier.

stdout

Standard Output

Numéro :

1

La sortie normale.

Exemple :

ls

affiche :

Documents

Images
stderr

Standard Error

Numéro :

2

Les erreurs.

Exemple :

ls dossier_inexistant

affiche :

No such file or directory

Cette erreur passe par stderr, pas par stdout.

Schéma
             Programme

               ▲

stdin (0)      │

               ▼

stdout (1)

               ▼

stderr (2)

Tous les programmes Linux fonctionnent ainsi.

Absolument tous.

Pourquoi deux sorties ?

Question.

Pourquoi avoir séparé :

stdout

et

stderr

Réponse.

Parce qu'on veut pouvoir traiter les erreurs différemment des résultats.

Un exemple concret :

ls /etc > resultat.txt

Les résultats vont dans le fichier.

Mais les erreurs restent affichées.

Très pratique.

Le Pipe

Le caractère :

|

est probablement l'une des inventions les plus élégantes d'Unix.

Il signifie :

Prends la sortie d'un programme et donne-la à un autre.

Exemple :

ls | wc -l

Que se passe-t-il ?

ls

↓

affiche les fichiers.

Au lieu de les envoyer au terminal...

Ils sont envoyés directement à :

wc

qui les compte.

Schéma :

ls

↓

stdout

↓

Pipe

↓

stdin

↓

wc

Magnifique.

Pourquoi Linux est si puissant ?

Parce que tous les programmes parlent la même langue.

Ils utilisent :

stdin
stdout
stderr

Ils peuvent donc être assemblés comme des briques LEGO.

Cas réel DevOps 💼

Imagine un serveur qui génère :

20 Go de logs.

Tu veux seulement les lignes contenant :

ERROR

Tu peux construire une chaîne :

cat application.log | grep ERROR | wc -l

Trois programmes.

Chacun fait une seule chose.

Ensemble, ils résolvent ton problème.

C'est la philosophie Unix :

Faire une seule chose, mais la faire parfaitement.

⚠️ Les erreurs classiques

❌ Confondre terminal et shell.

❌ Penser que Bash affiche les fenêtres.

❌ Ignorer stderr.

❌ Ne jamais utiliser le pipe.

⭐ Ce qu'un Senior ferait

Observe un ingénieur expérimenté.

Tu verras souvent des commandes comme :

journalctl -u nginx | grep ERROR | tail -20

Il combine de petits outils simples pour répondre à une question précise.

Il ne cherche pas une commande qui fait tout.

📝 Résumé

Aujourd'hui, tu as appris :

Le terminal est une application.
Le shell interprète les commandes.
Chaque terminal correspond à un pseudo-terminal (/dev/pts/...).
Chaque programme possède trois flux :
stdin
stdout
stderr
Le pipe permet de relier les programmes entre eux.