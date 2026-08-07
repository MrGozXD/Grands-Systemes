Exercice 3 

![[Pasted image 20260605153022.png]]![[Pasted image 20260605153044.png]]
![[Pasted image 20260605153112.png]]

Exercice 4 (à la suite de A4E03)

![[Pasted image 20260605153150.png]]

Exercice 5

![[Pasted image 20260605155302.png]]

## Trouvez les erreurs

//JDEMO01  JOB (ACCT#),'STEEVEA',CLASS=ZA,MSGCLASS=H,MSGLEVEL=(1,5),
//                 NOTIFY=&SYSUID,REGION=4M,TIME=0,30,
//                 RESTART=*,TYPRUN=SCAN,COMMENTAIRES ....
//***************************************************************
//*              ETAPE 01                                       *
//***************************************************************
//JDEMO01ETAPE01  EXEC PROC=IEFR14,TIME=(,15) ETAPE01
//SYSOUT   DD SYSOUT=*
//***************************************************************
//*              ETAPE 02                                       *
//***************************************************************
//JDEMO01ETAPE01  EXEC PGM(PROC4),TIME=(,50)
//SYSOUT   DD SYSOUT=*



TROUVEZ LES ERREURS AU SEIN DE CE JCL

le paramètre CLASS n'accepte qu'un seul caractère
MSGLEVEL =(1,1)
manque les parenthèses à TIME -> TIME=(0,30)
Pas de paramètres pour RESTART -> RESTART = *nom d'étape*
COMMENTAIRES n'existe pas en JCL donc faut juste faire SCAN COMMENTAIRES
JDEMO01ETAPE01 -> Nom trop long, max 8 char
Sur la même ligne et pour le suivant TIME, la somme des valeurs doit être inférieure ou égale à celle dans le TIME de description du job
ligne 14, pareil nom trop long pour l'étape
ligne 14, PGM=PROC4

## 1

Créer le fichier APIX.AJC.FICTEST.DATA avec les attributs suivants : 3 pistes d’espace primaire et 2 d’espace secondaire ; longueur d’enregistrement 70, taille du bloc 700. L'enregistrement sera Fixe et Bloqué. Si l’étape se termine mal, le fichier sera tout de même catalogué.

![[Pasted image 20260605092017.png]]

## 2

Créer un JOB avec les trois steps suivants :
- Lister dans une SYSOUT, dans la classe de sortie le contenu du fichier APIX.AJC.EMPLOYE.DATA 
- Copier dans le fichier APIX.AJC.FICTEST.DATA le contenu du fichier APIX.AJC.EMPLOYE.DATA 
- Copier dans un nouveau fichier APIX.AJC.COMMANDE.DATA (de longueur d’enregistrement 50) le contenu des deux fichiers APIX.AJC.COMM.DATA et APIX.AJC.COMMD.DATA

![[Pasted image 20260605100420.png]]
![[Pasted image 20260605100600.png]]

Remarque : je peux faire une concaténation sans soucis car COMM et COMMD ont la même structure

## 3

![[Pasted image 20260605153022.png]]![[Pasted image 20260605153044.png]]
![[Pasted image 20260605153112.png]]
## 4

![[Pasted image 20260605153150.png]]
## 5

![[Pasted image 20260605165110.png]]

## 6

KSDS

![[Pasted image 20260608143945.png]]
![[Pasted image 20260608121906.png]]

ESDS

![[Pasted image 20260608123423.png]]![[Pasted image 20260608123453.png]]

RRDS

![[Pasted image 20260608124947.png]]
![[Pasted image 20260608125015.png]]

## 7

![[Pasted image 20260608143007.png]]
![[Pasted image 20260608143102.png]]![[Pasted image 20260608143125.png]]
![[Pasted image 20260608143148.png]]

## 8

//CRFICH    PROC CLASS=A,
//               DSN=APIX.AJC.DEFAULT,
//               SPACE1=1,
//               SPACE2=1
//ETAPE01   EXEC PGM=IEFBR14
//NEWFICH   DD DSN=&DSN,
//             DISP=(NEW,CATLG,DELETE),
//             SPACE=(TRK,(&SPACE1,&SPACE2)),
//             DCB=(RECFM=FB,LRECL=80,BLKSIZE=800),
//             CLASS=&CLASS
//          PEND

