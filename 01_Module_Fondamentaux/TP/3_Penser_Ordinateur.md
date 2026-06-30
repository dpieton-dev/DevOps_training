🧪 TP 3 — Observer ton processeur

Cette fois, nous allons regarder ton processeur avec des outils simples.

Exécute :

uname -m

👉 Tu devrais voir x86_64, ce qui confirme que ton système est 64 bits.

Puis :

lscpu

Observe notamment :

Architecture
CPU(s)
Thread(s) per core
Core(s) per socket
Model name

Ensuite :

cat /proc/cpuinfo | less

Ne cherche pas encore à tout comprendre. Observe simplement la quantité d'informations exposées par le noyau.

Enfin :

nproc

Cette commande affiche le nombre de processeurs logiques disponibles pour ton système.