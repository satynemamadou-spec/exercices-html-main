# Exercice 14 — Audit d'accessibilité

**Niveau 3 · Arbre** · ★★★☆ · Durée : 1 h · Notions : accessibilité (a11y), `lang`, `title`, `meta description`, `alt`, hiérarchie des titres, `label`, `caption` / `th`, repères sémantiques, Lighthouse

> Le site du « Marché bio du quartier » fonctionne… pour certains visiteurs seulement. Une personne aveugle qui utilise un lecteur d'écran, ou quelqu'un qui navigue uniquement au clavier, s'y perd complètement. Vous êtes chargé(e) de l'**audit** : trouver les problèmes, les corriger et prouver que la page s'est améliorée.

## Objectifs

- Comprendre pourquoi l'accessibilité concerne **tout le monde** (handicap, téléphone, connexion lente, moteurs de recherche).
- Utiliser un outil d'audit automatique (Lighthouse) et savoir qu'il ne détecte pas tout.
- Naviguer dans une page uniquement au clavier.
- Corriger une page avec une checklist de 10 points.

## Fichiers fournis

```
14-accessibilite/
├── README.md
├── index.html        ← la page à auditer et à corriger (pleine de problèmes !)
└── images/
    ├── logo.svg  tomate.svg  mangue.svg  mais.svg
    └── feuille-deco.svg
```

> **À savoir :** la page est **volontairement** mal construite. Passez-la d'abord au validateur W3C : il n'affiche qu'un avertissement (la langue manquante)… alors que la page contient plus de dix problèmes ! Une page « valide » n'est pas forcément une page accessible.

## Consigne

1. **Mesurer avant de corriger.** Ouvrez `index.html` avec **Live Server** (Lighthouse ne fonctionne pas bien sur un fichier ouvert par double-clic). Dans Chrome ou Edge : F12 → onglet **Lighthouse** → cochez **Accessibilité** et **SEO** → *Analyser*. Notez les deux scores et la liste des problèmes trouvés.
   - Sous Firefox : F12 → onglet **Accessibilité** → *Vérifier les problèmes* → *Tous les problèmes*.
2. **Le test du clavier.** Rechargez la page, posez la souris, et naviguez **uniquement avec la touche Tab** (Maj + Tab pour reculer, Entrée pour cliquer). Que se passe-t-il quand vous arrivez sur le logo ? Le champ de recherche dit-il ce qu'il faut y taper ?
3. **Corriger** la page en suivant la checklist ci-dessous. Gardez le même contenu, changez les balises et les attributs.
4. **Mesurer après.** Relancez Lighthouse. Objectif : **95 ou plus** en accessibilité. Comparez avec vos scores de l'étape 1.
5. **Rédiger** un mini-rapport (5 lignes, dans un fichier `audit.md` ou sur papier) : scores avant / après, les 3 problèmes qui vous semblent les plus graves et pourquoi.

### La checklist d'accessibilité (10 points)

| # | Point à vérifier | Question à se poser |
|---|---|---|
| 1 | **Langue** | La balise `<html>` indique-t-elle la langue de la page ? |
| 2 | **Titre** | Le `<title>` décrit-il vraiment la page (et pas « Document ») ? |
| 3 | **Description** | Y a-t-il une `<meta name="description">` qui résume la page en une ou deux phrases ? |
| 4 | **Images** | Chaque `alt` décrit-il le contenu de l'image ? Les images purement décoratives ont-elles `alt=""` ? |
| 5 | **Titres** | Un seul `<h1>` ? Les niveaux se suivent-ils sans saut (h1 → h2 → h3) ? Les titres sont-ils de vrais `<h2>`… et pas du texte en gras ? |
| 6 | **Liens** | Le texte de chaque lien indique-t-il sa destination, même lu seul (pas de « cliquez ici ») ? Chaque lien-image a-t-il un nom ? |
| 7 | **Formulaires** | Chaque champ a-t-il un `<label>` relié ? (Un `placeholder` ne suffit pas.) |
| 8 | **Tableaux** | Le tableau a-t-il une légende `<caption>` et des en-têtes `<th>` avec `scope` ? |
| 9 | **Repères** | La page utilise-t-elle `<header>`, `<nav>`, `<main>` et `<footer>` au lieu de `<div>` ? |
| 10 | **Nouvel onglet** | Les liens qui ouvrent un nouvel onglet préviennent-ils l'utilisateur ? |

