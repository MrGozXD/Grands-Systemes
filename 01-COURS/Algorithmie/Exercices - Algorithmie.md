# Exercices

## 01

Ecrire un programme qui lit le prix HT d’un article, le nombre d’articles et le taux de TVA, et qui fournit le prix total TTC correspondant. Faire en sorte que des libellés apparaissent clairement.

DEBUT

 // DECLARATIONS
 prix_HT : réels
 nb_articles : entiers
 taux_TVA : réels
 prix_TTC : réels

 // INITIALISATIONS
 prix_HT<-- 0.0
 nb_articles <-- 0
 taux_TVA <-- 0.0
 prix_TTC <-- 0.0

 // CORPS DU PROGRAMME
 AFFICHER "Prix HT de l'article ?"
 SAISIR prix_HT
 AFFICHER "Combien d'article ?"
 SAISIR nb_articles
 AFFICHER "Taux de TVA en % ?"
 SAISIR taux_TVA
 prix_TTC <-- prix_HT*nb_articles*(1+taux_TVA/100)
 AFFICHER "Prix total TTC : ", prix_TTC

FIN

## 02

Un magasin de reprographie facture 0,10 E les dix premières photocopies, 0,09 E les vingt suivantes et 0,08 E au-delà.

Ecrivez un algorithme qui demande à l’utilisateur le nombre de photocopies effectuées et qui affiche la facture correspondante.

DEBUT

    // DECLARATIONS
    nb_photocopies : entiers
    prix : réels

    // INITIALISATIONS
    nb_photocopies <-- 0
    prix <-- 0.0

    // CORPS DU PROGRAMME
    AFFICHER "Nombre de photocopies effectuées ?"
    SAISIR nb_photocopies

    SI nb_photocopies <= 10 ALORS
        prix <-- nb_photocopies * 0.10
 SINON
  SI nb_photocopies <= 30 ALORS
         prix <-- 10 *0.10 + (nb_photocopies - 10)* 0.09
     SINON
         prix <-- 10 *0.10 + 20* 0.09 + (nb_photocopies - 30) * 0.08
     FINSI
    FINSI

    AFFICHER "Total à régler en € : ", prix

FIN

## 03

A l’issue de la saisie de 3 valeurs numériques distinctes, afficher la valeur maximale.

DEBUT

    // DECLARATIONS
    a : réels
    b : réels
    c : réels
 max : réels

    // INITIALISATIONS
    a <-- 0.0
    b <-- 0.0
 c <-- 0.0
 max <-- 0.0

    // CORPS DU PROGRAMME
    AFFICHER "a = ? :"
    SAISIR a
 AFFICHER "b = ? :"
    SAISIR b
    AFFICHER "c = ? :"
    SAISIR c

    max <-- a
    SI b > max ALORS
        max <-- b
    FINSI
    SI c > max ALORS
        max <-- c
    FINSI

    AFFICHER "La valeur maximale est : ", max

FIN

## 04

A l’issue de la saisie de 3 valeurs distinctes, afficher ces valeurs dans l’ordre croissant.

DEBUT

    // DECLARATIONS
    a : réels
    b : réels
    c : réels
 temp : réels

    // INITIALISATIONS
    a <-- 0.0
    b <-- 0.0
 c <-- 0.0
 temp <-- 0.0

    // CORPS DU PROGRAMME
    AFFICHER "a = ? :"
    SAISIR a
 AFFICHER "b = ? :"
    SAISIR b
    AFFICHER "c = ? :"
    SAISIR c

    SI a > b ALORS
     temp <-- a
     a <-- b
     b <-- temp
    FINSI 
    SI a > c ALORS
     temp <-- a
     a <-- c
     c <-- temp
 FINSI
 SI b > c ALORS
  temp <-- b
  b <-- c
  c <-- temp
 FINSI
 AFFICHER "Valeurs dans l'ordre croissant : ", a, ", ", b, ", ", c
FIN

## 05

On considère une classe de nb Elèves. Pour chaque élève, sera saisi :

- son nom

- sa note

Afficher pour chaque élève s’il est admis ou non, la note la plus élevée, la note le plus faible, la moyenne de la classe.

La note saisie doit être comprise entre 0 et 20.

DEBUT

 // DECLARATIONS
  nb_elèves : entiers
  nom : string
  note : réels
  note_max : réels
  note_min : réels
  sum_notes : réels
  i : entiers

 // INITIALISATIONS
 nb_élèves <-- 0
 nom <-- ""
 note <-- 0.0
 note_max <-- 0.0
 note_min <-- 20.0
 sum_notes <-- 0.0
 i <-- 0.0

 // CORPS DU PROGRAMME
 AFFICHER "Nombre d'élèves ? : "
 SAISIR nb_élèves

 Si nb_élèves > 0 ALORS
  POUR i <-- 1 à nb_élèves
   AFFICHER "Nom de l'élève n°", i, " ?"
   SAISIR nom
   AFFICHER "Note de ", nom, " [0;20] : "
   SAISIR note

   TANT QUE note < 0 OU note > 20
    AFFICHER "Note invalide. Réessayez : "
    SAISIR note
   FIN TANT QUE

   SI note >= 10 ALORS
    AFFICHER nom, " est admis"
   SINON
    AFFICHER nom, " n'est pas admis"
   FIN SI

   SI note > note_max ALORS
    note_max <-- note
   FIN SI
  
   SI note < note_min ALORS
    note_min <-- note
   FIN SI

   sum_notes <-- sum_notes + note
  FIN POUR

  AFFICHER "Note maximale : ", note_max
  AFFICHER "Note minimale : ", note_min
  AFFICHER "Moyenne de la classe : ", sum_notes/nb_élèves
 SINON
  AFFICHER "Aucun élève dans la classe."
 FIN SI

