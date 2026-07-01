🧪 TP 10 — Observer ton réseau

Nous allons réutiliser des commandes que tu connais déjà, mais avec un nouveau regard.

1. Voir les interfaces réseau
ip a

Observe :

lo (loopback) ;
wlp3s0 (Wi-Fi) ;
docker0 (pont Docker) ;
les interfaces veth créées par Docker.

👉 Tu ne les vois plus comme de simples noms : tu sais maintenant qu'elles représentent des interfaces réseau.

2. Voir la table de routage
ip route

Repère :

la route par défaut (default via ...) ;
ton réseau local (192.168.1.0/24).

Nous apprendrons à lire cette table en détail dans le module Réseau.

3. Tester la communication

Tu l'as déjà fait :

ping -c 4 8.8.8.8

Observe :

le temps de réponse (time=...) ;
le TTL ;
les statistiques finales.
4. Tester le DNS
ping -c 4 google.com

Si cela fonctionne, ton ordinateur a réussi à résoudre le nom google.com en adresse IP.

5. Identifier les connexions réseau
ss -tuln

Cette commande affiche les ports sur lesquels des services écoutent.

Nous reviendrons dessus dans le module Linux.

🎯 Exercice de réflexion

Imagine que tu exécutes :

ping 8.8.8.8

Essaye de raconter le voyage du paquet :

Qui le crée ?
Qui l'envoie ?
Qui le reçoit ?
Comment la réponse revient-elle ?

Si tu arrives à raconter cette histoire avec tes mots, tu commences déjà à penser comme un administrateur réseau.

👨‍🏫 Mot du Lead DevOps

Dominique, tu viens de franchir une étape très importante.

Beaucoup de personnes utilisent un réseau tous les jours sans jamais se demander ce qui se passe lorsqu'elles ouvrent un navigateur ou exécutent un ping.

Toi, tu commences à construire un modèle mental.

Et ce modèle va énormément t'aider lorsque nous étudierons :

SSH ;
Git ;
Docker ;
Kubernetes ;
les API ;
le Cloud.

Car toutes ces technologies reposent sur les mêmes principes réseau.
