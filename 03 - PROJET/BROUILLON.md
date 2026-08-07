coquille dans le fichier, taille maxime du fichie new prod est de 50, pas 45

copier api9.source.sql.bddorder
M.11.1

![[Pasted image 20260804125004.png]]

 TRAITEMENT-PROD

- MOVE ENR TO VARIABLE EDITION

- FORMATAGE-DESCRIPTION

- CONVERSION-USD

- INSERERDANSTABLE-NEWPROD

-   
    JCTP01

  

FORMATAGE-DESCRIPTION.

_*> Convertir la première lettre en majuscule_           

MOVE WS-PRODUCT-NAME(1:1) TO WS-FIRST-CHAR           INSPECT WS-FIRST-CHAR CONVERTING LOWER-CASE TO UPPER-CASE           

_*> Convertir le reste en minuscules_           

MOVE WS-PRODUCT-NdAME(2:29) TO WS-OTHER-CHARS           INSPECT WS-OTHER-CHARS CONVERTING UPPER-CASE TO LOWER-CASE           

_*> Reconstruire le nom du produit_           

MOVE WS-FIRST-CHAR TO WS-PRODUCT-NAME(1:1)           

MOVE WS-OTHER-CHARS TO WS-PRODUCT-NAME(2:29).

  

CORRECT-PRODUCT-NAME.           

  

  

CONVERSION-USD.

  

INSERERDANSTABLE-NEWPROds

![[Pasted image 20260805093945.png]]![[Pasted image 20260805094009.png]]

```
jetp04
```

![[Pasted image 20260805094726.png]]


![[Pasted image 20260805122810.png]]

