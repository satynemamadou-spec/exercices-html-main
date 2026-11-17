# Exercice 10 — Chasse aux bugs

**Niveau 2 · Pousse** · ★★☆☆ · Durée : 40 min · Notions : validateur W3C, lecture des messages d'erreur, outils de développement (F12), test d'une page

> Le site du « Verger des Collines » a été codé beaucoup trop vite. Le navigateur affiche quand même quelque chose… mais la page contient **10 erreurs** : **8** sont détectables par le validateur W3C, et **2** ne peuvent être trouvées qu'en **testant** la page. À vous de toutes les débusquer !

## Objectifs

- Utiliser le validateur W3C pour trouver les erreurs de syntaxe HTML.
- Lire un message d'erreur (en anglais) et retrouver la ligne concernée.
- Corriger méthodiquement : **la première erreur d'abord**, puis revalider.
- Comprendre que le validateur ne suffit pas : il faut aussi **tester** sa page (liens, images, Console).

## Fichiers fournis

```
10-debogage/
├── README.md       ← cette consigne
├── index.html      ← la page buggée (toutes les erreurs sont ici)
├── contact.html    ← une page correcte, vers laquelle pointe le lien « Contact »
└── images/
    └── mangue.svg
```

## Consigne

1. **Observez** : ouvrez `index.html` dans le navigateur. Qu'est-ce qui cloche visuellement ? Notez-le (texte en gras partout ? image absente ? titre de l'onglet ?).
2. **Validez** : ouvrez le [validateur W3C](https://validator.w3.org/#validate_by_input) (onglet *Validate by Direct Input*), copiez-collez **tout** le code de `index.html`, puis cliquez sur **Check**.
3. **Corrigez une erreur à la fois** : lisez la **première** erreur, repérez le numéro de ligne (*From line X*), corrigez dans VS Code, puis recopiez le code et revalidez.
   > **Attention :** le validateur peut afficher **plus de messages que de bugs** : une seule erreur peut en provoquer d'autres « en cascade ». C'est pour cela qu'on corrige toujours la première erreur avant de regarder les suivantes.
4. **Notez chaque bug** dans le tableau ci-dessous (dans votre cahier ou dans un fichier `bugs.md`).
5. Quand le validateur affiche *« Document checking completed. No errors or warnings to show. »*, **testez la page** pour trouver les 2 bugs restants :
   - cliquez sur **chaque** lien ;
   - vérifiez que **chaque** image s'affiche ;
   - ouvrez les outils de développement (**F12**), onglet **Console** : les fichiers introuvables y apparaissent en rouge (erreur `404`).
6. Comparez votre tableau avec celui d'un ou une camarade.

### Mon rapport de bugs

| N° | Ligne | Problème trouvé | Ma correction | Trouvé grâce à… (validateur / test) |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |
| 6 | | | | |
| 7 | | | | |
| 8 | | | | |
| 9 | | | | |
| 10 | | | | |

## Critères de réussite

- [ ] Mon rapport de bugs contient les 10 erreurs, avec leur ligne et leur correction.
- [ ] Le validateur W3C n'affiche plus aucune erreur ni aucun avertissement.
- [ ] Tous les liens fonctionnent (y compris celui vers `contact.html`).
- [ ] Les deux images s'affichent et la Console (F12) ne montre aucune erreur.
- [ ] Le texte n'est plus en gras partout, et l'onglet affiche un titre.
- [ ] Je n'ai rien supprimé d'utile : tout le contenu d'origine est toujours là.

## Indices

<details>
<summary>Indice 1 — Comment lire un message du validateur ?</summary>

Exemple (qui ne vient pas de cette page) :

> **Error:** End tag `div` seen, but there were open elements.
> From line 12, column 3; to line 12, column 8

Traduction : « Balise fermante `</div>` trouvée alors que des éléments ouverts à l'intérieur n'ont pas été fermés. » Le problème est souvent **juste au-dessus** de la ligne indiquée : une balise ouverte qu'on a oublié de fermer.

</details>

<details>
<summary>Indice 2 — Petit dictionnaire des messages fréquents</summary>

| Message (anglais) | Signification |
|---|---|
| *doctype* | Il s'agit de la ligne `<!DOCTYPE html>`. |
| *missing a required instance of child element X* | Il manque un élément obligatoire X. |
| *Attribute X not allowed on element Y* | L'attribut X n'existe pas (ou est mal écrit) pour la balise Y. |
| *End tag X seen, but there were open elements* | Une balise ouverte avant X n'a pas été fermée. |
| *Unclosed element X* | La balise X n'est jamais fermée. |
| *Element X not allowed as child of element Y* | X n'a pas le droit d'être placé directement dans Y. |
| *Duplicate ID X* | Le même `id` est utilisé deux fois. |
| *must have an alt attribute* | Il manque l'attribut `alt` sur une image. |

</details>

<details>
<summary>Indice 3 — Pourquoi tout est en gras ?</summary>

Une balise de mise en forme ouverte et jamais fermée « déborde » sur la suite de la page : le navigateur essaie de deviner où elle aurait dû s'arrêter… et il devine mal.

</details>

<details>
<summary>Indice 4 — Les 2 bugs invisibles pour le validateur</summary>

Le validateur vérifie la **syntaxe** de votre code, mais il ne regarde **pas** si les fichiers que vous visez existent vraiment. Comparez lettre par lettre les chemins écrits dans le code avec les vrais noms des fichiers et des dossiers.

</details>

## Bonus

- Créez à votre tour une petite page contenant **3 bugs** cachés, puis échangez-la avec un ou une camarade : qui trouve le plus vite ?
- Installez dans VS Code une extension qui signale les erreurs HTML pendant que vous tapez (par exemple **HTMLHint**), puis rouvrez le fichier de départ : quelles erreurs voit-elle ?
- Testez le fichier de départ dans deux navigateurs différents (Chrome et Firefox) : l'affichage est-il exactement le même ?

## Questions de compréhension

1. Pourquoi le navigateur affiche-t-il quand même une page pleine d'erreurs ? Pourquoi est-ce dangereux de s'y fier ?
2. Qu'est-ce qu'une erreur **404** ?
3. Pourquoi le validateur n'a-t-il pas trouvé les bugs 9 et 10 ?
4. Pourquoi faut-il corriger la **première** erreur avant les autres ?

## Lien avec le brief PlantEvo

Lors de l'évaluation, votre code source sera **relu** devant vous (« Revue du code source ») et la grille évalue un « code source correctement commenté et organisé ». Prenez l'habitude : avant chaque rendu, **chaque page** passe au validateur, **chaque lien** est cliqué et **chaque image** est vérifiée.

## Ressources

- [Validateur W3C (Nu Html Checker)](https://validator.w3.org/#validate_by_input)
- [MDN — Déboguer du HTML](https://developer.mozilla.org/fr/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML)
- [MDN — Qu'est-ce que les outils de développement du navigateur ?](https://developer.mozilla.org/fr/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools)

---

Exercice suivant : [11 — Inscription aux ateliers de l'exposition](../../niveau-3-arbre/11-formulaires/README.md)
