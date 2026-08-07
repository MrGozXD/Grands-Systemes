
### Contexte
La société **AJCFRAME** reçoit **2 fichiers** recensant les ventes réalisées par des prestataires localisés en **Europe** et en **Asie** :
- `PROJET.VENTESEU.DATA` (Europe)
- `PROJET.VENTESAS.DATA` (Asie)

**Objectif** :
1. Importer ces ventes en base de données.
2. Augmenter le solde (balance) de chaque client en fonction des ventes.
3. Mettre à jour le stock de chaque produit en fonction des quantités vendues.

---

### Structure des fichiers
Les deux fichiers ont **la même structure** et sont **triés** selon :
- N° de Commande
- N° de Client
- N° d'employé
   Position (DE-A) | Longueur (LG) | Type | Nom | Observations |
 |-----------------|---------------|------|-----|--------------|
 | 1-3 | 3 | N | N° COMMANDE | Numéro unique de commande |
 | 4-13 | 10 | A | DATE COMMANDE | Format : JJ/MM/AAAA |
 | 14-15 | 2 | N | N° EMPLOYE | Identifiant de l'employé |
 | 16-19 | 4 | N | N° CLIENT | Identifiant du client |
 | 20-22 | 3 | A | N° PRODUIT | Référence du produit |
 | 23-27 | 5 | N | PRIX | Prix en USD (5 chiffres, dont 2 décimales) |
 | 28-29 | 2 | N | QUANTITE COMMANDEE | Quantité vendue |
 | 30-35 | 6 | A | RESERVE | Champ réservé |

**Contraintes** :
- Pas de doublon sur le **N° PRODUIT** dans une même commande.
- Un seul **employé**, une seule **date**, et un seul **client** par commande.
- **Stock suffisant** pour couvrir les ventes.

---

### Jeux de données

#### Fichier : PROJET.VENTESAS.DATA
 | N°COMM | DATE COMM | N°EMP | N°CLIENT | N°PROD | PRIX (USD) | QUANTITE COMMANDEE | RESERVE |
 |--------|-----------|-------|----------|--------|------------|----------------------|---------|
 | 501 | 15/10/2023 | 20 | 0003 | P02 | 1549.00 | 10 | |
 | 501 | 15/10/2023 | 20 | 0003 | P03 | 3075.00 | 02 | |
 | 502 | 02/11/2024 | 30 | 0002 | P05 | 5025.00 | 07 | |
 | 503 | 05/11/2025 | 50 | 0001 | P15 | 10.00 | 01 | |
 | 505 | 17/11/2025 | 40 | 0004 | P10 | 01.00 | 01 | |
 | 505 | 17/11/2025 | 40 | 0004 | P12 | 04.00 | 01 | |

#### Fichier : PROJET.VENTESEU.DATA
| N°COMM | DATE COMM | N°EMP | N°CLIENT | N°PROD | PRIX (USD) | QUANTITE COMMANDEE | RESERVE |
 |--------|-----------|-------|----------|--------|------------|----------------------|---------|
 | 500 | 10/10/2023 | 10 | 0004 | P01 | 2000.00 | 03 | |
 | 500 | 10/10/2023 | 10 | 0004 | P03 | 3575.00 | 02 | |
 | 500 | 10/10/2023 | 10 | 0004 | P04 | 1000.00 | 05 | |
 | 502 | 02/11/2024 | 30 | 0002 | P02 | 1500.00 | 03 | |
 | 502 | 02/11/2024 | 30 | 0002 | P03 | 3575.00 | 05 | |
 | 503 | 05/11/2025 | 50 | 0001 | P11 | 05.00 | 01 | |
 | 504 | 07/11/2025 | 40 | 0003 | P14 | 01.00 | 01 | |
 | 504 | 07/11/2025 | 40 | 0003 | P16 | 04.00 | 04 | |

| N°COMM | DATE COMM | N°EMP | N°CLIENT | N°PROD | PRIX (USD) | QUANTITE COMMANDEE | RESERVE |
| ------ | --------- | ----- | -------- | ------ | ---------- | ------------------ | ------- |
|        |           |       |          |        |            |                    |         |
 | 500 | 10/10/2023 | 10 | 0004 | P01 | 2000.00 | 03 | |
 | 500 | 10/10/2023 | 10 | 0004 | P03 | 3575.00 | 02 | |
 | 500 | 10/10/2023 | 10 | 0004 | P04 | 1000.00 | 05 | |
 | 502 | 02/11/2024 | 30 | 0002 | P02 | 1500.00 | 03 | 
 | 502 | 02/11/2024 | 30 | 0002 | P03 | 3575.00 | 05 | 
 | 503 | 05/11/2025 | 50 | 0001 | P11 | 05.00 | 01 | 
 | 504 | 07/11/2025 | 40 | 0003 | P14 | 01.00 | 01 | 
 | 504 | 07/11/2025 | 40 | 0003 | P16 | 04.00 | 04 | 

## Résumé 

Lire 2 fichiers triés (attention il y aura de la rupture de fichiers) et mettre à jour la base de données. Certains produits n'ont pas de prix renseigné dans les fichiers fournis, il faudra aller les récupérer en base de données.

## Choix faits

Un seul programme COBOL
En vue de l'énoncé, on n'aura pas d'erreurs à gérer.
Synchronisation à gérer