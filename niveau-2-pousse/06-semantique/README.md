# Exercice 06 — De la « soupe de div » à une page sémantique

**Niveau 2 · Pousse** · ★★☆☆ · Durée : 45 min · Notions : `header`, `nav`, `main`, `article`, `aside`, `footer`, `time`

> Un stagiaire a codé le blog du « Potager Malin ». La page s'affiche correctement… mais elle est entièrement construite avec des `<div>` et des `<span>`. Pour un moteur de recherche ou un lecteur d'écran (le logiciel qui lit la page à voix haute pour les personnes aveugles), c'est un gros bloc sans aucune structure. Votre mission : redonner du sens à cette page.

## Objectifs

- Comprendre la différence entre une balise **neutre** (`<div>`, `<span>`) et une balise **sémantique** (qui dit ce que contient le bloc).
- Découper une page en grandes zones : en-tête, navigation, contenu principal, contenu complémentaire, pied de page.
- Choisir la bonne balise pour chaque bloc et savoir **justifier** son choix.

## Fichiers fournis

```
06-semantique/
├── README.md     ← cette consigne
└── index.html    ← la page « soupe de div » à transformer
```

## Consigne

**Étape 0 — Sur papier (10 min).** Ouvrez `index.html` dans le navigateur. Sur une feuille, dessinez la page sous forme de rectangles (un rectangle par grand bloc) et écrivez dans chaque rectangle son rôle : « titre du site », « menu », etc. Vous venez de faire votre première **maquette fil de fer** (*wireframe*).

Ensuite, modifiez `index.html` (les numéros correspondent aux commentaires `TODO` du fichier) :

