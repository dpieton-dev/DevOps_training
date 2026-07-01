# Comment un ordinateur communique avec un autre ?

"Un ordinateur isolé est une calculatrice. Un ordinateur connecté devient une machine capable de collaborer avec le monde entier."

---

# 🎯 Objectifs

À la fin de ce chapitre tu comprendras :
* Pourquoi le réseau existe.
* Ce qu'est une carte réseau.
* Ce qu'est une adresse IP.
* Ce qu'est une adresse MAC.
* Ce qu'est un paquet.
* Pourquoi on parle de couches réseau.
* Ce qui se passe lorsque tu fais un ping.
* Ce qui se passe lorsque tu ouvres un site web.
* Mise en situation

Imagine que ton ordinateur est seul.

Il possède :

un CPU
de la RAM
un SSD

Il fonctionne parfaitement.

Mais...

Il ne peut parler à personne.

Il ne peut pas :

ouvrir Google ;
télécharger Ubuntu ;
utiliser GitHub ;
envoyer un e-mail ;
communiquer avec un autre serveur.

Il est complètement isolé.

Le problème

Comment faire communiquer deux ordinateurs ?

Prenons deux PC.

PC A

PC B

Question.

Comment PC A peut-il dire :

Bonjour PC B ?

Une analogie

Imagine deux personnes.

Elles veulent communiquer.

Il faut :

une langue ;
une adresse ;
un moyen de transport.

Le réseau fonctionne exactement comme cela.

Les trois éléments indispensables

Pour communiquer il faut :

Un expéditeur

↓

Une adresse

↓

Un moyen de transport
La carte réseau

Chaque ordinateur possède une carte réseau.

Sur ton Ubuntu.

Tu peux déjà la voir.

Tu l'avais observée avec :

ip a

Tu avais :

wlp3s0

Ton interface Wi-Fi.

Et :

enp2s0

Ta carte Ethernet.

La carte réseau est au réseau ce que le clavier est à l'utilisateur.

Elle permet d'envoyer et de recevoir des informations.

Les données

Question.

Peut-on envoyer un fichier de 3 Go d'un seul coup ?

Non.

Ce serait beaucoup trop gros.

Le réseau découpe les données.

En petits morceaux.

Ces morceaux s'appellent :

Paquets

ou

Packets.

Une analogie

Imagine un déménagement.

Tu ne mets pas toute ta maison dans un seul carton.

Tu fais :

Carton 1

Carton 2

Carton 3

Le réseau fait exactement cela.

Que contient un paquet ?

Chaque paquet possède :

Expéditeur

Destinataire

Données

Contrôle

Comme une lettre.

Adresse MAC

Chaque carte réseau possède un numéro unique.

La MAC Address.

Par exemple.

5C:EA:1D:4C:81:17

Tu reconnais quelque chose ?

C'est exactement celle que tu avais vue avec :

ip a

Sur ton Ubuntu.

La MAC est :

L'identité physique de la carte réseau.

Elle ne change presque jamais.

Adresse IP

La MAC identifie la carte.

Mais...

Sur Internet.

On utilise surtout :

L'adresse IP.

Chez toi :

Tu avais :

192.168.1.36

C'est ton adresse dans ton réseau local.

Une analogie

Imagine un immeuble.

La MAC.

↓

La personne.

L'adresse IP.

↓

L'appartement.

Les deux sont nécessaires.

Le switch

Dans un réseau local.

Les ordinateurs sont reliés à un switch.

Le switch connaît les adresses MAC.

Il sait :

Qui est connecté sur quel port.

Le routeur

Pour sortir de ton réseau.

Tu passes par :

Routeur

Chez toi.

C'est ta box Internet.

Elle relie :

Ton réseau

↓

Internet.

Le paquet voyage

Imaginons :

Tu fais :

ping 8.8.8.8

Le paquet suit ce chemin.

Ton PC

↓

Carte réseau

↓

Switch

↓

Routeur

↓

FAI

↓

Internet

↓

Google DNS

↓

Réponse

Et le chemin retour est similaire.

Pourquoi plusieurs couches ?

Question.

Pourquoi le réseau est-il aussi compliqué ?

Pourquoi ne pas envoyer directement des données ?

Parce que plusieurs problèmes doivent être résolus.

Par exemple :

Qui est le destinataire ?

Comment découper les données ?

Comment vérifier qu'elles arrivent ?

Comment les réassembler ?

Comment chiffrer les échanges ?

Chaque problème est traité par une couche différente.

Nous détaillerons les modèles OSI et TCP/IP dans le module Réseau.

Cas réel DevOps 💼

Un développeur te dit :

« Le serveur ne répond plus. »

Avant d'accuser l'application, un ingénieur vérifie :

Le câble est-il branché ?
L'interface réseau est-elle active ?
L'adresse IP est-elle correcte ?
Le routeur répond-il ?
Le DNS fonctionne-t-il ?
Le pare-feu bloque-t-il la communication ?

Le réseau est souvent la première étape du diagnostic.

⚠️ Les erreurs classiques

❌ « L'adresse IP est gravée dans le matériel. »

Non. C'est l'adresse MAC qui est liée à la carte réseau.

❌ « Un fichier est envoyé d'un seul bloc. »

Non. Il est découpé en paquets.

❌ « Internet est un seul réseau. »

Non. C'est un immense réseau de réseaux.

⭐ Ce qu'un Senior ferait

Lorsqu'une communication échoue, un ingénieur raisonne par couches :

Le lien physique fonctionne-t-il ?
L'interface réseau est-elle active ?
Les adresses IP sont-elles correctes ?
Le routage est-il correct ?
Le service distant écoute-t-il ?
L'application répond-elle ?

Il ne saute jamais directement à la conclusion.

📝 Résumé

Aujourd'hui, tu as appris que :

Une carte réseau permet de communiquer.
Les données sont découpées en paquets.
Une adresse MAC identifie une interface réseau.
Une adresse IP identifie une machine sur un réseau.
Les switchs utilisent les adresses MAC.
Les routeurs relient plusieurs réseaux.
