# Qu'est-ce qu'un ordinateur ?

## Objectifs
À la fin de ce chapitre, tu seras capable de répondre à des questions comme :

* Qu'est-ce qu'un ordinateur ?
* Pourquoi un processeur est-il indispensable ?
* Pourquoi la RAM est-elle différente du SSD ?
* Pourquoi un ordinateur ne démarre pas directement Linux ?
* Que fait le BIOS/UEFI ?
* Pourquoi un système d'exploitation existe-t-il ?

Et surtout, On comprendra enfin ce qui se passe réellement lorsque l'on appuie sur le bouton Power.

----
## Définition :
Un ordinateur est :
**Une machine électronique programmable capable de recevoir des données, de les traiter selon un programme et de produire un résultat.**

----
## Une analogie :
Imagine un restaurant.
On va comparer un ordinateur à un restaurant.

| Restaurant      || Ordinateur             |
| --------------- || ---------------------- |
| Client          || Utilisateur            |
| Recette         || Programme              |
| Cuisinier       || CPU                    |
| Plan de travail || RAM                    |
| Réserve         || Disque SSD             |
| Chef de cuisine || Système d'exploitation |
| Serveur         || Interface utilisateur  |

----
## Les quatre composants essentiels
Tous les ordinateurs possèdent ces quatre éléments.

                +----------------+
                |      CPU       |
                +----------------+
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
      RAM          Stockage      Périphériques

## 1️⃣ Le CPU
Le CPU signifie :
**Central Processing Unit**
En français :
**Unité Centrale de Traitement**

C'est le cerveau mais attention il exécute simplement.

## 2️⃣ La RAM
Pourquoi avons-nous besoin de RAM alors que nous avons déjà un SSD ?
Car le **CPU** travaille directement avec la **RAM** et pas avec le SSD.
Si tu éteins l'ordinateur, la RAM se vide mais le SSD garde les données.

## 3️⃣ Le stockage

Le stockage est la mémoire permanente.
Chez toi :

Probablement un SSD, Il contient :
* Ubuntu
* Tes photos
* Tes projets PHP
* Tes vidéos
* Tes documents

Même ordinateur éteint.

## 4️⃣ Les périphériques

Tout ce qui permet de communiquer avec l'ordinateur.

Exemples:

Clavier, Souris, Écran, Carte réseau, Clé USB, Webcam, Microphone, Imprimante...

----

## Schéma
               Utilisateur
                   │
                   ▼
              Clavier / Souris
                   │
                   ▼
                  CPU
                   │
          ┌────────┴────────┐
          │                 │
          ▼                 ▼
         RAM             Carte Réseau
          │
          ▼
         SSD

----

## Cas Réel DevOps
Imagine un serveur de production.

Il possède :
* 64 Go de RAM
* 8 To de SSD
* 16 cœurs CPU

Un développeur dit :
"L'application est lente."

La première chose que l'on fera n'est pas de redémarrer le serveur.

On se demandera :
* Le CPU est-il saturé ?
* La RAM est-elle pleine ?
* Le disque est-il lent ?
* Le réseau est-il saturé ?

Là, on voit déjà le lien entre l'informatique fondamentale et le métier de DevOps.

----

## ⚠️ Les erreurs classiques

❌ "Plus de SSD rendra mon application plus rapide."
Pas forcément, si le problème est le CPU, changer le SSD ne changera rien.

❌ "La RAM sert à stocker les fichiers."
Non, elle sert à stocker les données temporairement, pendant leur traitement.

❌ "Le CPU décide quoi faire."
Non, il exécute des instructions.

La logique vient du programme.

⭐ Ce qu'un DevOps ferait

Face à une application lente, un ingénieur ne commence pas par modifier le code.

Il cherche d'abord à mesurer :
* l'utilisation CPU ;
* la mémoire ;
* les entrées/sorties disque ;
* le réseau.

On ne corrige jamais un problème que l'on n'a pas identifié.
C'est un principe que tu retrouveras tout au long de ce cours.

----
## 📝 Résumé

* Un ordinateur est une machine programmable.
* Le CPU exécute les instructions.
* La RAM sert d'espace de travail rapide.
* Le SSD stocke les données de manière permanente.
* Les périphériques permettent les échanges avec l'extérieur.
* Les données passent toujours par la RAM avant d'être traitées par le CPU.
