# Intro

## Quid Mainframe ?

Le Mainframe, aussi connu sous le nom d'ordinateur central, est un puissant et fiable type d'ordinateur utilisé par les entreprises et organisations pour exécuter des applications critiques et des traitements de données à grande échelle.

Il offre une gamme de service essentiels, notamment le stockage et le traitement de données volumineuses, la fourniture d'applications critiques, la gestion des transactions en temps réel et la sécurité des données.

C'est particulièrement adapté aux entreprises traitant de grandes quantités de données comme les banques, les bourses, les compagnies d'assurance, les télécommunications et les administrations publiques, en raison de sa fiabilité exceptionnelle qui permet des opérations critiques 24/7 sans interruption.

Le Mainframe offre un environnement stable et sécurisé, reconnu pour sa protection des données sensibles telles que financières ou personnelles contre les attaques informatiques.

Les premiers modèles étaient massifs mais les versions modernes sont beaucoup plus compactes. Les serveurs Mainframe intègrent divers périphériques de stockage avancés et des technologies de virtualisation pour une performance optimale.

## Architecture des Mainframes

Naissance de COBOL : 1959
Créé par Grace Hopper

Les Mainframes reposent sur une architecture de traitement centralisé, où un seul processeur principal gère toutes les opérations de traitement des données. Cette conception permet une évolutivité remarquable, avec la capacité d'ajouter des processeurs supplémentaires, de la mémoire et d'autres composants pour répondre aux besoins changeants des entreprises.

Les principales parties des mainframes comprennent : 
 - Le processeur central
 - Les unités de stockage
 - Les canaux de communication
 - Les périphériques

Cette infrastructure permet aux mainframes de fournir des performances élevées, une gestion fiable des données et un communication efficace au sein des environnements d'informatiques d'entreprise.

Les Mainframes utilisent divers OS pour gérer les ressources informatiques et exécuter des programmes. Voici quelques-uns des systèmes d'exploitation couramment utilisés : 

- z/OS : OS principal des mainframes, développé par IBM
- z/VM : Il s'agit d'un système d'exploitation de virtualisation
- z/VSE : Cet OS est dédié au traitement de transactions à grande échelle
- Linux sur z : Il s'agit d'une version de Linux open source conçue pour fonctionner sur les mainframes IBM

Ces OS spécialisés permettent aux mainframes de répondre aux exigences de performance, de sécurité et d'évolutivité des applications critiques des entreprises à grande échelle.

## Mainframe : Langages de programmation

Les mainframes prennent en charge plusieurs langages de programmation pour le développement d'applications : 
- COBOL
- Assembleur
- PL/I
- Java
- Python

Ces langages diversifiés offrent aux développeurs une gamme d'outils pour créer des applications adaptées aux besoins spécifiques 

## Mainframe : Avantages

Les mainframes offrent plusieurs avantages clés : 
- Puissance de traitement
- Fiabilité
- Sécurité
- Evolutivité

En résumée, les mainframes sont des systèmes informatiques fiables, sécurisés et puissants, idéaux pour les entreprises nécessitant un traitement rapide et sûr de volumes importants de données critiques.

## Mainframe : Inconvénients

Les inconvénients des mainframes sont les suivants : 
- Coûts
- Complexité
- Dépendance vis-à-vis des fournisseurs

Malgré ces inconvénients, les mainframes restent populaires pour de nombreuses organisations gérant des opérations commerciales et gouvernementales critiques. Ils évoluent pour répondre aux besoins changeants des entreprises, notamment en intégrant des fonctionnalités cloud et d'analyse en temps réel.

La décision d'utiliser un mainframe dépend des besoins spécifiques de l'organisation. Il est important de peser soigneusement les avantages et inconvénients pour déterminer si un mainframe est la meilleure option pour gérer les opérations informatiques critiques.

## TSO : Time Sharing Option

CE logiciel permet à de multiples utilisateurs à partir de terminaux éloignés d'accéder au système dans un environnement en temps partagé.

Il est possible à l'utilisateur d'effectuer les travaux suivants : 
- Se connecter au système avec Login/Mot de Passe
- Manipuler des ressources grâce à diverses commandes
- Définir et exécuter des travaux batch (décrit par un JCL)
- Définir et exécuter des travaux interactifs (CLIST ou procédures REXX)

Lorsqu'un utilisateur se connecte au Mainframe via TSO : 
- Une session TSO est créée
- Le système démarre un espace d'adressage dédié à cet utilisateur
- L'utilisateur peut exécuter des commandes TSO ou lancer l'interface ISPF.

Chaque session TSO est isolée, ce qui permet un vrai time-sharing (partage du temps machine entre plusieurs utilisateurs simultanés).

## ISPF : Interactive System Productivity Facility

ISPF est une application qui fonctionne au-dessus de TSO


PDS = Partitioned DataSet = un répertoire
Membre = fichier 