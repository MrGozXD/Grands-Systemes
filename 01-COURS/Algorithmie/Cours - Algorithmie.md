## Intro

Etapes de conception d'un algorithme : Analyse -> Conception -> Programmation -> Test

Qualité d'un bon algorithme : 
- Correct
- Complet
- Efficace

## Les objets de base

### Caractéristiques

Un identificateur :
- Nom attribué arbitrairement par le programmeur
- Il ne doit pas être ambigu

Un type:
- Nature de l'objet qui peut être simple ou composée (tableaux)

Une valeur : 
- Variable
- Constante

### Types

Les caractères : lettres, signes de ponctuations, chiffres, décimaux, symboles spéciaux

Textes ou chaînes de caractères : série de caractères

Les logiques, les booléens ou indicateurs : false/true, 0/1

Les nombres : entiers et réels

### Types composés

Les tableaux : objet à un seul identificateur, un seul type mais plusieurs valeurs, chacune repérée par un indice

Les fichiers : ensemble de valeur résidant sur un support externe. Il y a un découpage en article auquel on peut accéder (de façon séquentielle ou direct)

## Les actions de base

Un algorithme se structure comme ci :

Début
	DECLARATIONS
	INITIALISATIONS
	CORPS DU PROGRAMME
Fin 
### L'affectation

Consiste à attribuer à un objet appelé VAR une valeur E

Notation : VAR <-- E ou E peut être une constante, une autre variable, une expression arithmétique quelconque

Var et E doivent être du même type

Quelques affectations particulières : 
- Initialisation
- Incrémentation/Décrémentation
### La lecture

A partir d'un clavier :
- SAISIR nomObjet
### L'écriture

A l'écran :
- AFFICHER "Message"
- AFFICHER nomObjet
- AFFICHER "Mon objet: " nomObjet  *// Concaténation*
## Les structures de base

L'enchaînement : consiste à enchaîner 2 actions au moins l'une à la suite de l'autre

Le choix : consiste à choisir entre l'exécution de l'action 1 ou de l'action 2 suivant une certaine condition vérifiée ou pas.

La répétition : consiste à répéter l'exécution d'une ou plusieurs actions jusqu'à ce qu'une condition soit vérifiée ou non.

Tout programme est un enchaînement d'actions

## Les tableaux

Un tableau est une structure de données linéaire qui permet de stocker des données de même type.

Chacune des valeurs est repérée par un indice indiquant la position de la donnée dans le tableau.

U n tableau est une suite d'éléments. Chaque élément correspond à une variable. Cette variable aura le nom du tableau. On leur affectera un indice qui correspondra au rang de l'élément dans le tableau T.

Le nombre d'éléments contenus dans un tableau T s'appelle la *dimension* d'un tableau.

```
// DECLARATIONS
T(5) : entier
indice : entier

// INITIALISATIONS
indice <-- 0

// CORPS DU PROGRAMME
POUR indice <-- 0 à 4
	AFFICHER "Saisir un entier : "
	SAISIR T(indice)
FIN POUR
```