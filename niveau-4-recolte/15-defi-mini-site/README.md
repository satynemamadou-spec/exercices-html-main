# Exercice 15 — Défi : le mini-site « Le marché des saveurs »

**Niveau 4 · Récolte** · ★★★★ · Durée : 3 h · Notions : toutes celles des exercices 01 à 14

> Le marché des saveurs, une coopérative de producteurs, veut un petit site vitrine pour présenter ses produits aux visiteurs du Salon de l'agriculture. Vous avez reçu deux maquettes et un cahier des charges. À vous de jouer, du papier jusqu'au site terminé !

Ce défi est une **répétition générale du brief PlantEvo** : même démarche (maquette → arborescence → code → tests → documentation), sur un autre sujet.

## Objectifs

- Partir d'une maquette pour construire un site de plusieurs pages.
- Réutiliser **seul** tout ce que vous avez appris : structure, sémantique, liens, ancres, images, tableau, formulaire.
- Tester et valider son travail (liens, validateur, Lighthouse).
- Documenter son projet dans un `README.md`.

## Fichiers fournis

```
15-defi-mini-site/
├── README.md                 ← cette consigne
├── maquettes/
│   ├── maquette-accueil.svg  ← maquette de la page d'accueil
│   └── maquette-categorie.svg← maquette d'une page catégorie
└── images/                   ← images de départ (SVG + photo optimisée)
    ├── logo.svg
    ├── mangue.svg  banane.svg  cacao.svg      (fruits)
    ├── tomate.svg  piment.svg  carotte.svg    (légumes)
    ├── mais.svg    riz.svg     sorgho.svg     (céréales)
    └── parcelle-800.jpg / .webp, parcelle-1600.jpg / .webp (photo d'accueil)
```

Ouvrez les deux maquettes dans votre navigateur (glisser-déposer le fichier) avant de commencer.

## Cahier des charges

### Arborescence attendue

```
15-defi-mini-site/
├── index.html            ← accueil
├── README.md             ← VOTRE documentation (remplace cette consigne : gardez-en une copie !)
├── pages/
│   ├── fruits.html
│   ├── legumes.html
│   ├── cereales.html
│   └── contact.html
└── images/
```

> **Astuce :** avant de remplacer ce `README.md` par votre documentation, renommez-le en `CONSIGNE.md`.

### Exigences fonctionnelles

