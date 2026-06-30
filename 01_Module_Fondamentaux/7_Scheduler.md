## Le Scheduler : le chef d'orchestre du processeur

"Le CPU est extrêmement rapide, mais c'est le Scheduler qui décide qui a le droit de l'utiliser."

---

## 🎯 Objectifs

À la fin de ce cours tu comprendras :
* Pourquoi Linux a besoin d'un scheduler.
* Comment plusieurs programmes semblent s'exécuter en même temps.
* Ce qu'est un quantum.
* Ce qu'est un context switch.
* Pourquoi un processus peut monopoliser un CPU.
* Pourquoi certains processus sont prioritaires.
* Ce qu'est un cœur CPU.
* Pourquoi un CPU peut afficher 800 % d'utilisation.
* Mise en situation

---

# Mise en situation

Imagine une seule caisse dans un supermarché.
Il y a : 20 clients et une seule caissière

Comment fait-elle ?
Elle traite :

        Client 1
           ↓
        Client 2
           ↓
        Client 3
           ↓
          ...

Très simple.

Maintenant imagine que tu as :

Firefox
Docker
PHP
MariaDB
Spotify
VS Code
Bash
GNOME

Tous veulent utiliser le CPU. Le processeur ne peut pas exécuter tout le monde simultanément (sur un même cœur).
Quelqu'un doit choisir.

---

## Le Scheduler

Le Scheduler est une partie du Kernel. Son métier est simple.
Il répond sans arrêt à cette question :
**Quel processus doit utiliser le processeur maintenant ?**
et cela des millions de fois par seconde.

---

## Une analogie

Imagine un chef de gare. Il possède : 10 trains et une seule voie.

Il décide :

        Train A
          ↓
        Train B
          ↓
        Train C

Le Scheduler fait exactement cela avec les processus.

---

## Le Quantum

Le Scheduler donne un petit morceau de temps CPU.
Par exemple :

Firefox : 2 ms
Puis,
Docker : 2 ms
Puis,
PHP : 2 ms
Puis,
Redis : 2 ms

Et ainsi de suite.
On appelle ce petit morceau de temps : **le quantum**.

---

## Pourquoi seulement quelques millisecondes ?

Parce que si Firefox gardait le processeur pendant : 30 secondes
Plus rien d'autre ne fonctionnerait. 

le curseur de la souris se figerait, Le clavier ne répondrait plus, la musique s'arrêterait.
Le **Scheduler** évite cela.

---

## Le changement de contexte

Souviens-toi du chapitre précédent, avant de passer au processus suivant. Linux sauvegarde :
* les registres
* les variables
* le compteur d'instruction

Puis restaure ceux du prochain processus. C'est le :  **Context Switch**

Schéma :
            Firefox
              ↓
            Sauvegarde
              ↓
             PHP
              ↓
            Sauvegarde
              ↓
            Docker
              ↓
            Sauvegarde
              ↓
            Redis

Très rapidement.
Tu as alors l'impression que tout fonctionne en même temps.

---

## Les cœurs CPU

Question.
Ton processeur possède par exemple :
4 cœurs

Cela signifie que le Scheduler dispose :
* CPU 1
* CPU 2
* CPU 3
* CPU 4

Chaque cœur peut exécuter un processus à un instant donné.
Exemple :

CPU 1 : Firefox
CPU 2 : PHP
CPU 3 : Docker
CPU 4 : MariaDB

Cette fois, ils travaillent réellement en parallèle.

---

## Hyper-Threading

Tu as peut-être remarqué avec :
```bash
lscpu
```
Quelque chose comme :
* Core(s) per socket : 4
* CPU(s) : 8

Pourquoi ?
Parce que certains processeurs présentent **deux processeurs logiques par cœur physique**.
Cela permet d'utiliser plus efficacement les ressources du processeur, même si ce n'est pas équivalent à avoir deux cœurs physiques. Nous y reviendrons lorsque nous parlerons des performances.

---

## Priorité des processus

Tous les processus n'ont pas la même importance. Exemple :

Tu déplaces la souris : Le Scheduler doit réagir très vite.
En revanche :
Une sauvegarde nocturne peut attendre quelques millisecondes.

Linux attribue donc des priorités.

---

## Nice

Tu entendras souvent parler de :  **nice** ou **renice**.
Ces outils permettent d'influencer la priorité d'un processus.
Nous les utiliserons dans le module Linux.

---

## Pourquoi un CPU peut afficher 400 % ?

Sous Linux, quand tu vois : **CPU -> 400 %**

Ce n'est pas une erreur, imaginons :
4 cœurs.
Chaque cœur : **100 %**.
Donc : 100 % + 100 % + 100 % + 100 % = 400 %

Sur une machine de 8 cœurs :
800 % est parfaitement normal.

---

## Cas réel DevOps 💼

Imagine un serveur : 16 cœurs.

Une application PHP utilise : 1600 %
Cela signifie qu'elle utilise tous les cœurs disponibles.
La question n'est plus **" Pourquoi le CPU est élevé ? "** mais **" Pourquoi cette application utilise-t-elle autant de cœurs ? "**

Tu vois comme le raisonnement change ?

---

## Pourquoi Linux paraît-il fluide ?

Parce que le Scheduler change de processus extrêmement rapidement, on ne voit jamais ces changements car ils sont trop rapides.

---

## Le Scheduler moderne

Linux utilise aujourd'hui un ordonnanceur appelé : **CFS (Completely Fair Scheduler)**

Son objectif : **Être le plus juste possible**.

Il essaie de donner à chaque processus une part équitable du processeur, tout en tenant compte de leurs priorités.
Nous n'entrerons pas encore dans ses algorithmes, mais retiens son nom : il reviendra plus tard.

---

## ⚠️ Les erreurs classiques

❌ « Mon processeur exécute toutes les applications en même temps. »
Pas exactement. Sur un cœur, il alterne très rapidement entre elles.

❌ « 100 % CPU signifie que tout le serveur est bloqué. »
Pas forcément. Cela peut concerner un seul cœur ou un seul processus.

❌ « Plus de cœurs résout tous les problèmes. »
Non. Certaines applications ne savent pas utiliser plusieurs cœurs efficacement.

---

## ⭐ Ce qu'un DevOps ferait

Devant un serveur lent, un ingénieur ne se contente pas de regarder le pourcentage CPU.
Il se pose des questions :

* Combien de cœurs possède la machine ?
* Quels processus sont gourmands ?
* Les processus attendent-ils le disque ?
* Le scheduler passe-t-il trop de temps à faire des changements de contexte ?
* Y a-t-il des processus bloqués ?

Les outils ne sont qu'une aide. Le diagnostic commence par les bonnes questions.

---

## 📝 Résumé

Aujourd'hui, tu as appris que :

* Le Scheduler décide quel processus utilise le CPU.
* Il distribue le temps processeur par petits quanta.
* Il effectue des changements de contexte.
* Les processeurs modernes possèdent plusieurs cœurs.
* Les priorités influencent l'ordre d'exécution.
* Le pourcentage CPU dépend du nombre de cœurs disponibles.