## Critères de réussite

- [ ] J'ai noté les scores Lighthouse **avant** et **après** correction.
- [ ] Les 10 points de la checklist sont respectés.
- [ ] Au clavier, chaque lien et chaque champ est atteignable et compréhensible.
- [ ] Le score Lighthouse Accessibilité est de **95 ou plus**.
- [ ] Le code passe le validateur W3C sans erreur ni avertissement.
- [ ] Mon mini-rapport d'audit est rédigé.

## Indices

<details>
<summary>Indice 1 — Un lien qui contient seulement une image</summary>

Quand un lien ne contient qu'une image, c'est le `alt` de l'image qui donne son nom au lien. Si le `alt` est vide, le lecteur d'écran annonce juste « lien »… vers où ? Décrivez **la destination** du lien, pas le dessin.
</details>

<details>
<summary>Indice 2 — Image informative ou décorative ?</summary>

Posez-vous la question : « Si l'image disparaît, est-ce que je perds une information ? »

- Oui → `alt` qui décrit l'information (« Une tomate rouge bien mûre »).
- Non, elle est là pour faire joli → `alt=""` (vide, mais présent !).

Un `alt` comme `"image"` ou `"photo1.svg"` n'apporte rien : c'est comme s'il n'y en avait pas.
</details>

<details>
<summary>Indice 3 — Le titre en gras</summary>

`<p><b>Nos produits</b></p>` *ressemble* à un titre pour les yeux, mais pour un lecteur d'écran ou un moteur de recherche, c'est un simple paragraphe. Les personnes aveugles naviguent souvent de titre en titre : ce titre-là est invisible pour elles.
</details>

<details>
<summary>Indice 4 — Où mettre l'avertissement « nouvel onglet » ?</summary>

Le plus simple : dans le texte du lien lui-même, par exemple « … (nouvel onglet) ».
</details>

## Bonus

- Ajoutez un **lien d'évitement** tout en haut de la page : « Aller au contenu principal », qui pointe vers l'`id` de votre `<main>`. Testez-le avec la touche Tab.
- Écoutez votre page avec un **lecteur d'écran** : NVDA (Windows, gratuit), Orca (Linux), VoiceOver (Mac : Cmd + F5). Comparez la version avant et après.
- Faites l'audit Lighthouse de **votre page PlantEvo** et corrigez les problèmes trouvés.

## Questions de compréhension

1. Citez trois types de personnes qui profitent d'une page accessible (pas seulement des personnes en situation de handicap).
2. Pourquoi un score Lighthouse de 100 ne garantit-il pas qu'une page est accessible ?
3. Quelle est la différence entre `alt=""` et l'absence d'attribut `alt` ?
4. En quoi l'accessibilité aide-t-elle aussi le référencement (SEO) ?

## Lien avec le brief PlantEvo

Votre site servira d'**outil pédagogique pour tous les visiteurs** du stand. Avec 80 % d'images, les textes alternatifs sont essentiels : sans eux, une grande partie de votre page est vide pour un lecteur d'écran. Passez cette checklist sur votre projet avant la présentation : c'est aussi un critère de « convivialité de l'interface ».

## Ressources

- [MDN — Qu'est-ce que l'accessibilité ?](https://developer.mozilla.org/fr/docs/Learn/Accessibility/What_is_accessibility)
- [MDN — HTML : une bonne base pour l'accessibilité](https://developer.mozilla.org/fr/docs/Learn/Accessibility/HTML)
- [MDN — `<img>` et l'attribut `alt`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/img)
- [Chrome — Présentation de Lighthouse](https://developer.chrome.com/docs/lighthouse/overview?hl=fr)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [15 — Défi : le marché des saveurs](../../niveau-4-recolte/15-defi-mini-site/README.md)
