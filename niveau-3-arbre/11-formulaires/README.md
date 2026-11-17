# Exercice 11 — Inscription aux ateliers de l'exposition

**Niveau 3 · Arbre** · ★★★☆ · Durée : 1 h · Notions : `form`, `label`, `input`, `select`, `textarea`, `fieldset`, `legend`, `button`

> Votre stand à l'exposition agricole propose des ateliers gratuits. Les visiteurs doivent pouvoir s'inscrire en ligne. Vous allez créer le formulaire d'inscription.

## Objectifs

- Construire un formulaire complet avec les bons types de champs.
- Relier chaque champ à son étiquette (`<label for>` + `id`).
- Comprendre à quoi sert l'attribut `name` en observant les données envoyées.
- Utiliser la validation intégrée du navigateur (`required`, `type="email"`, `min`, `max`).

## Fichiers fournis

```
11-formulaires/
├── README.md
├── index.html   ← le formulaire à construire (TODO)
└── merci.html   ← page de confirmation (déjà prête, ne pas modifier)
```

## Consigne

Travaillez dans `index.html`. Chaque étape correspond à un `TODO` du fichier.

1. **Le formulaire.** Créez une balise `<form>` avec `action="merci.html"` et `method="get"`. Tous les champs suivants vont **à l'intérieur**.
2. **Bloc « Vos informations ».** Créez un `<fieldset>` avec la légende (`<legend>`) « Vos informations », puis :
   - un champ **Nom** (texte, obligatoire) ;
   - un champ **Prénom** (texte) ;
   - un champ **E-mail** (type `email`, obligatoire) ;
   - un champ **Téléphone** (type `tel`).
3. **Bloc « Votre visite ».** Un deuxième `<fieldset>` avec :
   - la **date de visite** (type `date`) ;
   - le **créneau** : deux boutons radio « Matin » et « Après-midi » (un seul choix possible !) ;
   - l'**atelier** choisi, dans une liste déroulante `<select>` : Les semences, Le compost, L'irrigation goutte-à-goutte, Les plantes médicinales ;
   - le **nombre de personnes** (type `number`, de 1 à 10).
4. **Bloc « Vos centres d'intérêt ».** Un troisième `<fieldset>` avec quatre cases à cocher : Agriculture, Environnement, Numérique, Cuisine (plusieurs choix possibles).
5. **Message.** Ajoutez une zone de texte `<textarea>` « Votre message ou vos questions » (5 lignes).
6. **Consentement.** Ajoutez une case à cocher **obligatoire** : « J'accepte d'être recontacté(e) au sujet de mon inscription ».
7. **Boutons.** Ajoutez un bouton « Envoyer mon inscription » (`type="submit"`) et un bouton « Effacer » (`type="reset"`).
8. **Testez !**
   - Cliquez sur « Envoyer » avec le formulaire vide : que se passe-t-il ?
   - Tapez un e-mail sans `@` : que dit le navigateur ?
   - Remplissez tout correctement et envoyez. Sur la page `merci.html`, **regardez la barre d'adresse** : vous y voyez vos données sous la forme `name=valeur&name=valeur…`. Retrouvez chacun de vos champs.

> **À savoir :** rien n'est vraiment envoyé : il n'y a pas de serveur pour recevoir les données. Le traitement des formulaires côté serveur (back-end) viendra plus tard dans la formation. Pour l'instant, on construit la partie visible.

**Règle d'or** : chaque champ a un `<label>` dont l'attribut `for` est égal à l'`id` du champ, **et** un attribut `name`.

## Critères de réussite

- [ ] Tous les champs sont à l'intérieur d'un seul `<form action="merci.html" method="get">`.
- [ ] Il y a 3 `<fieldset>`, chacun avec sa `<legend>`.
- [ ] Chaque champ a un `<label>` relié (cliquer sur le texte du label place le curseur dans le champ ou coche la case).
- [ ] Chaque champ a un attribut `name` (vérifiez dans la barre d'adresse après l'envoi).
- [ ] Les deux boutons radio ont le **même** `name` : on ne peut en cocher qu'un seul.
- [ ] Le nom, l'e-mail et le consentement sont obligatoires (`required`).
- [ ] Le nombre de personnes est limité de 1 à 10.
- [ ] Le formulaire vide ne peut pas être envoyé.
- [ ] Le code passe le validateur W3C sans erreur.

## Indices

<details>
<summary>Indice 1 — Relier un label à un champ</summary>

Le `for` du label et l'`id` du champ doivent être **identiques** :

```html
<label for="ville">Ville</label>
<input type="text" id="ville" name="ville">
```

Le `name`, lui, sert à nommer la donnée envoyée : dans l'URL, vous verrez `ville=` suivi de ce que l'utilisateur a tapé.
</details>

<details>
<summary>Indice 2 — Les boutons radio</summary>

Les boutons radio d'un même groupe partagent le **même `name`** mais ont chacun un `id` différent et une `value` différente. C'est la `value` du bouton coché qui est envoyée.

```html
<input type="radio" id="taille-s" name="taille" value="s">
<label for="taille-s">Petit</label>
```
</details>

<details>
<summary>Indice 3 — La liste déroulante</summary>

Un `<select>` contient des `<option>`. Le texte de l'option est ce que voit l'utilisateur, la `value` est ce qui est envoyé.

```html
<select id="couleur" name="couleur">
  <option value="">-- Choisissez --</option>
  <option value="vert">Vert</option>
</select>
```
</details>

<details>
<summary>Indice 4 — Limiter un nombre</summary>

Regardez les attributs `min` et `max` de `<input type="number">`.
</details>

## Bonus

- Ajoutez l'attribut `autocomplete` sur le nom, l'e-mail et le téléphone (`autocomplete="family-name"`, `"email"`, `"tel"`) : le navigateur propose de remplir automatiquement.
- Ouvrez la page sur votre téléphone (ou dans le mode « appareil mobile » des outils de développement, F12) : le clavier change-t-il pour les champs `email`, `tel` et `number` ?
- Ajoutez un champ « Ville » avec une liste de suggestions grâce à `<datalist>`.
- Utilisez l'attribut `pattern` pour exiger un numéro de téléphone de 10 chiffres.

## Questions de compréhension

1. Quelle est la différence entre l'attribut `id` et l'attribut `name` d'un champ ?
2. Pourquoi est-il important d'utiliser `<label>` plutôt qu'un simple texte à côté du champ ? (Pensez aux personnes aveugles et aux écrans tactiles.)
3. Quelle différence voyez-vous entre `method="get"` et `method="post"` ? Pourquoi ne faut-il **jamais** envoyer un mot de passe avec `get` ?
4. La validation du navigateur (`required`, `type="email"`) suffit-elle à protéger un site ? Pourquoi ?

## Lien avec le brief PlantEvo

Votre page d'exposition peut proposer un petit formulaire « Laissez-nous votre avis » ou « Posez une question au stand ». Des champs bien étiquetés rendent la page utilisable par tous les visiteurs.

## Ressources

- [MDN — `<form>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/form)
- [MDN — `<input>` et ses types](https://developer.mozilla.org/fr/docs/Web/HTML/Element/input)
- [MDN — `<label>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/label)
- [MDN — `<select>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/select)
- [MDN — `<fieldset>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/fieldset)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [12 — Le plan de la ferme](../12-image-cliquable/README.md)