| N° | Exigence |
|----|----------|
| F1 | **Accueil** : titre du site, image d'accueil, texte de présentation (2–3 phrases), une section « Nos catégories » avec 3 cartes (image + titre + phrase + lien) vers les pages catégories. |
| F2 | **Menu** identique sur les 5 pages (Accueil, Fruits, Légumes, Céréales, Contact). La page en cours est signalée avec `aria-current="page"`. |
| F3 | **Pages catégories** : un `<h1>`, une introduction courte, **au moins 3 produits** présentés en `<figure>` + `<figcaption>`. Règle du brief : **80 % d'images, 20 % de texte**. |
| F4 | Chaque page catégorie se termine par un lien **« ↑ Retour au menu »** qui ramène à la section « Nos catégories » de l'accueil (lien vers une ancre d'une autre page). |
| F5 | Au moins **un tableau** sur une des pages (exemple : origine des céréales, saisons des fruits…), avec `<caption>` et `<th>`. |
| F6 | **Contact** : un formulaire (nom, e-mail, sujet en liste déroulante, message, bouton d'envoi) et l'adresse (fictive) du marché. |
| F7 | Un **pied de page** sur toutes les pages : © année, votre nom, crédits des images. |

### Exigences techniques

| N° | Exigence |
|----|----------|
| T1 | Structure HTML complète sur chaque page (`DOCTYPE`, `lang`, `charset`, `viewport`, `<title>` différent pour chaque page). |
| T2 | Balises sémantiques : `<header>`, `<nav>`, `<main>`, `<footer>` (+ `<section>`, `<article>`, `<figure>` quand c'est pertinent). |
| T3 | Hiérarchie des titres respectée : un seul `<h1>` par page, pas de saut de niveau. |
| T4 | Images : `alt` pertinent, `width` et `height`, formats optimisés (SVG pour les illustrations, WebP + JPG de secours pour les photos), **chaque image < 200 Ko**, `loading="lazy"` pour les images sous la ligne de flottaison. |
| T5 | Noms de fichiers en minuscules, sans espace ni accent. |
| T6 | **0 erreur** au validateur W3C sur chaque page. |
| T7 | Score **Accessibilité ≥ 90** dans Lighthouse (page d'accueil). |
| T8 | Code indenté et commenté (un commentaire au début de chaque grande partie). |
| T9 | Pas de CSS obligatoire. Si vous avez déjà commencé le CSS, vous pouvez ajouter **une seule** feuille `style.css` (en bonus). |

## Étapes conseillées

1. **Maquette (30 min)** — Étudiez les deux maquettes fournies. Sur papier (ou Excalidraw / Figma), dessinez **la maquette de la page Contact**, qui n'est pas fournie. Annotez chaque bloc avec la balise que vous comptez utiliser.
2. **Arborescence (10 min)** — Créez les dossiers et les fichiers vides. Vérifiez les noms (T5).
3. **Squelette commun (30 min)** — Codez `index.html` avec seulement l'en-tête, le menu et le pied de page. Copiez ce squelette dans les 4 pages de `pages/`, puis **corrigez les chemins** (`../index.html`, `../images/logo.svg`…) et l'attribut `aria-current`.
4. **Contenu (1 h 15)** — Remplissez l'accueil, puis une page catégorie. Quand elle est terminée et testée, dupliquez-la pour les deux autres. Terminez par le contact.
5. **Tests (20 min)** — Remplissez la grille ci-dessous, passez chaque page au validateur, lancez Lighthouse.
6. **Documentation (20 min)** — Écrivez votre `README.md` (voir modèle plus bas).
7. **Bonus** — Publiez le site sur GitHub (dépôt + GitHub Pages).

### Grille de test des liens

Cliquez sur **chaque lien depuis chaque page** et cochez quand il fonctionne :

| Depuis ↓ / Vers → | Accueil | Fruits | Légumes | Céréales | Contact | Retour au menu |
|---|---|---|---|---|---|---|
| index.html | ☐ | ☐ | ☐ | ☐ | ☐ | — |
| fruits.html | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |
| legumes.html | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |
| cereales.html | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |
| contact.html | ☐ | ☐ | ☐ | ☐ | ☐ | — |

### Modèle de documentation (`README.md`)

```markdown
# Le marché des saveurs

## Description
(2–3 phrases : à quoi sert le site, pour qui)

## Arborescence
(copie de l'arborescence de votre dossier)

## Pages
- index.html : …
- pages/fruits.html : …

## Choix techniques
(ex. : pourquoi des SVG pour les illustrations, pourquoi <figure>, comment fonctionne le lien « Retour au menu »)

## Tests réalisés
- Validateur W3C : … erreur(s)
- Lighthouse accessibilité : …/100

## Difficultés rencontrées et solutions
…

## Crédits
(sources des images et des informations)
```

## Grille d'auto-évaluation (/20)

| Critère | Points | Mon score |
|---|---|---|
| **Structure & sémantique** — head complet (1), repères header/nav/main/footer (2), hiérarchie des titres (1), listes / figure / tableau bien utilisés (1) | 5 | |
| **Navigation** — menu sur toutes les pages (1), tous les liens fonctionnent (2), « Retour au menu » + `aria-current` (1) | 4 | |
| **Images** — `alt` pertinents (1), formats optimisés et poids < 200 Ko (2), `width`/`height` + `lazy` (1) | 4 | |
| **Formulaire** — labels et types adaptés (1), `name` + `required` (1) | 2 | |
| **Qualité du code** — 0 erreur au validateur (1), indentation + commentaires (1), nommage des fichiers (1) | 3 | |
| **Documentation** — README complet (1), crédits des images (1) | 2 | |
| **Total** | **20** | |

## Indices

<details>
<summary>Indice 1 — Le lien « Retour au menu » vers une autre page</summary>

Donnez un `id` à la section des catégories de l'accueil. Depuis une page de `pages/`, le lien doit d'abord **remonter d'un dossier**, puis viser la page, puis l'ancre : `chemin/vers/la-page.html#mon-id`. Revoyez l'exercice 07.
</details>

<details>
<summary>Indice 2 — Une carte de catégorie</summary>

Une carte est un bloc autonome qui a du sens tout seul : c'est un bon candidat pour `<article>`. Elle contient une image, un titre de niveau inférieur à celui de la section, une phrase et un lien.
</details>

<details>
<summary>Indice 3 — La photo d'accueil en WebP avec secours JPG</summary>

C'est le rôle de `<picture>` : une `<source>` avec `type="image/webp"`, puis un `<img>` classique en JPG. Revoyez l'exercice 13.
</details>

<details>
<summary>Indice 4 — Le logo cliquable</summary>

Un logo qui renvoie à l'accueil est une image dans un lien. Son `alt` doit décrire **la destination** du lien (par exemple « Accueil – Le marché des saveurs »), pas le dessin.
</details>

## Bonus

- **Image cliquable** : sur l'accueil, ajoutez une image dont les zones mènent aux 3 catégories (`<map>` / `<area>`, exercice 12), en plus du menu texte.
- **GitHub** : créez un dépôt, poussez votre site, activez GitHub Pages et testez tous les liens **en ligne** (attention aux majuscules dans les noms de fichiers !).
- **Oral** : préparez une présentation de 3 minutes sur **un** choix technique de votre site. C'est un entraînement à la soutenance du brief.

## Questions de compréhension

1. Pourquoi faut-il **une maquette** avant de coder ?
2. Pourquoi le chemin du logo n'est-il pas le même dans `index.html` et dans `pages/fruits.html` ?
3. Quelle différence entre `<section>` et `<article>` ? Donnez un exemple tiré de votre site.
4. Votre page fonctionne sur votre ordinateur mais pas sur GitHub Pages : citez deux causes possibles.

## Lien avec le brief PlantEvo

Tout y est : page d'accueil, menu, pages de détail à 80 % d'images, lien de retour au menu, images optimisées, code commenté, documentation technique et dépôt GitHub. Si vous réussissez ce défi, vous savez faire **toute la partie technique** du brief.

## Ressources

- [Validateur W3C (saisie directe)](https://validator.w3.org/#validate_by_input)
- [Squoosh — compresser ses images](https://squoosh.app)
- [MDN — Structure d'un document HTML](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
- [GitHub Pages — documentation](https://docs.github.com/fr/pages/getting-started-with-github-pages)

---

Bravo, vous avez terminé la série ! Retour au [sommaire des exercices](../../README.md).
