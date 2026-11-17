# Exercice 08 — La ferme pédagogique (mini-site)

**Niveau 2 · Pousse** · ★★☆☆ · Durée : 1 h 30 · Notions : arborescence d'un site, chemins relatifs, menu commun, `aria-current`

> La ferme pédagogique « Les Jeunes Pousses » accueille des classes pour découvrir l'agriculture. Elle vous demande un petit site de **4 pages** avec un menu identique sur chaque page. Cette fois, vous partez d'une feuille blanche : c'est vous qui créez les fichiers !

## Objectifs

- Organiser un site en **dossiers** et en **fichiers** (l'arborescence).
- Écrire les bons **chemins relatifs** selon l'endroit où se trouve la page (`../` pour remonter d'un dossier).
- Répéter le même en-tête et le même menu sur toutes les pages.
- Indiquer la page en cours dans le menu avec `aria-current="page"`.

## Fichiers fournis

```
08-mini-site/
├── README.md       ← cette consigne
└── images/
    ├── logo.svg    (120 × 120 px)
    ├── mais.svg    (400 × 300 px)
    ├── tomate.svg  (400 × 300 px)
    └── poule.svg   (400 × 300 px)
```

### Arborescence à obtenir

```
08-mini-site/
├── index.html            ← Accueil
├── pages/
│   ├── cultures.html     ← Nos cultures
│   ├── animaux.html      ← Nos animaux
│   └── infos.html        ← Infos pratiques
└── images/
```

## Consigne

**Étape 0 — Sur papier (10 min).** Dessinez :
- le **plan du site** : 4 rectangles (les pages) reliés par des flèches (les liens) ;
- une **maquette rapide** de la page d'accueil : où se trouvent le logo, le menu, le titre, l'image, le pied de page ?

Ensuite, sur l'ordinateur :

1. Dans VS Code, créez le dossier `pages/` et les 4 fichiers HTML vides de l'arborescence ci-dessus. Respectez les noms : **minuscules, sans espace, sans accent**.
2. Codez `index.html` :
   - la structure de base (`<!DOCTYPE html>`, `<head>` avec `charset`, `viewport` et un `<title>` explicite) ;
   - un `<header>` avec le logo (`images/logo.svg`) et le nom de la ferme ;
   - un `<nav>` avec une liste de 4 liens : Accueil, Nos cultures, Nos animaux, Infos pratiques ;
   - un `<main>` avec un `<h1>`, un paragraphe de présentation et au moins une image ;
   - un `<footer>` avec © 2026 et votre nom.
3. **Testez** les liens du menu de `index.html` avant d'aller plus loin (les pages sont encore vides, mais elles doivent s'ouvrir).
4. Copiez le `<header>`, le `<nav>` et le `<footer>` dans les 3 autres pages, puis **adaptez tous les chemins** : ces pages sont dans le dossier `pages/`, elles ne « voient » pas les fichiers de la même façon que `index.html`. Complétez d'abord ce tableau sur papier :

   | Depuis… | vers `index.html` | vers `pages/cultures.html` | vers `images/logo.svg` |
   |---|---|---|---|
   | `index.html` | `index.html` | `pages/cultures.html` | `images/logo.svg` |
   | `pages/animaux.html` | ? | ? | ? |

5. Dans le menu de chaque page, ajoutez `aria-current="page"` sur le lien de **la page en cours** (et uniquement celui-là).
6. Remplissez les pages :
   - **Nos cultures** : un `<h1>`, une courte introduction, le maïs et la tomate, chacun dans une `<figure>` avec une `<figcaption>` ;
   - **Nos animaux** : un `<h1>`, l'image de la poule, un paragraphe et une liste des animaux de la ferme ;
   - **Infos pratiques** : un `<h1>`, une adresse (inventée) dans une balise `<address>`, les horaires d'ouverture sous forme de liste et un lien `mailto:` vers `contact@example.com`.
7. À la fin du `<main>` de chaque page intérieure, ajoutez un lien « ← Retour à l'accueil ».
8. **Testez tous les liens** en remplissant cette grille (oui / non) :

   | Je suis sur… | Accueil | Nos cultures | Nos animaux | Infos pratiques | ← Retour | Logo affiché |
   |---|---|---|---|---|---|---|
   | `index.html` | | | | | — | |
   | `pages/cultures.html` | | | | | | |
   | `pages/animaux.html` | | | | | | |
   | `pages/infos.html` | | | | | | |

9. Passez **chacune** des 4 pages au validateur W3C.

## Critères de réussite

