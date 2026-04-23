---
marp: true
theme: default
paginate: true
---

<!-- _class: lead -->
<!-- _paginate: false -->

# Artisanat logiciel, qualité et Git avancé

**R2.03 - Qualité de développement**

IUT d'Aix-Marseille - BUT Informatique, 1re année

---

## Le module R2.03 en un coup d'oeil

<style scoped>
blockquote { font-size: 0.92rem; }
</style>

> Apprendre à produire du code **propre**, **testé**, **relu** et **maintenable**. Passer de "ça marche sur ma machine" à un vrai réflexe professionnel.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; font-size: 1.5rem;">
<div style="background: #4a90d9; color: white; padding: 1rem 1.2rem; border-radius: 10px;">
🔀 <b>Git professionnel</b><br/>Rebase, cherry-pick, PR, review
</div>
<div style="background: #27ae60; color: white; padding: 1rem 1.2rem; border-radius: 10px;">
✅ <b>TDD baby-steps</b><br/>RED - GREEN - REFACTOR
</div>
<div style="background: #e8a838; color: white; padding: 1rem 1.2rem; border-radius: 10px;">
🥋 <b>Kata & pair programming</b><br/>Driver / navigator, ping-pong
</div>
<div style="background: #e74c3c; color: white; padding: 1rem 1.2rem; border-radius: 10px;">
🧹 <b>Refactoring</b><br/>Code smells, transformations de Fowler
</div>
</div>

---

## Organisation du module

<div style="display: flex; gap: 0.8rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.2rem; border-radius: 12px 12px 0 0; flex: 1; text-align: center;">
<div style="font-size: 1.8rem; font-weight: bold;">CM1</div>
<div style="margin-top: 0.3rem;">Artisanat + Git</div>
</div>
<div style="background: #e8a838; color: white; padding: 1.2rem; border-radius: 12px 12px 0 0; flex: 1; text-align: center;">
<div style="font-size: 1.8rem; font-weight: bold;">CM2</div>
<div style="margin-top: 0.3rem;">TDD + Refactoring</div>
</div>
</div>

<div style="display: flex; gap: 0.8rem; text-align: center; font-size: 1.5rem; color: #999;">
<div style="flex: 1;">↓</div>
<div style="flex: 1;">↓</div>
</div>

<div style="display: flex; gap: 0.8rem;">
<div style="background: #d0e2f3; color: #2c5f8a; padding: 0.8rem; border-radius: 0 0 12px 12px; flex: 1; text-align: center; font-weight: bold;">
TP1 Git + TP2 TDD
</div>
<div style="background: #fae5c0; color: #8a6a1f; padding: 0.8rem; border-radius: 0 0 12px 12px; flex: 1; text-align: center; font-weight: bold;">
TP3 Kata + TP4 Refactoring
</div>
</div>

<div style="display: flex; gap: 2rem; margin-top: 1.5rem;">
<div style="flex: 1;">

**👥 Équipe pédagogique**
- S. Nedjar (responsable)
- S. Nabitz, L. Sakli Miled

</div>
<div style="flex: 1;">

**⏱️ Volume horaire** : 22 h
- CM (4 h) + TD (5 h) + TP (13 h)
- Test écrit (2 h, le 15 juin)

</div>
</div>

---

## Évaluation

Trois notes, un objectif : vérifier que vous **maîtrisez des gestes de métier**, pas juste que votre code tourne.

<div style="display: flex; gap: 1.5rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">📝</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC1</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Moyenne autograding TP2, TP3, TP4</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 10</div>
</div>
<div style="background: #e8a838; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">🤝</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC2</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Participation + qualité des reviews PR</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 10</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">💻</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC3</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Mini-kata TDD sur feuille (2 h, sans outils)</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 40</div>
</div>
</div>

<div style="display: flex; height: 1.2rem; border-radius: 8px; overflow: hidden; margin-top: 1.2rem;">
<div style="background: #4a90d9; flex: 10; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">17%</div>
<div style="background: #e8a838; flex: 10; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">17%</div>
<div style="background: #e74c3c; flex: 40; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">66%</div>
</div>

<div style="margin-top: 0.8rem; font-size: 0.95rem; color: #666; text-align: center;">
Le TP1 Git est un TP de mise à niveau - non noté.
</div>

---

## Environnement de travail

Tout le module se fait sur **GitHub Codespaces** : aucune installation locale nécessaire.

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1.5rem;">
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">☕</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Java 25</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🧪</div>
<div style="font-weight: bold; margin-top: 0.3rem;">JUnit 6 + AssertJ</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">📦</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Maven (via mvnw)</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🔀</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Git + gh CLI</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🤖</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Copilot Chat (tuteur)</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">📊</div>
<div style="font-weight: bold; margin-top: 0.3rem;">ApprovalTests</div>
</div>
</div>

