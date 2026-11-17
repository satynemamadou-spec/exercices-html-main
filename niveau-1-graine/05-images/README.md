# Exercice 05 — Les images

**Niveau 1 · Graine** · ★☆☆☆ · Durée : 40 min · Notions : `<img>`, `src`, `alt`, `width`, `height`, `<figure>`, `<figcaption>`, image cliquable

> Le site du marché a besoin d'images pour donner envie aux visiteurs. Les illustrations sont prêtes dans le dossier `images` : à vous de les afficher… et de réparer celle qui est cassée.

## Objectifs

- Afficher une image avec `<img>` et un chemin relatif.
- Écrire un **texte alternatif** (`alt`) utile.
- Indiquer les dimensions d'une image avec `width` et `height`.
- Associer une image et sa légende avec `<figure>` et `<figcaption>`.
- Trouver pourquoi une image ne s'affiche pas, avec les outils du navigateur.
- Transformer une image en lien.

## Fichiers fournis

```
05-images/
├── README.md
├── index.html
└── images/
    ├── cacao.svg
    ├── mangue.svg
    ├── tomate.svg
    └── cereales/
        └── mais.svg
```

Toutes les illustrations mesurent 400 × 300 pixels.

## À lire avant de commencer : bien écrire un `alt`

L'attribut `alt` contient le texte qui **remplace** l'image quand elle ne peut pas être vue : par une personne aveugle (son lecteur d'écran lit le `alt`), quand l'image ne se charge pas, ou par un moteur de recherche.

| À faire | À éviter |
|---|---|
| Décrire ce que l'image montre d'utile : `alt="Mangue mûre, rouge et orange"` | Commencer par « Image de… » ou « Photo de… » (le lecteur d'écran annonce déjà que c'est une image) |
| Rester court : une phrase suffit | Recopier le nom du fichier : `alt="mangue.svg"` |
| Si l'image est un lien : décrire la **destination** du lien | Oublier l'attribut `alt` |
| Si l'image est purement décorative : `alt=""` (vide) | Mettre un `alt` vide sur une image qui apporte une information |

## Consigne

Les numéros correspondent aux commentaires `TODO` dans `index.html`.

1. **La mangue** : affichez `images/mangue.svg` avec :
   - un `alt` qui décrit l'image ;
   - `width="200"` et `height="150"` (l'image s'affiche en taille réduite de moitié).
2. **Le maïs** : affichez l'image du maïs. Attention, elle est rangée dans le **sous-dossier** `cereales` du dossier `images`. Mêmes dimensions.
3. **La tomate** : affichez `images/tomate.svg` à l'intérieur d'une balise `<figure>`, avec la légende « Botaniquement, la tomate est un fruit ! » dans une balise `<figcaption>`.
4. **Le cacao** : l'image ne s'affiche pas.
   - Ouvrez les outils de développement (`F12`), onglet **Console** : un message d'erreur indique le fichier introuvable.
   - Comparez le chemin écrit dans le code avec le contenu réel du dossier `images` : il y a **2 erreurs**. Corrigez-les.
   - Remplacez le `alt=""` par un vrai texte alternatif : cette image apporte une information, elle n'est pas décorative.
5. **Image cliquable** : faites de l'image de la mangue un lien vers `https://fr.wikipedia.org/wiki/Mangue`. Pour cela, placez la balise `<img>` **à l'intérieur** d'une balise `<a>`. Adaptez le `alt` : il doit maintenant décrire la destination du lien (relisez le tableau ci-dessus).
6. **Expériences** :
   - Supprimez `width` et `height` sur une image : que se passe-t-il ? Remettez-les.
   - Mettez `width="300"` et `height="100"` : l'image est-elle déformée ? Remettez les bonnes valeurs.
   - Renommez temporairement `tomate.svg` en `tomate2.svg` (dans l'explorateur de fichiers) et rechargez la page : qu'affiche le navigateur à la place de l'image ? Remettez le bon nom.

## Critères de réussite

- [ ] Les 4 images s'affichent.
- [ ] Chaque `<img>` a un attribut `alt` utile (pas de « image de… », pas de nom de fichier).
- [ ] Chaque `<img>` a un `width` et un `height` qui respectent les proportions (4 / 3).
- [ ] Le chemin du maïs passe par le sous-dossier `cereales`.
- [ ] La tomate est dans une `<figure>` avec une `<figcaption>`.
- [ ] Un clic sur la mangue ouvre l'article Wikipédia.
- [ ] Tous les chemins sont relatifs.

## Indices

<details>
<summary>Indice 1 — La structure d'une balise image</summary>

```html
<img src="chemin/vers/le-fichier.svg" alt="Description utile" width="200" height="150">
```

`<img>` est une balise **vide** : elle n'a pas de balise fermante `</img>`.

</details>

<details>
<summary>Indice 2 — Les 2 erreurs du cacao</summary>

Comparez lettre par lettre :
- le **nom du dossier** écrit dans le code et le vrai nom du dossier ;
- l'**extension** du fichier écrite dans le code (`.png`) et la vraie extension du fichier.

</details>

<details>
<summary>Indice 3 — La structure de <code>&lt;figure&gt;</code></summary>

```html
<figure>
  <img src="..." alt="..." width="..." height="...">
  <figcaption>La légende de l'image</figcaption>
</figure>
```

</details>

## Bonus

- Trouvez une vraie photo libre de droits (sur [Wikimedia Commons](https://commons.wikimedia.org), [Unsplash](https://unsplash.com/fr) ou [Pixabay](https://pixabay.com/fr/)), téléchargez-la dans le dossier `images` et affichez-la. Indiquez le nom de l'auteur et la source dans une `<figcaption>`.
- Il est aussi possible d'afficher une image directement depuis Internet avec une URL absolue (`src="https://…"`). Pourquoi est-ce préférable de télécharger l'image dans votre projet ? (Pensez à ce qui se passe si le site d'origine supprime l'image.)

## Questions de compréhension

1. À quoi sert l'attribut `alt` ? Citez deux situations où il est utilisé.
2. Pourquoi indiquer `width` et `height` alors que l'image s'affiche très bien sans ?
3. Quand doit-on écrire `alt=""` (vide) ?
4. Quelle est la différence entre `<figcaption>` et `alt` ?

## Lien avec le brief PlantEvo

Le brief demande « 80 % d'images et 20 % de texte » : les images sont au cœur de votre projet. Le jury vérifiera la qualité des images, leurs textes alternatifs, et le fait que le site n'utilise pas trop de liens externes. Pensez aussi à citer la source de chaque image.

## Ressources

- [MDN — `<img>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/img)
- [MDN — `<figure>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/figure)
- [MDN — Les images en HTML](https://developer.mozilla.org/fr/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [06 — De la « soupe de div » à une page sémantique](../../niveau-2-pousse/06-semantique/README.md)
