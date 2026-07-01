# Le voyage d'une commande

Comment une simple commande traverse tout l'ordinateur
---

## 🎯 Objectifs

À la fin de ce chapitre tu seras capable de suivre mentalement une commande depuis :
* ton clavier
* jusqu'au processeur
* puis au disque
* puis au noyau
* puis au terminal

Et surtout, tu comprendras enfin pourquoi Linux fonctionne comme il fonctionne.

---

## Mise en situation

Tu ouvres un terminal et tu écris :
```bash
ls
```
Puis tu appuies sur **Entrée**.

Que se passe-t-il ?

La plupart des gens répondent : Linux affiche les fichiers.
C'est vrai. Mais il manque environ... **150 étapes**. 😄

Aujourd'hui, nous allons toutes les résumer.

---

## Étape 1 — Le clavier

Tu appuies sur : L

Le clavier ne connaît pas la lettre L, Il ferme simplement un circuit électrique.
Une petite puce détecte cette fermeture, Elle génère un scan code (code matériel de la touche) et envoie ce code à l'ordinateur.

---

## Étape 2 — Le contrôleur USB

Le signal arrive sur :
```
Carte mère
    │
    ▼
Contrôleur USB
```
Le contrôleur transmet les données au processeur.

---

## Étape 3 — Une interruption

Le CPU ne regarde pas le clavier en permanence. Le clavier lui envoie une **interruption matérielle (IRQ)**.

Le CPU dit : « Quelqu'un demande mon attention. »

Il interrompt brièvement ce qu'il faisait.

**Petite parenthèse : les interruptions**

Imagine que tu lis un livre, Le téléphone sonne. 
Tu décroches -> Tu réponds -> Tu reprends ta lecture.

C'est exactement une interruption.
Sans interruptions, le CPU devrait vérifier des millions de fois par seconde si une touche a été pressée. Ce serait extrêmement inefficace.

---

## Étape 4 — Le noyau

Le noyau reçoit le scan code, Il consulte la disposition du clavier ou AZERTY selon le cas.

Il traduit :
```
Scan code
   ↓
   l
```
Puis transmet cette information au terminal.

---

## Étape 5 — Le terminal

Le terminal affiche : l

Mais Il ne lance rien. Il attend.

Tu tapes ensuite : s

Puis : Entrée.

---

## Étape 6 — Bash

Le terminal transmet la ligne complète :
```bash
ls
```
au shell Bash.

Bash est un processus. Son travail est d'interpréter ce que tu écris.

Première question de Bash
Bash se demande : Est-ce une commande interne ?
Comme :
* cd
* echo
* exit

Ici : ls

Non.

---

## Étape 7 — Recherche de la commande

Bash consulte une variable très importante :
```bash
echo $PATH
```
Chez vous, elle ressemble probablement à :
```
/usr/local/bin
/usr/bin
/bin
...
```

Bash cherche :
```
/usr/local/bin/ls
  Pas trouvé.
      ↓
 /usr/bin/ls
      ↓
   Trouvé.
```

---

## Étape 8 — Création du processus

Le noyau est sollicité, Bash dit : **« Peux-tu lancer /usr/bin/ls ? »**

Le noyau :

*crée un nouveau processus ;
*lui attribue un PID
*réserve de la mémoire
*charge l'exécutable en RAM

---

## Étape 9 — Le Scheduler

Le nouveau processus est prêt, mais il ne s'exécute pas immédiatement.

Le Scheduler décide :

Maintenant c'est au tour de ls.

---

## Étape 10 — Le processeur

Le CPU commence à exécuter les instructions du programme ls, il ne comprend pas :
```bash
ls
```

Il exécute des instructions machine.

---

## Étape 11 — Les appels système

ls veut connaître le contenu du répertoire, il ne lit pas directement le disque.

Il demande au noyau :

Peux-tu me donner la liste des fichiers ?

C'est un appel système.

Le noyau vérifie :

* les permissions
* le système de fichiers
* les inodes

Puis il lit les informations.

---

Étape 12 — Le disque

Si les données ne sont pas déjà en cache :

Le noyau lit le SSD.

Les informations remontent :

SSD

↓

RAM

↓

Kernel

↓

ls
Étape 13 — La sortie

ls reçoit les données.

Il prépare une sortie :

Documents

Images

devopslab

Téléchargements

Mais il ne les affiche pas.

Il écrit simplement dans la sortie standard (stdout).

Étape 14 — Le terminal

Le terminal reçoit cette sortie.

Il dessine les caractères.

Le GPU (ou la partie graphique du processeur) transforme ces caractères en pixels.

Ton écran les affiche.

Tu vois enfin :

Documents
Images
devopslab
Téléchargements
Le schéma complet

Voici le voyage de ta commande :

Tes doigts
     │
     ▼
Clavier
     │
     ▼
Contrôleur USB
     │
     ▼
Interruption (IRQ)
     │
     ▼
Kernel
     │
     ▼
Terminal
     │
     ▼
Bash
     │
     ▼
Recherche dans $PATH
     │
     ▼
Création du processus
     │
     ▼
Scheduler
     │
     ▼
CPU
     │
     ▼
Appels système
     │
     ▼
Kernel
     │
     ▼
SSD / RAM
     │
     ▼
stdout
     │
     ▼
Terminal
     │
     ▼
Écran
🎯 Ce schéma est le cœur de toute la formation

Regarde bien.

Nous venons d'utiliser presque tout ce que nous avons appris :

✅ CPU

✅ RAM

✅ Kernel

✅ Processus

✅ Scheduler

✅ Fichiers

✅ Système de fichiers

✅ Appels système

Tout est relié.

Cas réel DevOps 💼

Imagine maintenant que la commande :

ls

met 10 secondes à répondre.

Tu sais désormais où chercher :

Le clavier ? (peu probable)
Le shell ?
Le Scheduler ?
Le CPU ?
Le SSD ?
Le système de fichiers ?
Les permissions ?
Un montage réseau lent ?

Un ingénieur DevOps ne cherche pas une "commande magique". Il décompose le problème en étapes.

⚠️ Les erreurs classiques

❌ « ls affiche les fichiers directement. »

Non. Il demande au noyau.

❌ « Bash exécute les commandes lui-même. »

Non. Il demande au noyau de créer un processus.

❌ « Le disque envoie les données au CPU. »

Non. Les données passent d'abord par la RAM.

⭐ Ce qu'un Senior ferait

Quand une commande est lente, il ne se demande pas seulement "quelle commande utiliser ?".

Il se demande :

Où est le ralentissement ?
CPU ?
RAM ?
Cache ?
Disque ?
Réseau ?
Système de fichiers ?
Noyau ?
Processus bloqué ?

👉 Le diagnostic est un raisonnement, pas une suite de commandes.
