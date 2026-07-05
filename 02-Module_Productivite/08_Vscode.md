VS Code : Construire un environnement DevOps professionnel

"Les meilleurs outils ne rendent pas un ingénieur meilleur. Ils lui permettent de consacrer son énergie aux vrais problèmes."

🎯 Objectifs

À la fin de ce chapitre, tu seras capable de :

Configurer VS Code pour le DevOps.
Comprendre la philosophie des extensions.
Utiliser le terminal intégré efficacement.
Te connecter à un serveur Linux via Remote SSH.
Gérer Git sans quitter VS Code.
Travailler dans des conteneurs Docker.
Organiser un projet professionnel.
📖 Avant de commencer

Imagine deux développeurs.

Le premier ouvre :

un terminal ;
un explorateur de fichiers ;
un navigateur ;
un client Git ;
un client SSH.

Le second ouvre uniquement VS Code.

Les deux font exactement le même travail.

Qui sera le plus efficace ?

👉 Souvent le second, car il réduit les changements de contexte.

VS Code n'est pas un IDE

Contrairement à certains environnements très lourds, VS Code est :

léger ;
modulaire ;
personnalisable.

Tu n'installes que ce dont tu as besoin.

L'architecture de VS Code
                 VS Code

                     │

     ┌───────────────┼───────────────┐
     │               │               │
 Explorateur     Terminal      Extensions
     │               │               │
     └───────────────┼───────────────┘
                     │
              Serveurs distants

Les extensions ajoutent progressivement des fonctionnalités.

Les dossiers importants

VS Code distingue deux niveaux :

Les paramètres utilisateur

Ils s'appliquent à tous les projets.

Exemple :

thème ;
police ;
raccourcis.
Les paramètres du projet

Ils sont stockés dans :

.vscode/

On peut y trouver :

settings.json

launch.json

tasks.json

extensions.json

Toute l'équipe partage ainsi la même configuration.

Le terminal intégré

Ouvre un terminal avec :

