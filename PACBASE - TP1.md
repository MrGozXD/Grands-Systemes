
## Création des rubriques du fichier AJC.COMPTES.DATA

![[Pasted image 20260720093421.png]]
![[Pasted image 20260720093544.png]]
![[Pasted image 20260720093658.png]]
![[Pasted image 20260720093745.png]]
![[Pasted image 20260720093901.png]]
![[Pasted image 20260720095323.png]]![[Pasted image 20260720100432.png]]

## Création de la structure de données CB

![[Pasted image 20260720101148.png]]

## Création du segment CB00

![[Pasted image 20260720101404.png]]
![[Pasted image 20260720114323.png]]

## Création du programme TP1

![[Pasted image 20260720103258.png]]

Ensuite commande -P30 pour éditer la fonction 30 qui nous servira à afficher les infos du Compte Bancaire

![[Pasted image 20260720112023.png]]

-WED (depuis PPGMTP1) pour créer la variable me permettant d'utiliser la variable d'édition de SOLD

![[Pasted image 20260720111237.png]]

-CD (depuis PPGMTP1) pour définir les structures dans le programme PGMTP1

![[Pasted image 20260720121800.png]]

GP pour générer le programme

![[Pasted image 20260720123221.png]]

Programme généré : 

```cobol
000010 IDENTIFICATION DIVISION.
000020 PROGRAM-ID.  PGMTP1.                                             PGMTP1
000030 AUTHOR.          PROGRAMME TP1.                                  PGMTP1
000040 DATE-COMPILED.   20/07/98.                                       PGMTP1
000050 ENVIRONMENT DIVISION.                                            PGMTP1
000060 CONFIGURATION SECTION.                                           PGMTP1
000070 SOURCE-COMPUTER. IBM-370.                                        PGMTP1
000080 OBJECT-COMPUTER. IBM-370.                                        PGMTP1
000090 INPUT-OUTPUT SECTION.                                            PGMTP1
000100 FILE-CONTROL.                                                    PGMTP1
000110      SELECT     CB-FICHIER    ASSIGN    UT-S-CB.                 PGMTP1
000120 DATA DIVISION.                                                   PGMTP1
000130 FILE SECTION.                                                    PGMTP1
000140 FD                 CB-FICHIER                                    PGMTP1
000150      BLOCK              00000 RECORDS                            PGMTP1
000160      DATA RECORD                                                 PGMTP1
000170                    CB00                                          PGMTP1
000180           LABEL RECORD STANDARD.                                 PGMTP1
000190 01               CB00.                                           PGMTP1
000200   10             CB00-NCPT     PICTURE X(5).                     PGMTP1
000210   10             CB00-CIV      PICTURE X.                        PGMTP1
000220   10             CB00-NOM      PICTURE X(20).                    PGMTP1
000230   10             CB00-PREN     PICTURE X(20).                    PGMTP1
000240   10             CB00-SITF     PICTURE X.                        PGMTP1
000250   10             CB00-AD00.                                      PGMTP1
000260     11           CB00-NORUE    PICTURE X(4).                     PGMTP1
000270     11           CB00-LIRUE    PICTURE X(18).                    PGMTP1
000280     11           CB00-COPOS    PICTURE X(5).                     PGMTP1
000290     11           CB00-LIVIL    PICTURE X(15).                    PGMTP1
000300   10             CB00-DOUV     PICTURE X(8).                     PGMTP1
000310   10             CB00-SOLD     PICTURE S9(8)V99.                 PGMTP1
000320   10             CB00-FILLER   PICTURE X(3).                     PGMTP1
000330 WORKING-STORAGE SECTION.                                         PGMTP1
000340*UTILISATION DE LA ZONE EDITION DE SOLD                           7ED100
000350 01               WWED-SOLD     PICTURE +Z(8),99.                 7ED110
000360 01               DEBUT-WSS.                                      PGMTP1
000370   05             FILLER        PICTURE X(7) VALUE                PGMTP1
000380                                'WORKING'.                        PGMTP1
000390   05             IK            PICTURE X.                        PGMTP1
000400 01               CONSTANTES-PAC.                                 PGMTP1
000410   05             FILLER        PICTURE X(60) VALUE               PGMTP1
000420     '0064 LBA20/07/98PGMTP1TEST    12:32:21PGMTP1  BVAP20/07/1998PGMTP1
000430-    ''                                                           PGMTP1
000440 01               PAC-CONSTANTES REDEFINES CONSTANTES-PAC.        PGMTP1
000450   05             NUGNA         PICTURE X(5).                     PGMTP1
000460   05             APPLI         PICTURE X(3).                     PGMTP1
000470   05             DATGN         PICTURE X(8).                     PGMTP1
000480   05             PROGR         PICTURE X(6).                     PGMTP1
000490   05             CODUTI        PICTURE X(8).                     PGMTP1
000500   05             TIMGN         PICTURE X(8).                     PGMTP1
000510   05             PROGE         PICTURE X(8).                     PGMTP1
000520   05             COBASE        PICTURE X(4).                     PGMTP1
000530   05             DATGNC        PICTURE X(10).                    PGMTP1
000540 01               DATCE.                                          PGMTP1
000550   05             CENTUR        PICTURE XX VALUE                  PGMTP1
000560                                '19'.                             PGMTP1
000570   05             DATOR.                                          PGMTP1
000580     10           DATOA         PICTURE XX.                       PGMTP1
000590     10           DATOM         PICTURE XX.                       PGMTP1
000600     10           DATOJ         PICTURE XX.                       PGMTP1
000610 01               VARIABLES-CONDITIONNELLES.                      PGMTP1
000620   05             FT.                                             PGMTP1
000630     10           CB-FT         PICTURE X VALUE                   PGMTP1
000640                                '0'.                              PGMTP1
000650 01               COMPTEURS-FICHIERS COMPUTATIONAL-3.             PGMTP1
000660   05             5-CB00-CPTENR PICTURE S9(9) VALUE ZERO.         PGMTP1
000670 01               ZONES-UTILISATEUR PICTURE X.                    PGMTP1
000680 PROCEDURE DIVISION.                                              PGMTP1
000690 N01.                                                             PGMTP1
000700           NOTE *************************************.            PGMTP1
000710                *                                   *             PGMTP1
000720                *INITIALISATIONS                    *             PGMTP1
000730                *                                   *             PGMTP1
000740                *************************************.            PGMTP1
000750 F01.                                                             PGMTP1
000760     EXIT.                                                        PGMTP1
000770 N01CB.                                                           PGMTP1
000780           NOTE *INITIALISATION FICHIER  CB-FICHIER *.            PGMTP1
000790 F01CB.                                                           PGMTP1
000800     OPEN INPUT CB-FICHIER.                                       PGMTP1
000810 F01CB-FN.                                                        PGMTP1
000820     EXIT.                                                        PGMTP1
000830 F01-FN.                                                          PGMTP1
000840     EXIT.                                                        PGMTP1
000850*          NOTE *  DEBUT ITERATION DU PROGRAMME     *.            PGMTP1
000860 F05.                                                             PGMTP1
000870     EXIT.                                                        PGMTP1
000880 N05.                                                             PGMTP1
000890           NOTE *************************************.            PGMTP1
000900                *                                   *             PGMTP1
000910                *LECTURE FICHIERS ACCES SEQ. SANS DE*             PGMTP1
000920                *                                   *             PGMTP1
000930                *************************************.            PGMTP1
000940 N05CB.                                                           PGMTP1
000950           NOTE *LECTURE FICHIER         CB  SANS DE*.            PGMTP1
000960 F05CB.                                                           PGMTP1
000970     IF      CB-FT  =  '0'                                        PGMTP1
000980         NEXT SENTENCE                                            PGMTP1
000990     ELSE                                                         PGMTP1
001000         GO TO F05CB-FN.                                          PGMTP1
001010 F05CB-10.                                                        PGMTP1
001020     READ CB-FICHIER AT END                                       PGMTP1
001030         MOVE 1 TO CB-FT                                          PGMTP1
001040         GO TO F05CB-FN.                                          PGMTP1
001050     ADD 1 TO 5-CB00-CPTENR.                                      PGMTP1
001060 F05CB-FN.                                                        PGMTP1
001070     EXIT.                                                        PGMTP1
001080 F05-FN.                                                          PGMTP1
001090     EXIT.                                                        PGMTP1
001100 N20.                                                             PGMTP1
001110           NOTE *************************************.            PGMTP1
001120                *                                   *             PGMTP1
001130                *FIN DE TRAITEMENT                  *             PGMTP1
001140                *                                   *             PGMTP1
001150                *************************************.            PGMTP1
001160 F20.                                                             PGMTP1
001170     IF      FT  =  ALL '1'                                       PGMTP1
001180         NEXT SENTENCE                                            PGMTP1
001190     ELSE                                                         PGMTP1
001200         GO TO F20-FN.                                            PGMTP1
001210 F20CB.                                                           PGMTP1
001220     CLOSE CB-FICHIER.                                            PGMTP1
001230 F20CB-FN.                                                        PGMTP1
001240     EXIT.                                                        PGMTP1
001250 F2099. STOP RUN.                                                 PGMTP1
001260 F2099-FN.                                                        PGMTP1
001270     EXIT.                                                        PGMTP1
001280 F20-FN.                                                          PGMTP1
001290     EXIT.                                                        PGMTP1
001300 N30.                                                             P000
001310           NOTE *************************************.            P000
001320                *                                   *             P000
001330                *AFFICHAGE DU COMPTE BANCAIRE       *             P000
001340                *                                   *             P000
001350                *************************************.            P000
001360 F30.                                                             P000
001370     DISPLAY ---- INFORMATIONS CB ----                            P020
001380     DISPLAY 'COMPTE : ' CB00-NCPT                                P040
001390     DISPLAY 'NOM    : ' CB00-NOM                                 P060
001400     DISPLAY 'PRENOM : ' CB00-PREN                                P080
001410     MOVE CB00-SOLD TO WWED-SOLD                                  P100
001420     DISPLAY 'SOLDE  : ' WWED-SOLD.                               P120
001430 F30-FN.                                                          P120
001440     EXIT.                                                        P120
001450 F9099-ITER-FN.                                                   PGMTP1
001460     GO TO F05.                                                   PGMTP1
```