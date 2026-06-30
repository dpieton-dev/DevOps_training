## Que se passe-t-il lorsque tu appuies sur le bouton Power ?

# Objectifs
À la fin de ce chapitre, tu sauras expliquer :

* pourquoi un ordinateur ne démarre pas directement Linux
* le rôle du BIOS et de l'UEFI
* ce qu'est le POST
* le rôle du bootloader
* comment le noyau Linux démarre
* pourquoi systemd est le premier processus utilisateur.

---

## Comprendre le démarrage complet
Voici la chronologie que l'on va détailler.
            Bouton Power
                │
                ▼
            Alimentation (PSU)
                │
                ▼
            Carte mère
                │
                ▼
               CPU
                │
                ▼
            BIOS / UEFI
                │
                ▼
            POST (test matériel)
                │
                ▼
            Recherche d'un périphérique de démarrage
                │
                ▼
            GRUB (Bootloader)
                │
                ▼
            Kernel Linux
                │
                ▼
            systemd
                │
                ▼
            Services
                │
                ▼
            Écran de connexion

On doit connaitre le schéma par coeur car les devOps se repose dessus.

---

## Étape 1 - Le bouton Power
On appuie sur **POWER**

Cela envoi un signal électrique à la carte mère.

---

## Étape 2 - L'alimentation
L'alimentation (PSU) reçoit ce signal.
Son rôle est de transformer le courant du secteur (230 V) en plusieurs tensions adaptées aux composants.
Par exemple :
* 12 V pour certains composants puissants.
* 5 V pour d'autres circuits.
* 3,3 V pour la logique électronique.

⚠️ Le processeur ne peut pas être alimenté directement en 230 V.

---

## Étape 3 - La carte mère
Maintenant que tout est alimenté...
La carte mère devient le chef d'orchestre. Elle relie :
* le CPU
* la RAM
* les SSD
* les ports USB
* la carte graphique
* la carte réseau

Elle ne calcule rien. Elle met simplement tous les composants en relation.

---

## Étape 4 — Le CPU se réveille

Le processeur reçoit enfin du courant. Mais il y a un problème. Il ne sait toujours rien.
Imagine un employé qui arrive dans une entreprise. On lui donne :
* un bureau
* Un ordinateur

Mais aucune consigne alors Il attend.

Le CPU est dans la même situation.

Une question importante

### Comment le CPU sait-il quelle est sa première instruction ?

Il ne parcourt pas le SSD au hasard. Les ingénieurs ont prévu une règle, le processeur commence toujours son exécution à une adresse mémoire bien précise.

À cette adresse se trouve le code du firmware (BIOS ou UEFI).
C'est la première "personne" qui lui parle.

---

## Étape 5 — BIOS ou UEFI

Le BIOS (ou aujourd'hui plus souvent l'UEFI) est un petit programme stocké sur une mémoire spéciale de la carte mère.
Il est indépendant du SSD même si on enlève le disque dur...

Le BIOS est toujours présent, son rôle est de :
* initialiser le matériel
* vérifier que les composants répondent
* trouver un périphérique de démarrage
* lancer le bootloader

C'est lui qui prend la première décision.

---

## Étape 6 — Le POST

POST signifie :
    **Power-On Self-Test**

C'est l'auto-test de la machine. Le firmware vérifie notamment :
* la RAM
* le processeur
* la carte graphique
* le clavier
* les disques
* certains périphériques essentiels

Si un composant critique manque, le démarrage s'arrête.

**Pourquoi certains PC "bipent" au démarrage ?**

Ces bips sont des codes d'erreur.
Par exemple :
* RAM absente
* carte graphique défectueuse
* problème processeur

Avant même que l'écran fonctionne, le BIOS peut déjà communiquer grâce au haut-parleur de la carte mère.

---

## Étape 7 — Le bootloader

Une fois les tests terminés, le firmware cherche un périphérique de démarrage.
Par exemple :
* SSD
* disque dur
* clé USB
* DVD
* réseau (PXE)

