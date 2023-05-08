---
id: 8ybidecv7eurvmzmanfhibh
title: '2023-05-05'
desc: ''
updated: 1683548845890
created: 1683254110662
traitIds:
  - journalNote
---
# SOUTENANCE P13
Bonjour et bienvenue pour la présentation du projet 13 d'Openclassrooms. Cette présentation sera divisée en quatre parties distinctes. Tout d'abord, je vais rappeler le contexte et les objectifs du projet, pour ensuite passer à une démonstration de l'application, afin de vérifier que toutes les contraintes techniques & fonctionnelles ont été respectées. Ensuite, je vous présenterai le code que j'ai développé et expliquerai son fonctionnement. Enfin, je vous présenterai le fichier YAML pour les transactions.

## Contexte & Objectifs:
Le projet sur lequel j'ai travaillé consistait à développer une nouvelle application web pour la banque Argent Bank en utilisant React. Le principal objectif etait de developer le nouveau systeme d'authentification permettant aux utilisateurs de se connecter à leur profil, de gérer leur compte et de modifier certains éléments sur leur profil.

## Demo
Je vais maintenant vous faire une demo de l'application.

L'application doit respecter certaines contraites:
- L'utilisateur peut visiter la page d'accueil
- L'utilisateur peut se connecter au système
- L'utilisateur peut se déconnecter du système
- L'utilisateur ne peut voir les informations relatives à son propre profil qu'après s'être connecté avec succès
- L'utilisateur peut modifier le profil et conserver les données dans la base de données.

## Code

J'ai d'abord cree un fichier api.js pour pouvoir interagir avec mon backend. Donc j'ai 1 fonction qui envoient une requete posts pour gerer l'authentification de l'utilisateur et une fonction qui envoie une requete put afin que l'utilisateur puisse modifier certains element de son profil.

Ensuite j'ai cree un fichier authSlice.js qui me permet de gerer mon authentification en utilisant Redux Toolkit. J'ai d'abord cree une variable initialState avec les proprietes que mon slice gerera pour l'authentification.

Donc j'ai nomme mon slice 'login' ou j'ai cree plusieurs reducers, chacun de mes reducers ici est responsable d'une propriete specifique. Chaque reducers comportent 2 parametres (state qui defini l'etat initial de la propriete et un parametre action qui me permet de recuperer les donnees et de mettre a jour la propriete qui a ete modifier)

J'exporte ensuite mes differentes actions pour pouvoir les utiliser dans mes pages userLogin et userProfil.

J'exporte aussi mon reducer pour l'inclure dans mon store redux defini dans store.js

Dans la page qui gere le login de l'utilisateur j'ai importe les differentes actions de mon slice et la fonction userLogin qui correspond a mon appel api. Donc lorsque l'utilisateur soumet le formulaire de connexion la fonction handleloginformsubmit est appele. L'appel a ma requete api est effectue. Si la reponse de l.api est valide, le dispatch va ensuite renvoye les donnees aux differents reducers de mon fichier authSlice et l'utilisateur de son cote sera redirige vers sa page profil.

Si les variables storedEmail et storedPassword sont définies, le dispatch envoie ces données aux reducers correspondant aux propriétés email et password. Ca me permet de récupérer les données stockées localement et de les mettre à jour dans mon slice en utilisant dispatch.


Pour la page profil, j'importe egalement les differentes actions de mon slice et ma fonction qui gere l'appel a l'api.




## Fichier YAML