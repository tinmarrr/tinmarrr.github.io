---
layout: page
title:  Comment ca marche ?
subtitle:  Zoom sur les éléments techniques
---
L’outil créé par Razorfish s’appuie sur l’algorithme EcoIndex (outil open-source, développé par le collectif de développeurs GreenIT) pour mesurer l’empreinte environnementale des pages et sites web. 

## La mesure d'une page web

Cet outil attribue à chaque page web un score entre A à G, G étant le score le plus mauvais. Il a été élaboré afin de refléter certains paramètres techniques représentatifs de chaque partie des trois tiers d’une architecture web distribuée. 

![1.1](https://tinmarrr.github.io/photos/1.1.png)

Ainsi, dans l'Ecoindex, il a été choisi de représenter :
un terminal : par le nombre d’éléments du DOM (Document Object Model qui signifie « modèle d'objets de document » , C'est un ensemble d'objets ordonnés décrivant la structure de la page Web à afficher. Il s’agit de la succession d'éléments appelés balises HTML ou XML. Le navigateur internet parcourt donc tous les éléments du DOM un par un pour savoir quoi et comment afficher. GreenIT justifie le choix du DOM car il s’agit d’un élément nécessitant beaucoup de puissance sur le terminal (RAM, CPU) pour afficher la page web. Plus le DOM est petit et moins on risque de déclencher l’obsolescence d’un terminal vieillissant.
le réseau : par le poids de la page téléchargée des serveurs vers le terminal (exprimé en Ko transférés en download) ; GreenIT justifie le choix du poids de la page car cette donnée témoigne de la contribution (ou non) de la page à l’engorgement du réseau.
les serveurs : par le nombre de requêtes HTTP entre le terminal et les serveurs. Le nombre de requêtes HTTP était, pour les auteurs de l’Ecoindex, le seul élément technique objectif qui témoigne, avec plus ou moins d'exactitude, de la quantité de serveurs physiques nécessaire pour servir le site.
 
Ces données chiffrées sont ensuite utilisées dans la formule de calcul ci-dessous :

![1.2](https://tinmarrr.github.io/photos/1.2.png)
 
Afin de prendre en compte la disparité dans les mesures des trois indicateurs, GreenIT a fait le choix de positionner la valeur constatée pour chaque critère dans un quantile, en tenant compte de sa proximité avec les bornes inférieures/supérieures du quantile. Les bornes de l’échelle de l’EcoIndex (0 à 100) ont été mises au point et validées en analysant la base HTTParchive (500 000 URLs).
En sortie du calcul, nous obtenons le score Ecoindex de la page mesurée. Celui-ci est représenté sous la forme d’un score sur 100 (plus il est élevé, plus le site est éco-conçu). Ce score est également communiqué sous la forme d’une note de A à G pour faciliter la compréhension, sous la forme suivant : 

![1.3](https://tinmarrr.github.io/photos/1.3.png)

## Vers la mesure de l’impact d’un site internet

Afin de mesurer la performance environnementale d’un site web, razorfish a fait le choix de développer en collaboration avec GreenIT un outil interne basé sur la technologie de l’Ecoindex.
Les équipes de razorfish vont alors sélectionner les 10 pages les plus consultées du site internet et les inscrire dans un fichier CSV, importé par la suite sur l’outil propriétaire. A la suite de ces mesures, l’outil va établir une moyenne des 10 pages consultées pour attribuer une note globale au site.

## Estimation de l’impact environnemental

L’outil développé par GreenIT propose également de visualiser l’impact environnemental d’une page web en estimant la consommation d’eau nécessaire et les émissions de gaz à effet de serre provoqués par l’affichage de la page.
Ces calculs reposent sur l'estimation moyenne de l'impact environnemental pour une page Web depuis un poste fixe avec une connexion ADSL, c'est-à-dire :
2 g équivalents CO² par rapport au réchauffement global;
et 3 cl d’eau bleue par rapport à  la tension sur l’eau.
 
![1.4](https://tinmarrr.github.io/photos/1.4.png)

La première formule calcule la consommation d'eau en centilitres. Elle commence par un facteur de base de 3, qui représente l'impact minimal en eau. La partie variable ajuste cette consommation en fonction de la performance environnementale. La multiplication par 100 puis la division finale par 100 permettent d'obtenir un résultat précis et normalisé.

La seconde formule suit une logique similaire pour les émissions de gaz à effet de serre, mais avec un facteur de base de 2. La partie variable module les émissions proportionnellement au score EcoIndex. Cette approche garantit une relation directe entre la performance environnementale et les émissions de CO2.

Le terme 50-EcoIndex joue un rôle central dans les deux formules :
À un score de 50, ce terme devient nul, donnant un impact moyen
Pour un score supérieur à 50, le terme devient négatif, réduisant l'impact
