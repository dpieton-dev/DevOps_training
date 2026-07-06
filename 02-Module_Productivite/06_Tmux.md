# tmux : Ne perdez plus jamais votre terminal

"SSH te connecte au serveur. tmux fait en sorte que tu n'en sois jamais déconnecté."

## 🎯 Objectifs

À la fin de ce chapitre, tu seras capable de :

* Comprendre pourquoi tmux existe.
* Installer et configurer tmux.
* Créer plusieurs fenêtres et panneaux.
* Détacher et rattacher une session.
* Travailler sur plusieurs tâches simultanément.
* Comprendre pourquoi presque tous les administrateurs Linux utilisent tmux.


## 📖 Avant de commencer

Imagine cette situation.

Tu lances une mise à jour : sudo apt update && sudo apt upgrade

La mise à jour dure : 40 minutes.

Au bout de 35 minutes, le Wi-Fi se coupe, ton SSH est fermé et la mise à jour est interrompue.

Tu dois tout recommencer.

Cela arrive beaucoup plus souvent qu'on ne le croit.


## Pourquoi tmux a été créé ?

Parce qu'un terminal classique est lié à ta connexion.

Si la connexion disparaît : Le terminal disparaît.

Les processus reçoivent souvent un signal de fin et peuvent s'arrêter.

**tmux** change complètement cette logique.


## Une analogie

Imagine un bureau.

Sans tmux : Tu travailles sur la table.

Quelqu'un enlève la table. Tu perds tout.

Avec tmux : Tu travailles dans une pièce.

Même si tu quittes la pièce, la pièce reste et tu peux revenir plus tard.


## Qu'est-ce que tmux ?

tmux signifie : **Terminal Multiplexer**

Il permet de créer plusieurs terminaux dans un seul terminal.

Mais surtout, les sessions continuent de fonctionner même si tu te déconnectes.


## Architecture

Sans tmux :
```
SSH
↓
Bash
↓
Commande
```

Avec tmux :
```
SSH
↓
tmux
↓
Fenêtre 1

Fenêtre 2

Fenêtre 3
↓
Bash
```

tmux devient un intermédiaire entre toi et le shell.


## Installation

Sur Ubuntu :

* sudo apt update
* sudo apt install tmux

Vérifie ensuite : **tmux -V**

Tu devrais obtenir une version, par exemple : **tmux 3.x**


## Première session

Lance : tmux

Tu entres dans ta première session, Tu remarqueras une barre d'état en bas de l'écran.

C'est tmux.

Le préfixe

Toutes les commandes tmux commencent par :

Ctrl + B

Puis une autre touche.

Par exemple :

Ctrl + B

puis

d
Détacher une session

Tape :

Ctrl + B

d

Tu reviens au terminal normal.

Mais...

La session continue.

Voir les sessions
tmux ls

Exemple :

0: 1 windows
Revenir dans une session
tmux attach

ou

tmux attach -t 0

Tu retrouves exactement ton environnement.

Nommer une session

Au lieu d'un numéro :

tmux new -s devops

Puis :

tmux attach -t devops

C'est beaucoup plus pratique.

Les fenêtres

Créer une nouvelle fenêtre :

Ctrl + B

c

Fenêtre suivante :

Ctrl + B

n

Fenêtre précédente :

Ctrl + B

p

Lister les fenêtres :

Ctrl + B

w
Les panneaux

C'est ce qui fait la force de tmux.

Diviser verticalement :

Ctrl + B

%

Diviser horizontalement :

Ctrl + B

"

Exemple :

+-----------------------+
| journalctl -f        |
+-----------+-----------+
| htop      | Bash      |
+-----------+-----------+

Trois terminaux.

Une seule fenêtre.

Naviguer entre les panneaux
Ctrl + B

Flèche

Très simple.

Redimensionner

Maintenir :

Ctrl + B

Puis :

Ctrl + Flèche

(selon la configuration de tmux).

Nous personnaliserons cela plus tard.

Fermer un panneau

Quitter simplement le shell :

exit

ou

Ctrl + D

Le panneau disparaît.

Pourquoi les administrateurs adorent tmux ?

Imagine.

Tu surveilles :

