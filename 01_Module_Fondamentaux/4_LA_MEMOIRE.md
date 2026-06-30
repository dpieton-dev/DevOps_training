## La mémoire : comment un ordinateur se souvient-il ?

🎯 Objectifs

À la fin de ce chapitre, tu comprendras :
* Pourquoi il existe plusieurs types de mémoire.
* La différence entre registre, cache, RAM et SSD.
* Pourquoi un CPU peut attendre la mémoire.
* Ce qu'est la hiérarchie mémoire.
* Pourquoi ajouter de la RAM peut accélérer une machine.
* Pourquoi un SSD n'est pas un remplacement de la RAM.

**Mise en situation**

Imagine que tu es cuisinier 👨‍🍳.
Tu dois préparer un repas et tu as :
* une recette
* des ingrédients
* un plan de travail
* un garde-manger

Où vas-tu poser les ingrédients que tu utilises en ce moment ?
👉 Sur le plan de travail. Tu ne vas pas retourner au garde-manger toutes les 5 secondes.

Un ordinateur fonctionne exactement de la même manière.
La plus grande erreur des débutants pensent :
**"Plus de SSD = ordinateur plus rapide."** Ce n'est pas toujours vrai.

## Pourquoi ?

Parce que le CPU travaille principalement avec la mémoire, pas avec le SSD.

**La hiérarchie mémoire** 
Voici probablement le premier schéma que tu devras connaître par cœur.

                CPU
                 │
        ┌────────┴────────┐
        │                 │
    Registres           Cache L1
                          │
                        Cache L2
                          │
                        Cache L3
                          │
                         RAM
                          │
                         SSD
                          │
                     Disque externe
                          │
                       Internet

Plus on monte :

✅ plus c'est rapide
❌ plus c'est petit

Plus on descend :

✅ plus c'est grand
❌ plus c'est lent

## Les registres

Les registres sont à l'intérieur du processeur, ils sont minuscules mais incroyablement rapides.
On parle de quelques centaines d'octets seulement.

Pourquoi ?
Parce que le CPU travaille directement dessus.

Imagine ton cuisinier.
Les registres sont les ingrédients qu'il tient dans ses mains.

## Le cache

Le cache est une mémoire très rapide.Il sert à éviter que le CPU attende la RAM.
Il existe plusieurs niveaux:

**Cache L1**
Très petit, très rapide.
Quelques dizaines de Ko.

**Cache L2**
Plus gros, un peu moins rapide.

**Cache L3**
Encore plus gros, souvent partagé entre plusieurs cœurs.

**Pourquoi plusieurs caches ?**

Parce que fabriquer une mémoire ultra rapide coûte très cher. Les ingénieurs ont donc créé plusieurs niveaux.

Une analogie :

Imagine une bibliothèque.

        Le SSD
           ↓
    Le bâtiment entier.

        La RAM
           ↓
    La table sur laquelle tu travailles.

        Le cache
           ↓
    Les livres ouverts juste devant toi.

      Les registres
             ↓
    La phrase que tu lis actuellement.

**La RAM**

Nous avons déjà parlé de la RAM mais maintenant nous pouvons aller plus loin.

La RAM contient :
* les programmes en cours
* les données des programmes
* le système d'exploitation
* les fichiers ouverts

Lorsque tu ouvres Firefox :

Firefox est copié :

    SSD
     ↓
    RAM

Puis exécuté.

**Pourquoi pas directement le SSD ?**
Parce que le SSD est des dizaines de fois plus lent et le CPU passerait son temps à attendre.

**Le SSD**
Le SSD est un stockage permanent. Il garde :
* Ubuntu
* Docker
* PHP
* tes projets

Même lorsque le courant est coupé.

## Temps d'accès
Voici un ordre de grandeur.

Mémoire	Temps d'accès:
* Registre	~0,3 ns
* Cache L1	~1 ns
* Cache L2	~4 ns
* Cache L3	~10 ns
* RAM	~100 ns
* SSD NVMe	~50 000 ns
* Disque dur	~5 000 000 ns

👉 Le CPU est des milliers à des millions de fois plus rapide que les supports de stockage.
C'est pour cela que la hiérarchie mémoire est indispensable.

**Pourquoi le CPU attend-il ?**
Imagine un chef qui dit :
"Apporte-moi le dossier."

Si le dossier est :

Dans sa main
    ↓
Instantané.

Sur son bureau
    ↓
Très rapide.

Dans l'armoire
    ↓
Il attend un peu.

Dans un autre bâtiment
        ↓
Il attend longtemps.

Le CPU fait la même chose.

## Et le swap ?

Que se passe-t-il lorsque la RAM est pleine ?

Linux utilise un mécanisme appelé :  **Swap**
Le noyau déplace temporairement certaines données peu utilisées de la RAM vers le disque. Cela évite un plantage immédiat.

Mais attention :
Le disque est beaucoup plus lent.
Si le système utilise énormément le swap, les performances chutent fortement.
Nous étudierons ce mécanisme en détail dans le module Linux.

## Cas réel DevOps 💼

Un serveur de production possède :

* 8 Go de RAM.
* Une application Java consomme 7,8 Go.
* Le noyau commence à utiliser le swap.

Résultat :
Les utilisateurs se plaignent que le site est très lent.
Le problème n'est pas le CPU.
Le problème est la mémoire.

Un ingénieur DevOps vérifiera rapidement :
* la RAM disponible
* le swap utilisé
* les processus les plus gourmands


## ⚠️ Les erreurs classiques
❌ "Le cache est la même chose que la RAM."
Faux. Le cache est beaucoup plus petit et beaucoup plus rapide.

❌ "Le swap remplace la RAM."
Faux. Il la complète, mais avec un coût en performance.

❌ "Un SSD peut remplacer de la RAM."
Faux. Même un SSD très rapide reste très loin des performances de la RAM.

## ⭐ Ce qu'un DevOps ferait

Face à une application lente, un ingénieur ne regarde pas uniquement le CPU.

Il vérifie aussi :
* la RAM libre
* l'utilisation du swap
* les accès disque
* les entrées/sorties

Car un processeur très puissant peut passer son temps... à attendre des données.

## 📝 Résumé
Aujourd'hui, tu as appris que :

* Il existe plusieurs niveaux de mémoire.
* Les registres sont les plus rapides.
* Le cache évite au CPU d'attendre la RAM.
* La RAM est la mémoire de travail.
* Le SSD est un stockage permanent.
* Le swap est une extension de la RAM, mais beaucoup plus lente.