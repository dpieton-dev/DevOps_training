🧪 TP 8 — Explorer le système de fichiers spécial

Nous allons observer quelques répertoires particuliers.

Exécute :

ls /

Tu verras les grands répertoires du système.

Ensuite :

ls /dev | head

Observe les nombreux "fichiers" représentant des périphériques.

Puis :

ls /proc | head

Tu verras des numéros (PID) et des fichiers spéciaux.

Maintenant :

ls -li ~

La première colonne affiche les numéros d'inode.

Enfin :

stat ~/.bashrc

Cette commande donne des informations détaillées sur un fichier, notamment son inode, ses permissions et ses dates.

Ne t'inquiète pas si tout n'est pas encore clair : nous reviendrons en détail sur ces notions dans le module Linux.