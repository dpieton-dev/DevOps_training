Les outils indispensables d'un Ingénieur DevOps

"Un Senior ne remplace pas les outils classiques. Il les complète avec de meilleurs outils."

🎯 Objectifs

À la fin de ce chapitre, tu connaîtras :

Les outils Linux historiques.
Leurs équivalents modernes.
Quand utiliser chacun.
Les outils que j'installe sur pratiquement toutes mes machines.
📖 Avant de commencer

Imagine deux administrateurs.

Le premier utilise uniquement :

ls
cat
grep
find
top
du

Le second utilise :

eza
bat
ripgrep
fd
btop
ncdu
fzf

Les deux savent administrer Linux.

Le second ira souvent plus vite.

Une règle importante

Ne remplace jamais un outil que tu ne maîtrises pas.

D'abord :

find

Puis :

fd

D'abord :

grep

Puis :

ripgrep

Cette progression est essentielle.

Les outils historiques vs modernes
Historique	Moderne	Utilité
ls	eza	Afficher les fichiers
cat	bat	Lire un fichier
grep	ripgrep (rg)	Rechercher du texte
find	fd	Rechercher des fichiers
top	btop	Surveiller le système
du	ncdu	Analyser l'espace disque
man	tldr	Documentation simplifiée
cd	zoxide	Navigation intelligente
1️⃣ eza

Successeur moderne de ls.

Installation :

sudo apt install eza

Exemple :

eza

Affichage :

couleurs ;
icônes (selon le terminal) ;
permissions lisibles.

Arborescence :

eza --tree

Très pratique.

2️⃣ bat

Successeur de cat.

Installation :

sudo apt install bat

⚠️ Sous Ubuntu, la commande est :

batcat

Exemple :

batcat ~/.bashrc

Tu obtiens :

coloration syntaxique ;
numéros de lignes ;
pagination.
3️⃣ ripgrep

Nom :

rg

Installation :

sudo apt install ripgrep

Exemple :

rg "docker"

Recherche extrêmement rapide.

Plus rapide que :

grep -R

sur de gros projets.

4️⃣ fd

Alternative moderne à :

find

Installation :

sudo apt install fd-find

Sous Ubuntu :

fdfind

Exemple :

fdfind nginx

Beaucoup plus simple que :

find . -name "*nginx*"
5️⃣ jq

L'outil indispensable du DevOps.

Installation :

sudo apt install jq

Pourquoi ?

Les API renvoient souvent du JSON.

Exemple :

cat fichier.json | jq

Le JSON est automatiquement formaté.

Nous l'utiliserons énormément dans les modules API, Kubernetes et CI/CD.

6️⃣ tree

Installation :

sudo apt install tree

Exemple :

tree

Très utile pour documenter un projet.

7️⃣ htop

Version améliorée de top.

Installation :

sudo apt install htop

Tu peux :

tuer un processus ;
trier ;
rechercher.

Très agréable à utiliser.

8️⃣ btop

Encore plus moderne.

Installation :

sudo apt install btop

Il affiche :

CPU ;
RAM ;
réseau ;
disques ;
processus.

Personnellement, je préfère btop sur mon poste de travail et htop sur des serveurs plus légers.

9️⃣ ncdu

Analyse interactive de l'espace disque.

Installation :

sudo apt install ncdu

Exemple :

ncdu

Tu repères immédiatement les dossiers volumineux.

🔟 tldr

Les pages de manuel (man) sont très complètes, mais parfois longues.

tldr donne des exemples concrets.

Installation :

sudo apt install tldr

Premier téléchargement des pages :

tldr --update

Exemple :

tldr tar

Tu obtiens les usages les plus fréquents.

1️⃣1️⃣ fzf

Mon outil préféré.

Installation :

sudo apt install fzf

Recherche interactive.

Exemple :

history | fzf

Tu recherches dans ton historique de manière visuelle.

Nous reviendrons longuement dessus dans le module Bash.

1️⃣2️⃣ zoxide

Une révolution pour naviguer.

Au lieu de :

