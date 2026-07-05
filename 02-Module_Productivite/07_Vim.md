Vim : l'éditeur des administrateurs système

"Un administrateur Linux ne choisit pas toujours son éditeur. Il choisit d'être capable de travailler partout."

🎯 Objectifs

À la fin de ce chapitre, tu seras capable de :

Comprendre la philosophie de Vim.
Ouvrir et fermer un fichier sans stress.
Modifier un fichier de configuration.
Naviguer rapidement.
Copier, couper et coller du texte.
Rechercher dans un fichier.
Annuler et refaire des modifications.
Sauvegarder ton travail.
📖 Avant de commencer

Imagine.

Il est 2h du matin.

Le site de production est en panne.

Tu te connectes sur un serveur Linux minimal.

Tu tapes :

nano /etc/nginx/nginx.conf

Réponse :

nano: command not found

Tu essaies :

code .

Impossible.

Pas d'interface graphique.

Le seul éditeur disponible est :

vi

ou

vim

👉 C'est pour cela que tous les administrateurs apprennent au moins les bases de Vim.

Pourquoi Vim existe-t-il ?

Retour en 1976.

Les ordinateurs sont très lents.

La mémoire est limitée.

La souris n'existe pas.

Les ingénieurs veulent :

taper le moins possible ;
déplacer le moins possible leurs mains.

Vim est conçu pour éviter de quitter le clavier.

La philosophie de Vim

La première chose à comprendre est qu'il ne fonctionne pas comme Word ou VS Code.

Il fonctionne avec des modes.

Les modes de Vim

Il existe plusieurs modes, mais nous allons en apprendre quatre.

               +----------------+
               | Mode Normal    |
               +----------------+
                 ↑     ↓
      Esc        |     | i / a / o
                 |     ↓
          +----------------+
          | Mode Insertion |
          +----------------+
                 ↑
                Esc

Mode Visuel : sélectionner du texte
Mode Commande : sauvegarder, quitter...

Le plus important :

👉 Quand Vim démarre, tu es en mode Normal.

Tu ne peux pas écrire directement.

Pourquoi ?

Parce que les lettres deviennent des commandes.

Par exemple :

En mode Normal :

j

signifie :

Descendre.

Et non écrire la lettre j.

Premier réflexe

Créer un fichier :

vim test.txt

Tu arrives ici :

~
~
~
~

Tu es en mode Normal.

Comment écrire ?

Appuie sur :

i

(i comme Insert)

Tu passes en mode Insertion.

Tu peux maintenant écrire.

Exemple :

Bonjour Dominique
Revenir en mode Normal

Appuie sur :

Esc

Toujours.

Toujours.

Toujours.

Quand tu ne sais plus où tu es :

👉 Appuie sur Échap (Esc).

C'est le réflexe numéro 1.

Sauvegarder

Depuis le mode Normal :

Tape :

:w

Puis :

Entrée.

Le fichier est enregistré.

Quitter

Toujours depuis le mode Normal :

:q
Sauvegarder et quitter
:wq

ou

:x
Quitter sans enregistrer
:q!

Le fameux.

Tout le monde l'utilise.

Les déplacements

En mode Normal :

h

← gauche

j

↓ bas

k

↑ haut

l

→ droite

Pourquoi ces lettres ?

Parce qu'elles sont sous les doigts.

Les mains ne quittent jamais le clavier.

Déplacements modernes

Les flèches fonctionnent également.

Mais avec l'habitude, h j k l deviennent plus rapides.

Aller au début
gg
Aller à la fin
G
Début de ligne
0
Fin de ligne
$
Copier

En mode Normal :

yy

Copie la ligne.

Coller
p
Couper
dd

Supprime (et mémorise) la ligne.

Annuler
u
Refaire
Ctrl + R
Rechercher

Tape :

/erreur

Puis :

Entrée.

Vim cherche le mot :

erreur

Occurrence suivante :