<div style="background: #2c3e50; color: white; padding: 1.2rem 2rem; border-radius: 10px; text-align: center; margin-top: 1.5rem; font-size: 1.4rem;">
🌐 Page d'accueil étudiants : <a href="https://github.com/IUTInfoAix-R203/tp" style="color: #a0d8f8;">github.com/IUTInfoAix-R203/tp</a>
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 1 - Artisanat logiciel

Pourquoi on parle de "qualité" ?

---

## 🔨 Qu'est-ce que l'artisanat logiciel ?

<div style="display: flex; gap: 2rem; margin-top: 1rem; align-items: center;">
<div style="flex: 1;">

Un **artisan** ne se contente pas de livrer une table qui tient debout. Il la livre **bien finie**, **robuste**, **belle**, facile à réparer et qui résistera aux années.

Un **artisan du logiciel** ne se contente pas de livrer du code qui compile. Il livre du code qui est :

- **Lisible** par un autre humain
- **Testé** pour éviter les régressions
- **Simple** à modifier quand les besoins évoluent
- **Relu** par des pairs avant fusion

</div>
<div style="flex: 1; text-align: center;">

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; font-size: 1.2rem;">
« <b>Software Craftsmanship</b> » est un mouvement né dans les années 2000, en réaction à l'industrialisation du logiciel qui pressait les développeurs à livrer vite au détriment de la qualité.
</div>

</div>
</div>

---

## 🔨 Le manifeste de l'artisanat logiciel (2009)

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; font-size: 1.3rem; line-height: 1.6;">

> En tant qu'aspirants <b>Software Craftsmen</b>, nous visons non seulement :

| Au-delà de... | ... nous voulons : |
|---|---|
| du logiciel qui marche | du logiciel **bien conçu** |
| répondre au changement | **ajouter régulièrement de la valeur** |
| individus et interactions | une **communauté de professionnels** |
| collaborer avec le client | des **partenariats productifs** |

</div>

<div style="margin-top: 1rem; text-align: center; color: #666;">
Inspiré du <em>Manifeste Agile</em> (2001) - mais il ajoute un niveau d'exigence sur la <b>qualité intrinsèque</b> du code, pas juste sur le processus.
</div>

---

## 📉 Pourquoi c'est important : le coût des bugs

<div style="display: flex; gap: 2rem;">
<div style="flex: 1;">

Plus un bug est détecté **tard**, plus il coûte cher à corriger. Ordre de grandeur connu :

| Détecté pendant... | Coût relatif |
|---|---|
| Le développement | 1x |
| Les tests | 6x |
| La pré-production | 15x |
| **Chez le client** | **100x** |

</div>
<div style="flex: 1;">

<div style="background: #e74c3c; color: white; padding: 1.5rem; border-radius: 12px;">
<b>Cas célèbre : Knight Capital (2012)</b><br/>
Un bug dans un déploiement de trading automatique a fait perdre <b>440 millions de dollars en 45 minutes</b>. Rang de bourse : faillite. Cause : un drapeau mal réinitialisé dans un module obsolète.
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; font-size: 1.1rem;">
➡️ La qualité du code n'est pas un luxe d'esthète : c'est une question de <b>survie économique</b>.
</div>

</div>
</div>

---

## 💳 La dette technique

<div style="display: flex; gap: 2rem; margin-top: 1rem; align-items: center;">
<div style="flex: 1;">

Métaphore de **Ward Cunningham** (1992) : écrire du code sale pour livrer vite, c'est comme emprunter de l'argent.

Ça aide à court terme. Mais il faut **rembourser**, **avec intérêts**.

Quand la dette technique est élevée :

- Chaque nouvelle fonctionnalité prend plus de temps
- Les bugs se multiplient
- L'équipe **ralentit**, démotivée
- Le projet peut **mourir**

</div>
<div style="flex: 1;">

```mermaid
graph LR
    A[Code propre] -->|livraison| B[Valeur]
    C[Dette technique] -->|ralentit| B
    C -->|augmente| D[Bugs]
    D -->|augmente| C
    B -->|permet de rembourser| C
    
    style A fill:#27ae60,color:#fff
    style B fill:#4a90d9,color:#fff
    style C fill:#e74c3c,color:#fff
    style D fill:#c0392b,color:#fff
```

</div>
</div>

---

## 🧱 Les 4 piliers du module R2.03

