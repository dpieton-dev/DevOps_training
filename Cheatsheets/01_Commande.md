# 🧰 Boîte à outils du Senior  : Les commandes

Les commandes que vous utiliserez tous les jours.

---

📍 Savoir où je suis :
```bash
pwd
```
Affiche le dossier courant.

👤 Qui suis-je ?
```bash
whoami
```

Affiche l'utilisateur courant.

🖥 Quel shell j'utilise ?
echo $SHELL

🏠 Retourner immédiatement dans le Home

cd ou cd ~

Je ne tape jamais : cd /home/dominique, c'est inutile.

📂 Voir les fichiers cachés
ls -la

📁 Créer rapidement un laboratoire
mkdir -p ~/devopslab/tests

Le -p évite les erreurs si les dossiers existent déjà.

🧹 Nettoyer un terminal
clear

ou beaucoup plus souvent :

Ctrl + L

📌 Toujours savoir sur quelle machine je travaille

Très important. Sur un serveur de production :

hostname

ou

hostnamectl

Je vérifie presque toujours avant une manipulation importante.

🔍 Identifier le système

cat /etc/os-release

ou

hostnamectl

📋 Les commandes indispensables
pwd

whoami

hostname

hostnamectl

echo $SHELL

ls -la

cd ~

clear