//TESTJOB   JOB (ACCT#),'VOTRE-NOM',CLASS=A,MSGCLASS=H,
//              NOTIFY=&SYSUID
//***************************************************************
//*     DEFINITION DE LA PROCEDURE INLINE                      *
//***************************************************************
//CRFICH    PROC CLASS=A,
//               DSN=API4.AJC.DEFAULT,
//               SPACE1=1,
//               SPACE2=1
//ETAPE01   EXEC PGM=IEFBR14
//NEWFICH   DD DSN=&DSN,
//             DISP=(NEW,CATLG,DELETE),
//             SPACE=(TRK,(&SPACE1,&SPACE2)),
//             DCB=(RECFM=FB,LRECL=80,BLKSIZE=800),
//             SYSOUT=&CLASS
//          PEND
//***************************************************************
//*     TEST 1 : APPEL AVEC VALEURS PAR DEFAUT DU SPACE        *
//***************************************************************
//APPEL1    EXEC PROC=CRFICH,
//               DSN=API4.AJC.TEST91,
//               CLASS=H
//***************************************************************
//*     TEST 2 : SUBSTITUTION DU SPACE                         *
//***************************************************************
//APPEL2    EXEC PROC=CRFICH,
//               DSN=API4.AJC.TEST92,
//               CLASS=H,
//               SPACE1=3,
//               SPACE2=2


//TRIJOB    JOB (ACCT#),'VOTRE-NOM',CLASS=A,MSGCLASS=H,
//              NOTIFY=&SYSUID
//***************************************************************
//*     DEFINITION DE LA PROCEDURE INLINE                      *
//***************************************************************
//TRIPROC   PROC DSNENTR=APIX.AJC.EMPLOYE.DATA,
//               DSNSORTI=APIX.AJC.EMPLOYE.TRI,
//               DSNFINAL=APIX.AJC.EMPLOYE.FINAL
//***************************************************************
//*     ETAPE RAZ : SUPPRESSION DES FICHIERS                   *
//***************************************************************
//RAZ       EXEC PGM=IEFBR14
//DEL1      DD DSN=&DSNSORTI,
//             DISP=(MOD,DELETE,DELETE),
//             SPACE=(TRK,0)
//DEL2      DD DSN=&DSNFINAL,
//             DISP=(MOD,DELETE,DELETE),
//             SPACE=(TRK,0)
//***************************************************************
//*     ETAPE 01 : TRI SUR LE NOM (COL 6, LG 15)              *
//***************************************************************
//ETAPE01   EXEC PGM=SORT
//SYSPRINT  DD SYSOUT=*
//SYSOUT    DD SYSOUT=*
//SORTIN    DD DSN=&DSNENTR,
//             DISP=SHR
//SORTOUT   DD DSN=&DSNSORTI,
//             DISP=(NEW,CATLG,DELETE),
//             SPACE=(TRK,(5,5)),
//             DCB=(RECFM=FB,LRECL=70,BLKSIZE=700)
//SYSIN     DD *
  SORT FIELDS=(6,15,CH,A)
/*
//***************************************************************
//*     ETAPE 02 : COPIE DU FICHIER TRIE VERS FICHIER FINAL   *
//***************************************************************
//ETAPE02   EXEC PGM=IEBGENER
//SYSPRINT  DD SYSOUT=*
//SYSIN     DD DUMMY
//SYSUT1    DD DSN=&DSNSORTI,
//             DISP=SHR
//SYSUT2    DD DSN=&DSNFINAL,
//             DISP=(NEW,CATLG,DELETE),
//             SPACE=(TRK,(5,5)),
//             DCB=(RECFM=FB,LRECL=70,BLKSIZE=700)
//          PEND
//***************************************************************
//*     APPEL DE LA PROCEDURE                                  *
//***************************************************************
//APPEL1    EXEC PROC=TRIPROC,
//               DSNENTR=APIX.AJC.EMPLOYE.DATA,
//               DSNSORTI=APIX.AJC.EMPLOYE.TRI,
//               DSNFINAL=APIX.AJC.EMPLOYE.FINAL
![[Pasted image 20260609143131.png]]![[Pasted image 20260609145415.png]]

![[Pasted image 20260609145946.png]]

//APPELPROC JOB (ACCT#),'VOTRE-NOM',CLASS=A,MSGCLASS=H,
//              NOTIFY=&SYSUID
//***************************************************************
//*     DECLARATION DES BIBLIOTHEQUES DE PROCEDURES            *
//***************************************************************
//          JCLLIB ORDER=(APIX.SOURCE.PROCS,APIX.SOURCE.MESPROCS)
//***************************************************************
//*     RAZ : SUPPRESSION DU FICHIER AVANT CREATION            *
//***************************************************************
//RAZ       EXEC PGM=IEFBR14
//DEL1      DD DSN=APIX.AJC.MONFICH,
//             DISP=(MOD,DELETE,DELETE),
//             SPACE=(TRK,0)
//***************************************************************
//*     APPEL P1 : CREATION DU FICHIER SEQUENTIEL              *
//***************************************************************
//APPEL1    EXEC PROC=P1,
//               DSN=APIX.AJC.MONFICH,
//               SPACE1=3,
//               SPACE2=2
//***************************************************************
//*     APPEL P2 : COPIE DU CONTENU DANS LE FICHIER CREE      *
//***************************************************************
//APPEL2    EXEC PROC=P2,
//               DSNENTR=APIX.AJC.EMPLOYE.DATA,
//               DSNSORTI=APIX.AJC.MONFICH

![[Pasted image 20260609155638.png]]