Ce module vous équipe des **4 outils fondamentaux** de l'artisan logiciel :

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.5rem; border-radius: 12px;">
<div style="font-size: 2rem;">🔀 <b>Git avancé</b></div>
<div style="margin-top: 0.3rem;">Votre historique est une documentation exécutable. Branches, PR, reviews, rebase.</div>
<div style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.9;">→ TP1 (ce vendredi)</div>
</div>
<div style="background: #27ae60; color: white; padding: 1.5rem; border-radius: 12px;">
<div style="font-size: 2rem;">✅ <b>TDD</b></div>
<div style="margin-top: 0.3rem;">Écrire les tests <em>avant</em> le code. Spécification exécutable, filet de sécurité.</div>
<div style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.9;">→ TP2 (semaine prochaine)</div>
</div>
<div style="background: #e8a838; color: white; padding: 1.5rem; border-radius: 12px;">
<div style="font-size: 2rem;">🥋 <b>Kata & pair programming</b></div>
<div style="margin-top: 0.3rem;">Entraîner son geste technique à deux. Driver / navigator, ping-pong.</div>
<div style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.9;">→ TP3 (dans 2 semaines)</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.5rem; border-radius: 12px;">
<div style="font-size: 2rem;">🧹 <b>Refactoring</b></div>
<div style="margin-top: 0.3rem;">Transformer du code existant sans changer son comportement. Protégé par les tests.</div>
<div style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.9;">→ TP4 (dans 3 semaines)</div>
</div>
</div>

---

## 🧭 Où se situe R2.03 dans votre parcours BUT ?

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="background: #bdc3c7; color: #2c3e50; padding: 1rem; border-radius: 10px; flex: 1;">
<b>R1.01 (S1)</b> - bases programmation C++
</div>
<div style="background: #bdc3c7; color: #2c3e50; padding: 1rem; border-radius: 10px; flex: 1;">
<b>R2.01 (S2)</b> - POO Java (en parallèle)
</div>
<div style="background: #3498db; color: white; padding: 1rem; border-radius: 10px; flex: 1; font-weight: bold;">
<b>R2.03</b> - vous êtes ici
</div>
</div>

<div style="margin-top: 1.5rem; text-align: center; color: #666; font-size: 1.5rem;">
↓
</div>

<div style="background: #e74c3c; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 0.5rem;">
<b>SAÉ 2.01 - Développement d'une application</b><br/>
Vous allez coder <b>en équipe</b>, <b>sur plusieurs semaines</b>, un projet réel. Toutes les compétences de R2.03 (Git pro, tests, refactoring) y seront <b>immédiatement utiles</b>. Pas dans un lointain "après les études" - dans 3 semaines.
</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; font-size: 1.1rem; text-align: center;">
Tout ce qu'on apprend aujourd'hui, vous l'utilisez concrètement dans ~3 semaines.
</div>

---

## 🎯 Compétences BUT visées

Le référentiel BUT cible **trois compétences** pour R2.03 :

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-weight: bold; font-size: 1.2rem;">C1</div>
<div style="font-size: 0.95rem; margin-top: 0.3rem;">Développer des applications informatiques simples</div>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">
<b>AC2</b> : Élaborer des conceptions simples<br/>
<b>AC3</b> : Faire des essais et évaluer leurs résultats en regard des spécifications
</div>
</div>
<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-weight: bold; font-size: 1.2rem;">C4</div>
<div style="font-size: 0.95rem; margin-top: 0.3rem;">Concevoir et mettre en place une base de données</div>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">
<b>AC2</b> : Visualiser des données<br/>
<i>(traces et outils de débogage)</i>
</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-weight: bold; font-size: 1.2rem;">C5</div>
<div style="font-size: 0.95rem; margin-top: 0.3rem;">Identifier les besoins métiers des clients</div>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">
<b>AC2</b> : Mettre en place les outils de gestion de projet<br/>
<i>(Git / GitHub)</i>
</div>
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center;">
Mots-clés officiels du PN : <b>Qualité, Test, Gestion de version</b>.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 2 - Git professionnel

Retour aux bases, puis les concepts avancés qui changent la vie.

---

## 🔀 Ce que vous savez déjà (plus ou moins bien)

Au S1, vous avez utilisé Git. Vérifiez avec moi :

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
✅ <b>Je sais</b> :
<ul style="margin: 0.3rem 0; padding-left: 1.2rem;">
<li><code>git clone</code>, <code>git add</code>, <code>git commit</code>, <code>git push</code></li>
<li>Créer une branche</li>
<li>Ouvrir un fork sur GitHub</li>
</ul>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
❌ <b>Je ne sais pas (encore)</b> :
<ul style="margin: 0.3rem 0; padding-left: 1.2rem;">
<li>Écrire un message de commit lisible 6 mois plus tard</li>
<li>Intégrer une branche proprement (rebase vs merge)</li>
<li>Rattraper un commit perdu sans paniquer</li>
<li>Relire sérieusement la PR d'un pair</li>
</ul>
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center;">
La moitié de ce TP1 consiste à corriger les mauvaises habitudes prises au S1. L'autre moitié, à découvrir ce qui fait la différence en équipe.
</div>

---

## 🔀 Rappel express : le modèle Git

Un commit est un **snapshot** du projet à un instant donné, avec un ou plusieurs **parents**.

<div style="text-align: center; margin-top: 1rem;">

