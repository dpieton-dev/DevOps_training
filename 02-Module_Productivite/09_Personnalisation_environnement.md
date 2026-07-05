Personnaliser son environnement Bash

"Ne t'adapte pas à ton environnement. Construis un environnement qui s'adapte à toi."

🎯 Objectifs

À la fin de ce chapitre, tu seras capable de :

Comprendre le rôle du .bashrc.
Comprendre le rôle du .profile.
Personnaliser ton prompt (PS1).
Créer des alias utiles.
Créer des fonctions Bash.
Ajouter des variables d'environnement.
Recharger une configuration sans fermer le terminal.
Construire un .bashrc propre et maintenable.
📖 Avant de commencer

Imagine deux administrateurs.

Le premier

À chaque nouveau terminal, il retape :

cd ~/devopslab

Puis :

export PATH=...

Puis :

alias ll='ls -lah'

Tous les jours.

Le second

Ouvre un terminal.

Tout est déjà prêt.

Qui est le plus efficace ?

Évidemment le second.

Le démarrage d'un shell

Quand tu ouvres un terminal :

GNOME Terminal
        │
        ▼
Bash
        │
        ▼
Lecture du .bashrc
        │
        ▼
Prompt affiché

Le .bashrc est exécuté automatiquement.

Où se trouve-t-il ?

Dans ton dossier personnel :

~/.bashrc

Tu peux l'ouvrir avec :

vim ~/.bashrc

ou

code ~/.bashrc
Que contient-il ?

Par défaut Ubuntu ajoute :

les couleurs ;
quelques alias ;
l'autocomplétion ;
le prompt.

Nous allons l'améliorer.

Le .profile

Ne pas confondre :

.bashrc

et

.profile
.profile

Exécuté :

➡️ lors de la connexion.

.bashrc

Exécuté :

➡️ à chaque nouveau shell interactif.

C'est donc lui que nous modifierons le plus souvent.

Le Prompt

Lorsque tu ouvres un terminal :

Tu vois :

dominique@dominique-Inspiron-5770:~$

C'est le prompt.

Il est défini par une variable :

echo $PS1
Personnaliser le prompt

Exemple très simple :

PS1="DevOps> "

Résultat :

DevOps>

Le changement est temporaire.

Les séquences utiles
Code	Signification
\u	Utilisateur
\h	Nom de la machine
\w	Répertoire courant
\W	Dernier dossier
\t	Heure
\$	$ ou # selon les droits

Exemple :

PS1='\u@\h:\w\$ '

Tu retrouves le prompt classique.

Ajouter de la couleur

Exemple :

PS1='\[\e[32m\]\u@\h\[\e[0m\]:\w\$ '

Cela affiche le nom d'utilisateur et de la machine en vert.

Nous irons plus loin plus tard avec Git.

Les Alias

Tu connais déjà :

alias ll='ls -lah'

Voici ceux que je recommande.

alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'

Créer rapidement un dossier puis s'y déplacer :

mkcd () {
    mkdir -p "$1"
    cd "$1"
}

Utilisation :

mkcd test

Tu crées le dossier et tu y entres.

Les Fonctions

Une fonction est plus puissante qu'un alias.

Exemple :

bonjour () {
    echo "Bonjour Dominique !"
}

Puis :

bonjour

Résultat :

Bonjour Dominique !
Une fonction utile

Créer une sauvegarde :

backup () {
    cp "$1" "$1.bak"
}

Utilisation :

backup nginx.conf

Résultat :

nginx.conf.bak
Ajouter un dossier au PATH

Imaginons :

~/bin

Tu veux y placer tes scripts.

Ajoute dans ton .bashrc :

export PATH="$HOME/bin:$PATH"

Très important :

On ajoute au PATH.

On ne remplace pas le PATH.

Recharger le .bashrc

Après une modification :

Pas besoin de fermer le terminal.

Utilise :

source ~/.bashrc

ou

. ~/.bashrc

Le shell relit immédiatement le fichier.

Organiser son .bashrc

Je recommande toujours cette structure :

Variables

↓

PATH

↓

Alias

↓

Fonctions

↓

Personnalisation du prompt

↓

Autres options

Un fichier organisé est plus facile à maintenir.

