Bash : Le Shell des Ingénieurs

"Tu ne tapes pas des commandes dans Bash. Tu dialogues avec ton système."

🎯 Objectifs

À la fin de ce chapitre, tu comprendras :

Ce qu'est réellement Bash.
Comment Bash interprète une commande.
Ce qu'est une variable d'environnement.
Pourquoi $PATH est indispensable.
Les alias.
Les expansions (~, *, {}…).
Le fonctionnement de l'historique.
Les bases qui te serviront plus tard pour le scripting.
📖 Avant de commencer

Imagine un traducteur.

Tu dis :

Ouvre la porte.

Le traducteur transmet :

OPEN_DOOR()

au robot.

Le robot comprend.

Le traducteur, c'est Bash.

Le robot, c'est le noyau Linux.

Qu'est-ce que Bash ?

Bash signifie :

Bourne Again SHell

C'est un interpréteur de commandes.

Il lit ce que tu écris.

Il interprète.

Puis il demande au noyau d'exécuter les programmes.

Le chemin d'une commande

Lorsque tu tapes :

ls -la

Il se passe ceci :

Toi
 │
 ▼
Clavier
 │
 ▼
Terminal
 │
 ▼
Bash
 │
 ▼
Recherche de "ls"
 │
 ▼
Création d'un processus
 │
 ▼
Kernel
 │
 ▼
CPU

Tu retrouves ici tout ce que nous avons étudié dans le Module 01.

Les variables

Une variable est une zone mémoire contenant une information.

Par exemple :

prenom="Dominique"

Tu peux ensuite afficher cette valeur :

echo $prenom

Résultat :

Dominique

👉 Bash remplace $prenom par son contenu.

Les variables d'environnement

Certaines variables sont créées automatiquement.

Exemple :

echo $HOME

Chez toi :

/home/dominique

Autres variables importantes :

echo $USER
echo $PWD
echo $HOSTNAME
echo $LANG
echo $SHELL

Ces variables sont utilisées par de nombreux programmes.

La variable la plus importante : $PATH

Tape :

echo $PATH

Tu verras quelque chose comme :

/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

Chaque dossier est séparé par :

:
Pourquoi $PATH existe-t-il ?

Quand tu écris :

ls

Bash ne sait pas où se trouve ls.

Il parcourt les dossiers de $PATH, dans l'ordre :

/usr/local/bin
/usr/bin
/bin
...

Dès qu'il trouve un exécutable nommé ls, il s'arrête et le lance.

Démonstration

Vérifie où se trouve ls :

which ls

ou :

type ls

Tu devrais obtenir :

/usr/bin/ls
Les alias

Un alias est un raccourci.

Exemple :

alias ll="ls -lah"

Maintenant :

ll

équivaut à :

ls -lah

Très pratique.

Voir les alias existants
alias

Ubuntu en fournit déjà quelques-uns.

Les expansions

Bash possède une fonctionnalité très puissante : l'expansion.

Le tilde (~)
cd ~

Bash remplace ~ par :

/home/dominique
L'astérisque (*)
ls *.txt

Bash remplace *.txt par tous les fichiers se terminant par .txt.

Ce n'est pas ls qui le fait.

C'est Bash.

Les accolades ({})
mkdir projet/{docs,src,tests}

Bash développe automatiquement en :

projet/docs
projet/src
projet/tests

Une seule commande, trois dossiers créés.

Les variables dans une chaîne
echo "Bonjour $USER"

Résultat :

Bonjour dominique
L'historique

Chaque commande est enregistrée.

Affiche-le :

history

Le fichier correspondant est :

cat ~/.bash_history

⚠️ Attention : certains secrets peuvent y apparaître si tu les tapes directement dans le terminal.

L'autocomplétion

Tu connais déjà Tab.

Mais Bash peut compléter :

les fichiers ;
les dossiers ;
certaines commandes ;
parfois les options.

Exemple :