FIN

## 06

## Exercice : Calcul de la paie hebdomadaire de n ouvriers

***Données en entrée :***

- Coût horaire : 8 € sur une base de 35 heures
- Les heures supplémentaires sont calculées de la façon suivante :
  - 125 % de la 36ème à la 45ème
  - 150% au-delà de la 45ème
- Les pourcentages de retenues de
  - sécurité sociale : 11,3%
  - Chômage : 2,12%
  - retraite : 1,84%

Toutefois, un plafond au niveau du salaire est fixé pour le calcul de la retenue de la sécurité sociale. Ce plafond est fixé à 500,00€.

Sera saisi pour chaque ouvrier, son nom, son nombre d’heures effectuées.

***Données en sortie :***

On affichera :

- pour chacun des Ouvriers :
  - Le salaire brut
  - Les montants de retenue

- pour l’ensemble des ouvriers :
  - Le cumul des sommes versées à chacun des organismes.

DEBUT

    // DECLARATIONS
    nb_ouvriers : entiers
    i : entiers
    nom : string
    heures : réels
    salaire_brut : réels
    heures_normales : réels
    heures_sup_125 : réels
    heures_sup_150 : réels
    retenue_ss : réels
    retenue_chomage : réels
    retenue_retraite : réels
    cumul_ss : réels
    cumul_chomage : réels
    cumul_retraite : réels
    salaire_base_ss : réels
    cout_horaire : réels
    plafond_ss : réels
    taux_ss : réels
    taux_chomage : réels
    taux_retraite : réels

    // INITIALISATIONS
 nb_ouvriers <-- 0
 i <-- 0
 nom <-- ""
 heures <-- 0.0
 salaire_brut <-- 0.0
 heures_normales <-- 0.0
 heures_sup_125 <-- 0.0
 heures_sup_150 <-- 0.0
 retenue_ss <-- 0.0
 retenue_chomage <-- 0.0
 retenue_retraite <-- 0.0
 cumul_ss <-- 0.0
 cumul_chomage <-- 0.0
 cumul_retraite <-- 0.0
 salaire_base_ss <-- 0.0
 cout_horaire <-- 8.0
 plafond_ss <-- 500.0
 taux_ss <-- 0.113
 taux_chomage <-- 0.0212
 taux_retraite <-- 0.0184

    // CORPS DU PROGRAMME
    AFFICHER "Nombre d'ouvriers ?"
    SAISIR nb_ouvriers

    SI nb_ouvriers > 0 ALORS
        POUR i DE 1 A nb_ouvriers FAIRE
            // Saisie des données de l'ouvrier
            AFFICHER "Nom de l'ouvrier ", i, " ?"
            SAISIR nom
            AFFICHER "Nombre d'heures effectuées par ", nom, " ?"
            SAISIR heures

            SI heures <= 35 ALORS
                salaire_brut <-- heures*cout_horaire
            SINON SI heures <= 45 ALORS
                salaire_brut <-- 35*cout_horaire+(heures-35)*cout_horaire*1.25
            SINON
                salaire_brut <-- 35*cout_horaire+10*cout_horaire*1.25+(heures-45)*cout_horaire*1.5
            FINSI

            salaire_base_ss <-- salaire_brut
            SI salaire_brut > plafond_ss ALORS
                salaire_base_ss <-- plafond_ss
            FINSI
            retenue_ss <-- salaire_base_ss * taux_ss

            retenue_chomage <-- salaire_brut * taux_chomage
            retenue_retraite <-- salaire_brut * taux_retraite

            AFFICHER "Ouvrier : ", nom,
            AFFICHER "Salaire brut : ", salaire_brut, " €"
            AFFICHER "Retenue sécurité sociale : ", retenue_ss, " €"
            AFFICHER "Retenue chômage : ", retenue_chomage, " €"
            AFFICHER "Retenue retraite : ", retenue_retraite, " €"

            cumul_ss <-- cumul_ss + retenue_ss
            cumul_chomage <-- cumul_chomage + retenue_chomage
            cumul_retraite <-- cumul_retraite + retenue_retraite
        FIN POUR

        AFFICHER "Total versé à la sécurité sociale : ", cumul_ss, " €"
        AFFICHER "Total versé au chômage : ", cumul_chomage, " €"
        AFFICHER "Total versé à la retraite : ", cumul_retraite, " €"
    SINON
        AFFICHER "Aucun ouvrier à traiter."
    FINSI

FIN

## 07

On considère un tableau T à une dimension de dimension 100 rempli de type numérique. Affichez la valeur max et le nombre de fois où cette valeur max apparaît.

DEBUT

 // DECLARATIONS
 T(100) : entiers
 indice : entiers
 max : entiers
 nb_max : entiers

 // INITIALISATIONS
 T <-- [100 entiers aléatoires]
 indice <-- 0
 max <-- 0
 nb_max <-- 0

 // CORPS DU PROGRAMME
  POUR indice <-- 0 à 99
  SI T(indice) > max ALORS
    max <-- T(indice)
    nb_max <-- 1
  SINON
   SI T(indice) = max ALORS
    nb_max <-- nb_max + 1
   FIN SI
  FIN SI
 FIN POUR

 AFFICHER "Valeur maximale : ", max
 AFFICHER "Nombre d'occurrences : ", nb_max