cd ~/devopslab/03-linux/scripts/tests

Tu écriras :

z tests

Il apprend les dossiers que tu fréquentes le plus.

Installation :

sudo apt install zoxide

Configuration dans .bashrc :

eval "$(zoxide init bash)"
Une boîte à outils moderne

Voici ce que j'installe généralement sur un nouveau poste :

Git
VS Code
Docker
tmux
Vim
eza
bat
ripgrep
fd
jq
tree
htop
btop
fzf
zoxide
ShellCheck

Cette liste évoluera avec la formation.

Cas réel DevOps 💼

Un pipeline CI échoue.

Tu reçois une réponse JSON de 500 lignes.

Avec :

cat reponse.json

Tu ne vois rien.

Avec :

jq .

Le JSON est immédiatement lisible.

Tu trouves l'erreur en quelques secondes.

⚠️ Les erreurs classiques

❌ Installer des outils sans savoir pourquoi.

❌ Utiliser un outil moderne sur un serveur minimal où il n'est pas disponible.

❌ Oublier les commandes historiques.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

connaît les commandes classiques ;
installe des outils modernes sur son poste ;
sait revenir aux outils historiques lorsqu'il travaille sur un serveur minimal.
📝 Résumé

Aujourd'hui, tu as découvert une boîte à outils moderne pour Linux.

Tu sais désormais qu'il existe des alternatives plus ergonomiques à de nombreuses commandes historiques, sans pour autant les remplacer dans ton apprentissage.

🧪 TP 10 — Construire ta boîte à outils
1. Installer les outils
sudo apt update

sudo apt install \
eza \
bat \
ripgrep \
fd-find \
jq \
tree \
htop \
btop \
ncdu \
tldr \
fzf \
zoxide
2. Tester chaque outil
eza
eza --tree
batcat ~/.bashrc
rg "alias" ~/.bashrc
fdfind bash
tree ~/devopslab
htop
btop
ncdu ~
tldr ls
history | fzf
3. Activer zoxide

Ajoute dans ton .bashrc :

eval "$(zoxide init bash)"

Recharge ensuite :

source ~/.bashrc
🎯 Challenge du chapitre

Installe tous ces outils sur ton poste.

Puis réponds à ces questions :

Quel outil remplace grep ?
Quel outil est idéal pour lire du JSON ?
Quel outil préfères-tu entre htop et btop ? Pourquoi ?
Dans quel cas utiliserais-tu tree ?
Pourquoi faut-il connaître les commandes historiques malgré l'existence d'outils modernes ?
🧰 Boîte à outils du Senior — Les indispensables

Si je devais choisir 10 outils seulement pour un poste DevOps, ce seraient :

Outil	Pourquoi
git	Versionner le code
tmux	Sessions persistantes
vim	Éditer partout
jq	JSON
ripgrep	Recherche ultra rapide
fzf	Recherche interactive
htop	Surveillance système
tree	Visualiser un projet
ShellCheck	Vérifier les scripts Bash
tldr	Trouver rapidement un exemple de commande
🧠 Comment raisonne un Senior ?

Situation : tu dois rechercher le mot password dans un projet de 30 000 fichiers.

Un débutant pense :

"Je vais ouvrir les fichiers un par un."

Un administrateur intermédiaire pense :

"Je vais utiliser grep -R."

Un senior pense :

"Je vais utiliser ripgrep, exclure les dossiers inutiles et obtenir le résultat en quelques secondes."

La différence ne réside pas seulement dans la commande, mais dans la capacité à choisir le bon outil.

📖 Anecdote d'entreprise

Sur un projet contenant plus de 2 millions de lignes de code, une recherche avec :

grep -R "TODO" .

prenait près de 30 secondes.

Après avoir adopté ripgrep, la même recherche s'effectuait en moins d'une seconde.

Sur une journée, où cette recherche était répétée des dizaines de fois, le gain de productivité était considérable.

🎓 Leçon : les bons outils ne remplacent pas les compétences, mais ils réduisent énormément le temps passé sur les tâches répétitives.