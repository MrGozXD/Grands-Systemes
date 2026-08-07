A faire en dernier

## Enoncé

Vous aurez à générer une facture par commande passée. L'ensemble des commandes avec leurs informations est recensé dans la base de données. 

Etant donné que l’accès aux tables est plus consommateur que l’accès aux fichiers, vous ferez en sorte d’exporter les données vers un fichier. Ce fichier se nommera PROJET.EXTRACT.DATA. 

A partir du fichier PROJET.EXTRACT.DATA, précédemment généré, Vous générerez la création des factures. Toutes les factures seront enregistrées dans un fichier PROJET.FACTURES.DATA.


## Résumé 

Dans un premier temps, extraire les données de la base de données et les enregistrer dans un fichier PROJET.EXTRACT.DATA.

Dans un second temps, à partir de PROJET.EXTRACT.DATA, générer les factures et les enregistrer dans un fichier PROJET.FACTURES.DATA

## Choix faits

2 programmes COBOL
2 JCL de compilation, un pour chaque programme
1 JCL en charge de la création des fichiers PROJET.EXTRACT.DATA et PROJET.FACTURES.DATA et de l'exécution des programmes. Ce JCL sera aussi en charge des SYSIN pour le taux de TVA et le premier numéro de facture.