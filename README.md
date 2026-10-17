# Mon portfolio

Site : <https://LapeyronniePaul.github.io/portfolio/>

Portfolio et journal de bord de mes projets de robotique, d'électronique embarquée et de programmation. Construit avec Jekyll et le thème Just the Docs. Aucun programme à installer : tout se modifie en Markdown, directement sur GitHub ou dans VS Code.

## Structure

```
docs/
├── _config.yml            réglages du site (titre, pseudo...)
├── index.md               page d'accueil (présentation + CV)
├── journal.md             journal de bord (tableau)
├── assets/
│   ├── CV.pdf             ton CV (à ajouter)
│   └── images/            images des projets
└── projets/
    ├── index.md           galerie d'images cliquables
    └── minitto/index.md   page du projet Minitto
```

## Mise en ligne (une seule fois)

1. Crée un repo **public** nommé `portfolio` sur GitHub.
2. Envoie-y le **contenu** de ce dossier (pas le dossier lui-même).
3. Remplace `LapeyronniePaul` dans `docs/_config.yml`, `docs/index.md` et ce README.
4. *Settings → Pages → Deploy from a branch → `main` / `/docs` → Save*.
5. Ajoute ton CV : `docs/assets/CV.pdf` (nom exact, avec les majuscules).
6. Remplace `docs/assets/images/minitto.svg` par une photo de ton robot (voir plus bas).

## Ajouter un projet (sans programme)

1. Copie le dossier `docs/projets/minitto/` en le renommant (ex. `docs/projets/dobo/`). Sur GitHub : ouvre `docs/projets/minitto/index.md`, copie son contenu, puis *Add file → Create new file* avec le nom `docs/projets/dobo/index.md` et colle.
2. Dans ce nouveau fichier, change le `title`, le `nav_order` (2, 3...) et tout le contenu.
3. Ajoute l'image du projet dans `docs/assets/images/` (ex. `dobo.jpg`).
4. Dans `docs/projets/index.md`, copie le bloc `<a class="carte"> ... </a>` de Minitto, colle-le en dessous et change le lien, l'image, le titre et le résumé.
5. Mets les fichiers du projet (code, PDF, schémas) dans le dossier du projet et lie-les dans la section « Fichiers ».

## Ajouter une entrée au journal

Ouvre `docs/journal.md` et ajoute une ligne **juste sous** `|------|-------|--------|` :

```
| 18/10/2026 | Titre de ce que j'ai fait | Résumé en une ou deux phrases. |
```

## Remplacer l'image de Minitto

1. Prends une photo (JPG, idéalement moins de 1 Mo).
2. Envoie-la dans `docs/assets/images/` sous le nom `minitto.jpg`.
3. Dans `docs/projets/index.md` et `docs/projets/minitto/index.md`, remplace `minitto.svg` par `minitto.jpg`.

## Prévisualiser en local (optionnel, nécessite Ruby)

```bash
cd docs
bundle install
bundle exec jekyll serve
```
