---
id: zc01bs3j7c305r78itrtrtd
title: '2023-03-16'
desc: ''
updated: 1681115200735
created: 1678939836120
traitIds:
  - journalNote
---

## Soutenance P11:

# Sommaire:

1. Contexte & Objectifs
2. Site
3. Code

Bonjour et bienvenue à la présentation du projet 11 d'Openclassrooms. Cette présentation sera structurée en trois parties distinctes. Dans la première partie, je vais rappeler le contexte et les objectifs du projet. Ensuite, je vais vous présenter le site qui a été réalisé, cette étape me permettra de vou presenter la navigation entre les pages mais également de vérifier ensemble que les contraintes fonctionnelles ont été respectées. Enfin, dans la dernière partie, je vous montrerai mon code tout en expliquant mes choix.

1. Pour rappeler le contexte du projet, Kasa avait pour ambition de procéder à une refonte complète de son site web en utilisant la stack JavaScript React. Ma mission consistait donc à développer l'application en conformité avec les exigences techniques et fonctionnelles spécifiées.

2. Je vais à présent procéder à la présentation du site qui a été réalisé.
   Contraintes fonctionnelles:
   Pour le défilement des photos dans la galerie (composant Gallery):

   - Si l'utilisateur se trouve à la première image et qu'il clique sur "image précédente", la galerie affiche la dernière image.
   - Inversement, quand l'image affichée est la dernière de la galerie, si l'utilisateur clique sur "image suivante", la galerie affiche la première image.
   - S'il n'y a qu'une seule image, les boutons "suivant" et "précédent" ainsi que la numérotation n'apparaissent pas.
   - Collapse : Par défaut, les Collapse sont fermés à l'initialisation de la page.

3. Je vais à présent vous présenter l'architecture de mon projet. Tout d'abord, j'ai initialisé le projet en utilisant Create React App. Ensuite, j'ai créé un dossier "assets" où j'ai placé mon fichier JSON ainsi que les différentes images et logos utilisés pour le projet. J'ai organisé mes composants React dans un dossier "components" et les différentes pages du site dans un dossier "pages". J'ai également créé un dossier "hooks" où j'ai développé deux hooks. Le premier me permet de récupérer l'ensemble des données en important le fichier JSON et en retournant son contenu, tandis que le second me permet de récupérer les informations spécifiques d'une location à partir de son ID. Pour cela, j'utilise le hook useData qui contient toutes les données, puis j'utilise la méthode "find" pour trouver l'objet qui a l'ID correspondant à celui fourni en argument. Enfin, tout le CSS du site a été placé dans un dossier "styles" en utilisant les modules CSS.

```
const Cards = ({ data }) => {
  const cardsList = data.map((location) => {
    const { cover, title, id } = location;

    return (
      <NavLink to={`location/${id}`} key={id}>
        <div className={style.cardWrap}>
          <img className={style.cardImage} src={cover} alt={title} />
          <h2 className={style.cardTitle}>{title}</h2>
        </div>
      </NavLink>
    );
  });

  return <div className={style.cardContainer}>{cardsList}</div>;
};

```

Le composant Cards me permet d'afficher les differentes locations sous formes de cartes. J'ai passe un props a mon composant que j ai nomme data qui est un tableau d'objets qui representent les differentes locations. J'ai utilise la methode .map pour boucler sur chaque location du tableau et generer une carte pour chacun d'entre eux. Les cartes sont ensuite retourne dans une div cardContainer. La carte est enveloppe dans une navlink qui permet de naviguer sur une autre page avec les details de chaque location.

---

```
const Gallery = ({ imageArray, desc }) => {
  const [currentIndex, setCurrentIndex] = useState(0);
  const displayArrow = imageArray.length > 1;

  const getNextIndex = (currentIndex, arrayLength) => {
    return currentIndex < arrayLength - 1 ? currentIndex + 1 : 0;
  };
  const getPrevIndex = (currentIndex, arrayLength) => {
    return currentIndex > 0 ? currentIndex - 1 : arrayLength - 1;
  };

  const next = () =>
    setCurrentIndex((prevIndex) => getNextIndex(prevIndex, imageArray.length));
  const previous = () =>
    setCurrentIndex((prevIndex) => getPrevIndex(prevIndex, imageArray.length));

  return (
    <div className={style.galleryContainer}>
      <img src={imageArray[currentIndex]} alt={desc} />
      {displayArrow && (
        <>
          <div className={style.arrowContainer}>
            <LeftArrow onClick={previous} className={style.arrow} />
            <RightArrow onClick={next} className={style.arrow} />
          </div>
          <div className={style.indexContainer}>
            <span>{`${currentIndex + 1}/${imageArray.length}`}</span>
          </div>
        </>
      )}
    </div>
  );
};

```

Le composant Gallery affiche une image à partir d'un tableau d'images et permet à l'utilisateur de naviguer entre les images en cliquant sur des flèches. La propriété "displayArrow" est utilisée pour décider s'il faut afficher ou non les flèches. L'état "currentIndex" est utilisé pour suivre l'index de l'image actuellement affichée. Les fonctions "next" et "previous" sont appelées lorsque les flèches sont cliquées pour afficher l'image suivante ou précédente.

---

React permet de construire des interfaces utilisateur modulaires et réutilisables en utilisant des composants. Les composants vous permettent de découper l’interface utilisateur en éléments indépendants et réutilisables.

useState est une fonction de React qui permet de déclarer et de gérer un état à l'intérieur d'un composant fonctionnel. Elle prend en argument une valeur initiale et renvoie un tableau contenant deux éléments : la valeur courante de l'état et une fonction pour mettre à jour cette valeur. Cela permet de modifier dynamiquement le contenu d'un composant en réponse à des événements ou à des changements de données.

useParams permet d'extraire les paramètres de l'URL dans un composant fonctionnel.

useNavigate qui permet de naviguer dans une application React en passant l'URL en tant qu'argument.

useEffect est utilisé pour effectuer une action spécifique (récupérer des données correspondant à une location en fonction d'un ID donné) lors du montage initial du composant. Il permet d'exécuter du code lors du montage initial du composant.