systemctl st<Tab>

devient souvent :

systemctl status
Les variables temporaires

Tu peux créer une variable :

formation="DevOps"

L'utiliser :

echo $formation

Puis la supprimer :

unset formation
Cas réel DevOps 💼

Un administrateur crée un script de sauvegarde.

Il écrit :

cp sauvegarde.tar.gz $BACKUP

Le problème ?

La variable $BACKUP n'existe pas.

Résultat :

La sauvegarde est copiée... dans le répertoire courant.

Depuis ce jour, beaucoup d'ingénieurs utilisent :

set -u

dans leurs scripts, pour provoquer une erreur lorsqu'une variable n'est pas définie.

Nous verrons cela dans le module Bash.

⚠️ Les erreurs classiques

❌ Confondre variable Bash et variable d'environnement.

❌ Modifier $PATH sans comprendre son rôle.

❌ Oublier les guillemets autour des variables contenant des espaces.

❌ Créer des alias trop complexes que personne d'autre ne comprend.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

garde un .bashrc propre et documenté ;
crée des alias utiles mais explicites ;
évite les alias qui modifient le comportement standard des commandes ;
connaît les principales variables d'environnement ;
vérifie toujours son $PATH lorsqu'une commande est introuvable.
📝 Résumé

Aujourd'hui, tu as appris que :

Bash est un interpréteur de commandes.
Les variables stockent des informations.
Les variables d'environnement sont partagées avec les programmes.
$PATH permet à Bash de retrouver les exécutables.
Les alias créent des raccourcis.
Les expansions sont réalisées par Bash avant l'exécution de la commande.
🧪 TP 4 — Découverte de Bash
1. Afficher les variables importantes
echo $USER
echo $HOME
echo $PWD
echo $SHELL
echo $PATH
2. Créer une variable
prenom="Dominique"
echo $prenom

Puis :

unset prenom
echo $prenom
3. Observer les alias
alias

Puis créer un alias :

alias ll="ls -lah"

Teste :

ll
4. Tester les expansions

Crée un laboratoire :

mkdir -p ~/devopslab/bash-lab
cd ~/devopslab/bash-lab

Puis :

touch fichier1.txt fichier2.txt image.jpg

Teste :

ls *.txt

Puis :

mkdir projet/{docs,src,tests}
tree projet

Si tree n'est pas installé :

sudo apt install tree
5. Vérifier où se trouve une commande
which ls
type ls
6. Lire l'historique
history
🎯 Challenge du chapitre

Réponds à ces questions :

Quelle est la différence entre une variable Bash et une variable d'environnement ?
Pourquoi $PATH est-il indispensable ?
Qui développe *.txt : Bash ou ls ?
Pourquoi un alias peut-il faire gagner du temps ?
Que se passe-t-il si une commande n'est présente dans aucun dossier de $PATH ?
🧰 Boîte à outils du Senior — Bash

Les commandes que j'utilise en permanence :

echo $PATH          # Voir le PATH
echo $HOME          # Dossier personnel
echo $PWD           # Répertoire courant
env                 # Variables d'environnement
printenv            # Idem
which               # Localiser une commande
type                # Nature d'une commande
alias               # Voir les alias
history             # Historique
Mes alias favoris
alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias grep='grep --color=auto'

👉 Ils restent simples, explicites et ne changent pas le comportement fondamental des commandes.

📖 Anecdote d'entreprise

Un ingénieur modifie la variable $PATH dans son .bashrc en oubliant d'ajouter les anciens chemins.

Après reconnexion, des commandes comme :

ls
cp
mv
systemctl

renvoient toutes :

command not found

Le système fonctionne toujours, mais Bash ne sait plus où trouver les exécutables.

Il a fallu ouvrir une session de secours et corriger le .bashrc.

🎓 Leçon : avant de modifier $PATH, on ajoute généralement un chemin, on ne remplace pas complètement la variable.