# Exercice 02 — Titres et paragraphes

**Niveau 1 · Graine** · ★☆☆☆ · Durée : 30 min · Notions : `<h1>` à `<h6>`, `<p>`, `<strong>`, `<em>`, `<i>`, `<br>`, `<hr>`

> Un agronome vous a envoyé le texte d'une fiche sur le maïs… mais sans aucune mise en forme. Votre mission : structurer ce texte avec les bonnes balises pour en faire une vraie page web.

## Objectifs

- Construire une hiérarchie de titres logique (`<h1>` → `<h2>` → `<h3>`).
- Découper un texte en paragraphes avec `<p>`.
- Choisir la bonne balise pour mettre en valeur un mot : `<strong>`, `<em>` ou `<i>`.
- Savoir quand utiliser (et ne pas utiliser) `<br>` et `<hr>`.

## Fichiers fournis

```
02-titres-paragraphes/
├── README.md     ← cette consigne
└── index.html    ← le texte brut, sans balises
```

## Consigne

Ouvrez `index.html` dans le navigateur **avant** de commencer : tout le texte est collé sur une seule ligne. C'est normal : en HTML, les retours à la ligne du code ne s'affichent pas. Seules les balises structurent la page.

1. **Le titre principal** : entourez `Le maïs` d'une balise `<h1>`. Il ne doit y avoir **qu'un seul** `<h1>` dans la page.
2. **Le sous-titre** : `Fiche culture` n'est pas une nouvelle partie, c'est une précision sur le titre. Mettez-le dans un simple `<p>`.
3. **Les grandes parties** : repérez les 4 grandes parties du texte et mettez leur titre en `<h2>`.
4. **Les sous-parties** : à l'intérieur des parties, repérez les titres de sous-parties et mettez-les en `<h3>`.
5. **Les paragraphes** : chaque phrase ou groupe de phrases qui n'est pas un titre va dans un `<p>`.
6. **Les mises en valeur** :
   - le nom scientifique *Zea mays* va dans une balise `<i>` (voir l'indice 2) ;
   - mettez en `<strong>` au moins deux groupes de mots **importants** : « la céréale la plus produite au monde » et « besoin d'eau régulièrement » ;
   - mettez en `<em>` le mot « surtout », sur lequel on insiste.
7. **La séparation** : ajoutez un `<hr>` juste avant les lignes « Fiche rédigée par » et « Date ».
8. **Les crédits** : mettez « Fiche rédigée par : … » et « Date : … » dans **un seul** `<p>`, avec un `<br>` entre les deux. Remplacez les crochets par votre prénom et la date du jour.
9. **Expérience** : dans un paragraphe, ajoutez 10 espaces et 3 retours à la ligne entre deux mots. Enregistrez et regardez le résultat. Que constatez-vous ? Annulez ensuite ce changement.
10. Supprimez le commentaire `TODO` et remplacez-le par des commentaires qui indiquent les grandes parties de la page (`<!-- Partie : Présentation -->`…).

## Critères de réussite

- [ ] Il y a un seul `<h1>` dans la page.
- [ ] Les niveaux de titres se suivent sans saut : pas de `<h3>` directement après le `<h1>`.
- [ ] Il y a 4 `<h2>` et 4 `<h3>`.
- [ ] Plus aucun texte n'est « libre » dans le `<body>` : tout est dans une balise.
- [ ] *Zea mays* est dans une balise `<i>`.
- [ ] Il y a au moins deux `<strong>` et un `<em>`.
- [ ] `<br>` n'est utilisé qu'une seule fois, dans les crédits (et jamais pour « faire de l'espace »).
- [ ] Le code est indenté et commenté.

## Indices

<details>
<summary>Indice 1 — Comment repérer la hiérarchie des titres ?</summary>

Imaginez la table des matières d'un livre :

```
Titre du livre             → h1
  Chapitre                 → h2
    Partie d'un chapitre   → h3
```

Les 4 grandes parties de la fiche sont celles qui sont précédées d'une ligne vide dans le fichier. Une partie peut contenir directement un paragraphe, ou bien des sous-parties.

</details>

<details>
<summary>Indice 2 — <code>&lt;strong&gt;</code>, <code>&lt;em&gt;</code> ou <code>&lt;i&gt;</code> ?</summary>

- `<strong>` : le contenu est **important** (affiché en gras par défaut).
- `<em>` : on **insiste** sur un mot, comme quand on le prononce plus fort (affiché en italique par défaut).
- `<i>` : le texte est d'une autre « nature » que le reste, **sans** importance particulière : un mot étranger, un terme technique… ou un **nom scientifique** d'espèce. C'est ce que recommande la spécification HTML.

`<em>` et `<i>` s'affichent tous les deux en italique, mais ils n'ont pas le même **sens**. Un lecteur d'écran, par exemple, peut prononcer différemment un `<em>`.

</details>

<details>
<summary>Indice 3 — Où placer le <code>&lt;hr&gt;</code> et le <code>&lt;br&gt;</code> ?</summary>

`<hr>` et `<br>` sont des balises **vides** : elles n'ont pas de balise fermante. On n'écrit donc jamais `</br>` ni `</hr>`.

Le `<br>` se place **à l'intérieur** du paragraphe, entre les deux lignes à séparer.

</details>

## Bonus

- Ajoutez une partie « Le saviez-vous ? » avec un `<h2>` et un paragraphe : le maïs est une plante dite « en C4 », très efficace pour transformer la lumière en matière (photosynthèse).
- Ajoutez la source de la fiche dans un `<p>` avec la balise `<cite>` : `<cite>FAO — Organisation des Nations unies pour l'alimentation et l'agriculture</cite>`.

## Questions de compréhension

1. Pourquoi ne doit-il y avoir qu'un seul `<h1>` par page ? (Pensez aux moteurs de recherche.)
2. Pourquoi ne faut-il pas choisir une balise de titre (`<h2>`, `<h3>`…) pour sa **taille** d'affichage ?
3. Quelle est la différence entre `<strong>` et `<b>` ? Entre `<em>` et `<i>` ?
4. Que fait le navigateur quand il rencontre plusieurs espaces ou retours à la ligne dans le code ?

## Lien avec le brief PlantEvo

Vos pages sur les végétaux auront des titres, des sous-titres et des noms scientifiques (*Marchantia*, *Pteridium aquilinum*…). Le critère de performance « Structure et utilisation efficace des balises » sera évalué : une hiérarchie de titres propre fait la différence.

## Ressources

- [MDN — Les éléments de titre `<h1>` à `<h6>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/Heading_Elements)
- [MDN — `<p>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/p)
- [MDN — `<strong>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/strong) · [`<em>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/em) · [`<i>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/i)
- [MDN — `<br>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/br) · [`<hr>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/hr)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [03 — Les listes](../03-listes/README.md)
