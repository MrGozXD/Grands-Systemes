## Exercice JCL 

![[Pasted image 20260706114930.png]]

### Modèle

``` jcl
//${NOMPG} JOB (ACCT#),'${NOM}',MSGCLASS=H,REGION=4M,
// CLASS=A,MSGLEVEL=(1,1),NOTIFY=&SYSUID,COND=(4,LT)
//*********************************
//* ETAPE 00 : CREATION DU FICHIER SEQUENTIEL AJC.EMPLOYE.SEQ
//***********************************
//STEP00 EXEC PGM=IEBGENER
//SYSPRINT DD SYSOUT=*
//SYSUT1 DD *
00114MOLITO PAULA 94000CRETEIL 1540000
01222HENRI MARC 75003PARIS 0950000
04592GIRAUD VALERIE 59000LILLE 0250000
05855DELORS JEAN 95200SARCELLES 0250000
06533LAURENT MELODIE 93000BOBIGNY 0180000
10058REVA MANU 69000LYON 0750050
11112RAMA FATY 93700DRANCY 0550050
45003TOURET DIANA 13001MARSEILLE 0789000
45895BAZEL MARIE 04330SENEZ 0350000
78996LOPEZ SANDRA 94120FONTENAY 0430000
87235ZEBULON HUGO 69100VILLEURBANNE 0290000
/*
//********************************************
//* ETAPE 01 : CREATION KSDS
//********************************************
//CREEKSDS EXEC PGM=IDCAMS
//SYSPRINT DD SYSOUT=*
//SYSIN DD *
	DEFINE CLUSTER (NAME(${FICHIER.KSDS}) -
	VOLUME(APIWK2) -
	TRK(1,1) -
	CISZ(4096) -
	FREESPACE(10,20) -
	KEYS(5,0) -
	RECORDSIZE(70, 70) -
	INDEXED) -
	DATA (NAME(${FICHIER.KSDS}.D)) -
	INDEX (NAME(${FICHIER.KSDS}.I))
/*
//********************************************
//* ETAPE 02 : TRI FICHIER SEQ
//********************************************
//STEP02 EXEC PGM=SORT
//SYSOUT DD SYSOUT=*
//SORTIN DD DSN=${FICHIERSEQ},DISP=SHR
//SORTOUT DD DSN=${FICHIERSEQ},DISP=SHR
//SYSIN DD *
  SORT FIELDS (1,5,CH,A)
/*
//*******************************************
//* ETAPE 03 : COPIE DANS KSDS
//*******************************************
//STEP03 EXEC PGM=IDCAMS
//SYSPRINT DD SYSOUT=*
//SYSIN DD *
	REPRO -
	INFILE(${FICHIERSEQ}) -
	OUTFILE(${FICHIER.KSDS})
/*
//*******************************************
//* ETAPE 04 : AFFICHAGE DU KSDS
//*******************************************
//STEP04 EXEC PGM=IDCAMS
//SYSPRINT DD SYSOUT=*
//SYSIN DD *
	PRINT -
	INFILE(${FICHIER.KSDS}) -
	CHARSET=EBCDIC
/*
```

## Exercice Cobol

### Fichier JCL : création du KSDS + compilation + exécution

```jcl
//${NOMPG} JOB (ACCT#),'${NOM}',MSGCLASS=H,REGION=4M, 
// CLASS=A,MSGLEVEL=(1,1),NOTIFY=&SYSUID,COND=(4,LT) /********************************* 
//* ETAPE DE CREATION DU KSDS
/********************************* 
//CREEKSDS EXEC PGM=IDCAMS 
//SYSPRINT DD SYSOUT=* 
//SYSIN DD * 
REPRO - 
INFILE(${FICHIERSEQ}) - 
OUTFILE(${FICHIER.KSDS}) 
/*
//***************************  
//* ETAPE DE COMPILATION  
//***************************  
//COMPIL EXEC IGYWCL,PARM.COBOL=(ADV,OBJECT,LIB,TEST,APOST)  
//SYSIN DD DSN=${USER}.SOURCE.COBOL(A4TP07),DISP=SHR  
//SYSLIB DD DSN=CEE.SCEESAMP,DISP=SHR  
//* DD DSN=${USER}.SOURCE.COPY,DISP=SHR  
//*************************** 
//* ETAPE DE LINKEDIT  
//***************************  
//LKED.SYSLMOD DD DSN=${USER}.COBOL.LOAD,DISP=(SHR,KEEP,KEEP)  
//LKED.SYSIN DD *  
NAME ${NOMPG}(R)  
/*
//***************************************************
//* ETAPE D'EXECUTION
//***************************************************
//E${NOMPG} EXEC PGM=${NOMPG}
//STEPLIB DD DSN=${USER}.COBOL.LOAD,DISP=SHR
//SYSOUT DD SYSOUT=*
//EMPKSDS DD DSN=${FICHIER.KSDS},DISP=SHR
//SYSIN DD *
60000
/*
```

### Fichier Cobol : ${NOMPG}.cbl 

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. ${NOMPG}.
       AUTHOR. ${NOM}.

       ENVIRONMENT DIVISION.
       INPUT-OUTPUT SECTION.
       FILE-CONTROL.
           SELECT EMPLOYE-FILE ASSIGN TO ${FICHIER.KSDS}
               ORGANIZATION IS INDEXED
               ACCESS MODE IS RANDOM
               RECORD KEY IS CODE-EMP
               FILE STATUS IS WS-FS.

       DATA DIVISION.
       FILE SECTION.
       FD  EMPLOYE-FILE.
       01  EMP-RECORD.
           05 CODE-EMP        PIC X(5).
           05 NOM-EMP         PIC X(15).
           05 PREN-EMP        PIC X(15).
           05 CP-EMP          PIC X(5).
           05 VILLE-EMP       PIC X(20).
           05 SALAIRE-EMP     PIC 9(7)V99.
           05 FILLER          PIC X(3).

       WORKING-STORAGE SECTION.
       01  WS-FS             PIC XX.
           88 FS-SUCCESS      VALUE '00'.
           88 FS-NOTFOUND     VALUE '02'.
       01  WS-CLE            PIC X(5) VALUE SPACES.
       01  WS-SALAIRE-AFF    PIC ZZZZ9.99.

       PROCEDURE DIVISION.
           OPEN INPUT EMPLOYE-FILE.
           IF NOT FS-SUCCESS
               DISPLAY 'ERREUR OUVERTURE FICHIER: ' WS-FS
               STOP RUN
           END-IF.
		   ACCEPT WS-CLE
           MOVE WS-CLE TO CODE-EMP.
           READ EMPLOYE-FILE
               INVALID KEY
                   DISPLAY 'ENREGISTREMENT NON TROUVE POUR CLE: ' WS-CLE
                   CLOSE EMPLOYE-FILE
                   STOP RUN
           END-READ.

           IF FS-SUCCESS
               MOVE SALAIRE-EMP TO WS-SALAIRE-AFF
               DISPLAY 'PRENOM : ' PREN-EMP
               DISPLAY 'NOM    : ' NOM-EMP
               DISPLAY 'SALAIRE: ' WS-SALAIRE-AFF
           END-IF.

           CLOSE EMPLOYE-FILE.
           STOP RUN.
```