Versionner son .bashrc

Je conseille de créer un dépôt Git :

dotfiles

Tu pourras y stocker :

.bashrc

.vimrc

.gitconfig

.tmux.conf

.profile

Ainsi, tu retrouveras ton environnement sur n'importe quelle machine.

Nous créerons ce dépôt dans le module Git.

Cas réel DevOps 💼

Un administrateur change de poste.

Il clone son dépôt dotfiles.

En moins de cinq minutes, il retrouve :

son prompt ;
ses alias ;
ses fonctions ;
sa configuration tmux ;
sa configuration Vim.

Son environnement est identique sur toutes les machines.

⚠️ Les erreurs classiques

❌ Modifier .bashrc sans faire de sauvegarde.

❌ Remplacer complètement le PATH.

❌ Créer des alias incompréhensibles.

❌ Ajouter des centaines de lignes inutiles.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

documente son .bashrc avec des commentaires ;
versionne ses fichiers de configuration ;
garde une structure claire ;
crée des alias simples ;
privilégie les fonctions pour les traitements un peu plus complexes.
📝 Résumé

Aujourd'hui, tu as appris que :

.bashrc configure ton shell.
.profile est lu lors de la connexion.
PS1 contrôle le prompt.
Les alias créent des raccourcis.
Les fonctions permettent d'automatiser de petites tâches.
source ~/.bashrc recharge la configuration.
🧪 TP 9 — Construire ton environnement Bash

⚠️ Avant toute modification, fais une sauvegarde :

cp ~/.bashrc ~/.bashrc.backup
1. Vérifier le prompt actuel
echo $PS1
2. Ajouter quelques alias

À la fin du fichier .bashrc :

alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias cls='clear'

Recharge ensuite :

source ~/.bashrc

Teste :

ll
3. Ajouter une fonction

Dans le .bashrc :

mkcd () {
    mkdir -p "$1"
    cd "$1"
}

Recharge :

source ~/.bashrc

Teste :

mkcd laboratoire
4. Ajouter ~/bin au PATH

Ajoute :

export PATH="$HOME/bin:$PATH"

Puis :

source ~/.bashrc
echo $PATH

Tu dois voir ~/bin au début de la liste.

5. Créer un dossier pour tes futurs scripts
mkdir -p ~/bin

Nous l'utiliserons dans les prochains modules.

🎯 Challenge du chapitre

Je te propose de construire progressivement ton propre .bashrc.

Il devra contenir :

des commentaires clairs ;
des alias utiles ;
la fonction mkcd ;
l'ajout de ~/bin au PATH ;
un prompt légèrement personnalisé.

Ne cherche pas à copier celui d'un autre. L'objectif est de comprendre chaque ligne.

🧰 Boîte à outils du Senior — Bash personnalisé

Les commandes que j'utilise le plus :

source ~/.bashrc      # Recharger Bash

echo $PATH            # Vérifier le PATH

alias                 # Voir les alias

type ll               # Vérifier un alias

printenv              # Variables d'environnement

env                   # Idem

Mes fonctions favorites :

mkcd dossier

backup fichier

extract archive.tar.gz   # (nous l'écrirons plus tard)

serve 8000               # (petit serveur HTTP local)
🧠 Comment raisonne un Senior ?

Situation : tu répètes la même commande plusieurs fois par jour.

Un débutant pense :

"Je vais la retaper."

Un senior pense :

"Puisque je la répète souvent, je vais l'automatiser."

C'est cette réflexion qui conduit naturellement aux alias, aux fonctions, puis aux scripts Bash, ensuite à Ansible et enfin aux pipelines CI/CD.

👉 L'automatisation commence souvent par une simple ligne dans un .bashrc.

📖 Anecdote d'entreprise

Un administrateur passait plusieurs minutes par jour à créer des dossiers, s'y déplacer et préparer des fichiers.

Il a ajouté une simple fonction :

mkcd () {
    mkdir -p "$1"
    cd "$1"
}

Ce n'était qu'une seule ligne de code.

Sur une année, elle lui a fait gagner plusieurs heures de travail répétitif.

🎓 Leçon : en DevOps, les plus grands gains de productivité viennent souvent de petites automatisations répétées quotidiennement.