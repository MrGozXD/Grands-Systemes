h
❑ CREATION DU PROGRAMME 
❑ PXHELLO ===
CEDA DEF PROG(PXHELLO) GROUP(APIX) 
CEDA INS PROG(PXHELLO) GROUP(APIX) 

❑ CREATION DE LA TRANSACTION
❑ TXHE ==== 
CEDA DEF TRANS(TXHE) GROUP(APIX) PROG(PXHELLO) 
CEDA INS TRANS(TXHE) GROUP(APIX)

❑ MAP AXMS1 – JCAXMS1 ===
CEDA DEF MAPSET(AXMS1) GROUP(APIX) 
CEDA INS MAPSET(AXMS1) GROUP(APIX) 
CECI SEND MAP(AXMAP1) MAPSET(AXMS1)

CEDA DEF MAPSET(A4MS2) GROUP(API4) 
CEDA INS MAPSET(A4MS2) GROUP(API4) 
CECI SEND MAP(A4MAP2) MAPSET(A4MS2)

![[Pasted image 20260707121049.png]]

❑ CREATION DU PROGRAMME 
❑ PXD02 ===
CEDA DEF PROG(P4D02) GROUP(API4) 
CEDA INS PROG(P4D02) GROUP(API4) 

❑ CREATION DE LA TRANSACTION
❑ TXD2 ==== 
CEDA DEF TRANS(T4D2) GROUP(API4) PROG(P4D02) 
CEDA INS TRANS(T4D2) GROUP(API4)

![[Pasted image 20260708105035.png]]
![[Pasted image 20260708115525.png]]![[Pasted image 20260708145929.png]]

CEDA DEF MAPSET(A4MS3) GROUP(API4) 
CEDA INS MAPSET(A4MS3) GROUP(API4) 
CECI SEND MAP(A4MAP3) MAPSET(A4MS3)

CEDA DEF PROG(P4D03) GROUP(API4) 
CEDA INS PROG(P4D03) GROUP(API4) 

CEDA DEF TRANS(T4D3) GROUP(API4) PROG(P4D03) 
CEDA INS TRANS(T4D3) GROUP(API4)

![[Pasted image 20260709111026.png]]
![[Pasted image 20260709112313.png]]![[Pasted image 20260709112718.png]]
![[Pasted image 20260709114540.png]]![[Pasted image 20260709114555.png]]![[Pasted image 20260709114640.png]]
![[Pasted image 20260709114657.png]]
![[Pasted image 20260709121424.png]]![[Pasted image 20260709121619.png]]
![[Pasted image 20260709122416.png|485]]![[Pasted image 20260709141112.png]]
JA4MS1


![[Pasted image 20260709155045.png]]


MOVE NUM1I TO ED-NUM1
MOVE NUM2I TO ED-NUM2
MOVE OPTYI  TO ED-OPTY
MOVE ED-NUM1 TO NUM1O
MOVE ED-NUM2 TO NUM2O
MOVE ED-OPTY TO OPTYO


![[Pasted image 20260710161621.png]]

![[Pasted image 20260713115137.png]]
![[Pasted image 20260713161351.png]]![[Pasted image 20260713161408.png]]

![[Pasted image 20260715092220.png]]



'API4.SOURCE.CICS(P4E4)'
'API4.SOURCE.CICS(P4DRES)'

![[Pasted image 20260717120721.png]]
![[Pasted image 20260720121216.png]]
PPGMT01P30

![[Pasted image 20260717123420.png]]
![[Pasted image 20260720092021.png]]
![[Pasted image 20260720115348.png]]
![[Pasted image 20260720164719.png]]
![[Pasted image 20260720164912.png]]

21/07

![[Pasted image 20260721095314.png]]
![[Pasted image 20260721101306.png]]
![[Pasted image 20260721103212.png]]
![[Pasted image 20260721110043.png]]
![[Pasted image 20260721110748.png]]
![[Pasted image 20260721111132.png]]
![[Pasted image 20260721111922.png]]
![[Pasted image 20260721112724.png]]




![[Pasted image 20260721164135.png]]![[Pasted image 20260721164147.png]]
![[Pasted image 20260721164229.png|490]]
![[Pasted image 20260721164617.png]]
![[Pasted image 20260721164347.png]]

![[Pasted image 20260721164726.png]]
![[Pasted image 20260721164743.png]]![[Pasted image 20260721165311.png]]
![[Pasted image 20260722092116.png]]![[Pasted image 20260722092252.png]]
![[Pasted image 20260722112843.png]]
![[Pasted image 20260722112814.png]]
![[Pasted image 20260722113725.png]]
![[Pasted image 20260722115709.png]]
![[Pasted image 20260722120158.png]]


```jcl
**** Top of Data ***************************

 //TRIOP  JOB (ACCT#),'AURORE',MSGCLASS=H,REGION=4M,

 //    CLASS=A,MSGLEVEL=(1,1),NOTIFY=&SYSUID,TIME=(0,30),

 //    RESTART=*,COND=(8,LT)

 //***************************

 //*  TRIE LE FICHIER OPERATIONS

 //***************************

 //SORTCOMG EXEC PGM=SORT

 //SYSOUT   DD SYSOUT=*

 //SORTIN   DD DSN=API8.AJC.OPER.DATA,DISP=SHR

 //SORTOUT  DD DSN=API8.AJC.OPER.DATA,DISP=SHR

 //SYSIN    DD *

    SORT FIELDS=(1,5,CH,A,24,1,CH,A)

 /*

 **************************** Bottom of Data *************************
```

![[Pasted image 20260722150122.png]]

CORRECTION PGMT05

![[Pasted image 20260722153128.png]]
![[Pasted image 20260722154124.png]]

PGMT06
![[Pasted image 20260722161834.png]]![[Pasted image 20260722162631.png]]![[Pasted image 20260722163039.png]]
![[Pasted image 20260722163718.png]]


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace prjConsCours5
{
    enum MesErreurs
    {
        ErrLongueur,
        ErrCalcul,
        ErrFichier
    }
    class MyException:Exception
    {
        private MesErreurs err;
        private string message;

        public MyException(MesErreurs typeErr):base()
        {
            err = typeErr;
        }

        public override string Message
        {
            get
            {
                switch (err)
                {
                    case MesErreurs.ErrLongueur:
                        message = "Erreur de longueur !";
                        break;
                    case MesErreurs.ErrFichier:
                        message = "Problème Fichier !";
                        break;
                    case MesErreurs.ErrCalcul:
                        message = "Erreur de calcul !";
                        break;
                    default:
                        break;
                }
            }
        }
    }
}


![[Pasted image 20260730125045.png]]