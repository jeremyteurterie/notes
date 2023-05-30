---
id: 0hua0a9zfhl65fidc1osgef
title: '2023-05-29'
desc: ''
updated: 1685439828337
created: 1685354783671
traitIds:
  - journalNote
---
# SOUTENANCE P14

## Presentation:
Bonjour et bienvenue pour la présentation du projet 14 d'Openclassrooms. Cette présentation sera divisée en quatre parties distinctes. Tout d'abord, je vais rappeler le contexte et les objectifs du projet, pour ensuite passer à une démonstration de l'application, ce qui nous permettra de verifier que les fonctionnalites sont toujours presentes par rapport a la version jQuery. Ensuite, je vous présenterai le code que j'ai développé et expliquerai son fonctionnement. Enfin, je finirai par vous presenter les tests lighthouse.

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

J'utilise Datatable de react-data-table-component.

Pour l'affichage des differents employees j'accede aux donnees de mon state redux en utilisant useSelector.

J'ai cree un tableau d'objet pour definir les differentes colonnes a afficher dans ma table.

Donc pour le filtrage des employees j'utilise un useState. ce useState est utilise pour stocker les données filtrées en fonction de ce qui a été saisi par l'utilisateur dans le champ de filtre. J'utilise la valeur employeeDatas pour definir l'etat initial de mon state, c'est recuperer a partir de mon store redux. Cela me permet de mettre a jour dynamiquement la liste des employees affiches en fonction de la recherche de l'utilisateur.

J'ai une fonction filterEmployees qui est appele lorsque l'événement onChange est déclenché sur le champ de recherche. Elle récupère la valeur saisie dans le champ de recherche à partir de event.target.value.

Ensuite, J'utilise la methode filter pour filtrer les données des employés (employeeDatas).

J'utilise egalement la methode some sur le tableau des valeurs pour verifier si l'une des valeurs contient la valeur saisie par l'utilisateur.

J'utilise ici la methode include pour faire en sorte que la recherche soit insensible a la casse.

Si au moins une des valeurs correspond a la valeur saisie, l'employee est inclus dans le tableau newData. J'apelle ensuite ma fonction setRecords pour definir le nouvel etat pour la variable records.

`store redux`

J'ai utilise la bibliotheque Redux persist pour mettre en place la persistance des données. J'ai d'abord cree un objet de configuration appele persisConfig, donc j'utilise ici le stockage local de mon navigateur.

J'ai ensuite utilise la fonction persistReducer pour combiner mon reducer avec la configuration de la persistance.

Donc ensuite ce nouveau reducer persistant je le passe du coup dans la configuration de mon store.

et pour finir je configure une variable persistor ou je passe en parametre mon store redux en utilisant la fonction persistStore. J'utilise ensuite cette fonction dans mon main.jsx

Le réducteur setUsersData est une fonction qui prend deux arguments : state et action. Il utilise la syntaxe de décomposition pour copier l'état actuel et ajouter les données de l'utilisateur fournies par action.payload à la propriété users. Il retourne un nouvel objet avec l'état mis à jour.

La ligne export const { setUsersData } = userSlice.actions; exporte l'action setUsersData générée automatiquement à partir du réducteur, ce qui permet de l'utiliser dans d'autres parties de l'application.

Enfin, la ligne export default userSlice.reducer; exporte le réducteur lui-même, qui sera utilisé pour combiner les réducteurs de toutes les tranches lors de la configuration du magasin Redux.




## Test Lighthouse

Donc les test lighthouse ont ete realiser en production. J'ai fait un npm build puis j'ai lance un serveur http local pour simuler un environnement de production.





En utilisant autoMergeLevel2, cela permet d'assurer une coherence entre l'etat persiste et l'etat actuel de l application.

Cela offre une expérience utilisateur fluide et continue, où les utilisateurs peuvent quitter votre application et y revenir ultérieurement tout en conservant leurs données et leurs préférences.

vous pouvez tester votre application web localement en simulant un environnement de production

J'ai utilise storybook, ca ma permis de developer et tester ma modal sans avoir a l'integrer dans une application complete.

J'ai egalement utilise rollup pour creer mon bundle final avant de le publier sur npm.


{modalOpen && <Modal trigger={modalOpen} setTrigger={setModalOpen} />} : Cela utilise une condition avec l'opérateur logique &&. Si modalOpen est true, le composant Modal sera rendu, sinon, il ne sera pas rendu.

<Modal trigger={modalOpen} setTrigger={setModalOpen} /> : Cela représente le composant Modal qui est rendu lorsque la condition est true. Les attributs trigger et setTrigger sont utilisés pour passer des valeurs à ce composant.

trigger={modalOpen} : Cela passe la valeur de modalOpen au composant Modal via la prop trigger. Cela permet au composant Modal de savoir si la fenêtre contextuelle doit être affichée ou masquée en fonction de la valeur de modalOpen.

setTrigger={setModalOpen} : Cela passe la fonction setModalOpen au composant Modal via la prop setTrigger. Cette fonction est utilisée par le composant Modal pour mettre à jour la valeur de modalOpen lorsque la fenêtre contextuelle est fermée.

En résumé, cette ligne de code affiche le composant Modal si modalOpen est true. Le composant Modal reçoit la valeur de modalOpen et la fonction setModalOpen pour gérer l'affichage de la fenêtre contextuelle et mettre à jour modalOpen lorsque la fenêtre contextuelle est fermée.