n

Occurrence précédente :

N
Les nombres

Très puissant.

Exemple :

10j

Descend de :

10 lignes.

20dd

Supprime :

20 lignes.

15yy

Copie :

15 lignes.

Cas réel DevOps 💼

Tu modifies :

/etc/nginx/nginx.conf

Tu dois :

ajouter une ligne ;
enregistrer ;
quitter ;
recharger Nginx.

Un administrateur expérimenté le fait en quelques secondes sans jamais utiliser la souris.

⚠️ Les erreurs classiques

❌ Oublier que Vim démarre en mode Normal.

❌ Essayer d'écrire sans passer en mode Insertion.

❌ Fermer le terminal au lieu de quitter Vim.

❌ Modifier un fichier système sans sauvegarde.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

sauvegarde avant une modification importante ;
utilise / pour rechercher rapidement ;
connaît u, dd, yy, p, gg, G par cœur ;
reste majoritairement en mode Normal.
📝 Résumé

Aujourd'hui, tu as appris :

Vim fonctionne avec des modes.
Esc ramène toujours au mode Normal.
i permet d'insérer du texte.
:w sauvegarde.
:q quitte.
:wq sauvegarde et quitte.
:q! quitte sans enregistrer.
yy, dd, p, u sont les commandes essentielles.
🧪 TP 7 — Premiers pas avec Vim

Nous allons créer un véritable terrain d'entraînement.

1. Créer un laboratoire
mkdir -p ~/devopslab/vim-lab
cd ~/devopslab/vim-lab
2. Créer un fichier
vim notes.txt
3. Passer en mode Insertion

Appuie sur :

i

Écris :

Bonjour Dominique

Bienvenue dans Vim

Je découvre les modes
4. Sauvegarder

Appuie sur :

Esc

Puis :

:w
5. Quitter
:q
6. Réouvrir
vim notes.txt

Teste ensuite :

gg
G
0
$
7. Copier

Sur une ligne :

yy

Puis :

p
8. Couper
dd

Puis :

p
9. Annuler
u
10. Refaire
Ctrl + R
11. Rechercher

Tape :

/Bonjour

Puis :

n
🎯 Challenge du chapitre

Sans regarder tes notes, ouvre un nouveau fichier et réalise les actions suivantes :

Créer config.txt.
Écrire trois lignes.
Sauvegarder.
Copier la deuxième ligne.
La coller deux fois.
Supprimer la première ligne.
Annuler.
Quitter en enregistrant.

Si tu y arrives, tu maîtrises déjà les bases indispensables de Vim.

🧰 Boîte à outils du Senior — Vim

Les commandes que je connais par cœur :

Commande	Action
i	Mode insertion
Esc	Retour au mode normal
:w	Sauvegarder
:q	Quitter
:wq	Sauvegarder et quitter
:q!	Quitter sans sauvegarder
yy	Copier une ligne
dd	Couper une ligne
p	Coller
u	Annuler
Ctrl + R	Refaire
gg	Début du fichier
G	Fin du fichier
/mot	Rechercher
n	Résultat suivant
N	Résultat précédent

👉 Avec seulement ces commandes, tu peux déjà éditer la plupart des fichiers de configuration sur un serveur Linux.

📖 Anecdote d'entreprise

Un administrateur devait corriger une erreur dans le fichier :

/etc/ssh/sshd_config

Il a ouvert Vim.

Ne sachant pas comment quitter, il a simplement fermé sa fenêtre SSH.

La modification n'a jamais été enregistrée.

Quelques minutes plus tard, il pensait avoir sécurisé le serveur... alors qu'en réalité rien n'avait changé.

Depuis ce jour, il répétait toujours aux nouveaux arrivants :

"Avant d'apprendre à modifier un fichier avec Vim, apprends à en sortir."

😄 Cette histoire fait sourire, mais elle est arrivée plus d'une fois dans des équipes d'administration.
