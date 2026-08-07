
## Enoncé

Par ailleurs, AJCFRAME souhaite se doter d’une IHM (Interface Homme Machine) permettant d’ajouter des pièces au sein d’un fichier ‘PROJET.NEWPARTS.KSDS’. Le contenu de ce fichier sera ajouté au sein de la table PARTS. 

Afin de garantir un accès sécurisé, l’utilisateur devra au préalable s’authentifier. Afin de vous faciliter la tâche, vous utiliserez le fichier ‘AJC.EMPLOYE.KSDS’ (le code employé correspondra au login et le prénom de l’employé au mot de passe). 

Seulement une fois authentifié, l’utilisateur sera en mesure de pouvoir ajouter des pièces. 

Afin d’éviter les doublons au sein de CICS, voici la nomenclature imposée : 
X : correspond au nom du groupe 
- Fichier PROJET.NEWPARTS.KSDS ➔ PARTSX 
- Fichier PROJET.EMPLOYE.KSDS ➔ USERSX 
- Vos noms de Mapset(s) et de Map(s) commenceront respectivement par MSX et MAPX 
- Vos noms de transaction(s) commenceront par TX
## Résumé 

Faire une IHM avec authentification de l'utilisateur permettant d'ajouter de nouvelles pièces.

## Choix faits

L'ajout d'une nouvelle pièce dans le fichier KSDS.
2 programmes COBOL : le 1er pour l'authentification, le 2ème pour l'ajout de pièces
2 mapsets à écrire : un pour l'écran d'authentification et un pour l'écran d'ajout de pièces
4 JCL de compilation : 2 pour les programmes COBOL et 2 pour les Mapsets
2 transactions : une pour l'authentification et une pour l'ajout de pièces

## Exécution

### Etape 1

Création de G1P5EMP, un JCL pour créer API4.PROJET.EMPLOYE.KSDS et l'alimenter avec les données de API4.AJC.EMPLOYE.DATA

Résultats : 

G1P5EMP
![[Pasted image 20260806113805.png]]
![[Pasted image 20260806113835.png]]
![[Pasted image 20260806113851.png]]

Création du KSDS
![[Pasted image 20260806111834.png]]
Remarque : la taille d'enregistrement est de 100 octets (et max 100) parce que ça a été repris d'un autre JCL qui faisait aussi une alimentation de KSDS à partir de EMPLOYE.DATA mais l'enregistrement d'un employé fait moins que cette taille choisie par sécurité.

Alimentation du KSDS
![[Pasted image 20260806112002.png]]
![[Pasted image 20260806112022.png]]

### Etape 2

Création de G1P5NPAR, un JCL pour créer API4.PROJET.NEWPARTS.KSDS.

La table PARTS est composée ainsi : 

| Champ  | Type        | Taille estimée<br>(octets) |
| ------ | ----------- | -------------------------- |
| PNQ    | CHAR(2)     | 2                          |
| PNAME  | VARCHAR(30) | 30 (max)                   |
| COLOR  | VARCHAR(30) | 30 (max)                   |
| WEIGHT | DEC(2)      | 2                          |
| CITY   | VARCHAR(20) | 20 (max)                   |
En prenant en compte les tailles estimées aux valeurs max et le fait qu'en VSAM il y a des indicateurs de longueur pour les champs VARCHAR, on peut estimer la taille max d'un enregistrement dans le KSDS de 2+30+1+30+1+2+20+1 = 87 octets. Par sécurité, on prendra une taille d'enregistrement de 100 octets.

Résultats :

G1P5NPAR
![[Pasted image 20260806115141.png]]![[Pasted image 20260806115208.png]]

Création du KSDS
![[Pasted image 20260806115305.png]]

### Etape 3

Création du mapset MS1G1P5 de l'écran d'authentification

L'écran d'authentification va se baser sur un écran déjà fait durant la formation (BMS.A4MSE4) qui est divisé en 3 zones principales :
- Le header qui contient la date, le nom du programme, le nom de la transaction, ainsi que l'heure
- Le body qui est le centre de l'écran où l'utilisateur fait ses entrées
- Le footer dans lequel sont affichés les messages d'erreur ainsi que les commandes et touches à disposition de l'utilisateur

Le body d'écran d'authentification contient un message invitant l'utilisateur à rentrer ses identifiants et 2 champs : login et mot de passe.
L'utilisateur a 2 commandes à disposition : Enter pour valider ses informations de connexion et F3 pour quitter l'écran.
Si l'utilisateur rentre les bonnes informations de connexion alors il est mené à un autre écran sinon un message d'erreur s'affiche en rouge dans le footer, "Mauvais login/mot de passe".

MS1G1P5

![[Pasted image 20260806144315.png]]
![[Pasted image 20260806123843.png]]
![[Pasted image 20260806123859.png]]![[Pasted image 20260806123918.png]]![[Pasted image 20260806123937.png]]![[Pasted image 20260806123952.png]]![[Pasted image 20260806124007.png]]![[Pasted image 20260806124026.png]]![[Pasted image 20260806124041.png]]![[Pasted image 20260806124100.png]]

Création de la map symbolique à partir du mapset

MS1G1P5J
![[Pasted image 20260806144649.png]]
![[Pasted image 20260806124910.png]]

Création de la map 

CEDA DEF MAPSET(MS1G1P5) GROUP(API4) 
CEDA INS MAPSET(MS1G1P5) GROUP(API4) 
CECI SEND MAP(MAP1P5) MAPSET(MS1G1P5)

![[Pasted image 20260806153209.png]]

### Etape 4

Création du programme d'authentification et sa transaction