## Enoncé

AJCFRAME vend des produits provenant de différents pays. Elle reçoit régulièrement des fichiers avec les nouveautés. 

Le fichier transmis est organisé à la façon d’un fichier csv. Le séparateur utilisé est le point-virgule. La taille maximale d’un enregistrement est de 45 caractères.

Le fichier contenant les nouveaux produits se nomme PROJET.NEWPRODS.DATA. 

Le fichier est organisé de la façon suivante : 

  NOM | SYMBOLE | OBSERVATIONS | NUMERO DE PRODUIT | CODE-PROD | DESCRIPTION | DESC-PROD | PRIX | PU-PROD | DEVISE | DE-PROD | STOCK | ST-PROD |
 |-----|---------|---------------|-------------------|-----------|-------------|-----------|------|---------|--------|---------|-------|---------|
 |     |         |               |                   |           |             |           |      |         | EUR    | EURO    |       |         |
 |     |         |               |                   |           |             |           |      |         | USD    | DOLLAR US|       |         |
 |     |         |               |                   |           |             |           |      |         | CNY    | YUAN RENMINBI |       |         |



Voici son contenu : 

P10;USB FLASH DRIVE;15;EUR;100 
P11;HEADPHONES;30.5;USD;150 
P12;MICRO;25.75;CNY;50 
P13;TABLET;125.20;CNY;25 
P14;LAPTOP;899.99;USD;30 
P15;MOTHERBOARD;60;EUR;20 
P06;DESKTOP COMPUTER;350.55;USD;20 
P07;DOCKING STATION;200;EUR;10 
P18;NETWORK SWITCH;150.75;CNY;30 
P19;LAPTOP GAMER;900;EUR;10 
P20;SSD HARD DISK;152.50;CNY;10 
P21;USB DRIVE;DO;19.99;20 
P12;KEYBOARD;11.99;EUR;200 
P23;LENOVO THINKPAD X1 CARBON GEN 13;999.99;EUR;15 P24;IDEAPAD SLIM 3I GEN 9;799;USD;10 
P25;THINKPAD T16 GEN 3;499.95;EUR;1O 

Votre objectif sera de traiter ce fichier et d’insérer les données des nouveaux produits au sein de la base de données. (Vous en profiterez pour formater les descriptions en mettant une majuscule au début de chaque mot, les autres seront en minuscules) Attention, au sein de ce fichier, les prix sont indiqués avec la devise du pays qui fournit le produit. Par conséquent, il faudra ainsi prévoir de convertir les prix en dollars. Vous pourrez soit mettre les taux de conversion au sein d’un fichier, soit en SYSIN. A noter qu'il est probable que d’autres monnaies soient susceptibles d’être ajoutées ultérieurement. De plus, vous devrez vous assurer que les données à insérer en base sont bien cohérentes. Si des données ne sont pas conformes (doublon, format, …), vous générerez un rapport d'erreurs dans un fichier nommée PROJET.NEWPRODS.ERR. Au sein de ce fichier d'erreurs, vous mettrez d'une part l'enregistrement complet non conforme et d'autre part, la raison ce cette non-conformité.

## Résumé 

Insérer les nouveaux produits de PROJET.NEWPRODS.DATA dans la BDD et logger les erreurs dans PROJET.NEWPRODS.ERR. Les taux de conversion seront en SYSIN et le fichier PROJET.NEWPRODS.ERR sera créé à partir du JCL d'exécution du programme. 

## Choix faits

Un seul programme COBOL = G1P1PG1
Taux de conversion en SYSIN
Fichier d'erreur écrasé ou créé s'il n'existe pas à l'exécution du programme.

## Exécution

DCLGEN de Products


![[Pasted image 20260804165819.png]]

![[Pasted image 20260804165913.png]]

Ne pas utiliser de COMP-3 en SYSIN, passer par une variable intermédiaire.

Rates à ne pas mettre en SYSIN mais dans un KSDS

Mettre des rollback