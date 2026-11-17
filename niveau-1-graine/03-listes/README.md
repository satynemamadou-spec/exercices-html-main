# Exercice 03 — Les listes

**Niveau 1 · Graine** · ★☆☆☆ · Durée : 30 min · Notions : `<ul>`, `<ol>`, `<li>`, listes imbriquées, `<dl>`, `<dt>`, `<dd>`

> Le club jardinage de votre quartier veut mettre en ligne un petit guide pour planter des tomates. Le texte est prêt, il reste à l'organiser en listes claires.

## Objectifs

- Choisir le bon type de liste : non ordonnée, ordonnée ou de définitions.
- Imbriquer une liste dans une autre **sans erreur**.
- Comprendre qu'une liste ne contient que des `<li>` (pour `<ul>` et `<ol>`).

## Fichiers fournis

```
03-listes/
├── README.md
└── index.html    ← le texte brut, avec des commentaires TODO
```

## Consigne

1. Mettez le titre `Planter des tomates au potager` dans un `<h1>`.
2. **Matériel** : mettez `Matériel nécessaire` dans un `<h2>`, puis transformez les 5 lignes suivantes en **liste non ordonnée** (`<ul>`) : l'ordre du matériel n'a pas d'importance.
3. **Étapes** : mettez `Les étapes` dans un `<h2>`, puis créez une **liste ordonnée** (`<ol>`) de 5 étapes principales :
   1. Semer les graines
   2. Repiquer les jeunes plants
   3. Tuteurer
   4. Arroser
   5. Récolter
4. **Sous-étapes** : les étapes « Semer » et « Repiquer » contiennent chacune 3 actions. Placez ces actions dans une liste ordonnée **imbriquée** (une liste à l'intérieur de l'étape). Ne tapez pas les numéros vous-même : c'est le navigateur qui les ajoute.
5. **Lexique** : mettez `Petit lexique` dans un `<h2>`, puis transformez les 3 définitions en **liste de définitions** (`<dl>`) : le mot dans un `<dt>`, sa définition dans un `<dd>`. Supprimez les deux-points « : », devenus inutiles.
6. Vérifiez le résultat dans le navigateur : les numéros, les puces et les décalages doivent apparaître tout seuls.
7. Remplacez les commentaires `TODO` par des commentaires utiles (`<!-- Liste du matériel -->`…).

## Critères de réussite

- [ ] Un `<h1>` et trois `<h2>`.
- [ ] Le matériel est dans un `<ul>` avec 5 `<li>`.
- [ ] Les étapes sont dans un `<ol>` avec 5 `<li>` principaux.
- [ ] Les sous-étapes sont dans des `<ol>` placés **à l'intérieur** d'un `<li>` (et non directement dans le `<ol>` parent).
- [ ] Aucun numéro n'est tapé à la main dans le texte.
- [ ] Le lexique utilise `<dl>`, `<dt>` et `<dd>`.
- [ ] Un `<ul>` ou un `<ol>` ne contient **que** des `<li>`.

## Indices

<details>
<summary>Indice 1 — <code>&lt;ul&gt;</code> ou <code>&lt;ol&gt;</code> ?</summary>

Posez-vous la question : « Si je mélange les éléments, est-ce que le sens change ? »

- Non → liste non ordonnée `<ul>` (*unordered list*) : une liste de courses, du matériel…
- Oui → liste ordonnée `<ol>` (*ordered list*) : une recette, un mode d'emploi, un classement…

</details>

<details>
<summary>Indice 2 — Comment imbriquer une liste correctement ?</summary>

La sous-liste se place **dans** le `<li>`, juste après son texte, **avant** la fermeture `</li>`. Exemple avec un autre sujet :

```html
<ol>
  <li>
    Préparer le jus de fruits
    <ol>
      <li>Laver les fruits.</li>
      <li>Couper les fruits en morceaux.</li>
    </ol>
  </li>
  <li>Servir bien frais.</li>
</ol>
```

**Erreur fréquente :** placer le `<ol>` imbriqué **entre** deux `<li>`, directement dans le `<ol>` parent. Le validateur le refuse.

</details>

<details>
<summary>Indice 3 — La structure d'une liste de définitions</summary>

```html
<dl>
  <dt>Terme</dt>
  <dd>Définition du terme.</dd>
</dl>
```

`<dl>` = *description list*, `<dt>` = *description term*, `<dd>` = *description details*.

</details>

## Bonus

- Ajoutez l'attribut `type="a"` aux sous-listes : les sous-étapes sont alors numérotées a, b, c.
- Ajoutez une partie « Top 3 des légumes faciles à cultiver » avec une liste ordonnée **à rebours** (3, 2, 1) grâce à l'attribut `reversed`.
- Testez l'attribut `start="4"` sur un `<ol>` : que se passe-t-il ?

## Questions de compréhension

1. Quelle est la différence entre `<ul>` et `<ol>` ? Donnez un exemple d'utilisation pour chacune.
2. Quelles balises peut-on placer directement dans un `<ul>` ?
3. Le saviez-vous ? Pour un botaniste, la tomate est un **fruit** : elle se forme à partir de la fleur et contient les graines. En cuisine, on la range pourtant avec les légumes.

## Lien avec le brief PlantEvo

Le menu de votre site sera une liste de liens (`<ul>` + `<li>`). Les grandes étapes de l'évolution des végétaux se prêtent aussi très bien à une liste ordonnée.

## Ressources

- [MDN — `<ul>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/ul)
- [MDN — `<ol>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/ol)
- [MDN — `<dl>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/dl)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [04 — Les liens](../04-liens/README.md)
