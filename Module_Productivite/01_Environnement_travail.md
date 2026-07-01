# L'environnement de travail d'un Ingénieur DevOps

"Ton poste de travail est ton atelier. Un bon artisan commence par organiser ses outils."

🎯 Objectifs

À la fin de ce chapitre tu sauras :

Organiser ton poste de travail.
Comprendre ce qu'est un terminal.
Organiser tes dossiers.
Différencier environnement graphique et terminal.
Comprendre le rôle du shell.
Préparer ton Ubuntu pour toute la formation.
Avant de commencer

Imagine un mécanicien.

Son garage est en désordre.

Les clés sont partout.

Les tournevis sont mélangés.

Les vis traînent au sol.

Peut-il travailler efficacement ?

Non.

Un DevOps fonctionne exactement de la même manière.

Ton poste de travail est un laboratoire

Pendant toute cette académie, ton ordinateur ne sera plus un simple PC.

Il deviendra :

Un laboratoire DevOps

Nous allons l'organiser comme une entreprise organise ses serveurs.

Notre environnement actuel

Tu m'as déjà fourni les informations de ta machine.

Tu disposes de :

Élément	Valeur
Distribution	Ubuntu 24.04.4 LTS
Utilisateur	dominique
Dossier personnel	/home/dominique
Shell	Bash
Docker	Installé
Réseau	Fonctionnel
Wi-Fi	wlp3s0
Adresse IP	192.168.1.36

👉 C'est parfait pour commencer.

Le bureau Linux

Quand Ubuntu démarre, plusieurs couches sont déjà en fonctionnement.

Matériel
      │
Kernel Linux
      │
systemd
      │
Services
      │
Serveur graphique
      │
GNOME
      │
Tes applications

Le bureau que tu vois n'est qu'une application parmi d'autres.

Ce n'est pas Linux.

Linux continue de fonctionner même sans interface graphique.

Le Terminal

Le terminal est simplement une fenêtre.

À l'intérieur de cette fenêtre fonctionne un programme appelé :

Shell

Dans ton cas :

echo $SHELL

tu obtiendras probablement :

/bin/bash

Le terminal et le shell sont deux choses différentes.

C'est une confusion très fréquente.

Une analogie

Imagine :

Le terminal est :

Le téléphone

Le shell est :

La personne qui répond

Le téléphone n'effectue aucun travail.

La personne oui.

Le Shell

Le shell est un interpréteur.

Tu écris :

ls

Le shell comprend cette commande.

Puis il demande au noyau de lancer le programme correspondant.

Souviens-toi du Module 01 :

Clavier
↓

Terminal

↓

Shell

↓

Kernel

↓

CPU

Tout est lié.

L'arborescence personnelle

Ton dossier personnel est :

/home/dominique

C'est ton espace privé.

Il contient :

Documents
Images
Téléchargements
.bashrc
.ssh
.config
etc.

Le point (.) devant un nom signifie que le fichier ou le dossier est caché par défaut.

Une bonne organisation

Nous allons utiliser une structure simple et durable.

Dans ~/devopslab, je te propose l'organisation suivante :

devopslab/
│
├── 00-roadmap/
├── 01-fondamentaux/
├── 02-productivite/
├── 03-linux/
├── 04-reseau/
├── 05-git/
├── 06-bash/
├── 07-architecture/
├── 08-api/
├── 09-bdd/
├── 10-docker/
├── 11-cicd/
├── 12-ansible/
├── 13-terraform/
├── 14-kubernetes/
├── 15-stockage/
├── 16-monitoring/
├── 17-devsecops/
├── 18-pki/
├── 19-cloud/
├── 20-windows/
├── 21-powershell/
├── 22-sre/
└── 23-projet-final/

👉 Chaque module contiendra ensuite ses propres cours, TP, labs et notes.

Les outils d'un DevOps

Un ingénieur passe son temps entre quelques outils.

