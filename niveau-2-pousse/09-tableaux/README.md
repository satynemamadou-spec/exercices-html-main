# Exercice 09 — Fiche comparative des cultures

**Niveau 2 · Pousse** · ★★☆☆ · Durée : 45 min · Notions : `table`, `caption`, `thead`, `tbody`, `tfoot`, `tr`, `th`, `td`, `scope`, `rowspan`, `colspan`

> Pour le stand de l'exposition, vous devez présenter six cultures vivrières sous forme de tableau comparatif. Les cultures d'une même famille botanique sont regroupées : il va falloir **fusionner des cellules**.

## Objectifs

- Construire un tableau de données bien structuré : légende, en-tête, corps, pied.
- Distinguer les cellules d'en-tête (`<th>`) des cellules de données (`<td>`).
- Fusionner des cellules sur plusieurs colonnes (`colspan`) ou plusieurs lignes (`rowspan`).
- Savoir qu'un tableau sert à présenter des **données**, jamais à faire la mise en page d'un site.

## Fichiers fournis

```
09-tableaux/
├── README.md     ← cette consigne
└── index.html    ← la page de départ (avec un peu de CSS pour voir les bordures)
```

## Consigne

Voici le tableau à obtenir :

```
┌────────────┬──────────┬───────────────────────────────────────────────────┐
│            │          │                  Caractéristiques                 │
│ Famille    │ Culture  ├──────────────────┬───────────────┬────────────────┤
│            │          │ Partie consommée │ Cycle (jours) │ Besoin en eau  │
├────────────┼──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Tomate   │ fruit            │ 90 à 120      │ moyen          │
│ Solanacées ├──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Piment   │ fruit            │ 90 à 150      │ moyen          │
├────────────┼──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Maïs     │ grains           │ 90 à 150      │ moyen à élevé  │
│ Poacées    ├──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Riz      │ grains           │ 100 à 150     │ élevé          │
├────────────┼──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Haricot  │ gousses, graines │ 60 à 90       │ moyen          │
│ Fabacées   ├──────────┼──────────────────┼───────────────┼────────────────┤
│            │ Arachide │ graines          │ 90 à 130      │ faible à moyen │
├────────────┴──────────┴──────────────────┴───────────────┴────────────────┤
│ Durées indicatives : elles varient selon la variété et le climat.         │
└───────────────────────────────────────────────────────────────────────────┘
```

Les numéros correspondent aux commentaires `TODO` du fichier `index.html`.

1. Créez le `<table>`, puis sa légende avec `<caption>` : « Comparaison de quelques cultures vivrières ».
2. Créez l'en-tête `<thead>`, sur **deux lignes** `<tr>` :
   - ligne 1 : « Famille » et « Culture » occupent **2 lignes** chacune (`rowspan="2"`), « Caractéristiques » occupe **3 colonnes** (`colspan="3"`) ;
   - ligne 2 : « Partie consommée », « Cycle (jours) », « Besoin en eau ».
   - Toutes ces cellules sont des `<th>`. Ajoutez `scope="col"` sur les en-têtes de colonne et `scope="colgroup"` sur « Caractéristiques ».
3. Créez le corps `<tbody>` avec les 6 lignes de données :
   - le nom de la famille n'est écrit **qu'une seule fois** pour deux cultures : `rowspan="2"` ;
   - le nom de la culture est l'en-tête de sa ligne : `<th scope="row">` ;
   - toutes les autres cellules sont des `<td>`.
4. Créez le pied `<tfoot>` : une seule cellule qui occupe les 5 colonnes, avec le texte « Durées indicatives : elles varient selon la variété et le climat. »
5. Vérifiez visuellement que votre tableau ressemble au modèle, puis passez votre page au validateur W3C : il signale les tableaux mal construits (« Table column … established by element … has no cells beginning in it », « row … is wider than the column count »…).

> **À savoir :** le petit bloc `<style>` du fichier sert seulement à afficher les bordures du tableau. Nous apprendrons le CSS plus tard.

## Critères de réussite

