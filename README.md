# SpaceInvaders
A Space Invaders game developed in Python 3 using object-oriented programming and Tkinter.

In Fr : 
# Space Invaders

Jeu vidéo de type **Space Invaders** développé en **Python 3** dans le cadre d'un projet universitaire en programmation orientée objet.

Le joueur contrôle un défenseur capable de se déplacer et de tirer sur une flotte d'aliens. Le jeu repose sur une architecture composée de plusieurs objets représentant les différents éléments du jeu : flotte d'aliens, aliens, défenseur, projectiles et gestion du score.

---

## Présentation

Le principe du jeu est simple : le **Defender** doit éliminer les aliens présents à l'écran à l'aide de projectiles.

Le jeu est développé en Python selon une approche **orientée objet**. L'interface graphique est réalisée avec **Tkinter**, notamment avec le composant `Canvas`, utilisé pour dessiner et déplacer les différents éléments du jeu.

Le projet met ainsi en pratique la conception d'un jeu à partir de plusieurs classes collaborant entre elles.

---

## Fonctionnalités

- Affichage du jeu dans une fenêtre graphique
- Création et déplacement d'une flotte d'aliens
- Déplacement du Defender
- Tir de projectiles
- Détection des collisions entre projectiles et aliens
- Suppression des aliens touchés
- Animation du jeu
- Gestion du score
- Sauvegarde des scores dans un fichier JSON
- Gestion du nom du joueur
- Conditions de victoire et de défaite

---

## Architecture

Le jeu est organisé autour de plusieurs classes :

```text
SpaceInvaders
      │
      ▼
     Game
      │
 ┌────┼───────────────┐
 ▼    ▼               ▼
Fleet Defender       Score
 │      │
 │      └──► Bullet
 │
 └──► Alien

Resultat
   │
   └──► Gestion des scores

Affichage
   │
   └──► Éléments d'interface
````

---

## SpaceInvaders

La classe `SpaceInvaders` constitue le point d'entrée du jeu.

Elle permet notamment de :

* créer la fenêtre principale ;
* initialiser ses attributs ;
* lancer le jeu ;
* démarrer la boucle principale de l'application.

La méthode `play` lance également le mécanisme d'animation du jeu.

---

## Game

La classe `Game` coordonne les différents éléments du jeu.

Elle est notamment responsable de :

* créer les objets du jeu ;
* créer le `Canvas` ;
* lancer l'animation ;
* déplacer les projectiles ;
* déplacer la flotte d'aliens ;
* gérer les touches du clavier ;
* gérer le score.

L'animation est réalisée grâce à la méthode `after` de `Canvas`, permettant d'exécuter régulièrement une fonction afin de maintenir la boucle d'animation.

---

## Fleet

La classe `Fleet` représente la flotte d'aliens.

Elle gère notamment :

* le nombre de lignes d'aliens ;
* le nombre de colonnes ;
* l'espacement entre les aliens ;
* les déplacements horizontaux et verticaux ;
* la taille de la flotte ;
* la collection d'objets `Alien`.

Lors de son installation, la flotte construit les différents aliens à l'aide de boucles imbriquées.

La classe gère également les collisions et la diminution progressive de la flotte lorsque des aliens sont éliminés.

Si la flotte atteint la zone de déplacement du Defender, la partie est perdue.

---

## Alien

La classe `Alien` représente un ennemi du Defender.

Chaque alien possède notamment :

* une identité ;
* un état de vie ;
* une représentation graphique.

Lorsqu'un alien est touché par un projectile :

1. son état passe à `False` ;
2. une explosion peut être affichée temporairement ;
3. le score est incrémenté ;
4. l'alien est retiré de la flotte.

Le jeu prévoit également une condition de victoire lorsque le Defender atteint **50 points**.

---

## Defender

La classe `Defender` représente le joueur.

Le Defender peut :

* être installé dans le `Canvas` ;
* se déplacer horizontalement ;
* rester dans les limites du `Canvas` ;
* tirer des projectiles.

Lorsqu'il tire, un nouvel objet `Bullet` est créé et ajouté à la collection de projectiles du Defender.

Une contrainte supplémentaire du projet est que le Defender doit **rester immobile pour tirer**.

---

## Bullet

La classe `Bullet` représente les projectiles tirés par le Defender.

Un projectile possède notamment :

* un rayon ;
* une couleur ;
* une vitesse ;
* un identifiant graphique ;
* un tireur.

Lors de sa création, sa position est calculée à partir de celle du Defender.

Le projectile se déplace ensuite vers le haut du `Canvas`.

Lorsqu'il sort de la zone de jeu, il est supprimé de la collection des projectiles.

---

## Gestion du score

Le score est géré par la classe `Score`.

Elle permet notamment de manipuler les informations associées au score et au joueur.

Les scores sont sauvegardés dans un fichier **JSON**, permettant de conserver les résultats entre plusieurs parties.

---

## Resultat

La classe `Resultat` permet de gérer une collection de scores.

Elle fournit notamment des mécanismes de :

### Importation

```python
Resultat().fromFile("monfichier.json")
```

### Exportation

```python
res = Resultat()
res.toFile("monfichier.json")
```

Les résultats sont ainsi sérialisés au format JSON.

---

## Affichage

La classe `Affichage` regroupe différents éléments destinés à l'interface graphique.

Elle permet notamment de gérer :

* l'affichage du nom du joueur ;
* une bannière Space Invaders ;
* les scores précédents ;
* les labels ;
* les champs de saisie ;
* la création d'un cadre dédié aux scores.

Cette classe est implémentée dans le projet mais certaines de ses fonctionnalités n'ont pas été intégrées au jeu final.

---

## Boucle de jeu

Le fonctionnement général du jeu repose sur une boucle d'animation :

```text
Initialisation
      │
      ▼