- [ ] Mon plan du site et ma maquette papier sont faits.
- [ ] L'arborescence est exactement celle demandée (noms en minuscules, sans espace ni accent).
- [ ] Les 4 pages ont le même `<header>`, le même `<nav>` et le même `<footer>`.
- [ ] Ma grille de test est entièrement verte : tous les liens et toutes les images fonctionnent depuis toutes les pages.
- [ ] Dans chaque menu, un seul lien porte `aria-current="page"` : celui de la page en cours.
- [ ] Chaque page a son propre `<title>` et son propre `<h1>`.
- [ ] Chaque image a un `alt` pertinent et des dimensions (`width`, `height`).
- [ ] Les 4 pages passent le validateur W3C sans erreur.

## Indices

<details>
<summary>Indice 1 — Les trois règles des chemins relatifs</summary>

Un chemin relatif part **toujours du dossier où se trouve la page en cours**.

| Je veux aller… | J'écris… | Exemple |
|---|---|---|
| vers un fichier du **même** dossier | `fichier.html` | `photo.svg` |
| vers un fichier dans un **sous-dossier** | `dossier/fichier.html` | `images/photo.svg` |
| vers un fichier du dossier **parent** (je remonte d'un cran) | `../fichier.html` | `../photo.svg` |

On peut combiner : `../images/photo.svg` = « je remonte d'un dossier, puis je descends dans `images/` ».

</details>

<details>
<summary>Indice 2 — À quoi ressemble <code>aria-current</code> ?</summary>

C'est un attribut que l'on ajoute sur un lien :

```html
<a href="exemple.html" aria-current="page">Exemple</a>
```

Il ne change rien à l'affichage pour l'instant, mais un lecteur d'écran annonce « page actuelle ». Plus tard, vous pourrez aussi le mettre en valeur avec du CSS.

</details>

<details>
<summary>Indice 3 — Copier-coller sans se tromper</summary>

1. Terminez et testez complètement le `<header>` et le `<nav>` de `index.html`.
2. Copiez-les dans `pages/cultures.html`, corrigez les chemins et testez.
3. Quand cette page fonctionne, copiez son en-tête et son menu dans les deux autres pages du dossier `pages/` : elles sont dans le même dossier, donc les chemins sont identiques. Il ne reste qu'à déplacer `aria-current`.

</details>

<details>
<summary>Indice 4 — Mon image ou ma page ne s'affiche pas</summary>

- Ouvrez les outils de développement (F12), onglet **Console** : une erreur `404 (Not Found)` indique le chemin qui ne fonctionne pas.
- Vérifiez les majuscules : `Images/Logo.svg` n'est pas `images/logo.svg` (sur un serveur, la différence compte).
- Depuis une page du dossier `pages/`, avez-vous pensé au `../` ?

</details>

## Bonus

- Rendez le logo cliquable : il ramène à l'accueil depuis n'importe quelle page. Quel `alt` faut-il alors lui donner ?
- Ajoutez une 5ᵉ page « Galerie » avec 4 images, et mettez à jour le menu des **5** pages… Vous comprenez maintenant pourquoi il vaut mieux bien réfléchir à son menu **avant** de coder !
- Sur la page d'accueil, ajoutez une liste « Au programme de la visite » dont chaque élément renvoie vers la page correspondante.

## Questions de compréhension

1. Pourquoi le même lien vers l'accueil s'écrit-il `index.html` dans une page et `../index.html` dans une autre ?
2. Quelle est la différence entre un chemin **relatif** (`../index.html`) et une adresse **absolue** (`https://www.exemple.com/index.html`) ? Quand utilise-t-on l'un ou l'autre ?
3. Si vous renommez `infos.html` en `contact.html`, que devez-vous modifier dans votre site ?
4. À quoi sert `aria-current="page"` ?

## Lien avec le brief PlantEvo

Le brief demande « une page d'accueil simple présentant le projet », « un menu statique avec des liens hypertexte » vers les différents types de végétaux et un lien pour « revenir au menu ». C'est exactement l'architecture de ce mini-site : page d'accueil + pages de détail + menu commun + lien de retour. Faites votre plan du site PlantEvo sur papier avant de coder, comme ici.

## Ressources

- [MDN — Créer des hyperliens (chemins relatifs et absolus)](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)
- [MDN — `<nav>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/nav) · [`<address>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/address) · [`<figure>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/figure)
- [MDN — `aria-current`](https://developer.mozilla.org/fr/docs/Web/Accessibility/ARIA/Attributes/aria-current)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [09 — Fiche comparative des cultures](../09-tableaux/README.md)
