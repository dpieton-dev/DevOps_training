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

---

## Mise en situation

Imagine que ton ordinateur est seul. Il possède :

* un CPU
* de la RAM
* un SSD

Il fonctionne parfaitement mais il ne peut parler à personne.

Il ne peut pas :

* ouvrir Google ;
* télécharger Ubuntu ;
* utiliser GitHub ;
* envoyer un e-mail ;
* communiquer avec un autre serveur.

Il est complètement isolé.

---

## Le problème

Comment faire communiquer deux ordinateurs ?

Prenons deux PC 
```
    PC A
    PC B
```

Question.

Comment PC A peut-il dire : Bonjour PC B ?

---

## Une analogie

Imagine deux personnes et elles veulent communiquer.

Il faut :

* une langue
* une adresse
* un moyen de transport

Le réseau fonctionne exactement comme cela.

---

## Les trois éléments indispensables

Pour communiquer il faut :

```
    Un expéditeur
        ↓
    Une adresse
        ↓
    Un moyen de transport
```

---

## La carte réseau

Chaque ordinateur possède une carte réseau, sur votre Ubuntu vous pouvez déjà la voir.

Vous l'avez observée avec :

```bash
ip a
```

Vous avez : **wlp3s0** votre interface Wi-Fi.

et

**enp2s0** votre carte Ethernet.

La carte réseau est au réseau ce que le clavier est à l'utilisateur. Elle permet d'envoyer et de recevoir des informations.

---

## Les données

Question : Peut-on envoyer un fichier de 3 Go d'un seul coup ?

Non, Ce serait beaucoup trop gros.

Le réseau découpe les données en petits morceaux.

Ces morceaux s'appellent :

```
Paquets ou Packets.
```

---

## Une analogie

Imaginez un déménagement. Vous ne mettez pas toute votre maison dans un seul carton.

Vous faites :

* Carton 1
* Carton 2
* Carton 3

Le réseau fait exactement cela.

---

## Que contient un paquet ?

Chaque paquet possède :

* Expéditeur
* Destinataire
* Données
* Contrôle

Comme une lettre.

---

## Adresse MAC

Chaque carte réseau possède un numéro unique.

La **MAC Address**.

Par exemple :  5C:EA:1D:4C:81:17

vous reconnaissez quelque chose ?

C'est exactement celle que vous aviez vue avec :
```bash
ip a
```

Sur votre Ubuntu, la MAC est :

L'identité physique de la carte réseau. Elle ne change presque jamais.

---

## Adresse IP

La MAC identifie la carte mais sur Internet. On utilise surtout : L'adresse IP.

Chez Vous : 192.168.X.XX

C'est votre adresse dans votre réseau local.

Imaginez un immeuble.

```
La MAC.
   ↓
La personne.

L'adresse IP.
     ↓
L'appartement.
```

Les deux sont nécessaires.

---

## Le switch

Dans un réseau local, les ordinateurs sont reliés à un switch.

Le switch connaît les adresses MAC. Il sait :

Qui est connecté sur quel port.

---

## Le routeur

Pour sortir de votre réseau. vous passez par : Routeur

Chez vous, C'est votre box Internet.

Elle relie :
```
votre réseau
    ↓
Internet.
```
---

## Le paquet voyage

Imaginons :

vous faites :
```bash
ping 8.8.8.8
```

Le paquet suit ce chemin.

```
votre PC
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
```

Et le chemin retour est similaire.

---

## Pourquoi plusieurs couches ?

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

---

## Cas réel DevOps 💼

Un développeur vous dit :

« Le serveur ne répond plus. »

Avant d'accuser l'application, un ingénieur vérifie :

* Le câble est-il branché ?
* L'interface réseau est-elle active ?
* L'adresse IP est-elle correcte ?
* Le routeur répond-il ?
* Le DNS fonctionne-t-il ?
* Le pare-feu bloque-t-il la communication ?

Le réseau est souvent la première étape du diagnostic.

---

## ⚠️ Les erreurs classiques

❌ « L'adresse IP est gravée dans le matériel. »
Non. C'est l'adresse MAC qui est liée à la carte réseau.

❌ « Un fichier est envoyé d'un seul bloc. »
Non. Il est découpé en paquets.

❌ « Internet est un seul réseau. »
Non. C'est un immense réseau de réseaux.

---

## ⭐ Ce qu'un Senior ferait

Lorsqu'une communication échoue, un ingénieur raisonne par couches :

* Le lien physique fonctionne-t-il ?
* L'interface réseau est-elle active ?
* Les adresses IP sont-elles correctes ?
* Le routage est-il correct ?
* Le service distant écoute-t-il ?
* L'application répond-elle ?

Il ne saute jamais directement à la conclusion.

---

## 📝 Résumé

Aujourd'hui, vous avez appris que :

* Une carte réseau permet de communiquer.
* Les données sont découpées en paquets.
* Une adresse MAC identifie une interface réseau.
* Une adresse IP identifie une machine sur un réseau.
* Les switchs utilisent les adresses MAC.
* Les routeurs relient plusieurs réseaux.