Ctrl + `

(le caractère accent grave).

Tu peux :

lancer Git ;
exécuter Docker ;
utiliser Bash ;
lancer des scripts.

Sans quitter VS Code.

Plusieurs terminaux

Tu peux ouvrir :

Terminal 1

Terminal 2

Terminal 3

Puis les renommer :

Docker

Git

Logs

Tests

Très pratique.

Les Workspaces

Tu peux ouvrir plusieurs dossiers :

Frontend

Backend

Infrastructure

Terraform

Dans une seule fenêtre.

C'est indispensable sur les gros projets.

Les extensions

Une extension ajoute une fonctionnalité.

Quelques exemples :

coloration YAML ;
Docker ;
Kubernetes ;
GitHub ;
Terraform ;
Ansible.
Les extensions indispensables (selon moi)
1. Docker

Permet de :

voir les conteneurs ;
démarrer ;
arrêter ;
consulter les logs.
2. Remote SSH

Extraordinaire.

Tu édites directement un serveur distant.

Comme s'il était local.

3. GitLens

Affiche :

qui a modifié une ligne ;
quand ;
pourquoi.

Très utile lors des revues de code.

4. YAML

Indispensable pour :

Kubernetes ;
GitHub Actions ;
GitLab CI ;
Docker Compose ;
Ansible.
5. Error Lens

Les erreurs apparaissent directement dans le code.

6. Markdown All in One

Pour notre académie.

Très pratique.

7. EditorConfig

Garantit une mise en forme cohérente entre les membres d'une équipe.

8. Prettier

Formatte automatiquement le code.

9. ShellCheck

Analyse les scripts Bash.

Il détecte énormément d'erreurs.

Remote SSH

L'une des meilleures fonctionnalités.

Architecture :

Ton PC

↓

VS Code

↓

SSH

↓

Serveur Linux

↓

VS Code Server

Le code reste sur le serveur.

Tu édites à distance.

Git intégré

VS Code détecte automatiquement Git.

Tu peux :

créer un commit ;
voir les différences ;
créer des branches ;
résoudre des conflits.

Sans quitter l'éditeur.

Docker intégré

L'extension Docker affiche :

images ;
conteneurs ;
volumes ;
réseaux.

Très pratique pour débuter.

Dev Containers

Une fonctionnalité fantastique.

Imagine.

Tu clones un projet.

Tu l'ouvres.

VS Code construit automatiquement un conteneur contenant :

PHP ;
Node.js ;
Composer ;
Git.

Tout est prêt.

Nous l'utiliserons dans le module Docker.

Paramètres que je recommande
Activer l'Auto Save

Recherche :

Auto Save

Je recommande :

afterDelay
Police

Je conseille :

JetBrains Mono

ou

Cascadia Code

avec les ligatures activées si tu les apprécies.

Taille
14

ou

16

Le confort visuel est important.

Formatage automatique

Active :

Format On Save
Organisation de l'écran

Voici mon organisation quotidienne :

+----------------------------------------------+
| Explorateur |          Code                  |
|             |                                |
|             |                                |
+-------------+-------------------------------+
| Terminal Git | Terminal Docker | Bash       |
+----------------------------------------------+

Je passe très rarement d'une fenêtre à une autre.

Cas réel DevOps 💼

Tu modifies un pipeline GitLab.

À gauche :

.gitlab-ci.yml

En bas :

Terminal

Tu exécutes :

git add .

git commit

git push

À droite :

Documentation officielle.

Tu fais tout dans une seule application.

⚠️ Les erreurs classiques

❌ Installer 150 extensions.

❌ Ouvrir 30 terminaux inutiles.

❌ Ne jamais utiliser le terminal intégré.

❌ Désactiver Git intégré.

❌ Ne jamais synchroniser ses paramètres.

⭐ Ce qu'un Senior ferait

Un ingénieur expérimenté :

installe peu d'extensions ;
les maintient à jour ;
partage les extensions recommandées via .vscode/extensions.json ;
garde une configuration simple et reproductible.
📝 Résumé

Aujourd'hui, tu as appris :

VS Code est une plateforme de travail.
Les extensions ajoutent des fonctionnalités.
Le terminal intégré remplace souvent un terminal externe.
Remote SSH permet d'éditer des serveurs distants.
Git et Docker sont parfaitement intégrés.
🧪 TP 8 — Construire ton environnement DevOps
1. Vérifier la version
code --version
2. Ouvrir ton laboratoire
cd ~/devopslab
code .
3. Installer les extensions suivantes

Je te conseille de commencer par celles-ci :

Extension	Pourquoi ?
Docker	Gérer les conteneurs
Remote - SSH	Éditer des serveurs distants
GitLens	Historique Git
YAML	Kubernetes, Docker Compose, Ansible
Markdown All in One	Documentation
ShellCheck	Vérifier les scripts Bash
EditorConfig	Uniformiser les projets
Error Lens	Afficher immédiatement les erreurs
Prettier	Formatage automatique

👉 N'en installe pas davantage pour le moment.

4. Activer les options suivantes

Dans les paramètres :

Auto Save → afterDelay
Format On Save → Activé
Font Size → 14 ou 16
Font Family → JetBrains Mono (si installée)
5. Ouvrir plusieurs terminaux

Crée trois terminaux et renomme-les :

Bash

Git

Docker
6. Tester Git intégré

Dans ~/devopslab, crée un fichier :

notes.md

Observe que VS Code détecte immédiatement cette modification dans la vue Source Control.

🎯 Challenge du chapitre

Configure VS Code de manière à ce qu'il devienne ton environnement principal.

Tu dois pouvoir :

ouvrir un projet ;
utiliser Git ;
ouvrir plusieurs terminaux ;
modifier un fichier Markdown ;
lancer une commande Docker ;
naviguer sans quitter l'éditeur.
🧰 Boîte à outils du Senior — VS Code
Les raccourcis que j'utilise le plus
Raccourci	Action
Ctrl + P	Rechercher un fichier
Ctrl + Shift + P	Palette de commandes
`Ctrl + ``	Ouvrir le terminal
Ctrl + B	Afficher/Masquer l'explorateur
Ctrl + Shift + E	Explorateur
Ctrl + Shift + G	Git
Ctrl + Shift + X	Extensions
Ctrl + /	Commenter une ligne
Alt + ↑ / ↓	Déplacer une ligne
Shift + Alt + ↓	Dupliquer une ligne
F2	Renommer un symbole
F12	Aller à la définition
Les extensions que je considère indispensables
✅ Docker
✅ Remote - SSH
✅ GitLens
✅ YAML
✅ ShellCheck
✅ Markdown All in One
✅ EditorConfig
✅ Error Lens
🧠 Comment raisonne un Senior ?

Situation : tu dois travailler sur un serveur distant.

Un débutant pense :

"Je vais ouvrir FileZilla, PuTTY, un terminal et VS Code."

Un senior pense :

"Je vais utiliser Remote SSH et tout faire dans un seul environnement."

Son objectif est de réduire les changements de contexte et de rester concentré sur le problème technique.

📖 Anecdote d'entreprise

Lors d'un audit, une équipe de dix développeurs avait chacun un formatage différent :

espaces ;
tabulations ;
fins de ligne.

Chaque commit modifiait des centaines de lignes inutilement.

Après avoir ajouté :

EditorConfig
Prettier

et partagé la configuration dans le dépôt Git, les revues de code sont devenues beaucoup plus simples.

🎓 Leçon : un bon environnement de travail améliore aussi la collaboration.