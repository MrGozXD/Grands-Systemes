# Exercice TSO/ISPF

## 1

Créer un DataSet Partitionné (PDS) nommé APIX.SOURCE.TESTTSO avec les caractéristiques suivantes : • Taille : Primary 5, Secondary 5 • Format : FB (Fixed Block) avec LRECL 80 Vous y copierez tous les fichiers du PDS APIX.SOURCE.JCL commençant par M. (Au besoin, vous en créerez quelques uns MVT, MVT1, MVT2, MOUV1) 


![[Pasted image 20260601155752.png]]

## 2

Ajouter les gares suivantes dans le fichier APIX.AJC.GARES.DATA et trier le sur le nom des gares. 
- 11GARE DE SAVIGNY
- 20GARE DE TOURNAN
- 15GARE DE ROISSY
- 13GARE DE GRETZ

![[Pasted image 20260601160431.png]]

## 3

Créer un fichier séquentiel APIX.AJC.STATIONS.DATA ayant les mêmes caractéristiques APIX.AJC.GARES.DATA, vous y ajouterez les 3 premières gares du fichier APIX.AJC.GARES.DATA

![[Pasted image 20260601162823.png]]

## 4

Renommer le membre MOUV1 du Dataset Partitionné APIX.SOURCE.TESTTSO en MVT3.
[[Pasted image 20260603083856.png]]

## 5

Copier le membre MVT le renommer en MVT2 du Dataset Partitionné APIX.SOURCE.TESTTSO

![[Pasted image 20260603084925.png]]![[Pasted image 20260603084947.png]]

## 6

Supprimer le membre MVT2 du Dataset Partitionné APIX.SOURCE.TESTTSO.

/ sur MVT2 puis Delete (4)

![[Pasted image 20260603085132.png]]

## 7 
Renseigner les caractéristiques suivantes à partir du Dataset Partitionné APIX.SOURCE.COPY Record format . . . : Record length . . . : Block size . . . . : 1st extent cylinders: Secondary cylinders : Data set name type :
![[Pasted image 20260603085327.png]]

## 8

Couper les 20 premières lignes du membre APIX.SOURCE.JCL(SKELJCL) au sein du nouveau membre APIX.SOURCE.TESTTSO(SKELCOB).

![[Pasted image 20260603092451.png]]

## 9

![[Pasted image 20260603093256.png]]

## 10 

![[Pasted image 20260603093321.png]]

## 11
![[Pasted image 20260603103127.png]]

## 12

![[Pasted image 20260603094906.png]]

## 13

![[Pasted image 20260603095040.png]]

## 14

![[Pasted image 20260603095140.png]]

## 15

![[Pasted image 20260603100200.png]]

## 16 

![[Pasted image 20260603104333.png]]


## 17

![[Pasted image 20260603104454.png]]


## 18

![[Pasted image 20260603104602.png]]

## 19

![[Pasted image 20260603104638.png]]

## 20

FIND  puis  D
![[Pasted image 20260603104720.png]]

## 21

![[Pasted image 20260603104846.png]]

## 22

![[Pasted image 20260603105205.png]]
![[Pasted image 20260603105821.png]]

## 23

