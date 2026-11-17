# Exercice 04 — Les liens

**Niveau 1 · Graine** · ★☆☆☆ · Durée : 40 min · Notions : `<a>`, `href`, chemins relatifs et absolus, `../`, `target="_blank"`, `mailto:`

> La ferme Bel Avenir a trois pages web… mais impossible de passer de l'une à l'autre ! Votre mission : relier les pages entre elles et vers l'extérieur.

## Objectifs

- Créer un lien vers une autre page du site avec un **chemin relatif**.
- Savoir descendre dans un dossier (`dossier/page.html`) et remonter d'un dossier (`../page.html`).
- Créer un lien vers un autre site (**URL absolue**) qui s'ouvre dans un nouvel onglet.
- Créer un lien e-mail avec `mailto:`.
- Écrire des textes de liens clairs.

## Fichiers fournis

```
04-liens/
├── README.md
├── index.html        ← page d'accueil
├── cultures.html     ← page « Nos cultures »
└── pages/
    └── contact.html  ← page « Nous contacter » (rangée dans un sous-dossier)
```

## À lire avant de commencer : les chemins

Un lien s'écrit avec la balise `<a>` et l'attribut `href` (la destination) :

```html
<a href="destination">Texte cliquable</a>
```

Il existe deux sortes de destinations :

- **URL absolue** : l'adresse complète d'une page sur Internet, qui commence par `https://`. Exemple : `https://developer.mozilla.org`.
- **Chemin relatif** : le chemin vers un fichier de **votre** site, calculé **à partir de la page où se trouve le lien**.

Prenons un autre site comme exemple :

```
mon-site/
├── accueil.html
├── images/
│   └── logo.png
└── blog/
    └── article.html
```

| Le lien est dans… | Il pointe vers… | Chemin à écrire | Règle |
|---|---|---|---|
| `accueil.html` | `images/logo.png` | `images/logo.png` | On **descend** dans le dossier `images` |
| `blog/article.html` | `accueil.html` | `../accueil.html` | `../` = on **remonte** d'un dossier |
| `blog/article.html` | `images/logo.png` | `../images/logo.png` | On remonte, puis on redescend |

**Attention aux noms de fichiers** : pas d'espace, pas d'accent, pas de majuscule (`nos-cultures.html` plutôt que `Nos Cultures.html`). Sur un serveur, `Contact.html` et `contact.html` sont deux fichiers différents !

## Consigne

Les numéros correspondent aux commentaires `TODO` dans les fichiers.

1. Dans `index.html`, transformez « Nos cultures » en lien vers `cultures.html`.
2. Dans `index.html`, transformez « Nous contacter » en lien vers la page `contact.html` rangée dans le dossier `pages`.
3. Dans `cultures.html`, ajoutez en haut de la page un lien « ← Retour à l'accueil » vers `index.html`.
4. Dans `pages/contact.html` :
   - le lien « ← Retour à l'accueil » ne fonctionne pas. Cliquez dessus, observez l'adresse dans la barre du navigateur, trouvez l'erreur et corrigez-la ;
   - ajoutez en bas de la page un lien vers la page « Nos cultures ».
5. Dans `index.html`, transformez « le site de la FAO » en lien vers `https://www.fao.org/home/fr`. Ce lien doit s'ouvrir dans un **nouvel onglet** : ajoutez `target="_blank"` et `rel="noopener"`.
6. Dans `pages/contact.html`, transformez l'adresse `contact@example.com` en lien e-mail : `href="mailto:contact@example.com"`. Cliquez dessus : que se passe-t-il ?
7. Dans `cultures.html`, le lien « cliquez ici » n'est pas clair (imaginez une personne aveugle qui écoute la liste des liens de la page : elle entendrait seulement « cliquez ici »). Réécrivez la phrase pour que le texte du lien décrive sa destination, par exemple : « Lire [l'article de Wikipédia sur l'agriculture] ».
8. **Testez tous vos liens** en remplissant ce tableau (recopiez-le sur papier ou dans un fichier) :

