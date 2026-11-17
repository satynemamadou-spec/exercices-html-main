# Exercice 13 — Alléger ses images

**Niveau 3 · Arbre** · ★★★☆ · Durée : 1 h · Notions : formats d'image, `width` / `height`, `loading="lazy"`, `<picture>`, `<source>`, `srcset`, `sizes`

> La page « Notre parcelle d'essai » met 30 secondes à s'afficher sur le téléphone des visiteurs du stand. La coupable : une seule photo de presque 6 Mo ! Votre mission : rendre la page beaucoup plus légère, sans perdre en qualité visible.

## Objectifs

- Mesurer le poids d'une page avec les outils de développement.
- Choisir le bon format selon le type d'image (photo, logo, schéma…).
- Toujours indiquer `width` et `height` pour éviter que la page « saute » au chargement.
- Proposer un format moderne (WebP) avec une solution de secours grâce à `<picture>`.
- Laisser le navigateur choisir la bonne taille d'image avec `srcset` et `sizes`.

## Fichiers fournis

```
13-images-optimisees/
├── README.md
├── avant.html                    ← la page lente (à analyser, ne pas modifier)
├── index.html                    ← la page à optimiser (TODO)
└── images/
    ├── parcelle-originale.png    ← la photo d'origine, très lourde
    ├── parcelle-400.jpg   parcelle-400.webp
    ├── parcelle-800.jpg   parcelle-800.webp
    ├── parcelle-1600.jpg  parcelle-1600.webp
    └── logo.svg
```

> **Attention :** pour cet exercice, ouvrez les pages avec **Live Server** (clic droit → « Open with Live Server ») plutôt qu'en double-cliquant : les mesures de l'onglet Réseau sont plus fiables.

## Consigne

### Partie A — Mesurer (sans coder)

1. **Analyser la page lente.** Ouvrez `avant.html`, puis les outils de développement (F12) → onglet **Réseau** (*Network*). Cochez **Désactiver le cache** (*Disable cache*) et rechargez la page (Ctrl + Maj + R). En bas de l'onglet, notez le **poids total transféré**.
   - Expérience : dans le menu de limitation (*No throttling*), choisissez **Slow 4G** et rechargez. Que voyez-vous ? Le texte sous la photo bouge-t-il au moment où l'image arrive ? Remettez ensuite *No throttling*.
2. **Comparer les fichiers.** Dans l'explorateur de fichiers (ou dans VS Code : clic droit sur le fichier → *Révéler dans l'explorateur*), relevez le poids de chaque image et complétez ce tableau dans un fichier `mesures.md` (ou sur papier) :

   | Fichier | Dimensions (px) | Poids |
   |---|---|---|
   | parcelle-originale.png | 2400 × 1600 | … |
   | parcelle-1600.jpg | 1600 × 1067 | … |
   | parcelle-1600.webp | 1600 × 1067 | … |
   | parcelle-800.jpg | 800 × 533 | … |
   | parcelle-800.webp | 800 × 533 | … |
   | parcelle-400.jpg | 400 × 267 | … |
   | parcelle-400.webp | 400 × 267 | … |

   Combien de fois `parcelle-800.webp` est-il plus léger que l'original ?
3. **Le bon format.** Pour chaque situation, quel format choisiriez-vous : **JPG**, **PNG**, **WebP** ou **SVG** ? (Plusieurs réponses sont parfois possibles.)

   | Situation | Format |
   |---|---|
   | Une photo d'un champ de maïs | … |
   | Le logo du site (formes simples, couleurs unies) | … |
   | Un schéma d'une fleur avec des flèches et des légendes | … |
   | Une capture d'écran avec du texte et un fond transparent | … |
   | Une icône de menu ☰ | … |

### Partie B — Coder (dans `index.html`)

4. **Une image bien dimensionnée.** Dans la section « La parcelle », affichez `images/parcelle-800.jpg` avec :
   - un `alt` qui décrit vraiment la photo ;
   - `width="800"` et `height="533"` (les dimensions réelles du fichier).

   Ces deux attributs permettent au navigateur de **réserver la place** de l'image avant son arrivée : le texte ne saute plus.
5. **WebP avec une solution de secours.** Remplacez votre `<img>` par une balise `<picture>` qui contient :
   - une `<source>` avec `type="image/webp"` et `srcset="images/parcelle-800.webp"` ;
   - **puis** votre `<img>` de l'étape 4 (le JPG), qui sert de secours pour les navigateurs qui ne connaissent pas le WebP.

   Rechargez : dans l'onglet Réseau, quel fichier a été téléchargé ?