- [ ] Le tableau a une légende `<caption>`.
- [ ] Il contient un `<thead>`, un `<tbody>` et un `<tfoot>`.
- [ ] Les en-têtes sont des `<th>` avec le bon `scope` ; les données sont des `<td>`.
- [ ] « Caractéristiques » s'étend bien sur 3 colonnes, « Famille » et « Culture » sur 2 lignes.
- [ ] Chaque nom de famille n'apparaît qu'une fois et s'étend sur ses 2 cultures.
- [ ] La note du pied de tableau occupe toute la largeur.
- [ ] Mon tableau ressemble au modèle et le validateur W3C n'affiche aucune erreur.

## Indices

<details>
<summary>Indice 1 — La structure de base d'un tableau</summary>

Un tableau se lit **ligne par ligne** : chaque `<tr>` (*table row*) contient ses cellules, de gauche à droite.

```html
<table>
  <caption>Titre du tableau</caption>
  <thead>
    <tr><th scope="col">Jour</th><th scope="col">Tâche</th></tr>
  </thead>
  <tbody>
    <tr><th scope="row">Lundi</th><td>Arroser</td></tr>
  </tbody>
</table>
```

</details>

<details>
<summary>Indice 2 — <code>colspan</code> et <code>rowspan</code> sur un autre exemple</summary>

```html
<tr>
  <td colspan="2">Cette cellule prend la place de 2 colonnes</td>
</tr>
<tr>
  <td rowspan="2">Cette cellule descend sur 2 lignes</td>
  <td>A</td>
</tr>
<tr>
  <!-- Une seule cellule ici : la première colonne est déjà occupée par le rowspan -->
  <td>B</td>
</tr>
```

</details>

<details>
<summary>Indice 3 — Mon tableau est tout décalé !</summary>

Comptez les colonnes de chaque ligne : chaque ligne doit en occuper **5**.
- Une cellule `colspan="3"` compte pour 3.
- Une cellule `rowspan="2"` compte pour 1 sur sa ligne **et** pour 1 sur la ligne suivante : la ligne suivante doit donc avoir **une cellule de moins**.

</details>

## Bonus

- Ajoutez la famille des Cucurbitacées : Pastèque (fruit, 80 à 100 jours, besoin en eau moyen) et Concombre (fruit, 50 à 70 jours, besoin en eau élevé).
- Créez un second tableau « Mon budget semences » (graine, quantité, prix unitaire, total) avec le **total général** dans le `<tfoot>`.
- Pour aller plus loin en accessibilité : utilisez **un `<tbody>` par famille** et `<th scope="rowgroup">` pour le nom de la famille.

## Questions de compréhension

1. Quelle est la différence entre `<th>` et `<td>` ? À quoi sert l'attribut `scope` ?
2. À quoi servent `<thead>`, `<tbody>` et `<tfoot>`, alors que le tableau s'affiche presque pareil sans eux ?
3. Pourquoi ne faut-il **jamais** utiliser un tableau pour faire la mise en page d'un site (placer un menu à gauche, un contenu à droite…) ?
4. Comment un lecteur d'écran peut-il savoir que « 100 à 150 » est le cycle du riz ?

## Lien avec le brief PlantEvo

Le brief vous demande « 80 % d'images et 20 % de texte ». Un petit tableau comparatif bien construit permet de résumer beaucoup d'informations en peu de place, sans longs paragraphes. Et si vous en utilisez un, le critère « Structure et utilisation efficace des balises » s'applique aussi à lui : `caption`, `th` et `scope` compris !

## Ressources

- [MDN — Les bases des tableaux HTML](https://developer.mozilla.org/fr/docs/Learn/HTML/Tables/Basics)
- [MDN — Fonctionnalités avancées et accessibilité des tableaux](https://developer.mozilla.org/fr/docs/Learn/HTML/Tables/Advanced)
- MDN : [`<table>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/table) · [`<th>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/th) · [`<td>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/td)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [10 — Chasse aux bugs](../10-debogage/README.md)