les logs Nginx ;
Docker ;
l'utilisation CPU ;
un script de déploiement.

Avec tmux :

+-------------------------+
| journalctl -f nginx    |
+-------------+-----------+
| docker logs | htop      |
+-------------+-----------+
| Bash principal          |
+-------------------------+

Tu vois tout en même temps.

Cas réel DevOps 💼

Tu lances :

ansible-playbook production.yml

Durée :

45 minutes.

Tu dois rentrer chez toi.

Tu fermes ton ordinateur.

Le lendemain.

Tu te reconnectes.

tmux attach

Le déploiement est terminé.

Tu n'as rien perdu.

⚠️ Les erreurs classiques

❌ Lancer plusieurs terminaux au lieu d'utiliser tmux.

❌ Oublier de nommer ses sessions.

❌ Fermer une session au lieu de la détacher.

❌ Ne jamais utiliser les panneaux.

⭐ Ce qu'un Senior ferait

Sur un serveur de production, un ingénieur expérimenté ouvre souvent une session tmux nommée :

maintenance

Il y place :

un panneau pour les logs ;
un panneau pour les commandes ;
un panneau pour la surveillance (htop) ;
un panneau pour les tests.

Si la connexion SSH est interrompue, tout continue de fonctionner.

📝 Résumé

Aujourd'hui, tu as appris que :

tmux est un multiplexeur de terminaux.
Une session tmux survit à une déconnexion SSH.
Une session peut contenir plusieurs fenêtres.
Une fenêtre peut contenir plusieurs panneaux.
tmux est un outil incontournable pour l'administration système.
🧪 TP 6 — Premiers pas avec tmux
1. Installer tmux
sudo apt update
sudo apt install tmux
2. Vérifier la version
tmux -V
3. Créer une session nommée
tmux new -s devops
4. Créer une deuxième fenêtre

Appuie sur :

Ctrl + B

c
5. Revenir à la première fenêtre
Ctrl + B

0

Puis retourne à la seconde avec :

Ctrl + B

1
6. Créer deux panneaux

Dans une fenêtre :

Ctrl + B, puis % (division verticale)
Ctrl + B, puis " (division horizontale)

Navigue ensuite entre les panneaux avec :

Ctrl + B

Flèches
7. Détacher la session
Ctrl + B

d

Tu reviens au terminal classique.

8. Vérifier les sessions
tmux ls
9. Revenir dans la session
tmux attach -t devops

Tu retrouves exactement tes fenêtres et tes panneaux.

🎯 Challenge du chapitre

Crée une session devops avec cette disposition :

+---------------------------+
| htop                     |
+-------------+-------------+
| bash        | bash        |
+-------------+-------------+

Si htop n'est pas installé :

sudo apt install htop

Ensuite :

Détache la session.
Ferme le terminal.
Ouvre un nouveau terminal.
Rattache la session.

Tu constateras que tout est resté en place.

🧰 Boîte à outils du Senior — tmux

Les commandes que j'utilise le plus :

tmux new -s projet      # Créer une session nommée
tmux ls                 # Lister les sessions
tmux attach -t projet   # Reprendre une session
tmux kill-session -t projet  # Supprimer une session
tmux kill-server        # Arrêter toutes les sessions

Les raccourcis indispensables :

Raccourci	Action
Ctrl + B, c	Nouvelle fenêtre
Ctrl + B, d	Détacher la session
Ctrl + B, n	Fenêtre suivante
Ctrl + B, p	Fenêtre précédente
Ctrl + B, %	Division verticale
Ctrl + B, "	Division horizontale
Ctrl + B, flèches	Changer de panneau
📖 Anecdote d'entreprise

Lors d'une migration de bases de données, un script devait durer près de 6 heures.

Un administrateur a lancé le script directement dans un terminal SSH.

Deux heures plus tard, une coupure VPN a interrompu la connexion… et le script s'est arrêté.

Le lendemain, un autre administrateur a relancé l'opération, mais cette fois dans une session tmux.

Une nouvelle coupure réseau s'est produite.

Cette fois, le script a continué son exécution.

À la reconnexion :

tmux attach

La migration était terminée.

🎓 Leçon : sur une opération longue ou critique, tmux est une assurance.