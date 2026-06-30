# Les fichiers : pourquoi Linux dit que "tout est un fichier" ?

"Sous Linux, presque tout est représenté comme un fichier."

---

## 🎯 Objectifs

À la fin de ce chapitre, tu comprendras :

* Ce qu'est réellement un fichier.
* Pourquoi un disque est un fichier.
* Pourquoi un clavier est un fichier.
* Pourquoi un terminal est un fichier.
* Ce qu'est un système de fichiers.
* Ce qu'est un inode.
* Pourquoi cette philosophie est l'une des plus grandes forces de Linux.

---

## Avant de commencer

Je vais te poser une question.
Sur ton ordinateur, un fichier est :
* un PDF ?
* une image ?
* une vidéo ?
* un document Word ?

👉 La réponse est **non**. Ce sont des exemples de fichiers.
Mais ce n'est pas la définition.

---

## Qu'est-ce qu'un fichier ?

La définition informatique est beaucoup plus simple :

**"Un fichier est une suite d'octets (bytes) stockée sur un support de stockage".**

Et c'est tout, prenons un exemple.

Le fichier : bonjour.txt
contient : Bonjour Dominique

Pour toi, c'est du texte mais pour Linux, c'est une suite d'octets.

Par exemple (en simplifiant) :
**42 6f 6e 6a 6f 75 72 ...**

Le système d'exploitation ne "voit" pas du texte. Il voit des données.

---

## Alors pourquoi un PDF est différent ?

Parce que le programme qui l'ouvre sait interpréter ces octets.

Exemple :

Firefox ouvre du HTML.
LibreOffice ouvre du DOCX.
VLC ouvre des vidéos.
Linux, lui, stocke simplement des données.

---

## La philosophie Unix

Les créateurs d'Unix avaient une idée brillante : **Tout peut être manipulé comme un fichier**.
Cette idée paraît étrange au début mais elle est incroyablement puissante.

#### Exemple 1 : le disque

Sous Linux : /dev/sda -> représente un disque.
Tu peux faire :
```bash
ls -l /dev/sda
```

Pourquoi est-ce un fichier ?
Parce que le noyau fournit une interface unique.

#### Exemple 2 : le clavier

Le clavier est également représenté comme un fichier.

Quand tu appuies sur une touche : A
Le noyau transmet cette information comme un flux de données. Les applications lisent ce flux.

#### Exemple 3 : le terminal

Le terminal est aussi un fichier.

Quand tu fais : echo Bonjour

Le noyau écrit ces caractères dans le "fichier" représentant ton terminal. Le terminal les affiche.

#### Exemple 4 : les processus

Même les processus ont une représentation dans le système de fichiers.

Regarde :
/proc

Ce dossier n'est pas un vrai dossier sur ton disque. Il est créé à la volée par le noyau.

Par exemple :
/proc/1 représente : systemd

Chaque processus possède son propre dossier.

---

## Une analogie

Imagine une mairie, chaque citoyen possède un dossier.

Linux fait pareil, chaque processus possède un dossier dans : **/proc**

---

## Le système de fichiers

Question.

Comment Linux retrouve-t-il un fichier parmi des millions ?

Grâce au système de fichiers.
Quelques exemples :

* ext4
* XFS
* Btrfs
* FAT32
* NTFS

Le système de fichiers organise les données sur le disque.

---

## Une bibliothèque

Imagine une immense bibliothèque.

Si les livres étaient posés au hasard...
Impossible de retrouver un ouvrage.

Le système de fichiers est le bibliothécaire.
Il sait où se trouve chaque "livre".

---

## L'inode

Voici un mot très important : **inode**
Quand tu crées un fichier :
```bash
touch rapport.txt
```

Linux crée en réalité deux choses :
* les données
* une fiche d'identité

Cette fiche s'appelle un **inode**. Elle contient notamment :
* le propriétaire 
* les permissions
* la taille
* les dates
* l'emplacement des données sur le disque

👉 Le nom du fichier n'est pas stocké dans l'inode. Nous verrons pourquoi dans le module Linux lorsque nous parlerons des liens physiques (hard links).

---

## Pourquoi est-ce génial ?

Imagine : photo.jpg
Tu peux renommer : vacances.jpg
Les données ne bougent pas car l'inode reste le même. Seule l'entrée dans le répertoire change.

---

## Cas réel DevOps 💼

Un administrateur reçoit une alerte : No space left on device
Pourtant :
```bash
df -h
```
montre encore de l'espace.

Que se passe-t-il ?
👉 Il est possible que le disque n'ait plus d'inodes disponibles.
Le problème n'est donc pas la place, mais le nombre maximal de fichiers.
C'est un cas réel que nous reproduirons dans le module Linux.

---

## ⚠️ Les erreurs classiques

❌ "Un fichier est forcément un document."
Non. Un fichier peut représenter un périphérique, un processus, un terminal ou une socket.

❌ "Le nom du fichier contient les données."
Non. Le nom est une entrée dans un répertoire. Les données sont décrites par l'inode.

❌ "Supprimer un fichier supprime immédiatement les données."
Pas toujours. Nous verrons que les données peuvent rester présentes tant qu'aucun autre fichier ne réutilise les blocs.

---

## ⭐ Ce qu'un DevOps ferait

Quand un problème de disque survient, un ingénieur ne regarde pas uniquement :
```bash
df -h
```
Il pense aussi :

* au nombre d'inodes
* au système de fichiers
* aux points de montage
* aux fichiers supprimés mais encore ouverts par un processus

Ce sont des causes classiques d'incidents en production.

---

## 📝 Résumé

Aujourd'hui, tu as appris que :

* Un fichier est une suite d'octets.
* Linux représente énormément de ressources sous forme de fichiers.
* Les périphériques sont accessibles via /dev.
* Les informations sur les processus sont exposées dans /proc.
* Le système de fichiers organise les données sur le disque.
* Les inodes décrivent les fichiers.