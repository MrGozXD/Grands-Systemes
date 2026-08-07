
## Enoncé

Programme qui calcule et exporte vers un fichier d'édition PROJET.STATS.DATA, le cumul des ventes par ville. Voici l'affichage attendu pour le cumul des ventes par ville 
******************************* * 
Nom Ville 1 : $ 999 999.99 *
* Nom Ville 2 : $ 999 999.99 * 
* … * 
* ******************************* 
* Total : $ 99 999 999.99 * *******************************



## Résumé 

Dans un premier temps, extraire les données utiles de la base de données et les enregistrer dans un fichier PROJET.VILLES.DATA.

Dans un second temps, à partir de PROJET.VILLES.DATA, calculer et exporter vers le fichier PROJETS.STATS.DATA, le cumul des ventes par ville.

## Choix faits

2 programmes COBOL :
- Celui d'extraction des données utiles fait à la main
- Celui du cumul des ventes fait avec Pacbase
2 JCL de compilation
1 JCL d'exécution des 2 programmes et de création des fichiers PROJET.VILLES.DATA et PROJETS.STATS.DATA