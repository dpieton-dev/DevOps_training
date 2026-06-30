# 🧪 TP 1 — Découvrir ton propre ordinateur

Nous allons terminer cette première leçon par un TP très concret. L'objectif n'est pas de lancer des commandes au hasard, mais de faire le lien entre la théorie et ta machine.

---

Exécute les commandes suivantes une par une :
```Bash
lscpu
```

👉 Observe :

* le modèle de ton processeur ;
* le nombre de cœurs (Core(s) per socket) ;
* le nombre de threads (CPU(s)) ;
* l'architecture (x86_64).

Ensuite :
```Bash
free -h
```

👉 Observe :

* la quantité de RAM installée ;
* la mémoire utilisée ;
* la mémoire disponible.

Puis :
```Bash
lsblk
```

👉 Repère :

* ton disque principal ;
* ses partitions ;
* leur taille.

Enfin :
```Bash
df -h
```

👉 Vérifie :

* les systèmes de fichiers montés ;
* l'espace utilisé ;
* l'espace libre.

---

Ne cherche pas encore à tout comprendre. On va revenir sur chacune de ces informations dans les prochains cours.