| Page de départ | Lien | Destination attendue | Fonctionne ? |
|---|---|---|---|
| `index.html` | Nos cultures | `cultures.html` | |
| `index.html` | Nous contacter | `pages/contact.html` | |
| `index.html` | Site de la FAO | fao.org (nouvel onglet) | |
| `cultures.html` | Retour à l'accueil | `index.html` | |
| `cultures.html` | Article Wikipédia | wikipedia.org | |
| `pages/contact.html` | Retour à l'accueil | `index.html` | |
| `pages/contact.html` | Nos cultures | `cultures.html` | |
| `pages/contact.html` | Adresse e-mail | logiciel de messagerie | |

## Critères de réussite

- [ ] Les 8 liens du tableau fonctionnent.
- [ ] Tous les liens internes utilisent des chemins **relatifs** (aucun `C:\…` ni `file:///…`).
- [ ] Le lien de retour de `pages/contact.html` utilise `../`.
- [ ] Le lien vers la FAO s'ouvre dans un nouvel onglet et contient `rel="noopener"`.
- [ ] Le lien e-mail commence par `mailto:`.
- [ ] Plus aucun lien « cliquez ici » : chaque texte de lien a du sens tout seul.

## Indices

<details>
<summary>Indice 1 — Le lien de retour de la page contact</summary>

Regardez où se trouve le fichier `contact.html` : dans le dossier `pages`. Le navigateur cherche donc `index.html` **dans le dossier `pages`**… où il n'existe pas. Relisez la deuxième ligne du tableau des chemins.

</details>

<details>
<summary>Indice 2 — Mon lien affiche « Fichier introuvable » ou une page d'erreur</summary>

- Vérifiez l'orthographe exacte du nom de fichier (majuscules, `s` final, extension `.html`).
- Demandez-vous : « Depuis le dossier de **cette** page, comment j'arrive au fichier visé ? »
- Regardez l'adresse dans la barre du navigateur après le clic : elle montre le chemin que le navigateur a essayé.

</details>

<details>
<summary>Indice 3 — Il ne se passe rien quand je clique sur le lien mailto</summary>

C'est normal si aucun logiciel de messagerie n'est configuré sur votre ordinateur. Le lien est quand même correct si vous voyez `mailto:contact@example.com` en survolant le lien (en bas à gauche du navigateur).

</details>

## Bonus

- Ajoutez un lien de téléphone avec `href="tel:…"` (pratique sur mobile : un clic lance l'appel).
- Ajoutez l'attribut `title` sur le lien de la FAO pour afficher une info-bulle : `title="Ouvre un nouvel onglet"`.
- Créez une quatrième page `pages/visite.html`, et reliez-la aux trois autres pages (dans les deux sens).

## Questions de compréhension

1. Quelle est la différence entre un chemin relatif et une URL absolue ? Quand utilise-t-on l'un ou l'autre ?
2. Que signifie `../` dans un chemin ?
3. Pourquoi faut-il éviter les espaces et les majuscules dans les noms de fichiers ?
4. Pourquoi « cliquez ici » est-il un mauvais texte de lien ?

## Lien avec le brief PlantEvo

Le brief demande « un menu statique avec des liens hypertexte » et, sur chaque page de détail, « un lien permettra de revenir au menu ». C'est exactement ce que vous venez de faire. Le brief demande aussi de « minimiser le nombre de liens externes » : utilisez-les seulement quand ils apportent vraiment quelque chose.

## Ressources

- [MDN — `<a>` : l'élément d'ancre](https://developer.mozilla.org/fr/docs/Web/HTML/Element/a)
- [MDN — Créer des hyperliens](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)
- [Validateur W3C](https://validator.w3.org/#validate_by_input)

---

Exercice suivant : [05 — Les images](../05-images/README.md)