FIN

## 08

On considère un tableau T de type caractère à une dimension de dimension 20 rempli.

| _   | T   | R   | _   | A   | _   | _   | I   | T   | _   | E   | _   | M   | _   | E   | _   | _   | N   | T   | _   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Remettre la chaine en supprimant les espaces vides dans un second tableau T2 de même dimension et type que T de façon à obtenir le tableau suivant :

| T   | R   | A   | I   | T   | E   | M   | E   | N   | T   | _   | _   | _   | _   | _   | _   | _   | _   | _   | _   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

_ : représente un espace

DEBUT

 // DECLARATIONS
  T[20] : caractères
  T2[20] : caractères
  indice1 : entiers
  indice2 : entiers

 // INITIALISATIONS
 T <-- [*TR_A__IT_E_M_E__NT*]
 T2 <-- [____________________]
 indice1 <-- 0
 indice2 <-- 0

 // CORPS DU PROGRAMME
 POUR indice1 <-- 0 à 19
  SI T[indice1] != _ ALORS
   T2[indice2] <- T[indice1]
   indice2 <-- indice2+1
  FIN SI
 FIN POUR

FIN

## 09

On considère un tableau T à une dimension, de dimension N connue, de type numérique rempli. Inverser les valeurs de ce tableau

a)            En utilisant un deuxième tableau T2

DEBUT

 // DECLARATIONS
 T[N] <-- entiers
 T2[N] <-- entiers
 indice <-- entiers

 // INITIALISATIONS
 T <-- [N entiers aléatoires]
 T2 <-- [N éléments vides]
 indice <-- 0

 // CORPS DU PROGRAMME
 POUR indice <-- 0 à N-1
  T2[indice]<--T[N-1-indice]
  indice <-- indice + 1
 FIN POUR

FIN

b)           Au sein du même tableau T

DEBUT

 // DECLARATIONS
 T[N] : entiers
 indice1 : entiers
 indice2 : entiers
 temp : entiers

 // INITIALISATIONS
 T <-- [N entiers aléatoires]
 indice1 <-- 0
 indice2 <-- 0
 temp <-- 0

 // CORPS DU PROGRAMME
 indice2 <-- N-1
 TANT QUE indice1 < indice2
  temp <-- T[indice1]
  T[indice1]<--T[indice2]
  T[indice2]<--temp
  indice1 <-- indice1+1
  indice2 <-- indice2-1
 FIN TANT QUE

FIN

## 10

Que fait ce programme ?

`//DECLARATIONS`
`T(100) : numérique entier`
`Tampon : numérique entier`
`i : numérique entier`
`j : numérique entier`

`//INITIALISATIONS`
`Tampon <-- 0`
`i <-- 0`
`j <-- 0`

`//CORPS DU PROGRAMME`
`POUR i = 0 à 98`
 `POUR j = (i + 1) à 99`
  `Si T(i) < T(j) alors`
   `Tampon <-- T(i)`
   `T(i) <-- T(j)`
   `T(j) <-- Tampon`
  `FIN SI`
 `FIN POUR`
`FIN POUR`

Trie les valeurs de façon décroissante

## 11

Mettre en place l'algorithme permettant d'effectuer le tri à bulle d'un tableau T à une dimension de longueur N rempli.

```
// DECLARATIONS
T(N) : numérique entier
temp : numérique entier
i : numérique entier
j : numérique entier

// INITIALISATIONS
temp <-- 0
i <-- 0
j <-- 0

// CORPS DU PROGRAMME
POUR i = 0 À N
    POUR j = 0 À N-1-i
        SI T(j) > T(j+1) ALORS
            temp <-- T(j)
            T(j) <-- T(j+1)
            T(j+1) <-- Tampon
        FIN SI
    FIN POUR
FIN POUR
```

## 12

On considère un tableau à deux dimensions, de dimensions (5 ,4) de type numérique rempli.  Ecrire l’algorithme qui permet d’afficher la somme par ligne.

```
DEBUT

    // DECLARATIONS
    T(5, 4) : entier
    i : entier
    j : entier
    sum_line : entier

    // INITIALISATIONS
    i <-- 0
    j <-- 0
    sum_line <-- 0

    // CORPS DU PROGRAMME
    POUR i <-- 0 à 4
        sum_line <-- 0
        POUR j <-- 0 à 3
            sum_line <-- sum_line + T(i,j)
        FIN POUR
        AFFICHER "Somme de la ligne ", i, " : ", sum_line
    FIN POUR

FIN
```

## 13

On considère un tableau à deux dimensions, de dimension (5,4). Mettre le produit de chaque colonne dans la dernière ligne. La dernière ligne devra être prise en compte dans le calcul.

```
DEBUT

    // DECLARATIONS
    T(5, 4) : entier
    i : entier
    j : entier
    product : entier

    // INITIALISATIONS
    i <-- 0
    j <-- 0
    product <-- 1

    // CORPS DU PROGRAMME
    POUR j <-- 0 à 3
        product <-- 1
        POUR i <-- 0 à 4
            product <-- product*T(i,j)
        FIN POUR
        T(4,j) <-- product
    FIN POUR

FIN
```

