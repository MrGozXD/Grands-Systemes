## PGMT05

![[Pasted image 20260722151135.png]]
## JCL DE TRI 

```jcl
 ***************************** Top of Data ***************************
 //TRIOP  JOB (ACCT#),'YANNIS',MSGCLASS=H,REGION=4M,
 //    CLASS=A,MSGLEVEL=(1,1),NOTIFY=&SYSUID,TIME=(0,30),
 //    RESTART=*,COND=(8,LT)
 //*******************************
 //*  TRIE LE FICHIER OPERATIONS
 //*******************************
 //SORTCOMG EXEC PGM=SORT
 //SYSOUT   DD SYSOUT=*
 //SORTIN   DD DSN=API4.AJC.OPER.DATA,DISP=SHR
 //SORTOUT  DD DSN=API4.AJC.OPER.DATA,DISP=SHR
 //SYSIN    DD *
    SORT FIELDS=(1,5,CH,A,24,1,CH,A)
 /*
 *************************** Bottom of Data *************************
```