Création du Canvas
      │
      ▼
Création de la flotte
      │
      ▼
Création du Defender
      │
      ▼
Boucle d'animation
      │
 ┌────┼───────────────┐
 ▼    ▼               ▼
Aliens  Projectiles  Clavier
 │      │               │
 └──────┴───────────────┘
          │
          ▼
      Collisions
          │
          ▼
     Mise à jour
       du score
          │
          ▼
      Victoire /
       Défaite
```

---

## Technologies

* **Python 3**
* **Programmation orientée objet**
* **Tkinter**
* **Canvas**
* **JSON**
* Gestion d'événements clavier
* Animation graphique
* Détection de collisions

---

## Objectifs pédagogiques

Ce projet avait notamment pour objectif de mettre en pratique la **programmation orientée objet en Python** à travers la conception d'un jeu vidéo.

Il permet de travailler sur :

* la conception de classes ;
* les attributs et méthodes ;
* la création et la manipulation d'objets ;
* les relations entre objets ;
* les collections d'objets ;
* la gestion des événements ;
* les animations graphiques ;
* la gestion des collisions ;
* la persistance des données avec JSON.

---

## Améliorations possibles

Plusieurs améliorations peuvent être envisagées pour poursuivre le développement du jeu.

Parmi celles envisagées dans le projet :

* améliorer l'intelligence artificielle des aliens ;
* permettre à certains aliens de tirer ;
* enrichir les mécanismes de jeu ;
* améliorer l'interface de gestion des scores ;
* développer davantage l'écran d'accueil et les scores précédents.

---

## Contexte

**Université de Bretagne Occidentale (UBO)**
**Licence 2 Informatique**
**Année universitaire 2021–2022**

Projet réalisé en binôme.

**Auteurs :**

* Houssam BACAR
* Karl Benard

---

## Licence

Projet réalisé dans un cadre universitaire et conservé à des fins pédagogiques et de portfolio.