## 14

On considère un tableau EMPLOYES(600, 4) rempli, de type entier :

| *Matricule* | *Salaire* | *Catégorie (1 à 7)* | *Niveau (1/2)* |
| ----------- | --------- | ------------------- | -------------- |
| 1           | 1500      | 2                   | 1              |
| 7           | 2500      | 4                   | 2              |
| 8           | 1100      | 7                   | 2              |
| …           | …         | …                   | …              |
|             |           |                     |                |

On considère le tableau PRIMES(7, 2) rempli, de type entier :

| *Niveau 1* | *Niveau 2* |
| ---------- | ---------- |
| 100        | 150        |
| 200        | 150        |
| …          | …          |

Ecrire l’algorithme qui permet d’afficher pour chaque matricule, le salaire avec la prime de chaque employé. Cette prime dépend donc du niveau d'ancienneté et de la catégorie à laquelle il appartient.

Exemple :

Matricule 1 gagne 1700.

```
DEBUT

    // DECLARATIONS
    EMPLOYES(600, 4) : entier
    PRIMES(7, 2) : entier
    i : entier
    matricule : entier
    salaire : entier
    catégorie : entier
    niveau : entier
    prime : entier
    salaire_avec_prime : entier

    // INITIALISATIONS
    i <-- 0
    matricule <-- 0
    salaire <-- 0
    catégorie <-- 0
    niveau <-- 0
    prime <-- 0
    salaire_avec_prime <-- 0

    // CORPS DU PROGRAMME
    POUR i <-- 0 à 599
        matricule <-- EMPLOYES(i, 0)
        salaire <-- EMPLOYES(i, 1)
        catégorie <-- EMPLOYES(i, 2)
        niveau <-- EMPLOYES(i, 3)

        prime <-- PRIMES(catégorie-1, niveau-1)

        salaire_avec_prime <-- salaire + prime

        AFFICHER "Matricule ", matricule, " gagne ", salaire_avec_prime
    FIN POUR

FIN
```

## 15

On considère un tableau Eleves(20, 4), rempli de type numérique

| *Matricule* | *Matière 1* | *Matière 2* | *Matière 3* |
| ----------- | ----------- | ----------- | ----------- |
| 4587        | 12          | 18          | 8           |
| 9858        | 20          | 2           | 13          |
| 9654        | 10          | 7           | 2           |
| …           | …           | …           | …           |

On considère un tableau Coefficients(3), rempli de type entier

| *Matière 1* | *Matière 2* | *Matière 3* |
| ----------- | ----------- | ----------- |
| 2           | 5           | 3           |

Ecrire l’algorithme qui permet de remplir un troisième tableau Resultats(20, 2) en respectant le modèle suivant :

| *Matricule* | *Moyenne* |
| ----------- | --------- |
| 4587        | 13.8      |
| 9858        | 8.9       |
| 9654        | 6.1       |
| …           | …         |

```
DEBUT

    // DECLARATIONS
    Eleves(20, 4) : réel
    Coefficients(3) : entier
    Resultats(20, 2) : réel
    i : entier
    matricule : entier
    sum_notes_coeff : réel
    sum_coeff : réel
    moyenne : réel

    // INITIALISATIONS
    i <-- 0
    matricule <-- 0
    sum_notes_coeff <-- 0.0
    sum_coeff <-- 0.0
    moyenne <-- 0.0

    // CORPS DU PROGRAMME
    POUR i <-- 0 à 19
        matricule <-- Eleves(i, 0)

        sum_notes_coeff <-- Eleves(i,1)*Coefficients(0)+Eleves(i,2)*Coefficients(1)+Eleves(i,3)*Coefficients(2)

        sum_coeff <-- Coefficients(0) + Coefficients(1) + Coefficients(2)

        moyenne <-- sum_notes_coeff / sum_coeff

        Resultats(i, 0) <-- matricule
        Resultats(i, 1) <-- moyenne
    FIN POUR

FIN
```

## 16

| **MAT** | **NOM**  | **PRENOM** | **SALAIRE** | **SERVICE**  |
| ------- | -------- | ---------- | ----------- | ------------ |
| 00001   | DUPONT   | Paul       | 2500        | MARKETING    |
| 00005   | MARTIN   | Valérie    | 3000        | MARKETING    |
| 00013   | KARIO    | Jen        | 2500        | INFORMATIQUE |
| 00017   | LOISON   | Charlotte  | 6000        | INFORMATIQUE |
| 00009   | BERTRAND | Alain      | 1500        | MARKETING    |
| 00021   | MASSY    | Laurent    | 1400        | COMPTABILITE |

Afficher le salaire Moyen des employés du service Marketing.

```
DEBUT

    // DECLARATIONS
    fin : entier
    sum : réel
    nb_employe : entier
    moyenne : réel

    // INITIALISATIONS
    fin <-- 0
    sum <-- 0.0
    nb_employe <-- 0
    moyenne <-- 0.0

    // CORPS DU PROGRAMME
    OUVRIR FICHIER EMPLOYES (Lecture)

    LIRE FICHIER EMPLOYES
    SI FF EMPLOYES ALORS
        fin <-- 1
    FIN SI

    TANT QUE fin = 0
        SI EMPLOYES.SERVICE == "MARKETING" ALORS
            sum <-- sum + EMPLOYES.SALAIRE
            nb_employe <-- nb_employe+1
        FIN SI

        LIRE FICHIER EMPLOYES
        SI FF EMPLOYES ALORS
            fin <-- 1
        FIN SI
    FIN TANT QUE

    SI nb_employe > 0 ALORS
        moyenne <-- sum/nb_employe
        AFFICHER "Salaire moyen du service Marketing : ", moyenne
    SINON
        AFFICHER "Aucun employé dans le service Marketing."
    FIN SI

    FERMER FICHIER EMPLOYES

FIN
```

