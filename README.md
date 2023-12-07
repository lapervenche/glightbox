# GLightbox

GLIGHTBOX est un pur javascript lightbox. Il peut afficher des images, des iframes, du contenu en ligne et des vidéos avec une lecture automatique en option pour YouTube, Vimeo et même des vidéos hébergées.

## Caractéristiques

- **Léger** - seulement 11KB Gzipped.
- **Rapide et Responsive** - fonctionne avec n'importe quelle taille d'écran.
- **Support multiples galeries** - Créer plusieurs galeries.
- **Responsive Images Support** - Laissez le navigateur utiliser l'image optimale pour la résolution de l'écran en cours.
- **Vidéo Support** - Youtube, Vimeo et vidéos embarquées avec autoplay (ou non)
- **Prise en charge de contenu en ligne** - afficher tout contenu en ligne.
- **Iframe support** - besoin d'intégrer une iframe? Pas de problème glightbox le propose!
- **Navigation au clavier** - esc, touches des flèches, onglet et entrée est tout ce dont vous avez besoin.
- **Navigation tactile** - événements tactiles mobiles sont du voyage.
- **Images zoomables** - zoommer et glisser sur les images sur mobile et sur ordinateur de bureau.
- **API** - contrôler la boîte à lumière avec les méthodes fournies
- **Skinable** - créez votre skin personnel ou modifiez les animations avec quelques modifications mineures de css

## Démo en direct

