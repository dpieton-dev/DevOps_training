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