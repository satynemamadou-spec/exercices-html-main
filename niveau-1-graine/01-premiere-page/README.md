# Exercice 01 — Ma première page web

**Niveau 1 · Graine** · ★☆☆☆ · Durée : 20 min · Notions : `<!DOCTYPE>`, `<html>`, `<head>`, `<body>`, `<meta charset>`, `<title>`, `<h1>`, `<p>`, commentaires

> Vous démarrez votre parcours de développeur web. Première mission : créer, de A à Z, une page qui vous présente.

## Objectifs

- Créer un fichier HTML dans VS Code et l'ouvrir dans un navigateur.
- Connaître par cœur la structure de base d'une page HTML.
- Comprendre la différence entre `<head>` (informations sur la page) et `<body>` (contenu affiché).
- Utiliser les outils du navigateur : code source et inspecteur.

## Fichiers fournis

Aucun ! Ce dossier ne contient que cette consigne. C'est vous qui créez le fichier.

## Consigne

1. Ouvrez ce dossier (`01-premiere-page`) dans VS Code (**Fichier → Ouvrir le dossier…**).
2. Créez un nouveau fichier nommé exactement `index.html` (en minuscules, sans espace).
3. Écrivez **à la main** (sans copier-coller, sans raccourci) la structure de base d'une page :
   - la ligne `<!DOCTYPE html>` ;
   - la balise `<html>` avec l'attribut `lang="fr"` ;
   - un `<head>` qui contient :
     - `<meta charset="UTF-8">`,
     - `<meta name="viewport" content="width=device-width, initial-scale=1.0">`,
     - un `<title>` : `Ma première page — Votre prénom` ;
   - un `<body>` (vide pour l'instant).
4. Dans le `<body>`, ajoutez un titre principal `<h1>` : `Bonjour, je m'appelle …` (avec votre prénom).
5. Sous le titre, ajoutez un paragraphe `<p>` de 2 ou 3 phrases : qui vous êtes, pourquoi vous voulez devenir développeur ou développeuse web, et un fruit ou une plante que vous aimez.
6. Juste au-dessus du `<h1>`, ajoutez un commentaire HTML : `<!-- Titre principal de la page -->`.
7. Enregistrez (`Ctrl + S`) et ouvrez la page dans le navigateur :
   - avec l'extension **Live Server** (clic droit sur le fichier → *Open with Live Server*),
   - ou par double-clic sur le fichier dans l'explorateur de fichiers.
8. Vérifiez :
   - le texte de votre `<title>` s'affiche dans l'**onglet** du navigateur ;
   - les accents (é, è, à, ç…) s'affichent correctement ;
   - le commentaire n'apparaît **pas** sur la page.
9. **Expérience** : supprimez la ligne `<meta charset="UTF-8">`, enregistrez, puis ouvrez la page **par double-clic**. Que deviennent les accents ? (Le résultat peut varier selon le navigateur.) Remettez ensuite la ligne.
10. Affichez le code source de la page (`Ctrl + U`), puis ouvrez l'inspecteur (`F12` ou clic droit → *Inspecter*). Repérez votre `<h1>` dans l'inspecteur.

## Critères de réussite

- [ ] Le fichier s'appelle `index.html` et se trouve dans le dossier `01-premiere-page`.
- [ ] La première ligne est `<!DOCTYPE html>`.
- [ ] La balise `<html>` a l'attribut `lang="fr"`.
- [ ] Le `<head>` contient `meta charset`, `meta viewport` et un `<title>` personnalisé.
- [ ] Le `<body>` contient exactement un `<h1>` et au moins un `<p>`.
- [ ] Chaque balise ouverte est fermée (sauf `<meta>`, qui n'a pas de balise fermante).
- [ ] Le code est indenté : chaque balise « enfant » est décalée de 2 espaces par rapport à son « parent ».
- [ ] Les accents s'affichent correctement dans le navigateur.

## Indices

<details>
<summary>Indice 1 — Dans quel ordre écrire les balises ?</summary>

Pensez à des boîtes rangées les unes dans les autres : `<html>` contient `<head>` et `<body>`. Le `<head>` se trouve **avant** le `<body>`. On ferme toujours une boîte avant de fermer celle qui la contient.

</details>

<details>
<summary>Indice 2 — Rien ne s'affiche ?</summary>

- Avez-vous bien enregistré le fichier (`Ctrl + S`) ? Un point blanc à côté du nom de l'onglet dans VS Code signifie « non enregistré ».
- Votre texte est-il bien **dans** le `<body>` ? Ce qui est dans le `<head>` ne s'affiche pas sur la page.
- L'extension du fichier est-elle bien `.html` (et pas `.html.txt`) ?

</details>

<details>
<summary>Indice 3 — Le raccourci Emmet (pour la suite)</summary>

Une fois que vous savez écrire la structure de mémoire, VS Code peut la générer pour vous : tapez `!` puis appuyez sur `Tab`. Pensez ensuite à remplacer `lang="en"` par `lang="fr"`.

</details>

## Bonus

- Ajoutez un deuxième paragraphe : ce que vous aimeriez créer comme site web à la fin de la formation.
- Créez une copie de votre fichier et changez seulement le `<title>`. Ouvrez les deux pages dans deux onglets : voyez-vous la différence ?

## Questions de compréhension

1. Quelle est la différence entre le `<head>` et le `<body>` ?
2. À quoi sert l'attribut `lang="fr"` ? (Pensez aux lecteurs d'écran et aux moteurs de recherche.)
3. À quoi sert la ligne `<!DOCTYPE html>` ?
4. Pourquoi est-il utile d'écrire des commentaires dans son code, alors qu'ils ne s'affichent pas ?

## Lien avec le brief PlantEvo

Toutes les pages de votre projet PlantEvo Viewer commencent par cette structure. Le jury regardera votre code source : un squelette propre et bien indenté est la première chose qu'il verra.

## Ressources

- [MDN — Structure d'un document HTML](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Getting_started)
- [MDN — `<head>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/head)
- [MDN — `<title>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/title)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [02 — Titres et paragraphes](../02-titres-paragraphes/README.md)
