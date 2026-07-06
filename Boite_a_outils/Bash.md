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