🧪 TP 6 — Observer les processus

Nous allons regarder les processus qui vivent actuellement sur ton Ubuntu.

Exécute :

ps

Tu verras les processus associés à ton terminal.

Ensuite :

ps -ef

Tu obtiendras la liste complète des processus du système.

Puis :

pstree

Si la commande n'est pas disponible :

sudo apt install psmisc

pstree est très intéressante, car elle affiche l'arbre des processus. Tu pourras y retrouver systemd à la racine.

Ensuite :

top

Observe :

les PID ;
l'utilisation CPU ;
la mémoire ;
les états des processus.

Quitte avec :

q

Enfin :

echo $$

Cette commande affiche le PID de ton shell Bash actuel.

Puis :

ps -f -p $$

Tu verras les informations détaillées sur le processus qui exécute ton terminal.
