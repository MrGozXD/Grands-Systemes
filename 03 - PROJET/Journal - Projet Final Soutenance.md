En binôme avec Arthur MONTESINOS dans la réunion 1

## Jour 1 

Le but du projet est d'être totalement autonome, un point avec Steeve toutes les 2 semaines. Steeve répondra à nos interrogations comme un client et nous donnera des pistes si on bloque.
Le dernier jour de formation : oral avec un manager d'Alteca.
Certaines parties sont indépendantes et peuvent être faites dans n'importe quel ordre. La 2ème est liée à la première
La présentation sur Teams (enregistrée) : 30min de présentation, 15min de discussion.
Note bien tout ce qui est fait/dit/décidé pour pouvoir le ressortir à la présentation

Questions : 
- On veut faire la partie 4 en pacbase, possible de faire des requêtes SQL ? ou alors faudra-t-il passer par un fichier intermédiaire ? ===> passer par un fichier intermédiaire

Avancée : 
- Prise de connaissance du sujet
- Reformulation du sujet et questions à Steeve pour s'assurer de la bonne compréhension du sujet
- Définitions des grandes lignes des plans pour chaque partie (cf les documents PARTIE)
- Création des tables utilisées dans le projet 
- Création du dataset de la partie 1 à la main
 ![[Pasted image 20260804143408.png]]
- Création des datasets de la partie 2 à la main
![[Pasted image 20260804143829.png]]
![[Pasted image 20260804143902.png]]
- Pair programming pour la première partie, afin de définir nos standards de développement ensemble.

## Jour 2

Reprise de la partie 1,  on veut contrôler la conformité des valeurs données pour le prix unitaire et le stock d'un produit. Notre version de Z/Os ne supporte pas la fonction TEST-NUMVAL donc nous implémentons notre propre version. 

Notre implémentation de la fonction ne couvre pas tous les edge cases, nous avons décidé que Yannis continuerai de développer cette fonction pendant que Arthur avance sur les autres fonctionnalités.

Nous avons aussi pensé à implémenter un TU pour notre fonction NUMVAL.

## Jour 3

Point avec Steeve, on lui a expliqué notre méthode de pair programming pour la première partie, il nous a fait quelques retours.
Arthur attaque la partie 2
Yannis attaque la partie 5
DCLGEN des différentes tables
PRODUCTS = PRD
PARTS = PAR
PARTSUPP = PSU
SUPPLIER = SUP
DEPTS = DEP
ORDERS = ORD
ITEMS = ITM
EMPLOYEES = EMP
CUSTOMERS = CUS