## 17

À partir d'un fichier séquentiel « MOUVEMENT » contenant des opérations sur des mouvements bancaires et sortir un état par compte client qui contient :

- Le numéro de client
- Les sous cumuls de chacune des opérations
- Le total de tous les mouvements du compte

Les opérations concernées sont uniquement :

- Les retraits effectués sur le distributeur automatique de billets
- Les factures carte bleue
- Les dépôts guichet

Chaque opération est identifiée par un code opération selon la correspondance suivante :

**R : Retrait DAB (Distributeur Automatique de Billets)**
**C : Paiement Carte Bleue**
**D : Dépôt Guichet**

Les opérations d’un type différent sont écartées de ce traitement.

**DESCRIPTION DU FICHIER MOUVEMENT (MVT)**
***Type : Séquentiel – Trié sur le Numéro de Compte Client dans l’ordre croissant***

| Numéro de compte du client                     |
| ---------------------------------------------- |
| Date du mouvement bancaire (Format : AAAAMMJJ) |
| Montant du mouvement                           |
| Code du mouvement bancaire                     |
| Zone non utilisée                              |

Jeu d’essai

| Numéro de Compte | Date Opération | Montant | Code Opération |
| ---------------- | -------------- | ------- | -------------- |
| 00001            | 20000220       | 100,10  | C              |
| 00001            | 20000222       | 500,00  | D              |
| 00001            | 20000225       | 251,00  | C              |
| 00001            | 20000225       | 100,00  | R              |
| 00001            | 20000225       | 300,00  | R              |
| 00003            | 20000201       | 100,75  | C              |
| 00003            | 20000203       | 600,00  | D              |
| 00005            | 20000213       | 300,00  | R              |
| 00011            | 20000210       | 1000,00 | C              |
| 00011            | 20000211       | 300,00  | D              |

```
DEBUT

 // DECLARATIONS
 
 num_compte_courant : string
 num_compte_precedent : string
 montant : réel
 code_op : string
 cumul_R : réel
 cumul_C : réel
 cumul_D : réel
 total : réel
 fin_fichier : booléen
 
 // INITIALISATIONS
 
 num_compte_courant <-- ""
 num_compte_precedent <-- ""
 montant <-- 0.0
 code_op <-- ""
 cumul_R <-- 0.0
 cumul_C <-- 0.0
 cumul_D <-- 0.0
 total <-- 0.0
 fin_fichier <-- FAUX
 
 // CORPS DU PROGRAMME
 
 OUVRIR FICHIER MOUVEMENT (Lecture)
 LIRE FICHIER MOUVEMENT
 SI FF MOUVEMENT ALORS
     fin_fichier <-- VRAI
 SINON
     num_compte_precedent <-- MOUVEMENT.Numéro_de_compte
 FIN SI
 
 TANT QUE fin_fichier = FAUX
     num_compte_courant <-- MOUVEMENT.Numéro_de_compte
     montant <-- MOUVEMENT.Montant
     code_op <-- MOUVEMENT.Code_Opération
 
     SI num_compte_courant != num_compte_precedent ALORS
         AFFICHER "Compte : ", num_compte_precedent
         AFFICHER "R : ", cumul_R
         AFFICHER "C : ", cumul_C
         AFFICHER "D : ", cumul_D
         AFFICHER "Total : ", total
 
         cumul_R <-- 0.0
         cumul_C <-- 0.0
         cumul_D <-- 0.0
         total <-- 0.0
         num_compte_precedent <-- num_compte_courant
     FIN SI
 
     SI code_op == "R" ALORS
         cumul_R <-- cumul_R + montant
         total <-- total - montant
     SINON SI code_op == "C" ALORS
         cumul_C <-- cumul_C + montant
         total <-- total - montant
     SINON SI code_op == "D" ALORS
         cumul_D <-- cumul_D + montant
         total <-- total + montant
     FIN SI
 
     LIRE FICHIER MOUVEMENT
     SI FF MOUVEMENT ALORS
         fin_fichier <-- VRAI
     FIN SI
 FIN TANT QUE
 
 SI num_compte_precedent != "" ALORS
     AFFICHER "Compte : ", num_compte_precedent
     AFFICHER "R : ", cumul_R
     AFFICHER "C : ", cumul_C
     AFFICHER "D : ", cumul_D
     AFFICHER "Total : ", total
 FIN SI

 FERMER FICHIER MOUVEMENT

FIN
```

## 18

À partir d'un fichier séquentiel « MOUVEMENT », il faut mettre à jour le fichier indexé et « COMPTES BANCAIRES » et sortir en état sur lequel on trouvera :

- Le numéro de client
- Les sous-cumuls de chacune des opérations
- Le total de tous les mouvements du compte
- Le montant du nouveau solde

Les opérations concernées sont uniquement :

