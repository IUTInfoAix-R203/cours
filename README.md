# <img src="https://raw.githubusercontent.com/IUTInfoAix-R510/Syllabus/main/assets/logo.png" alt="class logo" class="logo"/> R2.03 — Qualité de développement

### IUT d'Aix-Marseille — Département Informatique Aix-en-Provence

* **Ressource :** [R2.03](https://cache.media.enseignementsup-recherche.gouv.fr/file/SPE4-MESRI-17-6-2021/35/5/Annexe_17_INFO_BUT_annee_1_1411355.pdf)

* **Responsable :** [Sébastien Nedjar](mailto:sebastien.nedjar@univ-amu.fr)

* **Enseignantes :**
  * [Sophie Nabitz](mailto:sophie.nabitz@univ-avignon.fr)
  * [Leïla Sakli Miled](mailto:leila.SAKLI@univ-amu.fr)

## Cours magistraux

Ce dépôt contient les supports des **2 cours magistraux** du module R2.03 (BUT Informatique, 1re année, semestre 2). Chaque CM de 2h introduit les concepts clés utilisés dans les TP de la semaine qui suit.

| CM | Titre | Prépare | Bloom |
|---|---|---|---|
| [CM1](cm1-artisanat-et-git.md) | Artisanat logiciel, qualité, Git avancé | TP1 Git + TP2 TDD | Comprendre → Appliquer |
| [CM2](cm2-tdd-refactoring.md) | TDD, refactoring, code smells, Clean Code | TP3 Kata + TP4 Refactoring | Analyser → Créer |

Deux **démos live** de 20 min complètent les CM, en ouverture des séances TP :
- **Démo TP3** : kata en pair programming (driver/navigator) sur Bowling ou Tennis
- **Démo TP4** : refactoring IDE sur Gilded Rose (code smell → Fowler refactoring)

### Fil rouge

Trois thèmes traversent l'ensemble des CM :

- **🔨 Artisanat** : conventions (Conventional Commits) → baby steps → kata comme exercice régulier
- **✨ Qualité** : tests comme spécification exécutable → couverture → code smells → refactorings
- **🤝 Collaboration** : Git avancé → Pull Request + review → pair programming

### Format

Les supports sont rédigés en **Markdown avec frontmatter [Marp](https://marp.app/)** :
- Lisibles directement sur GitHub (Markdown standard)
- Convertis automatiquement en slides HTML + PDF par la CI et publiés sur GitHub Pages : <https://iutinfoaix-r203.github.io/cours/>
- Éditables dans VS Code avec l'extension Marp (prévisualisation en temps réel)

Les diagrammes utilisent **[Kroki](https://kroki.io/)** (Mermaid, PlantUML, etc.) via le plugin `markdown-it-kroki`.

## Développement local

```bash
npm ci                    # installe Marp CLI + plugin Kroki
npm run dev               # serveur avec hot reload sur http://localhost:8080
npm run build             # génère _site/cm*.html
```

## Organisation du dépôt

```
cours/
├── cm1-artisanat-et-git.md   # CM1 — slides Marp
├── cm2-tdd-refactoring.md    # CM2 — slides Marp
├── assets/                   # Images et diagrammes partagés
├── marp.config.js            # Config Marp + plugin Kroki
├── package.json              # Dépendances npm
└── .github/workflows/
    └── marp-pages.yml        # Build HTML+PDF et déploiement GitHub Pages
```

Les anciens cours (2022, format remark.js) sont archivés dans [`IUTInfoAix-R203-archive/cours`](https://github.com/IUTInfoAix-R203-archive/cours).
