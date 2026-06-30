# Les processus : les êtres vivants du système

"Un ordinateur ne fait jamais plusieurs choses à la fois. Il donne simplement l'illusion de le faire."

## 🎯 Objectifs

À la fin de ce chapitre, tu sauras répondre à ces questions :

* Qu'est-ce qu'un processus ?
* Quelle est la différence entre un programme et un processus ?
* Qu'est-ce qu'un PID ?
* Comment Linux exécute plusieurs applications en même temps ?
* Pourquoi un processus peut-il planter sans faire tomber tout le système ?
* Pourquoi Docker n'est finalement qu'un ensemble de processus ?


## Avant de commencer...

Je vais te poser une question. Tu regardes actuellement :

* Firefox (ou Chrome)
* ChatGPT
* VS Code
* GNOME
* Docker
* Le Wi-Fi
* L'horloge
* Le son

Tu pourrais penser que ton processeur fait tout cela en même temps.
Eh bien, non.

**Le plus grand tour de magie de Linux**

Le processeur ne fait qu'une seule instruction à la fois (par cœur d'exécution).
Alors comment peut-il donner l'impression que tout fonctionne simultanément ?

👉 Grâce au **partage du temps** (time sharing).

---

## Une analogie

Imagine un professeur qui doit répondre à 30 élèves.

Il ne répond pas aux 30 en même temps ce qu'il fait :

* Élève 1 → 2 secondes
* Élève 2 → 2 secondes
* Élève 3 → 2 secondes
...
* Élève 30 → 2 secondes

Comme il change très vite d'élève...
Tout le monde a l'impression qu'il s'occupe de chacun en permanence.
Linux fait exactement cela.

---

## Qu'est-ce qu'un programme ?

Un programme est un fichier.
Par exemple :
```bash
/usr/bin/firefox
/usr/bin/php
/usr/bin/bash
```

Un programme ne fait rien, il est simplement stocké sur le disque. Comme un livre dans une bibliothèque.

---

## Qu'est-ce qu'un processus ?

Un processus est :

Un programme en cours d'exécution, voilà la différence fondamentale :

Le fichier :

      /usr/bin/firefox
            ↓
      doubles-cliques dessus.
            ↓
      Linux crée : Processus Firefox

Le fichier n'a pas changé, ce qui change, c'est qu'il est maintenant chargé en mémoire et exécuté par le processeur.

Une image mentale

Imagine un livre de cuisine.

      Le livre :
          ↓
      Programme.

      Le cuisinier qui suit la recette :
                  ↓
              Processus.

Le livre ne cuisine pas, le cuisinier oui.

---

## Chaque processus possède sa propre identité

Linux attribue un numéro unique : Le **PID**.

PID signifie :  **Process ID**
Exemple :

Firefox : PID 4512
PHP :     PID 7211
Docker:   PID 1350

Chaque processus possède son propre numéro comme une carte d'identité.

---

## Pourquoi un PID ?

Imagine qu'il y ait : 300 processus.

Comment dire au noyau de tuer Firefox. Il faut pouvoir l'identifier.
Le **PID** sert précisément à cela.

---

## Le premier processus

Souviens-toi du chapitre précédent, le premier processus lancé par le noyau est :
```bash
systemd
```
Son PID est toujours : 1

C'est un nombre spécial et tous les autres processus descendent de lui, directement ou indirectement.

---

## Les processus forment une famille

Linux fonctionne comme un arbre généalogique.
```bash
systemd (PID 1)
│
├── NetworkManager
│
├── sshd
│
├── Docker
│      │
│      ├── Container 1
│      └── Container 2
│
└── gdm
      │
      └── bash
            │
            └── vim
```
Chaque processus est créé par un autre. On parle de **processus parent** et **processus enfant**.

---

## Les états d'un processus

Un processus ne fait pas toujours la même chose. Il peut être :

* Running  -> le processeur exécute ses instructions
* Sleeping -> il attend quelque chose

Par exemple :
* une réponse réseau
* un fichier
* une saisie clavier

Stopped -> il est suspendu.
Zombie  -> il est terminé, mais son parent n'a pas encore récupéré son état.

nous reviendrons sur les zombies dans le module Linux.

---

## Le changement de contexte (Context Switch)

Voici l'un des concepts les plus importants.

Le processeur exécute :
      Firefox
Puis :
      VS Code
Puis :
      Docker
Puis :
      PHP

Très rapidement à chaque changement, Linux sauvegarde l'état du processus courant et restaure celui du suivant. C'est ce qu'on appelle un **changement de contexte**.
C'est grâce à cela que plusieurs applications semblent fonctionner simultanément.

---

## Pourquoi un processus plante-t-il seul ?

Imaginons :

Firefox contient un bug. Il tente d'accéder à une zone mémoire interdite.
Le noyau dit : **Non**.

Le processus est arrêté et les autres continuent.
C'est exactement ce qui évite qu'une seule application fasse tomber tout le système.

---

## Docker est-il un processus ?

Réponse : **Oui... et non**.

Le démon Docker est un processus. Les conteneurs, eux, exécutent également des processus.
En réalité, un conteneur n'est pas une machine virtuelle. C'est un ou plusieurs processus isolés par le noyau Linux.
Quand nous arriverons au module Docker, cette idée sera beaucoup plus facile à comprendre.

---

## Cas réel DevOps 💼

Un site web est lent.
Tu exécutes : 
```bash
top
```

Tu observes qu'un processus PHP-FPM utilise 100 % d'un cœur.
Tu sais désormais que ce n'est pas "le serveur" qui est lent, mais un processus précis.
Le diagnostic devient beaucoup plus ciblé.

---

## ⚠️ Les erreurs classiques

❌ « Un programme et un processus, c'est la même chose. »
Non. Un programme est un fichier. Un processus est une exécution.

❌ « Un processus est forcément visible à l'écran. »
Non. La majorité des processus fonctionnent en arrière-plan.

❌ « Tous les processus utilisent le CPU en permanence. »
Non. Beaucoup passent leur temps à attendre une ressource.

---

## ⭐ Ce qu'un DevOps ferait

Quand un serveur est lent, il ne redémarre pas immédiatement.
Il cherche d'abord :
* Quel processus consomme le CPU ?
* Lequel consomme la mémoire ?
* Lequel attend le disque ?
* Lequel attend le réseau ?

Les outils viennent ensuite **(ps, top, htop, etc.)**. Ce qui compte d'abord, c'est la manière de raisonner.

---

## 📝 Résumé

Aujourd'hui, tu as appris que :
* Un programme est un fichier.
* Un processus est un programme en cours d'exécution.
* Chaque processus possède un PID.
* Les processus sont organisés en arbre.
* Linux partage le temps du processeur entre les processus.
* Le changement de contexte permet l'exécution de nombreuses applications sur un même processeur.