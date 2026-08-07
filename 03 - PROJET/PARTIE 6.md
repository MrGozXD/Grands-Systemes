
## Enoncé

AJCFRAME souhaite disposer d'un module autonome, développé en .NET, permettant de récupérer quotidiennement les taux de change des devises auprès d'une API REST publique, puis de les exporter vers plusieurs formats de fichiers, afin de pouvoir les partager avec d'autres systèmes ou partenaires ne travaillant pas dans le même format. 

Objectifs fonctionnels 
Récupérer, via une API REST de taux de change, les cours actuels des devises. 

Générer, à partir de ces données, trois fichiers d'export contenant les mêmes informations mais dans des formats différents : 
- Un fichier CSV 
- Un fichier JSON 
- Un fichier XML 

Chaque fichier doit contenir, pour chaque devise : son code, sa valeur (taux vers USD) et la date de cotation et sera nommé comme suit : Cotations-20250615.extension 

Le programme devra pouvoir être étendu à un nouveau format d'export (par exemple un format propriétaire demandé par un partenaire) sans modifier le code déjà écrit pour les formats existants. 

Le module devra impérativement mettre en pratique les concepts de la programmation orientée objet : 
• Encapsulation • Héritage • Polymorphisme

## Résumé 

Programme qui récupère les taux de change et génère des fichiers d'export

## Choix faits

Classe abstraite fichier
Une classe par format de fichier héritant de la classe abstraite