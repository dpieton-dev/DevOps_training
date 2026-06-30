# 🧪 TP 2 — Observer le démarrage de ton système

Nous allons déjà relier la théorie à ta machine Ubuntu.

Exécute les commandes suivantes :

```bash
hostnamectl
```

👉 Observe la version du noyau (Kernel) et le firmware (Firmware s'il est affiché).

Puis :
```bash
ps -p 1 -f
```
👉 Vérifie que le PID 1 est bien systemd.

Ensuite :
```bash
systemd-analyze
```
👉 Cette commande indique combien de temps ont pris :

le firmware (UEFI/BIOS)
le chargeur de démarrage
le noyau
l'espace utilisateur (userspace)

Enfin :
```bash
systemd-analyze blame | head -20
```
👉 Tu verras les services qui ont mis le plus de temps à démarrer.