```mermaid
graph LR
    A[A : init] --> B[B : ajoute feature X]
    B --> C[C : corrige typo]
    B --> D[D : experimentation]
    C --> E[E : merge D]
    D --> E
    
    style A fill:#bdc3c7
    style B fill:#bdc3c7
    style C fill:#4a90d9,color:#fff
    style D fill:#e8a838,color:#fff
    style E fill:#27ae60,color:#fff
```

</div>

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>HEAD</b> : pointeur sur le commit courant dans votre worktree
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>Branche</b> : pointeur <em>mobile</em> sur un commit (avance avec chaque commit)
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>Tag</b> : pointeur <em>fixe</em> sur un commit (ne bouge plus)
</div>
</div>

---

## 📝 Conventional Commits : le message qui documente

<div style="display: flex; gap: 2rem; margin-top: 1rem;">
<div style="flex: 1;">

Le message de commit que vous écrivez **aujourd'hui** sera relu par **quelqu'un d'autre** (ou vous-même) dans 6 mois, pour comprendre pourquoi telle ligne a été écrite.

Format **Conventional Commits** :

```
<type>(<scope>): <description>
```

**Types classiques** :
- `feat` : nouvelle fonctionnalité
- `fix` : correction de bug
- `docs` : documentation
- `refactor` : réorganisation
- `test` : ajout ou fix de tests
- `chore` : maintenance

</div>
<div style="flex: 1;">

<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Bons messages</b>
<pre style="background: rgba(0,0,0,0.2); padding: 0.6rem; border-radius: 4px; font-size: 0.85rem; margin-top: 0.5rem;">feat(auth): ajoute login via OAuth Google
fix(cart): corrige le total quand la remise est 0
docs(readme): detaille l'installation locale
refactor(facture): extrait appliquerTVA</pre>
</div>

<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px; margin-top: 1rem;">
<b>❌ Mauvais messages</b>
<pre style="background: rgba(0,0,0,0.2); padding: 0.6rem; border-radius: 4px; font-size: 0.85rem; margin-top: 0.5rem;">wip
fix
maj
trucs
ca marche enfin putain
update file</pre>
</div>

</div>
</div>

---

## 🔄 GitHub Flow : le workflow en 4 étapes

Le workflow standard en équipe (simplifié de Vincent Driessen) :

<div style="margin-top: 1rem;">

```mermaid
graph LR
    A[main stable] -->|créer| B[branche feature]
    B -->|commits| B
    B -->|push| C[Pull Request]
    C -->|review| D[feedback]
    D -->|corrections| B
    C -->|approved| E[merge]
    E --> A
    
    style A fill:#4a90d9,color:#fff
    style B fill:#e8a838,color:#fff
    style C fill:#8e44ad,color:#fff
    style D fill:#f39c12,color:#fff
    style E fill:#27ae60,color:#fff
```

</div>

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1; text-align: center;">
<b>1.</b> Une branche par fonctionnalité
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1; text-align: center;">
<b>2.</b> Commits atomiques + Conventional
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1; text-align: center;">
<b>3.</b> Pull Request dès qu'on est prêt à montrer
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; flex: 1; text-align: center;">
<b>4.</b> Merge après review
</div>
</div>

---

## 🔍 Pull Request : une conversation, pas un dépôt de code

<div style="display: flex; gap: 2rem; margin-top: 1rem;">
<div style="flex: 1;">

Une PR n'est pas un formulaire administratif. C'est une **invitation à discuter** du code que vous proposez d'intégrer.

Ce qu'elle permet :

- **Comprendre** votre intention (le message de PR est comme un mini-post-it)
- **Questionner** vos choix (un pair peut avoir une meilleure idée)
- **Vérifier automatiquement** les tests, la qualité, les conventions
- **Documenter** l'historique des décisions

</div>
<div style="flex: 1;">

<div style="background: #8e44ad; color: white; padding: 1.2rem; border-radius: 10px;">
<b>Checklist d'une bonne review</b>
<ul style="margin-top: 0.5rem;">
<li>Le code est-il lisible sans commentaire ?</li>
<li>Les noms sont-ils parlants ?</li>
<li>Y a-t-il des tests ? Passent-ils ?</li>
<li>Pas de code commenté qui traîne ?</li>
<li>Pas de <code>TODO</code> ou <code>FIXME</code> orphelins ?</li>
<li>La PR ne fait-elle qu'<em>une</em> chose ?</li>
</ul>
</div>

<div style="background: #e74c3c; color: white; padding: 0.8rem 1rem; border-radius: 8px; margin-top: 0.8rem; font-size: 0.95rem;">
❌ "LGTM" (Looks Good To Me) sans lire <b>n'est pas</b> une review. C'est un tampon, qui en plus engage votre nom.
</div>

</div>
</div>

---

## 🤖 Review automatique par Copilot