- Les retraits effectués sur le distributeur automatique de billets
- Les factures carte bleue
- Les dépôts guichet

Chaque opération est identifiée par un code opération selon la correspondance suivante :

**R : Retrait DAB**
**C : Paiement Carte Bleue**
**D : Dépôt Guichet**

Les opérations d'un type différent sont écartées de ce traitement et enregistrées dans un compte-rendu d'anomalie. Vous utiliserez un fichier ANOMALIES (même structure que le fichier MOUVEMENTS).

La définition du fichier des mouvements bancaires est identique à celle qui a été établi pour l’exercice précédent.

**DESCRIPTION DU FICHIER COMPTES BANCAIRES**
***Type : Indexé***

| Numéro de compte du client            |
| ------------------------------------- |
| Date d’Ouverture du Compte (AAAAMMJJ) |
| Solde du Compte                       |
| Date de dernière Mise à jour          |
| Zone non utilisée                     |

Jeux d’essai

FICHIER MOUVEMENT

| Numéro de Compte | Date Opération | Montant | Code Opération |
| ---------------- | -------------- | ------- | -------------- |
| 00001            | 20000220       | 100,10  | C              |
| 00001            | 20000222       | 500,00  | D              |
| 00001            | 20000225       | 251,00  | C              |
| 00001            | 20000225       | 100,00  | R              |
| 00001            | 20000225       | 300,00  | R              |
| 00003            | 20000201       | 100,75  | C              |
| 00003            | 20000203       | 600,00  | D              |
| 00005            | 20000213       | 300,00  | R              |
| 00011            | 20000210       | 1000,00 | C              |
| 00011            | 20000211       | 300,00  | D              |

FICHIER COMPTES BANCAIRES

| **Numéro de Compte** | **Date Ouverture Compte** | **Solde** | **Date Dernière MAJ** |
| -------------------- | ------------------------- | --------- | --------------------- |
| 00001                | 19990204                  | 2051,15   | 20000115              |
| 00002                | 19961112                  | -200,00   | 20000126              |
| 00003                | 19950225                  | 2687,78   | 20000114              |
| 00004                | 19980103                  | 100,55    | 20000103              |
| 00005                | 19970305                  | 1600,32   | 20000108              |
| 00006                | 19981212                  | 200,15    | 20000128              |
| 00007                | 19940615                  | 394,65    | 20000109              |
| 00008                | 19990609                  | 178,98    | 20000115              |
| 00009                | 20000101                  | -222,59   | 20000122              |
| 00010                | 19901230                  | -1110,32  | 20000130              |
| 00011                | 20000115                  | 908,75    | 20000129              |
| 00012                | 20000322                  | 987,52    | 20000105              |

```
DEBUT

 // DECLARATIONS

 num_compte_courant_mvmt : string
    num_compte_precedent_mvmt : string
    montant : réel
    code_op : string
    cumul_R : réel
    cumul_C : réel
    cumul_D : réel
    total : réel
    fin_fichier_mvmt : booléen
    date_dernière_maj : string
    solde_initial : réel
    nouveau_solde : réel
    
 // INITIALISATIONS
 
 num_compte_courant_mvmt <-- ""
    num_compte_precedent_mvmt <-- ""
    montant <-- 0.0
    code_op <-- string
    cumul_R <-- 0.0
    cumul_C <-- 0.0
    cumul_D <-- 0.0
    total <-- 0.0
    fin_fichier_mvmt <-- FAUX
    date_dernière_maj <-- ""
    solde_initial <-- 0.0
    nouveau_solde <-- 0.0
    
    
 // CORPS DU PROGRAMME
 
 OUVRIR FICHIER MOUVEMENT (Lecture)
    LIRE FICHIER MOUVEMENT
    SI FF MOUVEMENT ALORS
        fin_fichier_mvmt <-- VRAI
    SINON
        num_compte_precedent_mvmt <--MOUVEMENT.Numéro_de_compte
    FIN SI
    
    OUVRIR FICHIER COMPTES BANCAIRES (Lecture/Ecriture)

 OUVRIR FICHIER ANOMALIES (Ecriture)
    
    TANT QUE fin_fichier_mvmt = FAUX
        num_compte_courant_mvmt <-- MOUVEMENT.Numéro_de_compte
        montant <-- MOUVEMENT.Montant
        code_op <-- MOUVEMENT.Code_Opération

        SI code_op == "R" ALORS
            cumul_R <-- cumul_R + montant
            total <-- total - montant
            date_dernière_maj <-- MOUVEMENT.Date
          SINON SI code_op == "C" ALORS
              cumul_C <-- cumul_C + montant
              total <-- total - montant
              date_dernière_maj <-- MOUVEMENT.Date
            SINON SI code_op == "D" ALORS
                cumul_D <-- cumul_D + montant
                total <-- total + montant
                date_dernière_maj <-- MOUVEMENT.Date
                SINON ECRIRE FICHIER ANOMALIES (MOUVEMENT.Numéro_de_compte, MOUVEMENT.Date, MOUVEMENT.Montant, MOUVEMENT.Code_Opération)
            FIN SI
             
    FIN SI
        FIN SI
        
        LIRE FICHIER MOUVEMENT
        SI FF MOUVEMENT ALORS
            fin_fichier_mvmt <-- VRAI
        FIN SI
        
        SI fin_fichier = VRAI OU num_compte_courant_mvmt !=num_compte_precedent_mvmt ALORS
        

            LIRE FICHIER COMPTES BANCAIRES (num_compte_precedent_mvmt)
            solde_initial <-- COMPTES_BANCAIRES.Solde 

            
            nouveau_solde <-- solde_initial + cumul_D - cumul_R - cumul_C


            COMPTES_BANCAIRES.Solde <-- nouveau_solde
            COMPTES_BANCAIRES.Date_Dernière_MAJ <-- date_dernière_maj
            ECRIRE FICHIER COMPTES BANCAIRES (num_compte_precedent_mvmt)
            
            AFFICHER "Compte : ", num_compte_precedent
            AFFICHER "R : ", cumul_R
            AFFICHER "C : ", cumul_C
            AFFICHER "D : ", cumul_D
            AFFICHER "Total : ", total

            num_compte_precedent_mvmt <-- MOUVEMENT.Numéro_de_compte
            cumul_R <-- 0.0
            cumul_C <-- 0.0
            cumul_D <-- 0.0
            total <-- 0.0
        FIN SI
    FIN TANT QUE

 FERMER FICHIER MOUVEMENT
 FERMER FICHIER COMPTES BANCAIRES
 FERMER FICHIER ANOMALIES

FIN
```

