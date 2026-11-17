# Exercice 12 — Le plan de la ferme

**Niveau 3 · Arbre** · ★★★☆ · Durée : 45 min · Notions : `map`, `area`, `usemap`, `shape`, `coords`, ancres `#id`

> La ferme pédagogique veut un plan interactif : en cliquant sur une zone du plan (le champ, la mare, le poulailler…), le visiteur arrive directement sur l'explication de cette zone.

## Objectifs

- Transformer une image en **menu cliquable** avec `<map>` et `<area>`.
- Utiliser les trois formes de zones : rectangle, cercle et polygone.
- Lire des coordonnées en pixels sur une image.
- Combiner l'image cliquable avec des ancres (`href="#..."`) et des liens de retour.

## Fichiers fournis

```
12-image-cliquable/
├── README.md
├── index.html            ← la page à compléter (TODO)
└── images/
    └── plan-ferme.svg    ← le plan (800 × 500 px), avec un quadrillage tous les 50 px
```

## Consigne

Ouvrez `index.html` dans le navigateur : le plan s'affiche, suivi de 6 sections (une par zone). Pour l'instant, rien n'est cliquable.

1. **Relier l'image à une carte.** Ajoutez l'attribut `usemap="#plan"` sur l'image du plan, puis créez juste en dessous une balise `<map name="plan"></map>`.
2. **Donner un `id` à chaque section.** Ajoutez `id="champ"`, `id="serre"`, `id="mare"`, `id="verger"`, `id="poulailler"` et `id="accueil"` sur les 6 sections. Ajoutez aussi `id="plan"` sur la `<section>` qui contient l'image.
3. **Première zone : le champ de maïs (exemple donné).** Dans la `<map>`, ajoutez :

   ```html
   <area shape="rect" coords="50,50,350,250" href="#champ" alt="Champ de maïs">
   ```

   Testez : en cliquant sur le champ, la page descend jusqu'à la section du champ.
4. **Les autres zones.** À vous de trouver les coordonnées en lisant le **quadrillage** dessiné sur le plan (une ligne tous les 50 px, les nombres sont écrits en haut et à gauche) :
   - la **Serre** (rectangle) ;
   - la **Mare** (cercle) ;
   - le **Verger** (polygone à 4 sommets) ;
   - le **Poulailler** (rectangle, sans le toit) ;
   - l'**Accueil** (polygone en forme de maison, 5 sommets).
5. **Liens de retour.** À la fin de chaque section, ajoutez un lien « ↑ Retour au plan » qui ramène à `#plan`.
6. **Menu texte.** Sous l'image, ajoutez un `<nav>` avec une liste de liens texte vers les 6 zones. (Une image cliquable seule n'est pas accessible à tout le monde : il faut toujours proposer une alternative en texte.)
7. **Testez** chaque zone, chaque lien du menu texte et chaque lien de retour.

### Comment écrire les coordonnées ?

L'origine `0,0` est le **coin en haut à gauche** de l'image. `x` augmente vers la droite, `y` vers le bas.

| Forme | `shape` | `coords` | Exemple |
|---|---|---|---|
| Rectangle | `rect` | `x1,y1,x2,y2` → coin haut-gauche puis coin bas-droit | `coords="10,20,110,70"` |
| Cercle | `circle` | `x,y,r` → centre puis rayon | `coords="60,60,40"` |
| Polygone | `poly` | `x1,y1,x2,y2,x3,y3,…` → chaque sommet, dans l'ordre | `coords="0,0,100,0,50,80"` (triangle) |

## Critères de réussite

- [ ] L'image a `usemap="#plan"` et la `<map>` a `name="plan"`.
- [ ] Les 6 zones sont cliquables, chacune mène à la bonne section.
- [ ] J'ai utilisé au moins une fois `rect`, `circle` et `poly`.
- [ ] Chaque `<area>` a un `alt` qui décrit la destination.
- [ ] Chaque section a un lien « ↑ Retour au plan » qui fonctionne.
- [ ] Un menu texte (`<nav>`) propose les mêmes 6 liens.
- [ ] Le code passe le validateur W3C sans erreur.

## Indices

<details>
<summary>Indice 1 — Comment savoir si ma zone est bien placée ?</summary>

Passez la souris sur le plan : le curseur devient une **main** uniquement au-dessus des zones cliquables. Promenez la souris le long des bords de chaque zone pour vérifier.
</details>

<details>
<summary>Indice 2 — Le cercle de la mare</summary>

Repérez le **centre** du cercle sur le quadrillage, puis comptez combien de pixels il y a entre le centre et le bord : c'est le rayon.
</details>

<details>
<summary>Indice 3 — Les polygones</summary>

Partez d'un sommet, puis tournez autour de la forme dans le sens des aiguilles d'une montre en notant chaque sommet `x,y`. Ne refermez pas la forme : le navigateur relie automatiquement le dernier point au premier.
</details>

<details>
<summary>Indice 4 — Un clic ne fait rien ?</summary>

Vérifiez : le `#` est bien présent dans `usemap="#plan"` mais **pas** dans `name="plan"` ; l'`id` de la section est écrit exactement comme dans le `href` de l'area.
</details>

## Bonus

- Ajoutez une 7ᵉ zone de votre choix : le **chemin** (par exemple la portion verticale entre le champ et la serre).
- Ajoutez un attribut `title` sur chaque `<area>` : une bulle d'aide apparaît au survol.
- Réduisez la fenêtre du navigateur ou ajoutez `width="400" height="250"` sur l'image : les zones fonctionnent-elles encore au bon endroit ? Expliquez pourquoi.

## Questions de compréhension

1. Pourquoi les coordonnées ne fonctionnent-elles plus si l'image est affichée plus petite ? Quel problème cela pose-t-il sur téléphone ?
2. Pourquoi faut-il un `alt` sur chaque `<area>` ?
3. Quelle est la différence entre `usemap="#plan"` et `href="#plan"` ?

## Lien avec le brief PlantEvo

Le brief indique : « Ce menu pourra éventuellement être une **image cliquable** ». Vous savez maintenant le faire ! N'oubliez pas : un menu texte en plus de l'image, et un lien de retour au menu dans chaque partie.

## Ressources

- [MDN — `<map>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/map)
- [MDN — `<area>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/area)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [13 — Alléger ses images](../13-images-optimisees/README.md)