Dans vos Codespaces, **Copilot Code Review** s'active automatiquement à chaque PR ouverte.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Ce qu'il fait bien</b>
<ul style="margin-top: 0.3rem;">
<li>Détecter les fautes de frappe</li>
<li>Signaler les noms confus</li>
<li>Proposer des simplifications</li>
<li>Trouver des bugs évidents</li>
</ul>
</div>
<div style="background: #e8a838; color: white; padding: 1rem; border-radius: 10px;">
<b>⚠️ Ses limites</b>
<ul style="margin-top: 0.3rem;">
<li>Ne comprend pas toujours l'intention métier</li>
<li>Peut suggérer des choses hors sujet</li>
<li>Ne remplace <b>pas</b> la review humaine</li>
</ul>
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; font-size: 1.1rem; text-align: center;">
En binôme au TP3 (kata), chacun fera <b>au moins 2 reviews</b> sur la PR de l'autre. Discutez avec l'auteur, ne validez pas aveuglément.
</div>

---

## 🔀 Merge vs rebase : deux façons d'intégrer une branche

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="flex: 1;">

<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px; text-align: center;">
<b>git merge</b>
</div>

```mermaid
graph LR
    A[A] --> B[B]
    B --> C[C]
    B --> D[D]
    C --> E[M merge]
    D --> E
    
    style A fill:#bdc3c7
    style B fill:#bdc3c7
    style C fill:#4a90d9,color:#fff
    style D fill:#e8a838,color:#fff
    style E fill:#27ae60,color:#fff
```

<ul style="margin-top: 0.5rem; font-size: 0.9rem;">
<li>✅ Préserve l'historique réel</li>
<li>❌ Crée un commit de merge, historique "en arête de poisson"</li>
</ul>

</div>
<div style="flex: 1;">

<div style="background: #e8a838; color: white; padding: 1rem; border-radius: 10px; text-align: center;">
<b>git rebase</b>
</div>

```mermaid
graph LR
    A[A] --> B[B]
    B --> C[C]
    C --> Dp[D']
    
    style A fill:#bdc3c7
    style B fill:#bdc3c7
    style C fill:#4a90d9,color:#fff
    style Dp fill:#e8a838,color:#fff
```

<ul style="margin-top: 0.5rem; font-size: 0.9rem;">
<li>✅ Historique linéaire, lisible</li>
<li>⚠️ Réécrit les commits (nouveaux SHA)</li>
</ul>

</div>
</div>

---

## ⚖️ La règle d'or

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; text-align: center; font-size: 1.8rem; margin-top: 2rem;">
<b>Rebase</b> tes commits <b>tant que la branche est locale</b>.<br/>
<b>Merge</b> dès qu'elle est <b>partagée</b> avec d'autres.
</div>

<div style="margin-top: 1.5rem; font-size: 1.1rem; text-align: center; color: #666;">
Pourquoi ? Le rebase <b>change les SHAs</b>. Si ton coéquipier a déjà basé du travail sur ta branche publique, ton rebase lui fait perdre ses commits.
</div>

