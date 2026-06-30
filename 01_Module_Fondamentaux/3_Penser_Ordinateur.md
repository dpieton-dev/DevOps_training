# Comment pense un ordinateur ?

## 🎯 Objectifs

Pourquoi un ordinateur ne comprend que deux états.
Ce qu'est un bit.
Ce qu'est un octet.
Pourquoi on parle de 32 bits et de 64 bits.
Comment un processeur "lit" une instruction.
Pourquoi un ordinateur est incapable de réfléchir.
Une question

---
## Imaginer

Je vous donne un ordinateur neuf, sans système et sans programme.

Je lui demande :
Fais-moi un café.
Que va-t-il faire ?
👉 Rien.

## Pourquoi ?

Parce qu'il ne sait pas ce qu'est un café.

Il ne sait même pas ce qu'est un mot. Il ne comprend absolument rien.

Le plus grand mensonge de l'informatique

On entend souvent :
* Les ordinateurs sont intelligents.
C'est faux, ils sont rapides, très rapides mais ils sont incapables de réfléchir. Un processeur ne fait qu'une seule chose.
Il exécute des instructions.

## Pourquoi seulement deux états ?
Imaginons une ampoule.

Elle peut être :
Éteinte ou Allumée
Il n'y a pas d'autre possibilité.
Les transistors fonctionnent presque de cette manière.
Ils sont :
OFF ou ON

En informatique, on représente cela par :
0 et 1
C'est tout.
Toute l'informatique repose sur cela.

## Le Bit

Le mot Bit vient de :
**Binary Digit**

Un bit est la plus petite information qu'un ordinateur puisse manipuler.
Il ne peut prendre que deux valeurs :

0 ou 1

## Huit bits

Que se passe-t-il si on regroupe plusieurs bits ?

Exemple : 01001010
Ici : nous avons 8 bits

Et huit bits forment : 1 octet (en anglais : Byte)

Pourquoi huit ?
Bonne question, ce n'est pas une loi de la nature. C'est un choix historique devenu un standard.

Un octet permet de représenter : 256 valeurs

Pourquoi ?
Parce que : 2⁸ = 256

Exercice mental

Imagine quatre interrupteurs.
Chaque interrupteur possède deux états.
Combien existe-t-il de combinaisons ?
Réponse : 2⁴ = 16

Avec huit interrupteurs : 2⁸ = 256
Avec seize : 65536

Tu vois déjà pourquoi les ordinateurs deviennent très puissants lorsqu'on augmente le nombre de bits.

Une analogie

Imagine une boîte aux lettres.
Un bit :
Une seule case. □
Un octet :
Huit cases. □□□□□□□□
Chaque case peut contenir : 0 ou 1

Le nombre total de combinaisons devient énorme.

Pourquoi parle-t-on de 64 bits ?
Aujourd'hui, ton Ubuntu est :
x86_64

Tu l'as vu avec :
```bash
lscpu
```
ou
```bash
uname -m
```
Mais pourquoi 64 ?

Imagine une adresse

Supposons que tu habites dans une ville.

Si les numéros de maison vont seulement jusqu'à :

255

Tu ne peux pas avoir plus de 256 maisons.
Le processeur fonctionne pareil.

Plus il possède de bits pour adresser la mémoire, plus il peut gérer de mémoire.
32 bits

Un processeur 32 bits peut adresser environ :
4 Go de RAM

C'était largement suffisant dans les années 1990.
Aujourd'hui ?
Un simple navigateur peut consommer plusieurs gigaoctets.

## 64 bits
Un processeur 64 bits peut adresser une quantité gigantesque de mémoire (bien supérieure aux besoins actuels des PC).

C'est pour cela que les systèmes modernes utilisent presque exclusivement cette architecture.

Comment le CPU travaille ?

Le processeur répète toujours le même cycle.
Encore et encore.
Des milliards de fois par seconde.

        Lire une instruction
                │
                ▼
          La comprendre
                │
                ▼
          L'exécuter
                │
                ▼
          Lire la suivante

On appelle cela le cycle :

Fetch
Decode
Execute

Exemple

Imaginons le programme :
1 + 2
En réalité le CPU ne voit jamais :
1 + 2

Il voit quelque chose ressemblant à :
10100110
00110111
11000001

Chaque suite de bits représente une instruction.

## Pourquoi Linux existe-t-il ?

Imagine devoir écrire toi-même ces suites de 0 et de 1.

Tu deviendrais fou.
Linux, les compilateurs et les langages de programmation traduisent des instructions compréhensibles par l'humain en instructions compréhensibles par le processeur.
Par exemple, quand tu écris en PHP :
```php
$a = 1 + 2;
```
Il y a plusieurs étapes avant que le CPU exécute réellement une addition.
Nous verrons cette chaîne plus tard, mais retiens déjà qu'il existe de nombreuses couches entre ton code et le matériel.

## Cas réel DevOps 💼

Tu surveilles un serveur et tu vois :

CPU : 100 %

Cela ne signifie pas que le processeur "réfléchit".
Cela signifie qu'il passe tout son temps à exécuter des instructions.

La question devient alors :

Quelles instructions ?
Quel processus les demande ?
Pourquoi ?

C'est exactement ce que nous apprendrons avec des outils comme top, htop ou ps dans le module Linux.

## ⚠️ Les erreurs classiques

❌ « Plus de GHz = forcément un meilleur processeur. »
Faux. L'architecture, le nombre de cœurs, la mémoire cache et d'autres éléments comptent énormément.

❌ « Les ordinateurs comprennent le français ou l'anglais. »
Faux. Ils ne comprennent que des instructions codées.

❌ « 64 bits signifie que le processeur est deux fois plus rapide. »
Faux. Cela concerne principalement la taille des registres et l'adressage mémoire.

## Ce qu'un DevOps ferait

Un ingénieur ne regarde jamais uniquement le pourcentage de CPU.
Il se demande aussi :

Est-ce un ou plusieurs cœurs saturés ?
Est-ce du calcul ou de l'attente d'entrées/sorties ?
Le CPU attend-il le disque ?
Attend-il le réseau ?
Est-ce un problème d'application ou de système ?

Un simple "100 %" ne suffit jamais pour diagnostiquer un problème.

## 📝 Résumé
Aujourd'hui, tu as appris que :

Le processeur ne comprend que deux états : 0 et 1.
Un bit est la plus petite unité d'information.
Huit bits forment un octet.
L'architecture 64 bits permet d'adresser énormément de mémoire.
Le CPU exécute un cycle permanent : Fetch → Decode → Execute.
Un processeur n'est pas intelligent : il exécute des instructions.