Sur Ubuntu, le bootloader est généralement :    **GRUB**

GRUB affiche souvent un menu comme celui-ci :
* Ubuntu
* Advanced options
* Memory test

Pourquoi ?

Parce qu'il permet de choisir quel noyau démarrer.

**Pourquoi un bootloader est-il nécessaire ?**

Imagine que le SSD contient :
* Ubuntu
* Windows
* un ancien noyau Linux
* un mode de récupération

Qui choisit lequel lancer ?
Le bootloader. Il est le "chef d'orchestre" du démarrage des systèmes d'exploitation.

---

## Étape 8 — Le noyau Linux

GRUB charge alors le noyau Linux en mémoire.

Il faut se souvenir du cours précédent :
Le CPU ne travaille pas directement sur le SSD.

Le noyau est donc copié du disque vers la RAM.
Puis le processeur commence à exécuter ce noyau.
À partir de ce moment-là, Linux prend réellement le contrôle de la machine.

---

## Étape 9 — systemd

Le noyau Linux est capable de gérer le matériel. Mais il ne lance pas tout seul les services. Il démarre un premier processus utilisateur.

Sur Ubuntu, il s'agit de :
**systemd**
Il possède toujours le PID : **1**

C'est pourquoi, il y a quelques messages, je t'avais demandé d'exécuter :
```bash
ps -p 1
```
on avait vu : systemd

Ce n'était pas un hasard.

--- 

## Étape 10 — Les services

systemd lance progressivement :
* le réseau ;
* le serveur SSH ;
* les journaux ;
* le gestionnaire de connexion ;
* les services Docker (s'ils sont installés) ;
* et bien d'autres.

Chaque service est démarré dans un ordre précis, en respectant ses dépendances.

## Étape 11 — L'écran de connexion

Enfin, le gestionnaire de connexion graphique apparaît.
On saisit un mot de passe, la session est ouverte, le shell Bash est lancé.

Et seulement à ce moment-là, on peut commencer à utiliser l'ordinateur.

---

## Cas réel DevOps

Un serveur redémarre mais reste bloqué avant l'écran de connexion.
Selon l'étape où il s'arrête, le diagnostic sera différent :

* Aucun affichage → alimentation, carte mère ou CPU.
* Erreur pendant le POST → matériel.
* Pas de menu GRUB → problème de bootloader.
* Kernel panic → noyau Linux.
* Bloqué sur systemd → service défaillant.
* Pas de réseau après connexion → service réseau.

On voit déjà que connaître les étapes du démarrage permet de localiser rapidement une panne.

---

## ⚠️ Les erreurs classiques

❌ « Le BIOS est installé sur le disque dur. »
Faux. Il est stocké sur une mémoire de la carte mère.
❌ « GRUB est Linux. »
Faux. GRUB est lancé avant Linux.
❌ « Linux démarre dès que j'appuie sur Power. »
Faux. Plusieurs composants travaillent avant lui.

---

## Ce qu'un DevOps ferait

Un ingénieur ne dit pas simplement :
« Le serveur ne démarre pas. »
Il demande immédiatement :
* Jusqu'où le démarrage va-t-il ?
* Voit-on le firmware ?
* Le POST passe-t-il ?
* GRUB apparaît-il ?
* Le noyau démarre-t-il ?
* systemd lance-t-il les services ?

Chaque réponse réduit énormément le champ des causes possibles.

## 📝 Résumé

Aujourd'hui, tu as appris que le démarrage d'un ordinateur est une succession d'étapes :

* Le bouton Power envoie un signal.
* L'alimentation fournit les bonnes tensions.
* La carte mère initialise les composants.
* Le CPU commence à exécuter le firmware.
* Le BIOS ou l'UEFI effectue le POST.
* Le firmware cherche un périphérique de démarrage.
* GRUB est chargé.
* GRUB charge le noyau Linux en RAM.
* Le noyau lance systemd.
* systemd démarre les services.
* L'écran de connexion apparaît.
