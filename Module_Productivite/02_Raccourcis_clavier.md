# Les raccourcis clavier d'un Ingénieur DevOps

"La souris est pratique. Le clavier est rapide."

---

## 🎯 Objectifs

À la fin de ce chapitre, tu seras capable de :

* Travailler plusieurs heures sans souris.
* Ouvrir n'importe quelle application au clavier.
* Naviguer rapidement entre les fenêtres.
* Gérer plusieurs bureaux virtuels.
* Contrôler le terminal efficacement.
* Utiliser les raccourcis Bash indispensables.
* Comprendre pourquoi les ingénieurs privilégient le clavier
---

## Pourquoi les raccourcis sont importants ?

Imagine deux personnes.

Développeur A :

* main → souris
* clic
* retour clavier
* retour souris
* clic
* retour clavier

Développeur B : Il ne quitte jamais le clavier.

Qui sera le plus rapide ?

👉 Le deuxième. Pas parce qu'il tape plus vite mais parce qu'il ne perd jamais de temps à déplacer sa main.

---

## Les trois touches magiques

Sous Ubuntu, tu vas utiliser trois touches en permanence :
```
    Ctrl
     ↓
    Contrôle.

    Alt
     ↓
    Actions sur les fenêtres.

    Super
      ↓
    La touche Windows (⊞).
```

C'est probablement la touche la plus importante sous GNOME.

---

## Premier réflexe

Appuie simplement sur : Super

Tu verras :

* les applications ouvertes
* les bureaux virtuels
* la recherche

À partir de maintenant, oublie le menu Applications.

---

## Ouvrir une application

* Appuie sur : Super
* Puis tape : terminal
* Puis : Entrée

Pas de souris.

Même chose pour : 

* firefox
* code
* docker
* files
* settings

Tu peux lancer presque tout ainsi.

---

## Ouvrir directement un terminal

Le raccourci que tu utiliseras le plus : **Ctrl + Alt + T**

À connaître par cœur.

---

## Changer de fenêtre

Le classique :  **Alt + Tab**

Passe d'une application à l'autre.

Pour revenir en arrière : **Alt + Shift + Tab**

---

## Changer de fenêtre d'une même application

Si plusieurs fenêtres sont ouvertes :  **Alt + `**

(la touche située à gauche du 1 ou 7 sur un clavier AZERTY).

Très pratique avec plusieurs terminaux.

---

## Fermer une fenêtre

Alt + F4

Fonctionne quasiment partout.

---

## Verrouiller la session

Super + L

À utiliser dès que tu t'absentes. Un bon réflexe en entreprise.

---

## Les bureaux virtuels

Ubuntu permet d'avoir plusieurs espaces de travail.

Par défaut : 
```
Super + Page Haut
Super + Page Bas
```
ou

```
Ctrl + Alt + Flèche Haut
```

(selon la configuration GNOME). Tu peux aussi afficher les bureaux avec Super.

---

## Déplacer une fenêtre

Tu peux déplacer une fenêtre sans souris :
```
Alt + F7
```

Puis les flèches.

---

Redimensionner :
```
Alt + F8
```

---

## Mettre une fenêtre en plein écran
```
Super + Flèche Haut
```
---

Moitié gauche :
```
Super + Flèche Gauche
```

---

Moitié droite :
```
Super + Flèche Droite
```

Très utile avec :

* terminal
* navigateur
* documentation

---

## Afficher le bureau
```
Super + D
```
---

## Captures d'écran

Ubuntu possède des raccourcis très pratiques.

Capture complète : Impr. Écran

Zone : Shift + Impr. Écran

Fenêtre : Alt + Impr. Écran

Ces raccourcis sont très utiles pour documenter un incident ou rédiger une procédure.

---

## Le terminal : les raccourcis indispensables

Maintenant, les raccourcis que j'utilise tous les jours.

Annuler une commande : Ctrl + C

Très important. Tu l'utiliseras des milliers de fois.

Suspendre un processus : Ctrl + Z

Nous verrons plus tard la différence avec Ctrl + C.

Effacer l'écran : Ctrl + L

Equivalent à : clear

Mais plus rapide.

Fin de fichier / Déconnexion : Ctrl + D

Ferme le shell si aucune commande n'est en cours.

---

## Les raccourcis Bash (les plus précieux)

* Aller au début de la ligne : Ctrl + A
* Aller à la fin : Ctrl + E
* Effacer jusqu'au début : Ctrl + U
* Effacer jusqu'à la fin : Ctrl + K
* Effacer un mot précédent: Ctrl + W
* Effacer un caractère : Ctrl + H

(c'est l'équivalent de Backspace dans beaucoup de terminaux).

---

## L'historique

* Flèche Haut : Commande précédente.
* Flèche Bas : Commande suivante.
* Recherche dans l'historique : Ctrl + R

Exemple :

Tu tapes : docker

Bash retrouve immédiatement la dernière commande Docker utilisée.

👉 C'est probablement le raccourci qui te fera gagner le plus de temps dans toute ta carrière.

---

## L'autocomplétion

La touche : Tab

C'est magique.

Exemple :

* Tu écris : cd Doc
* Puis : Tab
* Bash complète : cd Documents/

Si plusieurs possibilités existent : Appuie deux fois sur Tab.

---

## Cas réel DevOps 💼

Imagine :

Tu dois redémarrer rapidement un service sur 15 serveurs différents.

Chaque seconde compte, grâce à :

* Ctrl + R
* Tab
* Ctrl + A
* Ctrl + E

Tu peux retrouver et adapter une commande en quelques secondes au lieu de la retaper entièrement.

---

## ⚠️ Les erreurs classiques

❌ Retaper une commande entière au lieu d'utiliser l'historique.

❌ Utiliser la souris pour ouvrir un terminal.

❌ Copier-coller systématiquement les chemins.

❌ Ne pas utiliser l'autocomplétion.

❌ Fermer un terminal avec la souris au lieu d'utiliser Ctrl + D ou exit.

---

## ⭐ Ce qu'un DevOps ferait

Observe un administrateur Linux expérimenté.

Tu verras souvent :

* très peu de souris ;
* énormément de clavier ;
* beaucoup de Tab ;
* beaucoup de Ctrl + R.

Ce n'est pas pour faire le "geek". C'est simplement plus efficace.

---

## 📝 Résumé

Aujourd'hui, tu as appris :

* les raccourcis GNOME essentiels ;
* les raccourcis du terminal ;
* les raccourcis Bash ;
* l'autocomplétion ;
* la recherche dans l'historique.

Tu viens probablement d'apprendre les raccourcis que tu utiliseras le plus souvent pendant toute ta carrière.
