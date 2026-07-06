🧰 Boîte à outils du Senior — SSH

Les commandes que j'utilise tous les jours :

ssh user@host                 # Connexion

ssh -p 2222 user@host         # Port personnalisé

ssh-keygen -t ed25519         # Générer une clé

ssh-copy-id user@host         # Copier la clé publique

ssh-add ~/.ssh/id_ed25519     # Ajouter une clé au SSH Agent

ssh -v user@host              # Mode verbeux (diagnostic)

scp fichier user@host:/tmp    # Copier un fichier

sftp user@host                # Transfert interactif

Les deux options que j'utilise le plus pour diagnostiquer un problème :

ssh -v

ssh -vvv

Le mode verbeux explique presque toujours pourquoi une connexion échoue.

📖 Anecdote d'entreprise

Lors d'une intervention, un administrateur reçoit ce message :

WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!

Son premier réflexe est de supprimer l'entrée du fichier known_hosts.

Un ingénieur senior, lui, s'arrête.

Il se pose la question :

Le serveur a-t-il réellement été réinstallé ?
Ou suis-je victime d'une attaque de type Man-in-the-Middle ?

Après vérification, le serveur avait effectivement été reconstruit. L'alerte était légitime.

🎓 Leçon : ne jamais ignorer un avertissement de sécurité sans comprendre son origine.