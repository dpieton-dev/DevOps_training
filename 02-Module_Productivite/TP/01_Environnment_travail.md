# 🧪 TP 1 — Découverte de ton environnement

Nous allons commencer très simplement.

1. Vérifier ton shell
echo $SHELL
2. Vérifier ton utilisateur
whoami
3. Vérifier ton dossier courant
pwd
4. Aller dans ton dossier personnel
cd ~

Puis :

pwd

Tu dois retrouver :

/home/dominique
5. Observer les fichiers cachés
ls -la

Repère notamment :

.bashrc
.profile
.ssh
.config

Tu les avais déjà vus lors de notre premier échange, mais tu sais maintenant pourquoi ils commencent par un point.

6. Vérifier ton environnement graphique
echo $XDG_CURRENT_DESKTOP

Tu devrais obtenir quelque chose comme :

GNOME
7. Vérifier ta session
loginctl

Tu verras les sessions actuellement ouvertes.

Nous reparlerons de cet outil lorsque nous étudierons systemd.

🎯 Challenge du chapitre

Sans regarder tes notes, explique avec tes propres mots :

Quelle est la différence entre le terminal et le shell ?
Pourquoi le bureau GNOME n'est-il pas "Linux" ?
Pourquoi les fichiers .bashrc ou .ssh commencent-ils par un point ?
Pourquoi un DevOps organise-t-il soigneusement son environnement de travail ?