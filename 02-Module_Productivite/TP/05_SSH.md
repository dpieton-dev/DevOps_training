🧪 TP 5 — Découverte de SSH

Même sans serveur distant, nous pouvons préparer ton environnement.

1. Vérifier la présence de SSH
ssh -V

Tu verras la version installée.

2. Vérifier le dossier SSH
ls -la ~/.ssh

Observe son contenu.

S'il n'existe pas encore, ce n'est pas un problème.

3. Générer une paire de clés

Nous utiliserons l'algorithme recommandé aujourd'hui :

ssh-keygen -t ed25519 -C "dominique@devopslab"

Lorsque l'assistant te pose des questions :

emplacement : Entrée (par défaut)
phrase secrète : tu peux en mettre une (recommandé) ou laisser vide pour le laboratoire

Tu obtiendras :

~/.ssh/id_ed25519

~/.ssh/id_ed25519.pub
4. Afficher la clé publique
cat ~/.ssh/id_ed25519.pub

Tu verras une longue ligne commençant par :

ssh-ed25519

C'est cette clé que l'on copie sur les serveurs.

5. Vérifier les permissions
ls -l ~/.ssh

Observe les droits.

La clé privée ne doit pas être lisible par d'autres utilisateurs.

6. Tester une connexion locale (si le serveur SSH est installé)

Vérifie d'abord :

systemctl status ssh

Si le service est actif :

ssh localhost

Tu te connecteras... à ta propre machine.

C'est un excellent exercice pour comprendre le fonctionnement de SSH.

🎯 Challenge du chapitre

Réponds aux questions suivantes :

Pourquoi la clé publique peut-elle être partagée sans risque ?
Pourquoi la clé privée doit-elle rester secrète ?
À quoi sert known_hosts ?
À quoi sert authorized_keys ?
Pourquoi SSH est-il plus sûr que Telnet ?