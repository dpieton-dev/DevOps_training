🧪 TP 3 — Explorer le terminal

Nous allons observer tous ces concepts.

1. Vérifier le terminal actuel
tty

Observe le résultat.

2. Ouvrir un deuxième terminal

Refais :

tty

Compare les deux résultats.

3. Vérifier le shell
echo $SHELL

Puis :

ps -p $$ -f

Cette commande affiche le processus correspondant à ton shell actuel.

4. Tester stdout
echo Bonjour

Tu écris sur la sortie standard.

5. Tester stderr
ls dossier_qui_n_existe_pas

Observe le message d'erreur.

6. Rediriger stdout
ls > fichiers.txt

Puis :

cat fichiers.txt

La sortie de ls a été enregistrée dans un fichier.

7. Rediriger stderr
ls dossier_qui_n_existe_pas 2> erreurs.txt

Puis :

cat erreurs.txt

Le message d'erreur a été capturé dans un fichier différent.

8. Utiliser un pipe
ls | wc -l

Tu comptes le nombre d'éléments du répertoire courant.

9. Chaîner plusieurs commandes
ls -la | grep bash

Tu affiches uniquement les fichiers contenant "bash" dans leur nom.

🎯 Challenge du chapitre

Réponds à ces questions sans regarder tes notes :

Quelle est la différence entre un terminal et un shell ?
Pourquoi tty affiche-t-il /dev/pts/0 ?
Pourquoi Linux sépare-t-il stdout et stderr ?
Explique avec tes mots ce que fait le caractère |.
🧰 Boîte à outils du Senior — Terminal

Voici les commandes que j'utilise quotidiennement :

history          # historique des commandes
clear            # nettoyer l'écran
reset            # réinitialiser un terminal "cassé"
tty              # afficher le terminal courant
whoami           # utilisateur courant
pwd              # répertoire courant
which            # où se trouve une commande ?
type             # nature d'une commande
man              # manuel
tldr             # aide simplifiée (à installer)

Et surtout, trois réflexes :

Toujours utiliser Tab pour compléter les commandes.
Toujours utiliser Ctrl + R pour retrouver une commande.
Toujours privilégier les pipes plutôt que des commandes compliquées.