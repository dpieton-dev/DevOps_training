# Virtualisation et Conteneurs

"Docker n'a pas remplacé les machines virtuelles. Il a résolu un problème différent."

---

## 🎯 Objectifs

À la fin de ce chapitre, tu comprendras :

Pourquoi la virtualisation a été inventée.
Ce qu'est une machine virtuelle.
Ce qu'est un hyperviseur.
Pourquoi une VM est plus lourde qu'un conteneur.
Ce qu'est réellement un conteneur.
Pourquoi Docker est si rapide.
Pourquoi Kubernetes utilise des conteneurs.
📖 Retour en arrière

Nous sommes en 2002.

Une entreprise possède un serveur.

Voici sa configuration :

2 processeurs
8 Go de RAM
500 Go de disque

À l'époque, c'était une machine très puissante.

L'entreprise installe :

Apache
PHP
MySQL

Et... c'est tout.

Le problème

Le serveur utilise seulement :

CPU : 8 %

RAM : 20 %

👉 80 % de la machine est inutilisée.

Pourtant...

L'entreprise achète quand même un deuxième serveur.

Puis un troisième.

Puis un quatrième.

Pourquoi ?

Parce qu'on évitait de mélanger les applications.

Pourquoi ?

Imaginons :

Serveur 1 :

Apache

Serveur 2 :

MySQL

Serveur 3 :

Mail

Chaque serveur coûte :

de l'argent ;
de l'électricité ;
du refroidissement ;
de la maintenance.

Le gaspillage était énorme.

L'idée géniale

Des ingénieurs se sont dit :

Pourquoi ne pas faire croire à un ordinateur qu'il est plusieurs ordinateurs ?

C'est la naissance de la virtualisation.

Une machine virtuelle

Une machine virtuelle est :

Un ordinateur logiciel.

Elle possède virtuellement :

un processeur ;
de la RAM ;
un disque ;
une carte réseau ;
un BIOS.

Comme une vraie machine.

Schéma

Avant :

Serveur

↓

Ubuntu

↓

Apache

Après :

Serveur physique

↓

Hyperviseur

↓

VM Ubuntu

VM Debian

VM Windows

VM Rocky Linux

Une seule machine.

Plusieurs ordinateurs virtuels.

L'hyperviseur

L'hyperviseur est un logiciel très spécial.

Il partage :

le CPU ;
la RAM ;
le disque ;
le réseau.

Entre plusieurs machines virtuelles.

Quelques exemples :

VMware ESXi
Hyper-V
KVM
Xen
VirtualBox (pour les postes de travail)
Pourquoi une VM est-elle lourde ?

Prenons une VM Ubuntu.

Elle contient :

son noyau Linux ;
systemd ;
les pilotes ;
les services ;
les bibliothèques ;
les applications.

Une deuxième VM Ubuntu contient... exactement la même chose.

Chaque VM embarque son propre système d'exploitation.

Une analogie

Imagine un immeuble.

Chaque appartement possède :

sa cuisine ;
sa salle de bain ;
son chauffage.

Beaucoup de choses sont dupliquées.

Les VM fonctionnent un peu de cette manière.

Docker arrive...

En 2013, un problème se pose.

Les développeurs veulent lancer rapidement des applications.

Ils se rendent compte que les VM sont parfois surdimensionnées pour ce besoin.

Pourquoi démarrer un système complet juste pour exécuter une application ?

L'idée de Docker

Docker dit :

Pourquoi créer plusieurs noyaux ?

Linux en possède déjà un.

Pourquoi ne pas partager le même noyau ?

Schéma

Machine virtuelle :

Application

↓

Bibliothèques

↓

Ubuntu

↓

Kernel Ubuntu

Deuxième VM :

Application

↓

Bibliothèques

↓

Ubuntu

↓

Kernel Ubuntu

Chaque VM possède son propre noyau.

Avec Docker :

Application 1

Application 2

Application 3

↓

Même noyau Linux

Un seul noyau.

Tout le monde le partage.

Alors qu'est-ce qu'un conteneur ?

Voici la définition que je veux que tu retiennes :

Un conteneur est un ou plusieurs processus isolés qui partagent le noyau du système hôte.

C'est tout.

Il n'y a pas de "mini Linux" à l'intérieur.

Pas de BIOS.

Pas de démarrage complet.

Pas de noyau supplémentaire.

Pourquoi Docker démarre si vite ?

Créer une VM :

créer un disque ;
démarrer le BIOS ;
lancer le bootloader ;
démarrer le noyau ;
lancer systemd.

Cela peut prendre plusieurs dizaines de secondes.

Créer un conteneur :

lancer un processus isolé.

Quelques centaines de millisecondes.

D'où vient cette isolation ?

Souviens-toi du chapitre sur les processus.

Le noyau Linux sait déjà isoler les processus.

Docker utilise principalement :

les namespaces (isolation) ;
les cgroups (limitation des ressources) ;
le système de fichiers en couches (OverlayFS).

Nous les étudierons en détail dans le module Docker.

VM ou conteneur ?
Machine virtuelle	Conteneur
Système complet	Application
Noyau dédié	Noyau partagé
Démarrage plus lent	Démarrage très rapide
Plus lourd	Plus léger
Isolation forte	Isolation de processus

👉 Aucun des deux n'est "meilleur". Ils répondent à des besoins différents.

Et Kubernetes ?

Kubernetes ne lance pas directement des applications.

Il orchestre des conteneurs.

Pourquoi ?

Parce qu'ils sont :

rapides ;
légers ;
faciles à remplacer ;
faciles à répliquer.

Tu comprends déjà pourquoi ils sont devenus la base des architectures modernes.

Cas réel DevOps 💼

Une entreprise possède une plateforme e-commerce.

Elle exécute :

80 microservices ;
chacun dans un conteneur Docker ;
orchestrés par Kubernetes.

Pourquoi ne pas utiliser 80 machines virtuelles ?

Parce que les conteneurs démarrent rapidement, consomment moins de ressources et sont plus faciles à déployer et à remplacer automatiquement.

⚠️ Les erreurs classiques

❌ « Un conteneur est une machine virtuelle légère. »

Non. Il s'agit de processus isolés qui partagent le noyau de l'hôte.

❌ « Docker remplace les machines virtuelles. »

Non. Les deux technologies coexistent et répondent à des besoins différents.

❌ « Un conteneur possède son propre noyau Linux. »

Non. Tous les conteneurs utilisent le noyau du système hôte.

⭐ Ce qu'un Senior ferait

Avant de choisir une technologie, un ingénieur se demande :

Ai-je besoin d'isoler un système complet ?
Ai-je besoin d'exécuter un autre système d'exploitation ?
Ai-je seulement besoin d'isoler une application ?

Ces questions orientent naturellement vers une VM ou un conteneur.

📝 Résumé

Aujourd'hui, tu as appris que :

La virtualisation permet de faire fonctionner plusieurs systèmes sur une même machine.
Les machines virtuelles possèdent chacune leur propre système d'exploitation.
Les conteneurs partagent le noyau du système hôte.
Docker utilise des mécanismes du noyau Linux pour isoler les processus.
Kubernetes orchestre des conteneurs, pas des machines virtuelles.