## 19

À partir d'un fichier « FACTURATION » détaillée et d’un fichier « ANNUAIRE » téléphonique, sortir une facture pour chaque abonné répertorié dans l'annuaire.

On éditera sur la facture :

- Le numéro de téléphone, le nom, le prénom de l'abonné
- Le montant de l'abonnement
- Le cumul des consommations

**DESCRIPTION DU FICHIER FACTURATION**

***Type : Séquentiel – trié sur le N° de Téléphone***

| N° de Téléphone   |
| ----------------- |
| Nombre d’unités   |
| Prix Unitaire     |
| Zone non utilisée |

**DESCRIPTION DU FICHIER ANNUAIRE**
**Type : Séquentiel – trié sur le N° de Téléphone**

| N° de Téléphone         |
| ----------------------- |
| Nom                     |
| Prénom                  |
| Adresse                 |
| Profession              |
| Montant de l’abonnement |
| Zone non utilisée       |

**REMARQUE :**

- Une facture correspond à un seul N° de Téléphone
- Un abonné n’ayant aucune consommation durant la période de référence est tout de même facturé sur l’abonnement

```
DEBUT

    // DECLARATIONS
    
    num_tel_fact : string
    num_tel_annuaire : string
    nom : string
    prenom : string
    montant_abonnement : réel
    cumul_consommation : réel
    fin_facturation : booléen
    fin_annuaire : booléen

    // INITIALISATIONS
    
    num_tel_fact <-- ""
    num_tel_annuaire <-- ""
    nom <-- ""
    prenom <-- ""
    montant_abonnement <-- 0.0
    cumul_consommation <-- 0.0
    fin_facturation <-- FAUX
    fin_annuaire <-- FAUX

    // CORPS DU PROGRAMME
    
    OUVRIR FICHIER FACTURATION (Lecture)
    OUVRIR FICHIER ANNUAIRE (Lecture)
    LIRE FICHIER FACTURATION
    SI FF FACTURATION ALORS
        fin_facturation <-- VRAI
    FIN SI
    LIRE FICHIER ANNUAIRE
    SI FF ANNUAIRE ALORS
        fin_annuaire <-- VRAI
    FIN SI

    TANT QUE fin_annuaire = FAUX
        num_tel_annuaire <-- ANNUAIRE.N°_de_Téléphone
        nom <-- ANNUAIRE.Nom
        prenom <-- ANNUAIRE.Prénom
        montant_abonnement <-- ANNUAIRE.Montant_de_l’abonnement

        cumul_consommation <-- 0.0

        TANT QUE fin_facturation = FAUX ET FACTURATION.N°_de_Téléphone != num_tel_annuaire
            LIRE FICHIER FACTURATION
            SI FF FACTURATION ALORS
                fin_facturation <-- VRAI
            FIN SI
        FIN TANT QUE

        TANT QUE fin_facturation = FAUX ET FACTURATION.N°_de_Téléphone = num_tel_annuaire
            cumul_consommation <-- cumul_consommation + FACTURATION.Nombre_d’unités * FACTURATION.Prix_Unitaire
            LIRE FICHIER FACTURATION
            SI FF FACTURATION ALORS
                fin_facturation <-- VRAI
            FIN SI
        FIN TANT QUE

        AFFICHER "Facture pour ", nom, " ", prenom, " (", num_tel_annuaire, ") :"
        AFFICHER "Abonnement : ", montant_abonnement, " €"
        AFFICHER "Consommation : ", cumul_consommation, " €"
        AFFICHER "Total à payer : ", montant_abonnement + cumul_consommation, " €"
    FIN TANT QUE
    
    FERMER FICHIER FACTURATION
    FERMER FICHIER ANNUAIRE

FIN
```

## 20

Une entreprise vend des instruments de mesure ainsi que des pièces détachées et des fournitures relatives à ces appareils.

Le magasinier est chargé de traiter les commandes des clients et de gérer le stock du magasin dont il a la charge.

Les instruments de mesure les pièces détachées et les fournitures sont classés suivant 3 catégories :

- G pour les instruments
- D pour les pièces détachées
- F pour les fournitures

**Objectifs du Traitement**

