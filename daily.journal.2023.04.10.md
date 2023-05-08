---
id: mm38p5ism6urc2xlw1x8ii0
title: '2023-04-10'
desc: ''
updated: 1681122654391
created: 1681114904174
traitIds:
  - journalNote
---
Bonjour et bienvenue pour la présentation du projet 12 d'Openclassrooms. Cette présentation sera structurée en trois parties. Dans la première partie, je vais rappeler le contexte et les objectifs du projet. Ensuite, je vais vous présenter le site qui a été réalisé. Enfin, dans la dernière partie, je vous montrerai mon code tout en expliquant mes choix.

### Contexte

SportSee est une startup spécialisée dans le coaching sportif. Dans le cadre de son développement, SportSee a décidé de lancer une nouvelle version de la page profil de l'utilisateur. L'objectif de cette page est de permettre à l'utilisateur de suivre le nombre de sessions réalisées ainsi que le nombre de calories brûlées. J'etais en charge de réaliser cette page en se basant sur des maquettes et des User Stories, tout en respectant les critères techniques énoncés par le lead développeur.

### Site

### Code

## Layout
J'ai cree un composant layout qui gere la disposition generale de l'application. Son rendu est conditionnel. S'il il n y a pas d'utilisateur selectionner, c'est a dire si l'id est undefined, le composant affiche deux boutons qui permettent de sélectionner un utilisateur. Si un utilisateur est sélectionné, le composant affiche le composant "Header" ainsi que les données de l'utilisateur sélectionné. Donc j ai utilise Outlet pour afficher dynamiquement les pages de l'application en fonction de l'utilisateur selectionner. Donc si l'utilisateur choisi le premier bouton, ma variable id serai aura l'id correspondant a l'utilisateur selectionner.

## Home
Ce code représente la page d'accueil de l'application. Sur cette page j'utilise le hook useOutletContext, ce qui permet d'accéder au contexte fourni par le composant Outlet utilisé dans le composant Layout que je vous ai presente juste avant. Je recupere l'id de l'utilisateur selectionne puis effectue plusieurs appels à des fonctions qui récupèrent les données de l'utilisateur via des requêtes HTTP. Donc en l'occurence ici j'ai utilise axios, je vais vous presenter le code juste apres. L'affichage des differents graphiques est gere sur cette page. Les graphiques sont conditionnellement rendus en fonction de la disponibilité des données associées. J'ai utilise des expressions ternaire pour faire cela. Par exemple, le composant BarChart n'est rendu que si userActivity est défini et contient des données valides, dans le cas contraire le graphique n'est pas affiche.

## Api
Dans ce code, j'ai un ensemble de fonctions qui me permettent de faire mes appels http, j'utilise axios pour effectuer mes requetes GET aupres de l'api en fonction de l'id fourni en argument. Dans chacune de ces fonctions j'utilise le hook useEffect, ce qui me permet de faire mes appels api seulement une fois, lorsque mon composant est monte. Les donnees sont stockes dans un useState. Dans chacune des fonctions, je verifier que les donnes recuperes soient bien formate. Par exemple dans getUserAcitivty La condition vérifie si l'objet data et sa propriété sessions existent et si sessions est un tableau.

## Graphique

# BarChart
Pour l'integration des graphiques, j'ai utilise recharts.
Dans chacun des composants j'utilise egalement la propriete propTypes pour valider les données qui sont passées au composant. Dans cette exemple, la propriete doit renvoyer une chaine de caracteres et des nombres pour kg et calories

BarChart: le composant de base qui crée le graphique en barres.
Bar: un sous-composant de BarChart qui représente les barres individuelles dans le graphique.
XAxis: un sous-composant de BarChart qui représente l'axe horizontal du graphique.
YAxis: un sous-composant de BarChart qui représente l'axe vertical du graphique.
CartesianGrid: un sous-composant de BarChart qui crée une grille de repères pour le graphique.
Tooltip: un sous-composant de BarChart qui crée une bulle d'information au survol d'une barre du graphique.
Legend: un sous-composant de BarChart qui crée la légende du graphique.
ResponsiveContainer: pour rendre le graphique réactif et permettre son affichage correct sur différents écrans.

La fonction ActivityToolTip est une fonction qui retourne un élément JSX représentant le tooltip (infobulle) affiché lorsqu'on survole une barre du graphique avec la souris. Elle prend en entrée un objet props qui contient deux propriétés :
payload : un tableau de données qui contient les valeurs de la barre survolée.
active : un booléen qui indique si le tooltip est actuellement affiché ou non.
La fonction ActivityToolTip vérifie si active est vrai, auquel cas elle retourne un élément JSX contenant les informations de la barre survolée sous la forme d'un texte avec la valeur en kilogramme et en kilocalories. Sinon, elle retourne null, ce qui signifie que le tooltip n'est pas affiché.

# PerformanceChart
PolarAngleAxis : c'est un composant Recharts utilisé pour afficher les axes angulaires d'un graphique en radar. Il affiche des noms d'étiquettes dans des emplacements angulaires précis. Dans ce cas, il affiche le nom des types de performances.

PolarGrid : c'est un composant Recharts qui ajoute une grille radiale à un graphique en radar. Dans ce cas, il ajoute des lignes radiales de référence au fond du graphique.

Radar : c'est un composant Recharts utilisé pour dessiner la zone de données sur un graphique en radar. Dans ce cas, il représente les valeurs de performances dans le graphique.

RadarChart : c'est un composant Recharts utilisé pour dessiner un graphique en radar. Il contient des axes, des légendes et des données à dessiner.

# ScoreChart
PieChart est un composant qui permet de créer un graphique en camembert.

Pie est un composant qui permet de dessiner un secteur du graphique en camembert, et qui prend en entrée les données sous forme d'un tableau.

Cell est un composant qui représente une cellule dans le graphique en camembert.

Legend est un composant qui permet de créer une légende pour le graphique.

La JSDoc est un outil qui permet de documenter le code JavaScript en utilisant des annotations spéciales dans les commentaires.
- Facilite la compréhension du code
- Améliore la collaboration
- Maintenance du code

Proptypes permet de s'assurer que les données passées à un composant sont du type attendu