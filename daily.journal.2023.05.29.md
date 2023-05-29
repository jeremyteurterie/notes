---
id: 0hua0a9zfhl65fidc1osgef
title: '2023-05-29'
desc: ''
updated: 1685357625963
created: 1685354783671
traitIds:
  - journalNote
---
# SOUTENANCE P13

## Presentation:
Bonjour et bienvenue pour la présentation du projet 14 d'Openclassrooms. Cette présentation sera divisée en quatre parties distinctes. Tout d'abord, je vais rappeler le contexte et les objectifs du projet, pour ensuite passer à une démonstration de l'application, ce qui nous permettra de verifier que les fonctionnalites sont toujours presentes par rapport a la version jQuery. Ensuite, je vous présenterai le code que j'ai développé et expliquerai son fonctionnement. Enfin, je finirai la presentation par les tests lighthouse.

## Contexte & Objectifs:
Le projet a été initié dans le but de moderniser notre application existante et d'améliorer ses performances. Actuellement, HRNet est développé en utilisant jQuery, ce qui présente des limitations et des problèmes de maintenabilité. Mon objectif principal etait de migrer l'ensemble de l'application HRNet vers React, en convertissant également certains des plugins jQuery actuels en composants React. Cela nous permettra d'adopter une approche plus modulaire et de profiter des avantages offerts par React en termes de développement et de performances.


## Demo:

Live.

## Code:

`composant Home`

Pour la gestion de mon formulaire, j'ai utilise le hook useState que j'ai nomme formData et ou j'ai defini toutes les proprietes correspondant aux champs de mon formulaire. Donc lorsque l'utilisateur interagit avec les different champs du formulaire, la fonction handleInputChange est appele. Dans cette fonction `name` correspondant a la propriete du champ de formulaire avec lequel l'utilisateur interagit et `value` correspondant a la nouvelle valeur choisi. L etat local formData est ensuite mis a jour en temps reel.

Lorsque le formulaire est soumis, la fonction handleSubmit est appele. Donc cette fonction permet plusieurs choses. De faire apparaitre une modal de confirmation lorsque la soumission du formulaire est correct. J'apelle donc mon state en changeant la valeur de l'etat a true.

J'utilise dispatch pour declencher l'action setUsersData, ce qui me permet de mettre a jour mon state redux et de pouvoir par la suite extraire les donnes de l'utilisateur dans mon autre composant qui affiche la liste des employees.

`composant Employees`

## Test Lighthouse