Vous pouvez vérifier la démo en direct [right here](https://biati-digital.github.io/glightbox/)

## Utilisation

```bash
$ npm install glightbox
# OR
$ yarn add glightbox
# OR
$ bower install glightbox
```

```javascript
// Using ESM specification
import '/path/to/glightbox.js';

// Using a bundler like webpack
import GLightbox from 'glightbox';
```

Ou télécharger et lier manuellement `glightbox.min.js` dans votre code HTML:

```html
<link rel="stylesheet" href="dist/css/glightbox.css" />
<script src="dist/js/glightbox.min.js"></script>

<!-- UTILISER UN CDN -->

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/glightbox/dist/css/glightbox.min.css" />
<script src="https://cdn.jsdelivr.net/gh/mcstudios/glightbox/dist/js/glightbox.min.js"></script>

<script type="text/javascript">
  const lightbox = GLightbox({ ...options });
</script>

<!-- Utilisation des modules ES -->

<script type="module">
  import 'https://cdn.jsdelivr.net/gh/mcstudios/glightbox/dist/js/glightbox.min.js';

  const lightbox = GLightbox({ ...options });
</script>
```

## Examples

```html
<!-- Simple image -->
<a href="large.jpg" class="glightbox">
  <img src="small.jpg" alt="image" />
</a>

<!-- Vidéo -->
<a href="https://vimeo.com/115041822" class="glightbox2">
  <img src="small.jpg" alt="image" />
</a>

<!-- Galerie -->
<a href="large.jpg" class="glightbox3" data-gallery="gallery1">
  <img src="small.jpg" alt="image" />
</a>
<a href="video.mp4" class="glightbox3" data-gallery="gallery1">
  <img src="small.jpg" alt="image" />
</a>

<!-- Simple Description -->
<a href="large.jpg" class="glightbox4" data-glightbox="title: My title; description: this is the slide description">
  <img src="small.jpg" alt="image" />
</a>

<!-- Description Avancée -->
<a href="large.jpg" class="glightbox5" data-glightbox="title: My title; description: .custom-desc1">
  <img src="small.jpg" alt="image" />
</a>

<div class="glightbox-desc custom-desc1">
  <p>The content of this div will be used as the slide description</p>
  <p>You can add links and any HTML you want</p>
</div>

<!-- URL sans extension -->
<a href="https://picsum.photos/1200/800" data-glightbox="type: image">
  <img src="small.jpg" alt="image" />
</a>
<!-- Ou en utilisant plusieurs attributs de données -->
<a href="https://picsum.photos/1200/800" data-type="image">
  <img src="small.jpg" alt="image" />
</a>

<!-- Utilisation d'images réactives: spécifiez les tailles et SRCSET via des attributs de données de la même manière
que vous le feriez avec la balise IMG.
     Voir:
https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images
 -->
<a href="deafult.jpg" class="glightbox6" data-title="Responsive example"
data-description="Your browser will choose the optimal image for the resolution"
data-sizes="(max-width: 600px) 480px, 800px"
data-srcset="img480.jpg 480w, img800.jpg 800w">
  <img src="small.jpg" alt="image" />
</a>
```

## Options des diapositives

You can specify some options to each individual slide, the available options are:

- title
- alt
- description
- descPosition
- type
- effect
- width
- height
- zoomable
- draggable

```html
<!-- Configuration d'une ligne -->
<a href="large.jpg" data-glightbox="title: Your title; description: description here; descPosition: left; type: image; effect: fade; width: 900px; height: auto; zoomable: true; draggable: true;"></a>

<!-- Plusieurs attributs de données / Vous pouvez utiliser les options comme attributs de données séparés -->
<a
  href="large.jpg"
  data-title="My title"
  data-description="description here"
  data-desc-position="right"
  data-type="image"
  data-effect="fade"
  data-width="900px"
  data-height="auto"
  data-zoomable="true"
  data-draggable="true"
></a>
```

## Lightbox Options

Exemple d'utilisation des options.

```javascript
const lightbox = GLightbox({
    touchNavigation: true,
    loop: true,
    autoplayVideos: true
});

// Au lieu d'utiliser un sélecteur, définissez les éléments de la galerie
const myGallery = GLightbox({
    elements: [
        {
            'href': 'https://picsum.photos/1200/800',
            'type': 'image',
            'title': 'My Title',
            'description': 'Example',
        },
        {
            'href': 'https://picsum.photos/1200/800',
            'type': 'image',
            'alt': 'image text alternatives'
        },
        {
            'href': 'https://www.youtube.com/watch?v=Ga6RYejo6Hk',
            'type': 'video',
            'source': 'youtube', //vimeo, youtube or local
            'width': 900,
        },
        {
            'content': '<p>This will append some html inside the slide</p>' // read more in the API section
        },
        {
            'content': document.getElementById('inline-example') // this will append a node inside the slide
        },
    ],
    autoplayVideos: true,
});
myGallery.open();

// Si plus tard, vous devez modifier les éléments, vous pouvez utiliser setElements
myGallery.setElements([...]);
```

| Option | Type | Defaut | Description |
| --- | --- | --- | --- |
| selector | string | `.glightbox` | Nom du sélecteur par exemple  '.glightbox' ou 'data-glightbox' ou '\*[data-glightbox]' |
| elements | array | `null` | Au lieu de passer un sélecteur, vous pouvez passer tous les éléments que vous voulez dans la galerie. |
| skin | string | `clean` | Nom de votre skin, il ajoutera une classe à la boîte à lumière afin que vous puissiez la styler avec css. |
| openEffect | string | `zoom` | Nom de l'effet sur la lightbox ouverte. (zoom, fade, none) |
| closeEffect | string | `zoom` | Nom de l'effet sur la lightbox lors de sa fermeture.  (zoom, fade, none) |
| slideEffect | string | `slide` | Nom de l'effet au changement de diapositive. . (slide, fade, zoom, none) |
| moreText | string | `See more` | Plus de texte pour les descriptions sur les appareils mobiles. |
| moreLength | number | `60` | Nombre de caractères à afficher sur la description avant d'ajouter le lien plus de texte (uniquement pour les mobiles), si 0 il affiche la description entière. |
| closeButton | boolean | `true` | Montrez ou cachez le bouton de fermeture. |
| touchNavigation | boolean | `true` | Activer ou désactiver la navigation tactile (swipe). |
| touchFollowAxis | boolean | `true` | Suivre l'image en glissant sur mobile.. |
| keyboardNavigation | boolean | `true` | Activer ou désactiver la navigation au clavier. |
| closeOnOutsideClick | boolean | `true` | Fermez la lightbox en cliquant à l'extérieur de la diapositive active. |
| startAt | number | `0` | Démarrer la lightbox à l'index défini. |
| width | number | `900px` | Largeur par défaut pour les éléments en ligne et les iframes, vous pouvez définir une taille spécifique sur chaque diapositive. Vous pouvez utiliser n'importe quelle unité, par exemple 90 % ou 100vw pour la pleine largeur. |
| height | number | `506px` | Hauteur par défaut pour les éléments en ligne et les iframes, vous pouvez définir une taille spécifique sur chaque diapositive. Vous pouvez utiliser n'importe quelle unité par exemple 90 % ou 100vh **Pour les éléments en ligne, vous pouvez mettre la hauteur à auto**. |
| videosWidth | number | `960px` | Largeur par défaut pour les vidéos. Les vidéos sont réactives de sorte qu'il n'est pas nécessaire de stipuler la hauteur. La largeur peut être en px% ou même vw par example, 500px, 90% ou 100vw pour les vidéos pleine largeur |
| descPosition | string | `bottom` | Position globale pour la description des diapositives, vous pouvez définir une position spécifique sur chaque diapositive (bottom, top, left, right). |
| loop | boolean | `false` | Boucles de boucle de fin. |
| zoomable | boolean | `true` | Permettre  l'activation ou la désactivation des images zoomables, vous pouvez également utiliser des données zoomables -zoomable="false" sur des nœuds individuels. |
| draggable | boolean | `true` | Permettre  l'activation ou la désactivation la fonction glisser de la souris pour aller à la diapositive prev et suivante (uniquement les images et le contenu en ligne), vous pouvez également utiliser des données data-draggable="false" sur les nœuds individuels. |
| dragToleranceX | number | `40` | Utilisé avec la fonction glisser. Nombre de pixels que l'utilisateur doit faire glisser pour passer à la diapositive prev ou suivante. |
| dragToleranceY | number | `65` | Utilisé avec la fonction glisser. Nombre de pixels que l'utilisateur doit faire glisser vers le haut ou vers le bas pour fermer la boîte à lumière (réglez à 0 pour désactiver la traînée verticale). |
| dragAutoSnap | boolean | `false` | Si true la diapositive change automatiquement en  prev/next ou fermer si le glissement de dragToleranceX ou dragToleranceY est atteint, sinon il attendra que la souris soit libérée. |
| preload | boolean | `true` | Permettre ou désactiver le préchargement. |
| svg | object | `{}` | Définissez vos propres icônes svg. |
| cssEfects | object | 'See animations' | Définir ou ajuster les animations de la boîte à lumière. Voir la section Animations dans le README. |
| lightboxHTML | string | 'See themes' | Vous pouvez complètement changer le html de GLightbox. Voir la section thématique du README. |
| slideHTML | string | 'See themes' | Vous pouvez complètement changer le html de la diapositive individuelle. Voir la section thématique du README. |
| autoplayVideos | boolean | `true` | L'auto-play des vidéos à l'ouverture. (mettre à false pour un lancement manuel d'une vidéo) |
| autofocusVideos | boolean | `false` | Si true la vidéo sera axée sur la lecture pour permettre les raccourcis clavier pour le lecteur, cela désactivera les flèches prev et next pour changer la diapositive, donc ne l'utilisez que si vous savez ce que vous faites. |
| plyr | object | `{}` | [Visualisez les options du lecteur vidéo.](#video-player) |

## Événements

Vous pouvez écouter les événements à l'aide de votre instance GLightbox (voir l'exemple sous le tableau). Vous pouvez utiliser la méthode API on() ou une fois().

```javascript
const lightbox = GLightbox();
lightbox.on('open', () => {
  // Do something
});

lightbox.once('slide_changed', () => {
  // Do something just one time
});
```

| Event Type          | Description                                                                                                                  |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| open                | Fournir une fonction lorsque la lightbox est ouverte.                                                                              |
| close               | Fournir une fonction lorsque la lightbox est fermée.                                                                              |
| slide_before_change | Déclencher une fonction avant le changement de diapositive.                                                                              |
| slide_changed       | Déclencher une fonction après le changement de la diapositive.                                                                             |
| slide_before_load   | Déclencher une fonction avant qu'une diapositive ne soit chargée pour la première fois, la fonction ne sera appelée qu'une seule fois                       |
| slide_after_load    | Déclencher une fonction après qu'une diapositive est chargée et son contenu est défini pour la première fois, la fonction ne sera appelée qu'une seule fois |
| slide_inserted      | Déclenchez une fonction après l'insertion d'une diapositive à l'aide d'insertSlide.                                                             |
| slide_removed       | Déclencher une fonction après qu'une diapositive a été enlevée                                                                                 |

```javascript
const lightbox = GLightbox();
lightbox.on('slide_before_change', ({ prev, current }) => {
  console.log('Prev slide', prev);
  console.log('Current slide', current);

  // Prev and current are objects that contain the following data
  const { slideIndex, slideNode, slideConfig, player, trigger } = current;

  // slideIndex - the slide index
  // slideNode - the node you can modify
  // slideConfig - will contain the configuration of the slide like title, description, etc.
  // player - the slide player if it exists otherwise will return false
  // trigger - this will contain the element that triggers this slide, this can be a link, a button, etc in your HTML, it can be null if the elements in the gallery were set dinamically
});

lightbox.on('slide_changed', ({ prev, current }) => {
  console.log('Prev slide', prev);
  console.log('Current slide', current);

  // Prev and current are objects that contain the following data
  const { slideIndex, slideNode, slideConfig, player, trigger } = current;

  // slideIndex - the slide index
  // slideNode - the node you can modify
  // slideConfig - will contain the configuration of the slide like title, description, etc.
  // player - the slide player if it exists otherwise will return false
  // trigger - this will contain the element that triggers this slide, this can be a link, a button, etc in your HTML, it can be null if the elements in the gallery were set dinamically

  if (player) {
    if (!player.ready) {
      // If player is not ready
      player.on('ready', (event) => {
        // Do something when video is ready
      });
    }

    player.on('play', (event) => {
      console.log('Started play');
    });

    player.on('volumechange', (event) => {
      console.log('Volume change');
    });

    player.on('ended', (event) => {
      console.log('Video ended');
    });
  }
});

// Useful to modify the slide
// before it's content is added
lightbox.on('slide_before_load', (data) => {
  // data is an object that contain the following
  const { slideIndex, slideNode, slideConfig, player, trigger } = data;

  // slideIndex - the slide index
  // slideNode - the node you can modify
  // slideConfig - will contain the configuration of the slide like title, description, etc.
  // player - the slide player if it exists otherwise will return false
  // trigger - this will contain the element that triggers this slide, this can be a link, a button, etc in your HTML, it can be null if the elements in the gallery were set dinamically
});

// Useful to execute scripts that depends
// on the slide to be ready with all it's content
// and already has a height
// data will contain all the info about the slide
lightbox.on('slide_after_load', (data) => {
  // data is an object that contain the following
  const { slideIndex, slideNode, slideConfig, player, trigger } = data;

  // slideIndex - the slide index
  // slideNode - the node you can modify
  // slideConfig - will contain the configuration of the slide like title, description, etc.
  // player - the slide player if it exists otherwise will return false
  // trigger - this will contain the element that triggers this slide, this can be a link, a button, etc in your HTML, it can be null if the elements in the gallery were set dinamically
});

// Trigger a function when a slide is inserted
lightbox.on('slide_inserted', (data) => {
  // data is an object that contain the following
  const { slideIndex, slideNode, slideConfig, player, trigger } = data;

  // slideIndex - the slide index
  // slideNode - the node you can modify
  // slideConfig - will contain the configuration of the slide like title, description, etc.
  // player - the slide player if it exists otherwise will return false
  // trigger - null
});

// Trigger a function when a slide is removed
lightbox.on('slide_removed', (index) => {
  // index is the position of the element in the gallery
});
```

## Lecteur vidéo

GLightbox inclut "[Plyr](https://plyr.io/)"  le meilleur joueur, vous pouvez passer n'importe quelle option Plyr au joueur, voir toutes les options disponibles ici Plyr options](https://github.com/sampotts/plyr). GLightbox n'injectera la bibliothèque du lecteur que si nécessaire et seulement lorsque la boîte à lumière est ouverte.

**Internet Explorer 11. Si vous avez besoin d'aide pour ce navigateur, vous devez définir l'url js pour utiliser la version polyplique. Ce n'est pas la valeur par défaut parce que IE11 est ancien et nous devons le laisser mourir.**

### Autoplay pour mobile/tablette

S'il vous plaît noter que l'autoplay est bloqué dans certains navigateurs, il n'y a rien que nous puissions faire pour changer que malheureusement, le navigateur décidera si votre vidéo peut être visualisée automatiquement. Veuillez ne pas publier de questions à ce sujet, informez-vous plutôt sur ce sujet:

- [https://webkit.org/blog/6784/new-video-policies-for-ios/](https://webkit.org/blog/6784/new-video-policies-for-ios/)
- [https://developers.google.com/web/updates/2017/09/autoplay-policy-changes](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes)
- [https://hacks.mozilla.org/2019/02/firefox-66-to-block-automatically-playing-audible-video-and-audio/](https://hacks.mozilla.org/2019/02/firefox-66-to-block-automatically-playing-audible-video-and-audio/)

ils décident si une vidéo peut être auto-jouée en se basant sur quelques règles

```
plyr: {
    js: 'https://cdn.plyr.io/3.6.2/plyr.polyfilled.js',
    ....
```

```javascript
const lightbox = GLightbox({
  plyr: {
    css: 'https://cdn.plyr.io/3.5.6/plyr.css', // Default not required to include
    js: 'https://cdn.plyr.io/3.5.6/plyr.js', // Default not required to include
    config: {
      ratio: '16:9', // or '4:3'
      muted: false,
      hideControls: true,
      youtube: {
        noCookie: true,
        rel: 0,
        showinfo: 0,
        iv_load_policy: 3
      },
      vimeo: {
        byline: false,
        portrait: false,
        title: false,
        speed: true,
        transparent: false
      }
    }
  }
});
```

## API

There are methods, setters and getters on a GLightbox object. The easiest way to access the GLightbox object is to set the return value from your call to a variable. For example:

```javascript
const lightbox = GLightbox({ ...options });
```

## Méthodes

Utilisation de la méthode par exemple:

```javascript
lightbox.nextSlide(); // Aller à la diapositive suivante
lightbox.close(); // Fermer la lightbox
```

| Option                 | Parameters         | Description                                                                |
| ---------------------- | ------------------ | -------------------------------------------------------------------------- |
| open                   | `node`             | Ouvrir la lightbox, yvous pouvez éventuellement passer un noeud.                         |
| openAt                 | `number`           | Ouvrir à l'index spécifique.                                                    |
| close                  | `-`                | fermer la lightbox.                                                        |
| reload                 | `-`                | Rechargez la lightbox, après avoir inséré du contenu avec de l'ajax.                    |
| destroy                | `-`                | Détruire et enlever tous les événements attachés.                                    |
| prevSlide              | `-`                |	Aller à la diapositive précédente.                                                  |
| nextSlide              | `-`                | Aller à la diapositive suivante.                                                      |
| goToSlide              | `number`           | Index de la diapositive.                                                        |
| insertSlide            | `object, index`    | Insérer une diapositive à l'index spécifié.                                     |
| removeSlide            | `index`            | Retirez la diapositive à l'index spécifié.                                       |
| getActiveSlide         | `-`                | Obtenir un glissement actif. Il retournera le nœud actif.                          |
| getActiveSlideIndex    | `-`                | Obtenez un glissement actif. Il retournera l'index du glissement actif.                   |
| slidePlayerPlay        | `number`           | Lire la vidéo dans la diapositive spécifiée.                                         |
| slidePlayerPause       | `number`           | Pause vidéo dans la diapositive spécifiée.                                        |
| getSlidePlayerInstance | `node, index`      | Obtenir le lecteur vidéo de la diapositive spécifiée.                           |
| getAllPlayers          | `-`                | Obtenez tous les lecteurs de vidéo.                                                  |
| setElements            | `[]`               | Mettre à jour les éléments de la galerie de la lightbox.                                      |
| on                     | `string, function` | Fixer un auditeur d'événement. Voir la section Événements                                 |
| once                   | `string, function` | Définissez un auditeur d'événement qui ne sera déclenché qu'une seule fois. Voir la section Événements |

```javascript
// Example set custom gallery items
// This overwrites all the items in the gallery
lightbox.setElements([
  {
    'href': 'https://picsum.photos/1200/800',
    'type': 'image' // Type is only required if GLightbox fails to know what kind of content should display
  },
  {
    'href': 'https://www.youtube.com/watch?v=Ga6RYejo6Hk',
    'type': 'video', // Type is only required if GLightbox fails to know what kind of content should display
    'width': '900px',
  },
  {
    'content': '<p>some html to append in the slide</p>',
    'width': '900px',
  }
]);


// Insert a single slide at the end of all the items,
lightbox.insertSlide({
    href: 'video url...',
    width: '90vw'
});

// Insert a single slide at index 2 or pass 0 to add it at the start
lightbox.insertSlide({
    href: 'video url...',
    width: '90vw'
}, 2);

// You can insert a slide with a defined html
lightbox.insertSlide({
    content: '<p>some html to append in the slide</p>',
    width: '90vw'
}, 2);

// Or if you prefer you can pass a node
// and it will be inserted in the slide
lightbox.insertSlide({
    content: document.getElementById('inline-example'),
    width: '90vw'
}, 2);

// Remove the slide at index 2
lightbox.removeSlide(2);

// Open the lightbox
lightbox.open();

// You can also open the lightbox at a specific index
lightbox.openAt(2);

// So imagine that you are making an ajax request that returns some html
// You can create an empty instance and append the content once is returned

const ajaxExample = GLightbox({ selector: null }); // or you can set the selector empty selector: ''

doAjaxCall({...}).then(response => {
    ajaxExample.insertSlide({
        width: '500px',
        content: response.html
    });
    ajaxExample.open();
})

// Or you could use the set elements method to empty all the slides if any

doAjaxCall({...}).then(response => {
    ajaxExample.setElements([
      {
        content: response.html
      }
    ]);
    ajaxExample.open();
})

```

## Animations

Les animations sont créées avec CSS, chaque effet a une valeur entrée et sortie et ils sont utilisés pour attacher les classes correctes au nœud.

Par exemple, si vous utilisez

```javascript
const glightbox = GLightbox({
  openEffect: 'zoom',
  closeEffect: 'fade',
  cssEfects: {
    // This are some of the animations included, no need to overwrite
    fade: { in: 'fadeIn', out: 'fadeOut' },
    zoom: { in: 'zoomIn', out: 'zoomOut' }
  }
});
```
L'effet ouvert utilisera cssEfects.zoom.in et ajoutera la classe gzoomIn, si vous regardez le CSS vous verrez :

```javascript
.gzoomIn {
    animation: gzoomIn .5s ease;
}

@keyframes gzoomIn {
    from {
        opacity: 0;
        transform: scale3d(.3, .3, .3);
    }
    to {
        opacity: 1;
    }
}
```

### Ajout d'une animation personnalisée

Vous pouvez créer n'importe quelle animation que vous voulez, vous pouvez trouver une inspiration dans la bibliothèque Animate.css, par exemple vous pouvez ajouter l'animation rebond comme ceci:

```javascript
const glightbox = GLightbox({
  openEffect: 'bounce', // Define that we want the bounce animation on open
  cssEfects: {
    // register our new animation
    bounce: { in: 'bounceIn', out: 'bounceOut' }
  }
});
```

```css
/*A g will be appended to the animation name so bounceIn will become gbounceIn */
.gbounceIn {
  animation: bounceIn 1.3s ease;
}

@keyframes bounceIn {
  from,
  20%,
  40%,
  60%,
  80%,
  to {
    animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  0% {
    opacity: 0;
    transform: scale3d(0.3, 0.3, 0.3);
  }

  20% {
    transform: scale3d(1.1, 1.1, 1.1);
  }

  40% {
    transform: scale3d(0.9, 0.9, 0.9);
  }

  60% {
    opacity: 1;
    transform: scale3d(1.03, 1.03, 1.03);
  }

  80% {
    transform: scale3d(0.97, 0.97, 0.97);
  }

  to {
    opacity: 1;
    transform: scale3d(1, 1, 1);
  }
}
```

## Thématique

Vous pouvez complètement personnaliser la structure de GLightbox et utiliser du CSS pour changer n'importe quelle partie que vous voulez. 

```javascript
const customLightboxHTML = `<div id="glightbox-body" class="glightbox-container">
    <div class="gloader visible"></div>
    <div class="goverlay"></div>
    <div class="gcontainer">
    <div id="glightbox-slider" class="gslider"></div>
    <button class="gnext gbtn" tabindex="0" aria-label="Next" data-customattribute="example">{nextSVG}</button>
    <button class="gprev gbtn" tabindex="1" aria-label="Previous">{prevSVG}</button>
    <button class="gclose gbtn" tabindex="2" aria-label="Close">{closeSVG}</button>
</div>
</div>`;

let customSlideHTML = `<div class="gslide">
    <div class="gslide-inner-content">
        <div class="ginner-container">
            <div class="gslide-media">
            </div>
            <div class="gslide-description">
                <div class="gdesc-inner">
                    <h4 class="gslide-title"></h4>
                    <div class="gslide-desc"></div>
                </div>
            </div>
        </div>
    </div>
</div>`;

const glightbox = GLightbox({
  lightboxHTML: customLightboxHTML,
  slideHTML: customSlideHTML,
  skin: 'supercool'
});
```

You can also define a skin name and the lightbox will append the class name "glightbox-supercool" so you can customize it with CSS, this will leave a barebones structure so you can change the buttons appearance, etc.

## Développement

```bash
$ npm install
$ npm run watch
```

## Browser Support

GLightbox a été testé dans les navigateurs suivants.

- Safari
- Mobile Safari
- Opera
- Edge
- Firefox
- Internet Explorer 11

Il fonctionnera dans n'importe quel autre navigateur prenant en charge CSS Flexbox

## Contribution
N'hésitez pas à signaler tout problème. Si vous souhaitez contribuer en corrigeant un bogue ou en mettant en œuvre une nouvelle fonctionnalité, veuillez d'abord lire le guide [CONTRIBUTING](./CONTRIBUTING.md).

## Dons

Si vous trouvez ce code utile, veuillez envisager un don pour maintenir l'augmentation de ce projet, n'importe quel montant est apprécié.

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://paypal.me/bdigital9816/5usd)

## Support

Nous ne fournissons qu'un support pour les bogues et les demandes de fonctionnalités, donc s'il vous plaît ne postez que des problèmes sur ces deux sujets, si vous avez besoin d'aide pour implémenter GLightbox ou vous commencez tout juste avec HTML/CSS/Javascript s'il vous plaît utiliser stackoverlow, vous serez en mesure de trouver plus d'aide là-bas. Cela nous aidera à maintenir les questions liées à la bibliothèque et à résoudre les problèmes plus rapidement.

## Changelog

#### Dernière version indéfinie
Voir le fichier [CHANGELOG.md](CHANGELOG.md) pour plus de details.

## License

Ce projet est sous licence du MIT - voir le dossier [LICENSE.md](LICENSE.md) pour plus de details.
