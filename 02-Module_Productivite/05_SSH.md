## SSH : Administrer un serveur à distance

"SSH est au DevOps ce que le volant est au conducteur."

## 🎯 Objectifs

À la fin de ce chapitre, tu comprendras :

Ce qu'est SSH.
Pourquoi SSH est sécurisé.
Comment fonctionne une connexion SSH.
La différence entre authentification par mot de passe et par clé.
Ce qu'est une paire de clés SSH.
Le rôle de known_hosts.
Le rôle de authorized_keys.
Les bonnes pratiques de sécurité.

## 📖 Avant de commencer

Imagine.

Tu travailles chez OVH.

Un serveur est situé dans un datacenter à : Paris.

Toi, tu es chez toi.

Comment faire ?

Tu ne peux pas brancher :

un clavier
une souris
un écran

Tu dois contrôler le serveur...

à distance.

---

## Avant SSH

Dans les années 80...

On utilisait : **Telnet**

Le problème ?

Le mot de passe circulait : en clair.

N'importe qui pouvait le lire.

C'était catastrophique.

## La naissance de SSH

SSH signifie : **Secure SHell**

Il remplace Telnet.

Son objectif :

Créer un tunnel sécurisé entre deux machines.

---

## Une analogie

Imagine une lettre.

Sans enveloppe.

Tout le monde peut la lire.

SSH ajoute une enveloppe blindée.

Même si quelqu'un intercepte le courrier...

Il ne peut pas le comprendre.

## Le principe

Tu exécutes : ssh utilisateur@serveur

Exemple : ssh dominique@192.168.1.50

Le client SSH contacte le serveur.

Ce qui se passe :
```
Ton PC
↓
SSH Client
↓
Internet
↓
SSH Server
↓
Bash
↓
Kernel
```

Tu obtiens un shell distant.

Comme si tu étais devant la machine.

SSH est-il un terminal ?

Non.

SSH transporte simplement :

ton clavier ;
ton écran ;
les données.

Le shell s'exécute sur le serveur.

Pas chez toi.

Authentification par mot de passe

Au début.

Tu saisis :

Mot de passe

Le serveur vérifie.

Puis ouvre la session.

Simple.

Mais pas idéal.

**Pourquoi ?**

Parce que :

on peut deviner un mot de passe ;
on peut le voler ;
on peut le réutiliser.
La solution

Les clés SSH.

**Les clés SSH**

Au lieu d'un mot de passe.

Tu possèdes :

Clé privée + Clé publique

Elles sont générées ensemble.

**Une analogie**

Imagine un cadenas.

La clé publique : Le cadenas.

Tu peux le donner à tout le monde.

La clé privée : La clé.

Tu ne la donnes jamais.

Génération

On utilise : ssh-keygen

Tu obtiens : id_ed25519

id_ed25519.pub

**La clé privée**

Exemple : ~/.ssh/id_ed25519

⚠️ Elle doit rester secrète.

Jamais :

GitHub
GitLab
Dropbox
Email
La clé publique

Exemple : ~/.ssh/id_ed25519.pub

Tu peux la copier sur les serveurs.

Elle ne permet pas de se connecter seule.

Le premier échange

Lors de la première connexion.

SSH demande :

Are you sure you want to continue connecting?

Pourquoi ?

Parce que tu ne connais pas encore ce serveur.

known_hosts

SSH enregistre ensuite :

~/.ssh/known_hosts

Il contient l'identité des serveurs déjà connus.

Pourquoi ?

Pour éviter une attaque.

Imagine.

Quelqu'un se fait passer pour ton serveur.

SSH détecte :

Ce n'est plus le même serveur.

Il affiche une alerte.

authorized_keys

Sur le serveur.

Chaque utilisateur possède :

~/.ssh/authorized_keys

Ce fichier contient :

Les clés publiques autorisées.

Si ta clé est présente.

Tu peux entrer.

Schéma

Ton PC

id_ed25519 (clé privée)
↓
SSH
↓
Serveur

authorized_keys (clé publique)

Les deux doivent correspondre.

**Le SSH Agent**

Question.

Dois-tu saisir la phrase secrète de ta clé à chaque connexion ?

Non.

Le SSH Agent peut conserver temporairement les clés déverrouillées en mémoire.

Nous le verrons plus loin.

**Les ports**

Par défaut.

SSH écoute sur : 22

Tu peux le vérifier sur un serveur : ss -tln

---

## Cas réel DevOps 💼

Imagine.

Tu dois administrer : 250 serveurs.

Tu ne peux évidemment pas taper 250 mots de passe.

Grâce aux clés SSH : Tu te connectes immédiatement.

C'est indispensable pour l'automatisation avec Ansible, Terraform ou les pipelines CI/CD.

## ⚠️ Les erreurs classiques

❌ Envoyer sa clé privée par mail.

❌ Donner les droits 777 au dossier .ssh.

❌ Désactiver toutes les protections du serveur SSH.

❌ Utiliser root directement en SSH sans nécessité.

## ⭐ Ce qu'un DevOps ferait

Un ingénieur expérimenté :

* utilise une clé ED25519 ;
* protège sa clé privée avec une passphrase ;
* désactive l'authentification par mot de passe sur les serveurs sensibles ;
* utilise sudo plutôt que de se connecter directement en root ;
* surveille les journaux SSH.

## 📝 Résumé

Aujourd'hui, tu as appris que :

* SSH permet d'administrer un serveur à distance.
* Il chiffre toutes les communications.
* Une paire de clés remplace avantageusement un mot de passe.
* known_hosts mémorise les serveurs connus.
* authorized_keys définit les clés autorisées.