- A partir du fichier **VENTE,** sortir en état détaillé sur la quantité vendue par fournisseur, par catégorie et par article
- Mettre à jour le champ quantité réelle du fichier STOCK
- Etablir une commande fournisseur quand cela est nécessaire c'est à dire lorsque la quantité réelle est inférieure à la quantité seuil.

La quantité à commander est alors coefficient-commande * Quantité seuil. Vous afficherez un message indiquant la quantité à commander.

**DESCRIPTION DU FICHIER VENTE**

***Type : Séquentiel – trié sur le Code Fournisseur / Catégorie / Article***

| Code Fournisseur  |
| ----------------- |
| Catégorie         |
| Code Article      |
| Quantité Vendue   |
| Date de Sortie    |
| Zone non utilisée |

**DESCRIPTION DU FICHIER STOCK**

***Type : Séquentiel Indexé***

|   |
|---|
|*Code Article – Clé Unique*|
|Libellé Article|
|Code Fournisseur|
|Quantité Réelle|
|Quantité Seuil (Quantité Minimale à maintenir en stock)|
|Coefficient Commande|
|Zone non utilisée|

**REMARQUES :**

On admettra l'unicité de référence (à un code Article est associé un et un seul fournisseur)

Pour simplifier le traitement, on supposera que la quantité d'articles à sortir est inférieure à la quantité réelle en stock.

Le fichier STOCK contient les références de tous les articles qui sont au magasin. La commande d'un article non référencée est donc une anomalie.

```

DEBUT

    // DECLARATIONS
    
    code_fournisseur : string
    categorie : string
    code_article : string
    quantite_vendue : entier
    date_sortie : string
    libelle_article : string
    quantite_reelle : entier
    quantite_seuil : entier
    coefficient_commande : entier
    fin_vente : booléen
    fin_stock : booléen
    total_fournisseur : entier
    total_categorie : entier
    total_article : entier

    // INITIALISATIONS
    
    code_fournisseur <-- ""
    categorie <-- ""
    code_article <-- ""
    quantite_vendue <-- 0
    date_sortie <-- ""
    libelle_article <-- ""
    quantite_reelle <-- 0
    quantite_seuil <-- 0
    coefficient_commande <-- 0
    fin_vente <-- FAUX
    fin_stock <-- FAUX
    total_fournisseur <-- 0
    total_categorie <-- 0
    total_article <-- 0

    // CORPS DU PROGRAMME
    
    OUVRIR FICHIER VENTE (Lecture)
    OUVRIR FICHIER STOCK (Lecture/Ecriture)
    
    LIRE FICHIER VENTE
    SI FF VENTE ALORS
        fin_vente <-- VRAI
    FIN SI
    TANT QUE fin_vente = FAUX



        SI code_fournisseur <> VENTE.Code_Fournisseur ALORS
            AFFICHER “totale de commande du fournisseur “ code_fournisseur “ est de “   total_fournisseur
            total_fournisseur ← 0
        FIN SI 

        SI categorie <> VENTE.Catégorie ALORS 
            AFFICHER “totale de commande du fournisseur “ code_fournisseur “ pour la categorie “ categorie  “est de “  total_categorie
            total_categorie ← 0
        FIN SI 

        SI code_article <> VENTE.Code_Article ALORS
            //cas quantitée réelle < quantité seuil
            SI quantite_reelle < quantite_seuil ALORS
                AFFICHER “Commande à passer pour l’article “, code_article, “:” , coefficient_commande*quantite_seuil, “unités au fournisseur ” code_fournisseur 
            FIN SI
            AFFICHER “totale de commande du fournisseur “ code_fournisseur “ pour l’article “ total_article  “est de “  total_article
            total_article ← 0
        FIN SI 

        total_fournisseur ← total_fournisseur + VENTE.Quantité_Vendue
        total_categorie ← total_categorie + VENTE.Quantité_Vendue
        total_article ← total_article + VENTE.Quantité_Vendue

        code_fournisseur <-- VENTE.Code_Fournisseur
        categorie <-- VENTE.Catégorie
        code_article <-- VENTE.Code_Article
        quantite_vendue <-- VENTE.Quantité_Vendue
        date_sortie <-- VENTE.Date_de_Sortie
 
        LIRE FICHIER STOCK (code_article)
        SI FF STOCK ALORS
         AFFICHER “Anomalie,” code_article”, introuvable”
        SINON
         libelle_article ← STOCK.libelle_article
         quantite_reelle ← STOCK.quantité_reelle
         quantite_seuil ← STOCK.quantite_seuil
         coefficient_commande ← STOCK.coefficient_commande

         quantite_reelle ← quantite_reelle - quantite_vendue
         STOCK.quantite_reelle ← quantite_reelle
         ECRIRE FICHIER STOCK (code_article)
        FIN SI
     LIRE(VENTE) 
     SI FF VENTE  ALORS 
      FLAG-FF <-- 1
     FIN SI
    FIN TANT QUE

    AFFICHER “totale de commande du fournisseur “ code_fournisseur “ est de “  total_fournisseur
    AFFICHER “totale de commande du fournisseur “ code_fournisseur “ pour la catégorie “ categorie  “est de “  total_categorie
    AFFICHER “totale de commande du fournisseur “ code_fournisseur “ pour l’article “ total_article  “est de “  total_article

    FERMER FICHIER VENTE
    FERMER FICHIER STOCK

FIN
```