6. **Laisser le navigateur choisir la taille.** Dans la `<source>` **et** dans l'`<img>`, remplacez le `srcset` par la liste des 3 tailles, avec leur largeur réelle suivie de `w`, et ajoutez l'attribut `sizes` :

   ```html
   srcset="images/parcelle-400.webp 400w, images/parcelle-800.webp 800w, images/parcelle-1600.webp 1600w"
   sizes="(max-width: 800px) 100vw, 800px"
   ```

   (Pour l'`<img>`, utilisez les fichiers `.jpg` et gardez `src="images/parcelle-800.jpg"`.)

   `sizes` dit au navigateur : « si l'écran fait 800 px de large ou moins, l'image occupe toute la largeur (`100vw`), sinon elle fait 800 px ». Le navigateur calcule alors quel fichier suffit.

   **Test** : outils de développement → icône **téléphone/tablette** (mode appareil, Ctrl + Maj + M) → choisissez *Responsive*, largeur **375**. Videz le cache et rechargez : quel fichier est téléchargé ? Essayez ensuite avec une largeur de 1200.
7. **Le chargement différé.** En bas de la page, dans la section « Souvenir de la récolte », affichez `images/parcelle-400.jpg` (400 × 267) avec l'attribut `loading="lazy"`. Le navigateur ne la télécharge que lorsque le visiteur s'en approche en faisant défiler la page.
   - **Attention :** ne mettez **pas** `loading="lazy"` sur l'image du haut de la page : elle doit s'afficher le plus vite possible !
   - Observez l'onglet Réseau en faisant défiler. (Le navigateur charge les images « lazy » un peu avant qu'elles n'arrivent à l'écran : si la page est courte, elle peut se charger tout de suite.)
8. **Comparer.** Mesurez le poids total de `index.html` comme à l'étape 1 et comparez avec `avant.html`.

### Partie C — Sur votre projet

9. **Squoosh.** Allez sur [squoosh.app](https://squoosh.app), déposez **une image de votre brief PlantEvo**, réduisez sa largeur (*Resize*, par exemple 1200 px), choisissez **WebP** avec une qualité d'environ 75. Objectif : **moins de 200 Ko** sans perte visible. Notez le poids avant / après.

## Critères de réussite

- [ ] Le tableau de mesures et le quiz des formats sont complétés.
- [ ] Toutes les `<img>` de `index.html` ont un `alt`, un `width` et un `height`.
- [ ] La photo principale est dans un `<picture>` : `<source type="image/webp">` d'abord, `<img>` JPG ensuite.
- [ ] `srcset` liste les 3 tailles avec leur largeur en `w`, et `sizes` est présent sur la `<source>` et l'`<img>`.
- [ ] Seule l'image du bas de page a `loading="lazy"`.
- [ ] La page optimisée pèse **au moins 50 fois moins** que `avant.html`.
- [ ] Une image de mon brief a été convertie en WebP et pèse moins de 200 Ko.
- [ ] Le code passe le validateur W3C sans erreur.

## Indices

<details>
<summary>Indice 1 — Où lire le poids total dans l'onglet Réseau ?</summary>

Tout en bas de l'onglet, une ligne indique par exemple : `5 requests | 5.8 MB transferred | …`. C'est le chiffre *transferred* (transféré) qui compte.
</details>

<details>
<summary>Indice 2 — L'ordre dans &lt;picture&gt;</summary>

Le navigateur lit les `<source>` dans l'ordre et prend **la première qu'il sait afficher**. L'`<img>` est toujours **la dernière** : elle est obligatoire, c'est elle qui porte le `alt`, le `width` et le `height`.

```html
<picture>
  <source type="image/avif" srcset="photo.avif">
  <img src="photo.jpg" alt="..." width="..." height="...">
</picture>
```
</details>

<details>
<summary>Indice 3 — Pourquoi un fichier de 800 px sur un écran de 375 px ?</summary>

Beaucoup de téléphones ont un écran « haute densité » : 2 ou 3 pixels physiques pour 1 pixel CSS. Une image affichée sur 375 px CSS a alors besoin de 750 ou 1125 pixels réels pour être nette. Le navigateur en tient compte ! Dans le mode appareil, le menu ⋮ → *Add device pixel ratio* permet de changer cette densité (DPR).
</details>

<details>
<summary>Indice 4 — Le fichier téléchargé ne change pas</summary>

Le navigateur garde en mémoire les images déjà téléchargées. Cochez **Désactiver le cache**, puis rechargez avec Ctrl + Maj + R.
</details>

## Bonus

- Avec Squoosh, créez une version **AVIF** de `parcelle-800.jpg` et ajoutez une `<source type="image/avif">` **avant** la source WebP. Comparez les poids.
- Ouvrez `images/logo.svg` dans VS Code : c'est du texte ! Pourquoi un logo en SVG reste-t-il net quelle que soit sa taille ?
- Lancez un audit **Lighthouse** (outils de développement → *Lighthouse* → *Performance*) sur `avant.html` puis sur `index.html` et comparez les scores.

## Questions de compréhension

1. Pourquoi un PNG n'est-il pas adapté pour une photo ?
2. À quoi servent `width` et `height` si l'image a déjà sa propre taille ?
3. Quelle est la différence entre `srcset` (avec des `w`) et `sizes` ? Lequel décrit les fichiers, lequel décrit l'affichage ?
4. Pourquoi ne faut-il pas mettre `loading="lazy"` sur l'image principale en haut de page ?

## Lien avec le brief PlantEvo

Votre page doit contenir **80 % d'images**, et les critères de performance demandent des « formats d'image optimisés » et des fichiers légers. Appliquez cette méthode à **toutes** les images de votre projet : bonne taille, bon format, `width`/`height`, et `loading="lazy"` pour celles qui sont loin dans la page.

## Ressources

- [MDN — `<picture>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/picture)
- [MDN — `<img>` : `srcset`, `sizes`, `loading`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/img)
- [MDN — Guide des types et formats de fichiers image](https://developer.mozilla.org/fr/docs/Web/Media/Formats/Image_types)
- [Squoosh — compresser et convertir ses images](https://squoosh.app)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [14 — Audit d'accessibilité](../14-accessibilite/README.md)
