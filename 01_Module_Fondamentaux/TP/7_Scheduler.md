🧪 TP 7 — Observer le Scheduler

Nous allons regarder quelques informations simples.

Exécute :

lscpu

Repère :

le nombre de cœurs ;
le nombre de processeurs logiques ;
les threads par cœur.

Ensuite :

top

Appuie sur :

1

Tu verras chaque cœur séparément.

C'est très utilisé en production.

Puis :

ps -eo pid,ppid,ni,comm --sort=ni | head -20

Observe la colonne NI (nice), qui reflète la priorité demandée par les processus.

Enfin :

uptime

Tu verras une information très importante :

load average

Nous ne l'étudierons pas aujourd'hui, mais sache qu'elle est l'un des premiers indicateurs consultés par un administrateur Linux.

🎓 Exercice de réflexion

Imagine un serveur avec :

8 cœurs ;
1 processus qui utilise 100 % d'un seul cœur.

Réfléchis :

Le serveur est-il forcément saturé ?
Les 7 autres cœurs sont-ils disponibles ?
Que se passerait-il si l'application savait utiliser plusieurs cœurs ?

Nous répondrons à ces questions dans le module Linux lorsque nous parlerons de performances.