1. Remplacez le bloc d'en-tête par un `<header>`. Le nom du blog devient le **seul** `<h1>` de la page ; le slogan devient un paragraphe `<p>`.
2. Remplacez le menu par un `<nav>`. Les liens forment une liste : utilisez `<ul>` et `<li>`, et supprimez les `|` (ils ne servent qu'à décorer).
3. Regroupez les deux articles dans un `<main>` (il ne peut y en avoir **qu'un seul** par page).
4. Transformez chaque article en `<article>`. Son titre devient un `<h2>`. **Gardez les `id`** existants : les liens du menu en ont besoin.
5. Placez chaque date dans une balise `<time>` avec un attribut `datetime` au format `AAAA-MM-JJ`.
   Exemple : `<time datetime="2026-01-31">31 janvier 2026</time>`.
6. Les lignes qui commencent par « - » sont de fausses listes : remplacez-les par de vraies listes `<ul>`/`<li>` (et supprimez les tirets).
7. Les textes deviennent des paragraphes `<p>` ; les `<span class="gras">` deviennent des `<strong>`.
8. L'encadré « Le conseil de la semaine » est un contenu complémentaire : utilisez `<aside>`, avec un titre `<h2>`.
9. Le pied de page devient un `<footer>`.
10. Supprimez les attributs `class` devenus inutiles, puis vérifiez votre code avec le [validateur W3C](https://validator.w3.org/#validate_by_input).

### Mémo des balises sémantiques

| Balise | Rôle | Exemples |
|---|---|---|
| `<header>` | En-tête de la page (ou d'un article) | logo, nom du site, slogan |
| `<nav>` | Bloc de liens de navigation **principaux** | menu du site, sommaire |
| `<main>` | Contenu principal, **unique** dans la page | tout ce qui est propre à cette page |
| `<article>` | Contenu **autonome**, qui aurait du sens publié seul | article de blog, fiche produit, commentaire |
| `<section>` | Partie thématique d'un document, avec un titre | chapitre « Présentation », « Culture » |
| `<aside>` | Contenu **complémentaire**, en marge du sujet | encadré, « à lire aussi », glossaire |
| `<footer>` | Pied de page (de la page ou d'un article) | copyright, contact, mentions |
| `<time>` | Date ou heure lisible par une machine | `<time datetime="2026-11-17">17 novembre</time>` |
| `<div>` / `<span>` | **Aucun sens** : seulement quand aucune autre balise ne convient | regrouper des éléments pour le CSS |

## Critères de réussite

- [ ] Ma maquette papier est faite et chaque rectangle correspond à une balise de mon code.
- [ ] Il ne reste aucun `<div>` ni `<span>` (ou je sais justifier chacun d'eux).
- [ ] La page contient exactement **un** `<h1>`, **un** `<main>` et **un** `<nav>`.
- [ ] Les liens du menu sont dans une liste `<ul>` et fonctionnent toujours.
- [ ] Chaque `<article>` et l'`<aside>` commencent par un titre `<h2>`.
- [ ] Les deux dates sont dans des `<time datetime="…">` au bon format.
- [ ] Les fausses listes sont devenues de vraies listes.
- [ ] Le validateur W3C n'affiche aucune erreur.

## Indices

<details>
<summary>Indice 1 — <code>&lt;article&gt;</code> ou <code>&lt;section&gt;</code> ?</summary>

Posez-vous la question : « Ce bloc aurait-il du sens tout seul, copié sur un autre site ? »
- Oui (un article de blog, une recette, une fiche) → `<article>`.
- Non, c'est une partie d'un ensemble plus grand (le chapitre « Utilisations » d'une fiche) → `<section>`.

</details>

<details>
<summary>Indice 2 — À quoi ressemble un menu bien structuré ?</summary>

```html
<nav>
  <ul>
    <li><a href="#exemple-1">Premier lien</a></li>
    <li><a href="#exemple-2">Deuxième lien</a></li>
  </ul>
</nav>
```

</details>

<details>
<summary>Indice 3 — Où placer l'<code>&lt;aside&gt;</code> ?</summary>

Un `<aside>` peut être à l'intérieur d'un `<article>` (s'il complète cet article précis) ou à côté du `<main>` (s'il concerne tout le site). Ici, le conseil de la semaine n'est lié à aucun article en particulier.

</details>

<details>
<summary>Indice 4 — Comment vérifier ma structure ?</summary>

Dans le validateur W3C, cliquez sur **More options**, cochez **outline**, puis lancez la vérification : le validateur affiche le plan (la hiérarchie des titres) de votre page. Chaque bloc doit avoir un titre qui a du sens.

</details>

## Bonus

- Ajoutez un `<header>` **à l'intérieur** de chaque article, qui regroupe le titre et la date. Eh oui : `<header>` n'est pas réservé au haut de la page !
- Écrivez un troisième article de votre choix (par exemple « Récupérer l'eau de pluie ») et ajoutez-le au menu.
- Placez le contact du pied de page dans une balise `<address>`.

## Questions de compréhension

1. Avant et après votre travail, la page s'affiche presque pareil. Alors, à quoi sert la sémantique ? (Pensez à trois « lecteurs » : un lecteur d'écran, un moteur de recherche, un autre développeur.)
2. Quelle est la différence entre `<article>` et `<section>` ?
3. Peut-on avoir plusieurs `<header>` dans une page ? Et plusieurs `<main>` ?
4. Pourquoi utiliser `<strong>` plutôt que `<b>` pour un passage important ?

## Lien avec le brief PlantEvo

La grille d'évaluation du brief contient le critère « **Structure et utilisation efficace des balises** » : c'est exactement ce que vous venez de travailler. Votre page PlantEvo doit avoir un `<header>`, un `<nav>` (votre menu), un `<main>` et un `<footer>`, et chaque grande partie de votre contenu mérite sa propre balise sémantique avec un titre.

## Ressources

- [MDN — Structure de document et de site web](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
- MDN : [`<header>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/header) · [`<nav>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/nav) · [`<main>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/main) · [`<article>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/article) · [`<section>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/section) · [`<aside>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/aside) · [`<footer>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/footer) · [`<time>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/time)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [07 — Le guide des fruits tropicaux](../07-ancres/README.md)
