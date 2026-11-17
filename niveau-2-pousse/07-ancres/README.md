# Exercice 07 — Le guide des fruits tropicaux

**Niveau 2 · Pousse** · ★★☆☆ · Durée : 40 min · Notions : attribut `id`, liens internes `href="#…"`, liens vers une section d'une autre page

> Le guide des fruits tropicaux de l'exposition est une très longue page. Les visiteurs se perdent en faisant défiler le texte ! Ajoutez un sommaire cliquable et des liens pour revenir au sommaire, afin que chacun puisse aller directement au fruit qui l'intéresse.

## Objectifs

- Donner un identifiant (`id`) à un élément pour en faire une **cible** de lien (une « ancre »).
- Créer des liens vers un endroit précis de la même page : `href="#identifiant"`.
- Créer un lien vers un endroit précis d'une **autre** page : `href="page.html#identifiant"`.
- Comprendre ce qui se passe dans la barre d'adresse et avec le bouton « Précédent ».

## Fichiers fournis

```
07-ancres/
├── README.md       ← cette consigne
├── index.html      ← le guide (une longue page avec 5 sections)
└── recettes.html   ← une page de recettes
```

## Consigne

Les numéros correspondent aux commentaires `TODO` des fichiers.

1. Dans `index.html`, donnez un `id` à chacune des 5 `<section>` (par exemple `id="mangue"` pour la section sur la mangue).
   Règles pour un bon `id` : **unique** dans la page, en **minuscules**, **sans espace ni accent**, qui commence par une lettre.
2. Dans le sommaire, transformez chaque élément de la liste en lien vers la section correspondante.
3. Ajoutez `id="sommaire"` sur le `<nav>`, puis, à la fin de **chaque** section, un lien « ↑ Retour au sommaire ».
4. Ajoutez `id="haut"` sur le `<header>`, puis un lien « Haut de page » dans le `<footer>`.
5. Dans `recettes.html`, sous la recette du jus de mangue, ajoutez un lien « En savoir plus sur la mangue » qui ouvre `index.html` **directement à la section de la mangue**.
6. Testez ! Cliquez sur chaque lien et observez :
   - la **barre d'adresse** : que s'ajoute-t-il à la fin de l'adresse ?
   - le bouton **Précédent** du navigateur : où vous ramène-t-il ?

> **Attention :** si la fenêtre est très grande, la page ne défile peut-être pas assez pour voir l'effet des liens : réduisez la hauteur de la fenêtre ou zoomez (Ctrl +).

## Critères de réussite

- [ ] Les 5 sections ont un `id` unique, en minuscules, sans espace ni accent.
- [ ] Les 5 liens du sommaire mènent à la bonne section.
- [ ] Chaque section se termine par un lien « ↑ Retour au sommaire » qui fonctionne.
- [ ] Le lien « Haut de page » du pied de page remonte tout en haut.
- [ ] Depuis `recettes.html`, le lien « En savoir plus sur la mangue » ouvre `index.html` sur la section de la mangue.
- [ ] Je sais expliquer ce que signifie `#mangue` à la fin de l'adresse.
- [ ] Le validateur W3C n'affiche aucune erreur (il signale notamment les `id` en double).

## Indices

<details>
<summary>Indice 1 — Le lien et sa cible</summary>

Un lien interne fonctionne en deux parties : une **cible** (un élément avec un `id`) et un **lien** dont le `href` commence par `#`.

```html
<h2 id="exemple">Un titre quelque part dans la page</h2>
…
<a href="#exemple">Aller au titre</a>
```

Attention : le `#` se met **dans le `href`**, jamais dans l'`id`.

</details>

<details>
<summary>Indice 2 — Viser une section d'une autre page</summary>

On écrit d'abord le chemin du fichier, puis `#` et l'identifiant, **sans espace** :

```html
<a href="autre-page.html#identifiant">…</a>
```

</details>

<details>
<summary>Indice 3 — Mon lien ne fait rien !</summary>

- Vérifiez l'orthographe : `#Mangue` et `#mangue` sont deux identifiants différents (majuscules ≠ minuscules).
- Vérifiez que l'`id` existe bien et qu'il n'est pas utilisé deux fois.
- Si la section est déjà visible à l'écran, le navigateur ne bouge pas : réduisez la fenêtre pour tester.

</details>

## Bonus

- Dans la recette de la salade de fruits, transformez le nom de chaque fruit en lien vers sa section dans le guide.
- Ajoutez une sixième section (le fruit tropical de votre choix), puis mettez à jour le sommaire. Vérifiez vos informations dans une source fiable !
- Testez `<a href="#">` : où vous emmène ce lien ? Pourquoi est-il préférable de viser un `id` précis ?

## Questions de compréhension

1. Qu'est-ce qui s'ajoute dans la barre d'adresse quand on clique sur un lien interne ? À quoi cela peut-il servir (pensez au partage d'un lien avec un ami) ?
2. Pourquoi un `id` doit-il être **unique** dans une page ?
3. Depuis `recettes.html`, quelle est la différence entre `href="#mangue"` et `href="index.html#mangue"` ?
4. Que fait le bouton « Précédent » après un clic sur un lien interne ?

## Lien avec le brief PlantEvo

Le brief demande un menu qui mène aux différents types de végétaux et, « lorsque l'utilisateur sera en train de consulter les détails sur un type de végétaux, un lien permettra de revenir au menu ». Les ancres sont la façon la plus simple de le faire si tout votre contenu est sur une seule page ; le lien `page.html#id` sert si votre site comporte plusieurs pages.

## Ressources

- [MDN — L'élément `<a>` (section « Liens vers un élément de la même page »)](https://developer.mozilla.org/fr/docs/Web/HTML/Element/a)
- [MDN — L'attribut `id`](https://developer.mozilla.org/fr/docs/Web/HTML/Global_attributes/id)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [08 — La ferme pédagogique](../08-mini-site/README.md)