<div style="display: flex; gap: 1rem; margin-top: 1.5rem;">
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>✅ OK</b> : je rebase ma branche locale <code>feat-login</code> avant de la pousser
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>❌ Danger</b> : je rebase <code>main</code> (partagée par toute l'équipe)
</div>
</div>

---

## 🍒 Cherry-pick : prendre un seul commit

<div style="display: flex; gap: 2rem; margin-top: 1rem;">
<div style="flex: 1;">

**Situation** : tu as un commit `ABCD` sur la branche `feat-experimental` qui contient un correctif de typo.

Tu veux **juste ce correctif** sur `main`, sans tirer tout le reste de la branche.

```bash
git checkout main
git cherry-pick ABCD
```

**Cas d'usage** :
- Rapatrier un hotfix isolé
- Récupérer un commit d'un collègue
- Re-appliquer un commit "perdu" après un reset

</div>
<div style="flex: 1;">

```mermaid
graph LR
    A[A] --> B[B]
    B --> C[C]
    C --> D[D hotfix]
    D --> E[E suite exp]
    B -->|cherry-pick D| Dp[D']
    
    style A fill:#bdc3c7
    style B fill:#4a90d9,color:#fff
    style C fill:#e8a838,color:#fff
    style D fill:#e74c3c,color:#fff
    style E fill:#e8a838,color:#fff
    style Dp fill:#e74c3c,color:#fff
```

<div style="background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; margin-top: 0.5rem; font-size: 0.9rem;">
⚠️ Cherry-pick copie le commit → <b>nouveau SHA</b>. Si tu finis par merger la branche plus tard, les deux commits cohabiteront.
</div>

</div>
</div>

---

## ✏️ Rebase interactif : nettoyer l'historique

`git rebase -i HEAD~3` ouvre un éditeur qui liste les 3 derniers commits :

<div style="background: #2c3e50; color: #eee; padding: 1rem; border-radius: 8px; font-family: monospace; margin-top: 1rem; font-size: 1rem;">

```
pick a1b2c3 wip
pick d4e5f6 maj
pick g7h8i9 fix typo

# Rebase ...
# p, pick = use commit
# r, reword = use commit, but edit commit message
# s, squash = use commit, meld into previous
# f, fixup = like squash, but discard this commit's message
# d, drop = remove commit
```

</div>

<div style="margin-top: 1rem;">

Vous pouvez :

- **`reword`** pour corriger un message de commit (`wip` → `feat(auth): ajoute login OAuth`)
- **`squash`** pour fusionner plusieurs commits en un seul
- **`fixup`** comme squash mais en jetant le message
- **`drop`** pour supprimer un commit entier
- **réordonner** les lignes pour réordonner les commits

</div>

---

## ✏️ Rebase interactif : exemple concret

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ Avant</b>

```
a1b2c3 wip
d4e5f6 maj
g7h8i9 fix typo
h1j2k3 oh j'avais oublié un test
m4n5o6 deuxième essai
```

Historique illisible. Que s'est-il réellement passé ?

</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Après rebase interactif</b>

```
x7y8z9 feat(auth): ajoute login OAuth Google
```

Un seul commit, message clair. L'histoire racontée au futur lecteur est : "à cette date, on a ajouté OAuth Google".

</div>
</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.1rem;">
Refaire son historique avant la PR, c'est un acte de <b>courtoisie</b> envers le relecteur.
</div>

---

## 🆘 Reflog : le filet de sécurité

**Situation cauchemar** : tu tapes `git reset --hard HEAD~5` et tu réalises que tu viens d'effacer 5 commits. **Pas de panique.**

<div style="margin-top: 1rem;">

```bash
git reflog
```

Affiche TOUTES tes actions récentes, même celles que tu crois avoir "annulées" :

</div>

```
a1b2c3 HEAD@{0}: reset: moving to HEAD~5
g7h8i9 HEAD@{1}: commit: feat: ajoute fonctionnalité X  ← ici !
d4e5f6 HEAD@{2}: commit: wip
...
```

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
Retour à l'état d'avant le reset :
<pre style="background: rgba(0,0,0,0.2); padding: 0.4rem; border-radius: 4px; margin-top: 0.5rem;">git reset --hard g7h8i9</pre>
</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 8px; flex: 1;">
<b>Git conserve ces commits "orphelins"<br/>pendant 90 jours</b> par défaut. Tant qu'il reste dans ce délai, <b>rien n'est vraiment perdu</b>.
</div>
</div>

---

## ⚠️ Commandes destructrices et leurs alternatives

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.5rem;">
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ git reset --hard</b><br/>Perd toutes les modifications non commitées.
</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ git reset (mixed par défaut)</b><br/>Déstage sans perdre le contenu.
</div>

<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ git push --force</b><br/>Écrase la branche distante, même si d'autres ont poussé après toi.
</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ git push --force-with-lease</b><br/>Refuse le push si quelqu'un a poussé entre-temps.
</div>

<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ git branch -D feature</b><br/>Supprime même une branche non fusionnée.
</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ git branch -d feature</b><br/>Refuse de supprimer si des commits sont non fusionnés.
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.1rem;">
Règle de survie : <b>toute commande destructrice a une variante sûre</b>. Utilisez-la par défaut.
</div>

---

## 🎬 Démo live : rebase d'une branche sur main

Je vais faire la démo suivante, posez des questions pendant :

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 1rem;">

1. Je clone `github.com/IUTInfoAix-R203/tp1` dans un Codespace
2. Je fais deux commits sur `main` pour simuler le travail d'un collègue
3. Je crée une branche `feat-exemple` et j'y fais deux commits
4. Je rebase ma branche sur `main` : `git rebase origin/main`
5. J'affiche l'historique avec `git log --oneline --graph --all`
6. Je pousse avec `git push --force-with-lease`

</div>

<div style="margin-top: 1rem; background: #e74c3c; color: white; padding: 1rem; border-radius: 8px;">
⚠️ Ce que vous allez voir que je <b>ne conseille pas en vrai</b> : je vais volontairement simuler un commit mal formé, pour vous montrer le rebase interactif pour le corriger.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 3 - Introduction au TDD

Écrire les tests avant le code. Oui, vraiment.

---

## 🐛 Le problème du code "ça marche sur ma machine"

<div style="display: flex; gap: 2rem; margin-top: 1rem;">
<div style="flex: 1;">

Combien de fois avez-vous :

- Livré un TP qui marchait chez vous mais pas chez le prof ?
- Corrigé un bug et fait réapparaître un autre que vous aviez résolu il y a 3 jours ?
- Modifié une fonction en ayant peur que ça casse ailleurs ?

Toutes ces situations ont la **même cause profonde** : vous n'avez pas de filet de tests qui vous dit quand vous avez cassé quelque chose.

</div>
<div style="flex: 1;">

<div style="background: #e74c3c; color: white; padding: 1.2rem; border-radius: 10px;">
<b>Sans tests</b>
<ul style="margin-top: 0.3rem;">
<li>Vous avez <b>peur</b> de modifier le code</li>
<li>Vous <b>perdez du temps</b> à tester manuellement</li>
<li>Les bugs se <b>multiplient silencieusement</b></li>
</ul>
</div>

<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px; margin-top: 1rem;">
<b>Avec tests</b>
<ul style="margin-top: 0.3rem;">
<li>Vous modifiez <b>sereinement</b></li>
<li>Le feedback est <b>instantané</b> (secondes)</li>
<li>Vous <b>documentez</b> le comportement attendu</li>
</ul>
</div>

</div>
</div>

---

## ✅ TDD : l'idée contre-intuitive

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 1rem; font-size: 1.3rem; text-align: center;">
<b>Écrire le test <em>avant</em> le code</b> qu'il vérifie.
</div>

<div style="display: flex; gap: 2rem; margin-top: 1.5rem;">
<div style="flex: 1;">

**Pourquoi c'est puissant ?**

1. Le test **précise** le comportement attendu (comme un cahier des charges)
2. Il **garantit** que vous n'écrivez que le code nécessaire
3. Il **sert** de filet quand vous refactorez ensuite
4. Il **guide** la conception de l'API (si le test est pénible à écrire, c'est que l'API est mal pensée)

</div>
<div style="flex: 1;">

**Pourquoi c'est contre-intuitif ?**

Notre réflexe naturel est : "j'écris le code, puis je testerai si j'ai le temps".

Résultat : on teste peu, on teste mal, et on teste **ce qu'on a codé** au lieu de **ce qu'il faudrait faire**.

TDD inverse la logique : on teste d'abord **le besoin**, puis on code le minimum pour y répondre.

</div>
</div>

---

## 🔁 Le cycle RED - GREEN - REFACTOR

<div style="text-align: center; margin-top: 1rem;">

```mermaid
graph LR
    A[🔴 RED : test qui échoue] -->|écrire code| B[🟢 GREEN : test passe]
    B -->|améliorer| C[🧹 REFACTOR : code propre, tests verts]
    C -->|test suivant| A
    
    style A fill:#e74c3c,color:#fff
    style B fill:#27ae60,color:#fff
    style C fill:#4a90d9,color:#fff
```

</div>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>🔴 RED</b><br/>Écrire un test qui échoue. Preuve qu'il teste vraiment quelque chose. <b>Ne pas coder</b> avant d'avoir vu le rouge.
</div>
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>🟢 GREEN</b><br/>Écrire le <b>minimum</b> de code pour que le test passe. Oui, même si c'est moche. <b>Fake it</b> si besoin.
</div>
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px;">
<b>🧹 REFACTOR</b><br/>Nettoyer le code <b>sans casser les tests</b>. C'est le moment d'extraire, renommer, simplifier.
</div>
</div>

---

## 🎣 Les 3 stratégies de Kent Beck

Pour passer du **RED** au **GREEN**, trois approches :

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-size: 2rem;">🟢 <b>Fake it</b></div>
<div style="margin-top: 0.5rem;">Retourner une <b>valeur en dur</b> qui fait passer le test.</div>
<pre style="background: rgba(0,0,0,0.2); padding: 0.6rem; border-radius: 4px; margin-top: 0.5rem; font-size: 0.85rem;">// Test : saluer("Alice") == "Hello, Alice!"
return "Hello, Alice!";</pre>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">Premier réflexe. Toujours.</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-size: 2rem;">🔺 <b>Triangulation</b></div>
<div style="margin-top: 0.5rem;">Un <b>2e test</b> avec une autre valeur t'oblige à généraliser.</div>
<pre style="background: rgba(0,0,0,0.2); padding: 0.6rem; border-radius: 4px; margin-top: 0.5rem; font-size: 0.85rem;">// Test 1 : saluer("Alice")
// Test 2 : saluer("Bob")
return "Hello, " + nom + "!";</pre>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">Quand fake it ne suffit plus.</div>
</div>

<div style="background: #4a90d9; color: white; padding: 1.2rem; border-radius: 10px;">
<div style="font-size: 2rem;">✅ <b>Obvious</b></div>
<div style="margin-top: 0.5rem;">L'implémentation tient en <b>une ligne évidente</b>.</div>
<pre style="background: rgba(0,0,0,0.2); padding: 0.6rem; border-radius: 4px; margin-top: 0.5rem; font-size: 0.85rem;">// Test : additionner(2, 3) == 5
return a + b;</pre>
<div style="margin-top: 0.5rem; font-size: 0.85rem; opacity: 0.9;">Rare. Mais OK si la solution est triviale.</div>
</div>
</div>

---

## 👣 Baby steps : petits pas, toujours

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 1rem; font-size: 1.2rem;">

**Règle absolue du TDD** : un test = une modification de code = un commit (ou au moins un point de contrôle mental).

Si vous ouvrez un fichier et vous modifiez 30 lignes entre deux exécutions de tests, **vous n'êtes plus en TDD** : vous êtes en train de coder "à l'ancienne" en priant pour que ça marche.

</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Bon rythme</b>
<ul style="margin-top: 0.3rem;">
<li>Activer 1 test</li>
<li>Le voir rouge (15s)</li>
<li>Écrire 3 lignes</li>
<li>Le voir vert (15s)</li>
<li>Cycle suivant</li>
</ul>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ Mauvais rythme</b>
<ul style="margin-top: 0.3rem;">
<li>Activer 5 tests d'un coup</li>
<li>Écrire 40 lignes sans tester</li>
<li>Lancer les tests : 3 verts, 2 rouges</li>
<li>Débugger sans savoir qui a cassé quoi</li>
</ul>
</div>
</div>

---

## 🎬 Kata live : HelloWorld en TDD

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 1rem;">

On va écrire ensemble une méthode `saluer(String nom)` qui retourne :

- `"Hello, World!"` si `nom` est `null` ou vide
- `"Hello, <nom>!"` sinon

**Tests** (fournis, je vais les activer un par un) :
1. `saluerSansNomRetourneHelloWorld()`
2. `saluerChaineVideRetourneHelloWorld()`
3. `saluerAliceRetourneHelloAlice()`
4. `saluerBobRetourneHelloBob()`

</div>

<div style="margin-top: 1.2rem; font-size: 1.1rem; text-align: center; color: #666;">
Observez le rythme : <b>activer → rouge → écrire → vert → commit</b>. Ne pas coder en avance.
</div>

---

## 🤖 Copilot Chat : votre tuteur, pas votre code-monkey

Le TP2 a un fichier `.github/copilot-instructions.md` qui configure Copilot comme **tuteur TDD** :

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Ce que Copilot fera</b>
<ul style="margin-top: 0.3rem;">
<li>Expliquer un concept TDD</li>
<li>Vous orienter vers la Javadoc</li>
<li>Suggérer du code <b>quand vous lui demandez 3 fois</b> (escalade)</li>
<li>Refuser de coder à votre place si un test n'est pas encore activé</li>
</ul>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px;">
<b>❌ Ce qu'il refusera</b>
<ul style="margin-top: 0.3rem;">
<li>"Écris tout le TP à ma place"</li>
<li>Donner une solution dès le premier prompt</li>
<li>Coder avant que vous ayez vu le rouge</li>
</ul>
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.1rem;">
<b>Au CC3 (15 juin), vous coderez sur feuille, sans outil.</b> Copilot est un tuteur pendant les TP ; vos réflexes doivent être les vôtres.
</div>

---

## 📚 Pour aller plus loin

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px;">
<b>🔀 Git</b>
<ul style="margin-top: 0.3rem; font-size: 0.95rem;">
<li><a href="https://git-scm.com/book/fr/v2" style="color: #a0d8f8;">Pro Git</a> (livre gratuit, français)</li>
<li><a href="https://learngitbranching.js.org/?locale=fr_FR" style="color: #a0d8f8;">Learn Git Branching</a> (tuto interactif)</li>
<li><a href="https://www.conventionalcommits.org/fr/" style="color: #a0d8f8;">Conventional Commits</a> (spec)</li>
<li><a href="https://ohshitgit.com/fr" style="color: #a0d8f8;">Oh Shit, Git !?!</a> (recettes de sauvetage)</li>
</ul>
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ TDD</b>
<ul style="margin-top: 0.3rem; font-size: 0.95rem;">
<li><em>Test-Driven Development by Example</em> - Kent Beck (2002)</li>
<li><em>The Art of Unit Testing</em> - Roy Osherove (3e éd. 2024)</li>
<li><a href="https://junit.org/junit5/docs/current/user-guide/" style="color: #a0d8f8;">JUnit 5 User Guide</a></li>
<li><a href="https://assertj.github.io/doc/" style="color: #a0d8f8;">AssertJ</a></li>
</ul>
</div>
</div>

---

<!-- _class: lead -->

# Ce qu'on fait maintenant

**🔀 TP1 - Git avancé** (cette semaine, ~2h non noté)
Rebase, cherry-pick, Conventional Commits, PR + review.

**✅ TP2 - TDD** (semaine prochaine, 6h noté)
Cycle RED-GREEN-REFACTOR, fake-it, triangulation, ApprovalTests.

**👉 Lien Classroom** sur [github.com/IUTInfoAix-R203/tp](https://github.com/IUTInfoAix-R203/tp)

---

<!-- _class: lead -->

# À suivre : CM2 - TDD avancé et refactoring

Dans 2 semaines, semaine du 4 mai.

Au programme : approfondir le TDD, découvrir les kata en pair programming, et préparer le refactoring du TP4.
