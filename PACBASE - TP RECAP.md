## Création des rubriques du fichier AJC.ETUDIANT.DATA

![[Pasted image 20260723144225.png]]
![[Pasted image 20260723144332.png]]
![[Pasted image 20260723152605.png]]
## Création de la structure XA eXAmen
![[Pasted image 20260723155148.png]]

## Création du segment XA00 EXAMEN
![[Pasted image 20260723155253.png]]

-CE

![[Pasted image 20260723155338.png]]

## Création de l'état EX1

Fait à partir de ET1

![[Pasted image 20260723145634.png]]

![[Pasted image 20260723152513.png]]
![[Pasted image 20260723163115.png]]![[Pasted image 20260723155539.png]]

## Création du programme PGMT08 pour imprimer les résultats d'examens

![[Pasted image 20260723153007.png]]

-CD

![[Pasted image 20260723155736.png]]

## COBOL Généré

```COBOL
000010 IDENTIFICATION DIVISION.
000020 PROGRAM-ID.  PGMT08.                                             PGMT08
000030 AUTHOR.         PGMT08 - IMPRESSION EXAMENS.                     PGMT08
000040 DATE-COMPILED.   23/07/98.                                       PGMT08
000050 ENVIRONMENT DIVISION.                                            PGMT08
000060 CONFIGURATION SECTION.                                           PGMT08
000070 SOURCE-COMPUTER. IBM-370.                                        PGMT08
000080 OBJECT-COMPUTER. IBM-370.                                        PGMT08
000090 SPECIAL-NAMES.                                                   PGMT08
000100      C01 IS SAUTP                                                PGMT08
000110      CSP IS SAUT0                                                PGMT08
000120      DECIMAL-POINT IS COMMA.                                     PGMT08
000130 INPUT-OUTPUT SECTION.                                            PGMT08
000140 FILE-CONTROL.                                                    PGMT08
000150      SELECT     EX-FICHIER    ASSIGN    UT-S-DDEX.               PGMT08
000160      SELECT     XA-FICHIER    ASSIGN    DA-I-DDXA.               PGMT08
000170 DATA DIVISION.                                                   PGMT08
000180 FILE SECTION.                                                    PGMT08
000190 FD                 EX-FICHIER                                    PGMT08
000200      BLOCK              00000 RECORDS                            PGMT08
000210      DATA RECORD                                                 PGMT08
000220                    EX00                                          PGMT08
000230           LABEL RECORD STANDARD.                                 PGMT08
000240 01               EX00.                                           PGMT08
000250   10             FILLER        PICTURE X(133).                   PGMT08
000260 FD                 XA-FICHIER                                    PGMT08
000270      BLOCK              00000 RECORDS                            PGMT08
000280      DATA RECORD                                                 PGMT08
000290                    XA00                                          PGMT08
000300           LABEL RECORD STANDARD.                                 PGMT08
000310 01               XA00.                                           PGMT08
000320   10             XA00-MAT-ST   PICTURE XX.                       PGMT08
000330   10             XA00-NOM-ST   PICTURE X(10).                    PGMT08
000340   10             XA00-NOT-ST   PICTURE 99V9.                     PGMT08
000350 WORKING-STORAGE SECTION.                                         PGMT08
000360 01               DEBUT-WSS.                                      PGMT08
000370   05             FILLER        PICTURE X(7) VALUE                PGMT08
000380                                'WORKING'.                        PGMT08
000390   05             IK            PICTURE X.                        PGMT08
000400 01               CONSTANTES-PAC.                                 PGMT08
000410   05             FILLER        PICTURE X(60) VALUE               PGMT08
000420     '0069 LBA23/07/98PGMT08TEST    16:38:56PGMT08  BVAP23/07/1998PGMT08
000430-    ''                                                           PGMT08
000440 01               PAC-CONSTANTES REDEFINES CONSTANTES-PAC.        PGMT08
000450   05             NUGNA         PICTURE X(5).                     PGMT08
000460   05             APPLI         PICTURE X(3).                     PGMT08
000470   05             DATGN         PICTURE X(8).                     PGMT08
000480   05             PROGR         PICTURE X(6).                     PGMT08
000490   05             CODUTI        PICTURE X(8).                     PGMT08
000500   05             TIMGN         PICTURE X(8).                     PGMT08
000510   05             PROGE         PICTURE X(8).                     PGMT08
000520   05             COBASE        PICTURE X(4).                     PGMT08
000530   05             DATGNC        PICTURE X(10).                    PGMT08
000540 01               DATCE.                                          PGMT08
000550   05             CENTUR        PICTURE XX VALUE                  PGMT08
000560                                '19'.                             PGMT08
000570   05             DATOR.                                          PGMT08
000580     10           DATOA         PICTURE XX.                       PGMT08
000590     10           DATOM         PICTURE XX.                       PGMT08
000600     10           DATOJ         PICTURE XX.                       PGMT08
000610 01               VARIABLES-CONDITIONNELLES.                      PGMT08
000620   05             FT.                                             PGMT08
000630     10           XA-FT         PICTURE X VALUE                   PGMT08
000640                                '0'.                              PGMT08
000650 01               INDICES       COMPUTATIONAL SYNC.               PGMT08
000660   05             J00           PICTURE S9(4) VALUE +1.           PGMT08
000670   05             J01           PICTURE S9(4) VALUE +1.           PGMT08
000680 01               COMPTEURS-FICHIERS COMPUTATIONAL-3.             PGMT08
000690   05             5-XA00-CPTENR PICTURE S9(9) VALUE ZERO.         PGMT08
000700 01               CAT-TAB.                                        PGMT08
000710   05             FILLER        PICTURE X(100) VALUE SPACES.      PGMT08
000720   05             FILLER        PICTURE X(100) VALUE SPACES.      PGMT08
000730 01               CAT-TAB-R     REDEFINES CAT-TAB.                PGMT08
000740   05             CAT           PICTURE XX OCCURS 0100.           PGMT08
000750 01               ST-TA.                                          PGMT08
000760   05             ST-ABS        PICTURE X VALUE SPACE.            PGMT08
000770   05             ST-T.                                           PGMT08
000780     07           ST-TT         OCCURS 40.                        PGMT08
000790       10         ST-ST         PICTURE XX.                       PGMT08
000800       10         ST-LI         PICTURE 99.                       PGMT08
000810       10         ST-SA         PICTURE 99.                       PGMT08
000820 01               CONTENU-DES-CATEGORIES.                         PGMT08
000830   05             TS-1-BB.                                        PGMT08
000840     10           ABS-1-BB      PICTURE X VALUE                   PGMT08
000850                                '*'.                              PGMT08
000860     10           FILLER        PICTURE X(42) VALUE               PGMT08
000870     '000101010201000301000401000501000601000501'.                PGMT08
000880     10           FILLER        PICTURE X(06) VALUE               PGMT08
000890     '000401'.                                                    PGMT08
000900   05             TS-1-CC.                                        PGMT08
000910     10           ABS-1-CC      PICTURE X VALUE                   PGMT08
000920                                ' '.                              PGMT08
000930     10           FILLER        PICTURE X(18) VALUE               PGMT08
000940     '000501020801000501'.                                        PGMT08
000950   05             TS-1-DD.                                        PGMT08
000960     10           ABS-1-DD      PICTURE X VALUE                   PGMT08
000970                                ' '.                              PGMT08
000980     10           FILLER        PICTURE X(06) VALUE               PGMT08
000990     '000401'.                                                    PGMT08
001000 01               TAILLES-DES-CATEGORIES COMPUTATIONAL-3.         PGMT08
001010   05             1-BB-NL       PICTURE S99 VALUE +07.            PGMT08
001020   05             1-CC-NL       PICTURE S99 VALUE +03.            PGMT08
001030   05             1-DD-NL       PICTURE S99 VALUE +01.            PGMT08
001040 01               COMPTEURS-ET-VARIABLES-EDITION.                 PGMT08
001050   05             COMPTEURS     COMPUTATIONAL-3.                  PGMT08
001060     10           5-EX00-1CLM   PICTURE S999 VALUE +60.           PGMT08
001070     10           5-EX00-1CE    PICTURE S9(9) VALUE ZERO.         PGMT08
001080     10           5-EX00-1CL    PICTURE S999 VALUE +60.           PGMT08
001090     10           5-EX00-1CL1   PICTURE S999 VALUE +60.           PGMT08
001100     10           5-EX00-1CP    PICTURE S9(7) VALUE ZERO.         PGMT08
001110   05             5-EX00-1DP    PICTURE X VALUE                   PGMT08
001120                                '1'.                              PGMT08
001130   05             ST-SLS.                                         PGMT08
001140     10           STX           PICTURE XX.                       PGMT08
001150     10           ST9           REDEFINES STX PICTURE 99.         PGMT08
001160     10           J02           PICTURE 99.                       PGMT08
001170     10           SAUT          PICTURE 99.                       PGMT08
001180   05             CATX          PICTURE XX VALUE SPACE.           PGMT08
001190 01               LIBELLES.                                       PGMT08
001200   05             1-LIB.                                          PGMT08
001210     10           1-LIB01.                                        PGMT08
001220       15         FILLER        PICTURE X(44) VALUE               PGMT08
001230     '     RESULTATS EXAMENS                      '.              PGMT08
001240       15         FILLER        PICTURE X(44) VALUE               PGMT08
001250     '                                            '.              PGMT08
001260       15         FILLER        PICTURE X(44) VALUE               PGMT08
001270     '                                            '.              PGMT08
001280     10           1-LIB02.                                        PGMT08
001290       15         FILLER        PICTURE X(44) VALUE               PGMT08
001300     '     PAGE : 0001                            '.              PGMT08
001310       15         FILLER        PICTURE X(44) VALUE               PGMT08
001320     '                                            '.              PGMT08
001330       15         FILLER        PICTURE X(44) VALUE               PGMT08
001340     '                                            '.              PGMT08
001350     10           1-LIB03.                                        PGMT08
001360       15         FILLER        PICTURE X(44) VALUE               PGMT08
001370     '                                            '.              PGMT08
001380       15         FILLER        PICTURE X(44) VALUE               PGMT08
001390     '                                            '.              PGMT08
001400       15         FILLER        PICTURE X(44) VALUE               PGMT08
001410     '                                            '.              PGMT08
001420     10           1-LIB04.                                        PGMT08
001430       15         FILLER        PICTURE X(44) VALUE               PGMT08
001440     '    ---------------------------------       '.              PGMT08
001450       15         FILLER        PICTURE X(44) VALUE               PGMT08
001460     '                                            '.              PGMT08
001470       15         FILLER        PICTURE X(44) VALUE               PGMT08
001480     '                                            '.              PGMT08
001490     10           1-LIB05.                                        PGMT08
001500       15         FILLER        PICTURE X(44) VALUE               PGMT08
001510     '    I           I            I      I       '.              PGMT08
001520       15         FILLER        PICTURE X(44) VALUE               PGMT08
001530     '                                            '.              PGMT08
001540       15         FILLER        PICTURE X(44) VALUE               PGMT08
001550     '                                            '.              PGMT08
001560     10           1-LIB06.                                        PGMT08
001570       15         FILLER        PICTURE X(44) VALUE               PGMT08
001580     '    I MATRICULE I    NOM     I NOTE I       '.              PGMT08
001590       15         FILLER        PICTURE X(44) VALUE               PGMT08
001600     '                                            '.              PGMT08
001610       15         FILLER        PICTURE X(44) VALUE               PGMT08
001620     '                                            '.              PGMT08
001630   05             1-LIB-R       REDEFINES 1-LIB.                  PGMT08
001640     10           1-LI00-1      OCCURS 006.                       PGMT08
001650       15         FILLER        PICTURE X(00132).                 PGMT08
001660 01               6-EX00.                                         PGMT08
001670   05             6-EX00-1.                                       PGMT08
001680     10           6-EX100-SAUT  PICTURE X.                        PGMT08
001690     10           6-EX100       PICTURE X(132).                   PGMT08
001700     10           6-EX101       REDEFINES 6-EX100.                PGMT08
001710       15         FILLER        PICTURE X(012).                   PGMT08
001720       15         6-EX101-XPAGE PICTURE ZZZ9.                     PGMT08
001730       15         FILLER        PICTURE X(116).                   PGMT08
001740     10           6-EX102       REDEFINES 6-EX100.                PGMT08
001750       15         FILLER        PICTURE X(009).                   PGMT08
001760       15         6-EX102-MAT-ST PICTURE XX.                      PGMT08
001770       15         FILLER        PICTURE X(008).                   PGMT08
001780       15         6-EX102-NOM-ST PICTURE X(10).                   PGMT08
001790       15         FILLER        PICTURE X(002).                   PGMT08
001800       15         6-EX102-NOT-ST PICTURE Z9,9.                    PGMT08
001810       15         FILLER        PICTURE X(097).                   PGMT08
001820 PROCEDURE DIVISION.                                              PGMT08
001830 N01.                                                             PGMT08
001840           NOTE *************************************.            PGMT08
001850                *                                   *             PGMT08
001860                *INITIALISATIONS                    *             PGMT08
001870                *                                   *             PGMT08
001880                *************************************.            PGMT08
001890 F01.                                                             PGMT08
001900     EXIT.                                                        PGMT08
001910 N01EX.                                                           PGMT08
001920           NOTE *INITIALISATION FICHIER  EX-FICHIER *.            PGMT08
001930 F01EX.                                                           PGMT08
001940     OPEN OUTPUT EX-FICHIER.                                      PGMT08
001950 F01EX-FN.                                                        PGMT08
001960     EXIT.                                                        PGMT08
001970 N01XA.                                                           PGMT08
001980           NOTE *INITIALISATION FICHIER  XA-FICHIER *.            PGMT08
001990 F01XA.                                                           PGMT08
002000     OPEN INPUT XA-FICHIER.                                       PGMT08
002010 F01XA-FN.                                                        PGMT08
002020     EXIT.                                                        PGMT08
002030 F01-FN.                                                          PGMT08
002040     EXIT.                                                        PGMT08
002050*          NOTE *  DEBUT ITERATION DU PROGRAMME     *.            PGMT08
002060 F05.                                                             PGMT08
002070     EXIT.                                                        PGMT08
002080 N05.                                                             PGMT08
002090           NOTE *************************************.            PGMT08
002100                *                                   *             PGMT08
002110                *LECTURE FICHIERS ACCES SEQ. SANS DE*             PGMT08
002120                *                                   *             PGMT08
002130                *************************************.            PGMT08
002140 N05XA.                                                           PGMT08
002150           NOTE *LECTURE FICHIER         XA  SANS DE*.            PGMT08
002160 F05XA.                                                           PGMT08
002170     IF      XA-FT  =  '0'                                        PGMT08
002180         NEXT SENTENCE                                            PGMT08
002190     ELSE                                                         PGMT08
002200         GO TO F05XA-FN.                                          PGMT08
002210 F05XA-10.                                                        PGMT08
002220     READ XA-FICHIER AT END                                       PGMT08
002230         MOVE 1 TO XA-FT                                          PGMT08
002240         GO TO F05XA-FN.                                          PGMT08
002250     ADD 1 TO 5-XA00-CPTENR.                                      PGMT08
002260 F05XA-FN.                                                        PGMT08
002270     EXIT.                                                        PGMT08
002280 F05-FN.                                                          PGMT08
002290     EXIT.                                                        PGMT08
002300 N20.                                                             PGMT08
002310           NOTE *************************************.            PGMT08
002320                *                                   *             PGMT08
002330                *FIN DE TRAITEMENT                  *             PGMT08
002340                *                                   *             PGMT08
002350                *************************************.            PGMT08
002360 F20.                                                             PGMT08
002370     IF      FT  =  ALL '1'                                       PGMT08
002380         NEXT SENTENCE                                            PGMT08
002390     ELSE                                                         PGMT08
002400         GO TO F20-FN.                                            PGMT08
002410 F20EX.                                                           PGMT08
002420     CLOSE EX-FICHIER.                                            PGMT08
002430 F20EX-FN.                                                        PGMT08
002440     EXIT.                                                        PGMT08
002450 F20XA.                                                           PGMT08
002460     CLOSE XA-FICHIER.                                            PGMT08
002470 F20XA-FN.                                                        PGMT08
002480     EXIT.                                                        PGMT08
002490 F2099. STOP RUN.                                                 PGMT08
002500 F2099-FN.                                                        PGMT08
002510     EXIT.                                                        PGMT08
002520 F20-FN.                                                          PGMT08
002530     EXIT.                                                        PGMT08
002540 N81.                                                             PGMT08
002550           NOTE *************************************.            PGMT08
002560                *                                   *             PGMT08
002570                *   EDITION  ETAT     1             *             PGMT08
002580                *                                   *             PGMT08
002590                *************************************.            PGMT08
002600 F81.                                                             PGMT08
002610     EXIT.                                                        PGMT08
002620 N81BB.                                                           PGMT08
002630           NOTE *  CHARGEMENT CATEGORIE    BB       *.            PGMT08
002640 F81BB.                                                           PGMT08
002650     IF      5-XA00-1CL NOT  <  5-XA00-1CLM                       PGMT08
002660         MOVE 01 TO 5-EX00-1CL                                    PGMT08
002670         ADD 1-BB-NL TO 5-EX00-1CL                                PGMT08
002680         MOVE 'BB' TO CAT (J00) ADD 1 TO J00.                     PGMT08
002690 F81BB-FN.                                                        PGMT08
002700     EXIT.                                                        PGMT08
002710 N81CC.                                                           PGMT08
002720           NOTE *  CHARGEMENT CATEGORIE    CC       *.            PGMT08
002730 F81CC.                                                           PGMT08
002740     ADD 1-CC-NL TO 5-EX00-1CL                                    PGMT08
002750     MOVE 'CC' TO CAT (J00) ADD 1 TO J00.                         PGMT08
002760 F81CC-FN.                                                        PGMT08
002770     EXIT.                                                        PGMT08
002780 N81DD.                                                           PGMT08
002790           NOTE *  CHARGEMENT CATEGORIE    DD       *.            PGMT08
002800 F81DD.                                                           PGMT08
002810     IF      5-XA00-1CL NOT  <  5-XA00-1CLM                       PGMT08
002820         ADD 1-DD-NL TO 5-EX00-1CL                                PGMT08
002830         MOVE 'DD' TO CAT (J00) ADD 1 TO J00.                     PGMT08
002840 F81DD-FN.                                                        PGMT08
002850     EXIT.                                                        PGMT08
002860 F81ZZ.                                                           PGMT08
002870     MOVE 1 TO J00.                                               PGMT08
002880 F81ZZ-005.                                                       PGMT08
002890     MOVE CAT (J00) TO CATX.                                      PGMT08
002900     IF      CATX  =  '  '                                        PGMT08
002910         MOVE 1 TO J00                                            PGMT08
002920         MOVE SPACE TO CAT-TAB                                    PGMT08
002930         GO TO F8199-FN.                                          PGMT08
002940     MOVE 0 TO J01.                                               PGMT08
002950     IF      CATX  =  'BB'                                        PGMT08
002960         MOVE TS-1-BB TO ST-TA                                    PGMT08
002970         GO TO F81ZZ-009.                                         PGMT08
002980     IF      CATX  =  'CC'                                        PGMT08
002990         MOVE TS-1-CC TO ST-TA                                    PGMT08
003000         GO TO F81ZZ-009.                                         PGMT08
003010     IF      CATX  =  'DD'                                        PGMT08
003020         MOVE TS-1-DD TO ST-TA                                    PGMT08
003030         GO TO F81ZZ-009.                                         PGMT08
003040 F81ZZ-009.                                                       PGMT08
003050     ADD 1 TO J01.                                                PGMT08
003060 F81ZZ-010.                                                       PGMT08
003070     MOVE ST-TT (J01) TO ST-SLS.                                  PGMT08
003080     IF      ST-SLS  =  SPACE                                     PGMT08
003090         ADD 1 TO J00                                             PGMT08
003100         GO TO F81ZZ-005.                                         PGMT08
003110     IF      J02  =                                               PGMT08
003120     '00' MOVE SPACE TO 6-EX100 ELSE                              PGMT08
003130         MOVE 1-LI00-1 (J02) TO 6-EX100.                          PGMT08
003140     IF      ST-ABS NOT  =                                        PGMT08
003150     ' ' AND SAUT = '01'                                          PGMT08
003160         ADD 1 TO 5-EX00-1CP.                                     PGMT08
003170 F81ZZ-FN.                                                        PGMT08
003180     EXIT.                                                        PGMT08
003190 N8100.                                                           PGMT08
003200           NOTE *    STRUCTURE 00  ETAT   1         *.            PGMT08
003210 F8100.                                                           PGMT08
003220     IF      STX  =                                               PGMT08
003230     '00'          GO TO F8199.                                   PGMT08
003240     GO TO F8101 F8102 DEPENDING ON ST9.                          PGMT08
003250 F8100-FN.                                                        PGMT08
003260     EXIT.                                                        PGMT08
003270 N8101.                                                           PGMT08
003280           NOTE *   EDITION  STRUCTURE   01         *.            PGMT08
003290 F8101.                                                           PGMT08
003300     MOVE 5-XA00-1CP TO 6-EX101-XPAGE.                            PGMT08
003310 F8101-99.                                                        PGMT08
003320     GO TO F8199.                                                 PGMT08
003330 F8101-FN.                                                        PGMT08
003340     EXIT.                                                        PGMT08
003350 N8102.                                                           PGMT08
003360           NOTE *   EDITION  STRUCTURE   02         *.            PGMT08
003370 F8102.                                                           PGMT08
003380     MOVE XA00-MAT-ST TO 6-EX102-MAT-ST.                          PGMT08
003390     MOVE XA00-NOM-ST TO 6-EX102-NOM-ST.                          PGMT08
003400     MOVE XA00-NOT-ST TO 6-EX102-NOT-ST.                          PGMT08
003410 F8102-99.                                                        PGMT08
003420     GO TO F8199.                                                 PGMT08
003430 F8102-FN.                                                        PGMT08
003440     EXIT.                                                        PGMT08
003450 N8199.                                                           PGMT08
003460           NOTE *   ECRITURE ETAT         1         *.            PGMT08
003470 F8199.                                                           PGMT08
003480     MOVE 6-EX00 TO EX00.                                         PGMT08
003490     IF      ST-ABS  =                                            PGMT08
003500     ' '        GO TO F8199-10.                                   PGMT08
003510     MOVE ' ' TO ST-ABS.                                          PGMT08
003520     IF      SAUT  =                                              PGMT08
003530     '01' MOVE 1    TO 5-EX00-1CL1                                PGMT08
003540         WRITE EX00 AFTER ADVANCING SAUTP                         PGMT08
003550             GO TO F8199-20.                                      PGMT08
003560     SUBTRACT 5-EX00-1CL1 FROM SAUT.                              PGMT08
003570 F8199-10.                                                        PGMT08
003580     IF      SAUT  =                                              PGMT08
003590     '00'                                                         PGMT08
003600         WRITE EX00 AFTER ADVANCING SAUT0                         PGMT08
003610     ELSE                                                         PGMT08
003620             WRITE EX00 AFTER ADVANCING SAUT                      PGMT08
003630             ADD SAUT TO 5-EX00-1CL1.                             PGMT08
003640 F8199-20.                                                        PGMT08
003650     ADD 1 TO 5-EX00-1CE.                                         PGMT08
003660     GO TO F81ZZ-009.                                             PGMT08
003670 F8199-FN.                                                        PGMT08
003680     EXIT.                                                        PGMT08
003690 F81-FN.                                                          PGMT08
003700     EXIT.                                                        PGMT08
003710 F9099-ITER-FN.                                                   PGMT08
003720     GO TO F05.                                                   PGMT08

```