Environ :

Terminal        ████████████████ 60 %

VS Code         ███████          20 %

Navigateur      ████             10 %

Documentation   ███              5 %

Réunions        ██               5 %

Le terminal est donc ton principal outil de travail.

Les espaces de travail (Workspaces)

Ubuntu permet d'utiliser plusieurs bureaux virtuels.

Imagine :

Bureau 1 : documentation.
Bureau 2 : terminal.
Bureau 3 : navigateur.
Bureau 4 : monitoring.

Tu changes de bureau sans fermer tes applications.

C'est extrêmement pratique lorsqu'on gère plusieurs environnements.

Une journée d'un DevOps

Imagine une matinée classique.

Tu as :

4 terminaux ouverts ;
VS Code ;
un navigateur avec la documentation ;
Grafana ;
GitLab ;
Slack ou Teams.

Tu passes constamment de l'un à l'autre.

L'objectif est de le faire sans perdre le fil.

Cas réel DevOps 💼

Tu es connecté sur :

un serveur de production ;
un serveur de préproduction ;
ta machine locale.

Une erreur de terminal peut être catastrophique.

Par exemple :

Tu crois être sur ton PC.

Tu es en réalité sur le serveur de production.

Tu exécutes :

rm -rf *

💥 Catastrophe.

Un environnement bien organisé réduit énormément ce type d'erreur.

⚠️ Les erreurs classiques

❌ Ouvrir tous les projets dans le même terminal.

❌ Utiliser le compte root en permanence.

❌ Travailler avec 25 onglets de navigateur sans organisation.

❌ Laisser le Bureau rempli de fichiers.

❌ Mélanger les projets personnels et professionnels.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

nomme clairement ses dossiers ;
sépare les environnements (local, test, production) ;
garde peu de fenêtres ouvertes mais bien organisées ;
utilise plusieurs terminaux spécialisés (logs, édition, SSH, Docker).

L'objectif n'est pas d'avoir un "bureau joli", mais un environnement où l'on retrouve immédiatement ce que l'on cherche.

📝 Résumé

Aujourd'hui, tu as appris que :

Le bureau graphique est une application, pas Linux.
Le terminal est une fenêtre.
Le shell est l'interpréteur des commandes.
Ton dossier personnel est ton espace de travail.
Une bonne organisation est essentielle pour éviter les erreurs.

🧰 Boîte à outils du Senior
Module 02 – Chapitre 1
L'environnement de travail

Voici les commandes que j'utilise pratiquement tous les jours.

📍 Savoir où je suis
pwd

Affiche le dossier courant.

👤 Qui suis-je ?
whoami

Affiche l'utilisateur courant.

🖥 Quel shell j'utilise ?
echo $SHELL
🏠 Retourner immédiatement dans le Home
cd

ou

cd ~

Je ne tape jamais :

cd /home/dominique

C'est inutile.

📂 Voir les fichiers cachés
ls -la

Je l'utilise probablement plusieurs dizaines de fois par jour.

📁 Créer rapidement un laboratoire
mkdir -p ~/devopslab/tests

Le -p évite les erreurs si les dossiers existent déjà.

🧹 Nettoyer un terminal
clear

ou beaucoup plus souvent :

Ctrl + L
📌 Toujours savoir sur quelle machine je travaille

Très important.

Sur un serveur de production :

hostname

ou

hostnamectl

Je vérifie presque toujours avant une manipulation importante.

🔍 Identifier le système
cat /etc/os-release

ou

hostnamectl
📋 Les commandes indispensables
pwd

whoami

hostname

hostnamectl

echo $SHELL

ls -la

cd ~

clear
⭐ Astuce du Senior

Je regarde systématiquement trois choses quand j'ouvre un terminal :

où je suis (pwd) ;
qui je suis (whoami) ;
sur quelle machine je suis (hostname).

Cette habitude évite énormément d'erreurs.