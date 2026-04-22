---
marp: true
theme: default
paginate: true
---

<!-- _class: lead -->
<!-- _paginate: false -->

# TDD, refactoring et code propre

**R2.03 - Qualité de développement**

IUT d'Aix-Marseille - BUT Informatique, 1re année

---

## Au programme de ce CM

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; font-size: 1.3rem;">
<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">✅</div>
<b>TDD approfondi</b><br/>
<span style="font-size: 0.9rem; opacity: 0.9;">F.I.R.S.T., stratégies de Beck, test doubles</span>
</div>
<div style="background: #e8a838; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🥋</div>
<b>Kata et pair programming</b><br/>
<span style="font-size: 0.9rem; opacity: 0.9;">Driver, navigator, ping-pong</span>
</div>
<div style="background: #e74c3c; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🧹</div>
<b>Code smells et refactoring</b><br/>
<span style="font-size: 0.9rem; opacity: 0.9;">Fowler, characterization tests</span>
</div>
</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; text-align: center; font-size: 1.1rem;">
Ce CM prépare <b>TP3 - Kata</b> (séance 3) et <b>TP4 - Refactoring</b> (séance 4).
</div>

---

## Où on en est

<div style="display: flex; gap: 0.8rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center; opacity: 0.55;">
<b>✓ CM1</b><br/><span style="font-size: 0.9rem;">Artisanat + Git + TDD intro</span>
</div>
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center; opacity: 0.55;">
<b>✓ TP1</b><br/><span style="font-size: 0.9rem;">Git avancé</span>
</div>
<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center; opacity: 0.55;">
<b>✓ TP2</b><br/><span style="font-size: 0.9rem;">TDD baby-steps</span>
</div>
<div style="background: #e8a838; color: white; padding: 1rem; border-radius: 10px; flex: 1.3; text-align: center; border: 3px solid #c87d00;">
<b>📍 CM2 (vous êtes ici)</b><br/><span style="font-size: 0.9rem;">TDD + Refactoring</span>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center;">
<b>TP3</b><br/><span style="font-size: 0.9rem;">Kata + pair prog</span>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center;">
<b>TP4</b><br/><span style="font-size: 0.9rem;">Refactoring</span>
</div>
<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; flex: 1; text-align: center;">
<b>CC3</b><br/><span style="font-size: 0.9rem;">Kata sur feuille</span>
</div>
</div>

<div style="margin-top: 1.5rem; font-size: 1.1rem; text-align: center;">
Ce que vous avez goûté au TP2, on va l'<b>approfondir</b>. Et on attaque le <b>refactoring</b> : transformer du code existant sans le casser.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 1 - TDD approfondi

On a vu le cycle RED-GREEN-REFACTOR. Maintenant, comment en tirer le maximum ?

---

## 🔁 Rappel : le cycle RED-GREEN-REFACTOR

```mermaid
graph LR
    R[RED<br/>Écrire un test<br/>qui échoue] --> G[GREEN<br/>Faire passer<br/>le test au plus vite]
    G --> F[REFACTOR<br/>Nettoyer<br/>sans casser]
    F --> R

    style R fill:#e74c3c,color:#fff
    style G fill:#27ae60,color:#fff
    style F fill:#4a90d9,color:#fff
```

<div style="display: flex; gap: 1.5rem; margin-top: 1rem;">
<div style="flex: 1; background: #fde8e6; padding: 1rem; border-radius: 10px; border-left: 5px solid #e74c3c;">
<b>RED</b> : j'écris <b>un seul</b> test. Il doit échouer pour la <b>bonne raison</b> (le comportement manque, pas une coquille de syntaxe).
</div>
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px; border-left: 5px solid #27ae60;">
<b>GREEN</b> : je code le <b>minimum</b> pour passer. Je n'ai <b>pas</b> le droit d'anticiper.
</div>
<div style="flex: 1; background: #e6f0f9; padding: 1rem; border-radius: 10px; border-left: 5px solid #4a90d9;">
<b>REFACTOR</b> : je nettoie (noms, duplication, lisibilité). La suite de tests reste <b>verte</b>.
</div>
</div>

---

## 🚦 Les 3 lois du TDD (Uncle Bob)

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; font-size: 1.25rem; line-height: 1.7;">

1. Tu n'écriras **pas de code de production** tant qu'un test **échoue** ne l'exige.
2. Tu n'écriras **pas plus de test** qu'il n'en faut pour **échouer** (une erreur de compilation compte comme un échec).
3. Tu n'écriras **pas plus de code de production** qu'il n'en faut pour faire **passer** le test qui échoue.

</div>

<div style="margin-top: 1rem; text-align: center; font-size: 1.1rem; color: #555;">
Ces lois semblent extrêmes. Elles sont là pour <b>forcer les baby-steps</b>.<br/>
À chaque cycle, vous alternez entre production et test toutes les <b>30 secondes à 2 minutes</b>.
</div>

---

## 🎯 Les 3 stratégies de Kent Beck (rappel TP2)

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 0.5rem;">

<div style="background: #fff3cd; padding: 1.2rem; border-radius: 10px; border-left: 5px solid #e8a838;">
<div style="font-size: 1.3rem;"><b>🎭 Fake it</b></div>
<div style="margin-top: 0.3rem; font-size: 0.95rem;">Je rends <b>exactement</b> ce que le test attend.</div>

```java
// Test : assertThat(add(1,2)).isEqualTo(3)
int add(int a, int b) { return 3; }
```
<div style="font-size: 0.85rem; margin-top: 0.3rem;">✔ Confirme que le test passe</div>
<div style="font-size: 0.85rem;">✔ Force à écrire un <b>2e test</b></div>
</div>

<div style="background: #d1ecf1; padding: 1.2rem; border-radius: 10px; border-left: 5px solid #17a2b8;">
<div style="font-size: 1.3rem;"><b>📐 Triangulation</b></div>
<div style="margin-top: 0.3rem; font-size: 0.95rem;">J'ajoute un 2e test pour <b>forcer la généralisation</b>.</div>

```java
assertThat(add(1,2)).isEqualTo(3);
assertThat(add(2,3)).isEqualTo(5);
// → return a + b;
```
<div style="font-size: 0.85rem; margin-top: 0.3rem;">✔ Très sûr, peu de sauts</div>
</div>

<div style="background: #d4edda; padding: 1.2rem; border-radius: 10px; border-left: 5px solid #27ae60;">
<div style="font-size: 1.3rem;"><b>💡 Obvious</b></div>
<div style="margin-top: 0.3rem; font-size: 0.95rem;">La solution est <b>évidente</b> : je la code directement.</div>

```java
int add(int a, int b) { return a + b; }
```
<div style="font-size: 0.85rem; margin-top: 0.3rem;">✔ Rapide quand ça va</div>
<div style="font-size: 0.85rem;">⚠ Risque de se tromper</div>
</div>

</div>

<div style="margin-top: 0.8rem; text-align: center; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px;">
<b>Règle d'or</b> : plus c'est compliqué, plus on ralentit (fake-it → triangulation). L'obvious, c'est pour les cas triviaux.
</div>

---

## ✅ Qu'est-ce qu'un bon test ? Le principe F.I.R.S.T.

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 0.3rem;">

| Lettre | Signifie | Pourquoi |
|---|---|---|
| **F**ast | Rapide (quelques ms) | On les lance des dizaines de fois par heure |
| **I**ndependent | Indépendants entre eux | Changer l'ordre ne doit rien casser |
| **R**epeatable | Reproductible | Pas de dépendance au réseau, à l'heure, à un fichier temporaire |
| **S**elf-validating | Auto-vérifiant | Rouge ou vert, pas de « regardez le log » |
| **T**imely | Écrit au bon moment | **Avant** le code, pas après |

</div>

<div style="margin-top: 1rem; text-align: center; font-size: 1.1rem;">
Robert C. Martin (<em>Clean Code</em>, 2008)
</div>

---

## 🧪 La structure AAA d'un test

<div style="display: flex; gap: 1rem; margin-top: 0.5rem;">
<div style="flex: 1; background: #e6f0f9; padding: 1rem; border-radius: 10px;">

**Arrange**
Préparer l'environnement, les données, les dépendances.

**Act**
Déclencher le comportement testé (UNE seule action).

**Assert**
Vérifier le résultat (idéalement UNE assertion principale).

</div>
<div style="flex: 1.3;">

```java
@Test
void additionne_deux_entiers_positifs() {
  // Arrange
  Calculatrice c = new Calculatrice();

  // Act
  int resultat = c.additionner(2, 3);

  // Assert
  assertThat(resultat).isEqualTo(5);
}
```

</div>
</div>

<div style="margin-top: 0.8rem; background: #2c3e50; color: white; padding: 0.8rem 1rem; border-radius: 8px;">
💡 <b>Astuce nommage</b> : <code>nom_scenario_comportement_attendu</code> ou <code>should_X_when_Y</code>. Un bon nom de test se lit comme une phrase.
</div>

---

## 📝 Exemple : noms de tests parlants

<div style="display: flex; gap: 1.5rem; margin-top: 0.5rem;">
<div style="flex: 1; background: #fde8e6; padding: 1.2rem; border-radius: 10px;">

**❌ Pas clair**

```java
@Test void test1() { ... }
@Test void testAdd() { ... }
@Test void testCalc() { ... }
@Test void bugFix12345() { ... }
```

On ne sait **pas ce qui est testé**, ni **quel comportement** est attendu.

</div>
<div style="flex: 1; background: #e6f5ec; padding: 1.2rem; border-radius: 10px;">

**✅ Clair**

```java
@Test void additionne_deux_positifs()
@Test void additionne_avec_zero_retourne_lautre_nombre()
@Test void solde_negatif_leve_exception()
@Test void panier_vide_a_un_total_zero()
```

On lit le test comme une **spécification**.

</div>
</div>

---

## 🎭 Les test doubles (bref aperçu)

Quand le code testé dépend d'autre chose (base de données, service externe, horloge), on utilise un **double** - un objet qui remplace la vraie dépendance dans le test.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.5rem;">

<div style="background: #e6f0f9; padding: 1rem; border-radius: 10px;">
<b>🪨 Stub</b> : renvoie une réponse prédéfinie.<br/>
<em>Exemple</em> : un repo qui renvoie toujours la même liste d'utilisateurs.
</div>

<div style="background: #fff3cd; padding: 1rem; border-radius: 10px;">
<b>🎯 Mock</b> : vérifie <b>comment</b> il est appelé.<br/>
<em>Exemple</em> : vérifier que <code>envoyerEmail</code> a bien été appelé 1 fois.
</div>

<div style="background: #d1ecf1; padding: 1rem; border-radius: 10px;">
<b>🕵️ Spy</b> : double qui enregistre les appels tout en utilisant la vraie implémentation.
</div>

<div style="background: #d4edda; padding: 1rem; border-radius: 10px;">
<b>🎪 Fake</b> : implémentation alternative simplifiée (ex : repo en mémoire au lieu d'une vraie BDD).
</div>

</div>

<div style="margin-top: 0.8rem; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; text-align: center;">
Dans ce module, on utilise <b>Mockito</b> (tp2 avancé, tp3). Pas obligatoire au CC3.
</div>

---

## 🎯 Exemple Mockito

```java
@Test
void envoie_un_email_quand_la_commande_est_validee() {
  // Arrange : on crée un mock
  EmailService email = mock(EmailService.class);
  GestionCommande g = new GestionCommande(email);

  // Act
  g.valider(new Commande("alice@iut.fr", 42));

  // Assert : on vérifie l'appel
  verify(email).envoyer("alice@iut.fr", "Commande 42 confirmée");
}
```

<div style="margin-top: 0.8rem; background: #fff3cd; padding: 1rem; border-radius: 8px;">
⚠️ <b>Ne pas abuser des mocks</b>. Un mock remplace une vraie dépendance : s'il est mal configuré, le test peut passer alors que le code est cassé.<br/>
Règle pragmatique : <b>mocker seulement ce qu'on ne contrôle pas</b> (I/O, réseau, horloge).
</div>

---

## 📸 ApprovalTests : quand la sortie est textuelle

Pour du code qui produit une sortie complexe (grille, JSON, rapport), écrire l'attendu à la main est pénible.

<div style="display: flex; gap: 1rem; margin-top: 0.5rem;">
<div style="flex: 1.2;">

```java
@Test
void grille_demineur_5x5() {
  List<String> entree = List.of(
    " *   ",
    "     ",
    "  *  ",
    "     ",
    "   * "
  );
  List<String> sortie =
    new GrilleDemineur(entree).annotee();
  Approvals.verifyAll("", sortie);
}
```

</div>
<div style="flex: 1;">

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px;">

**Principe**
1. Je lance le test
2. La sortie va dans `...received.txt`
3. Je <b>vérifie visuellement</b>
4. Je renomme `received` → `approved`
5. Le test compare ensuite `received` à `approved`

</div>

</div>
</div>

<div style="margin-top: 0.5rem; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; text-align: center;">
Utilisé au TP2 exercice 5 (Démineur) - gain énorme sur les grandes grilles.
</div>

---

## 💡 Règles pour ne pas se planter en TDD

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.5rem;">

<div style="background: #fde8e6; padding: 1rem; border-radius: 10px; border-left: 5px solid #e74c3c;">
<b>❌ Ne pas écrire plusieurs tests à la suite sans coder.</b><br/>
<span style="font-size: 0.9rem;">Un test écrit, un test codé. Sinon vous perdez le filet de sécurité.</span>
</div>

<div style="background: #fde8e6; padding: 1rem; border-radius: 10px; border-left: 5px solid #e74c3c;">
<b>❌ Ne pas écrire du code qui n'est pas couvert par un test.</b><br/>
<span style="font-size: 0.9rem;">Si vous écrivez une branche <code>if</code> en plus, un test doit l'exiger.</span>
</div>

<div style="background: #fde8e6; padding: 1rem; border-radius: 10px; border-left: 5px solid #e74c3c;">
<b>❌ Ne pas sauter le REFACTOR.</b><br/>
<span style="font-size: 0.9rem;">Le cycle est à 3 étapes, pas à 2. Sinon la dette technique explose.</span>
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px; border-left: 5px solid #27ae60;">
<b>✅ Vérifier que le test <u>échoue</u> avant de coder.</b><br/>
<span style="font-size: 0.9rem;">Sinon vous risquez un faux positif : un test qui passait déjà.</span>
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px; border-left: 5px solid #27ae60;">
<b>✅ Commit à chaque GREEN ou REFACTOR.</b><br/>
<span style="font-size: 0.9rem;">Chaque état vert est un point de sauvegarde exploitable.</span>
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px; border-left: 5px solid #27ae60;">
<b>✅ Un seul test qui échoue à la fois.</b><br/>
<span style="font-size: 0.9rem;">Focaliser l'attention. Pas 5 rouges en parallèle.</span>
</div>

</div>

---

## 📊 Pyramide des tests

```mermaid
graph BT
    subgraph P[" "]
        E2E["E2E / IHM<br/>peu, lents, fragiles"]
        INT["Intégration<br/>modéré, plus lents"]
        U["Tests unitaires<br/>beaucoup, rapides, précis"]
    end

    style U fill:#27ae60,color:#fff
    style INT fill:#e8a838,color:#fff
    style E2E fill:#e74c3c,color:#fff
```

<div style="margin-top: 0.5rem; display: flex; gap: 1rem;">
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 8px;">
<b>Beaucoup</b> de tests unitaires (vite, ciblés) : la base de la pyramide.
</div>
<div style="flex: 1; background: #fff3cd; padding: 1rem; border-radius: 8px;">
<b>Moins</b> de tests d'intégration (plusieurs classes ensemble).
</div>
<div style="flex: 1; background: #fde8e6; padding: 1rem; border-radius: 8px;">
<b>Encore moins</b> de tests bout-en-bout (lents, cassants).
</div>
</div>

<div style="margin-top: 0.5rem; text-align: center; font-size: 1rem; color: #555;">
Dans ce module, on se concentre sur la <b>base</b> : les tests unitaires.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 2 - Le kata et le pair programming

Comment on devient meilleur ? En répétant des gestes simples.

---

## 🥋 Qu'est-ce qu'un kata ?

<div style="display: flex; gap: 2rem; margin-top: 1rem;">
<div style="flex: 1;">

Dans les arts martiaux, un **kata** est une séquence de mouvements qu'on répète jusqu'à ce que le corps l'exécute sans y penser.

En programmation, un **coding kata** est un petit exercice qu'on refait **plusieurs fois** pour :

- **automatiser** des gestes (raccourcis IDE, TDD, refactoring)
- **essayer** des approches différentes
- **comparer** avec d'autres développeurs

Concept popularisé par **Dave Thomas** (*The Pragmatic Programmer*, 2003).

</div>
<div style="flex: 1;">

<div style="background: #e8a838; color: white; padding: 1.5rem; border-radius: 12px; font-size: 1.1rem;">

🎯 **Le but n'est pas de résoudre le problème.**
Le problème, vous le connaissez déjà.

Le but, c'est d'améliorer **votre façon** de le résoudre.

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; font-size: 0.95rem;">
Analogie : un pianiste ne joue pas ses gammes pour « réussir les gammes ». Il les joue pour <b>garder la main</b>.
</div>

</div>
</div>

---

## 🥋 Quelques kata célèbres

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; margin-top: 0.5rem; font-size: 0.95rem;">

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🎳 Bowling (Uncle Bob)</b><br/>
Calcul d'un score de bowling. Simple, mais plein de pièges sur les strikes et spares.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🎾 Tennis (various)</b><br/>
Afficher le score d'un jeu de tennis. Idéal pour les state machines.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🎲 Yahtzee</b><br/>
Scorer les combinaisons d'un jet de 5 dés. Bon terrain pour la stratégie.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🔢 String Calculator (Osherove)</b><br/>
Parser une chaîne et additionner les nombres. Progression en 9 étapes.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🗓️ Années bissextiles</b><br/>
Multi-règles booléennes. Premier kata idéal.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🏪 Gilded Rose (Emily Bache)</b><br/>
Kata de <b>refactoring</b> sur du legacy volontairement horrible.
</div>

</div>

<div style="margin-top: 0.8rem; text-align: center; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px;">
Au TP3, on en fera <b>5</b> : Années bissextiles, Tennis, Gestion employés, Pagination, Yahtzee.
</div>

---

## 🤔 Pourquoi refaire un kata qu'on sait résoudre ?

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.5rem;">

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>🏃 1ère fois</b> : je galère, je découvre les règles. Je code « quelque chose qui marche ».
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>2ème fois</b> : je vais plus vite, je vois les pièges. Je soigne le nommage.
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>3ème fois</b> : je teste une autre approche (fake-it seulement, triangulation seulement).
</div>

<div style="background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>10ème fois</b> : je suis fluide. Je peux me concentrer sur le <b>style</b>, pas le problème.
</div>

</div>

<div style="margin-top: 0.8rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; text-align: center; font-size: 1.1rem;">
Un sportif ne s'entraîne pas le jour du match. Un développeur non plus.
</div>

---

## 👥 Le pair programming

<div style="display: flex; gap: 1.5rem; margin-top: 0.3rem;">
<div style="flex: 1;">

**Deux personnes, un clavier.**

<div style="background: #4a90d9; color: white; padding: 1rem; border-radius: 10px; margin-top: 0.8rem;">
<b>🎮 Driver</b><br/>Celui qui tape. Se concentre sur le <b>comment</b> (syntaxe, IDE, tests qui passent).
</div>

<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px; margin-top: 0.5rem;">
<b>🧭 Navigator</b><br/>Celui qui pense. Se concentre sur le <b>quoi</b> (design, edge cases, lisibilité).
</div>

<div style="background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; margin-top: 0.8rem; text-align: center;">
On <b>échange</b> les rôles toutes les 7 à 10 minutes.
</div>

</div>
<div style="flex: 1;">

<div style="background: #e8a838; color: white; padding: 1.5rem; border-radius: 12px;">

**Bénéfices**

- Moins de bugs (deux cerveaux sur chaque ligne)
- Montée en compétences croisée
- Moins de « bus factor » sur le code
- Revue de code permanente, en temps réel
- Effet antisomnolent 😴

</div>

<div style="margin-top: 1rem; background: #fde8e6; padding: 1rem; border-radius: 10px; border-left: 5px solid #e74c3c;">

**⚠ Attention**
- Pas le même que « un qui code, un qui regarde son téléphone »
- Fatigant - faire des pauses toutes les heures

</div>

</div>
</div>

---

## 🏓 Le ping-pong TDD

Un cas particulier très puissant de pair programming :

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; margin-top: 0.5rem;">

1. **A écrit un test** qui échoue (RED).
2. **B écrit le code** qui fait passer (GREEN).
3. **B écrit le test suivant** qui échoue (RED).
4. **A écrit le code** qui fait passer (GREEN).
5. À tour de rôle pour **REFACTOR**.

</div>

<div style="display: flex; gap: 1rem; margin-top: 0.8rem;">
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>✅ Avantage 1</b> : chacun des deux <b>devine l'intention</b> de l'autre. Excellent pour le design.
</div>
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>✅ Avantage 2</b> : impossible d'écrire du code « en douce » sans test. Le coéquipier impose la discipline.
</div>
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>✅ Avantage 3</b> : on voit <b>immédiatement</b> si un test est mal écrit - l'autre ne sait pas quoi coder.
</div>
</div>

---

## 🎯 Démo en ouverture du TP3

Au début du TP3, on fera **20 min de kata live** en pair programming.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.8rem;">

<div style="background: #e6f0f9; padding: 1rem; border-radius: 10px;">
<b>Kata retenu</b> : <em>Tennis scoring</em><br/>
Un état (jeu en cours) + un comportement (marquer un point) → l'affichage du score.
</div>

<div style="background: #e6f0f9; padding: 1rem; border-radius: 10px;">
<b>Ce que vous verrez</b> :<br/>
- Alternance driver/navigator toutes les ~5 min<br/>
- Commit à chaque GREEN<br/>
- Pas de shortcut IDE (vous devez suivre)
</div>

</div>

<div style="margin-top: 0.8rem; background: #e8a838; color: white; padding: 1rem; border-radius: 10px; text-align: center; font-size: 1.1rem;">
🥋 Le but : que vous voyiez <b>à quoi ressemble</b> une séance TDD en binôme - pas juste lire le texte d'un kata.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Partie 3 - Code smells et refactoring

Du code qui marche, mais qui pue. On fait quoi ?

---

## 👃 Qu'est-ce qu'un code smell ?

<div style="display: flex; gap: 2rem; align-items: center; margin-top: 0.5rem;">
<div style="flex: 1.2;">

Terme inventé par **Kent Beck** et popularisé par **Martin Fowler** (*Refactoring*, 1999).

Un **code smell** est un **indice** que quelque chose ne va pas dans votre code. Pas un bug, pas une erreur de compilation - juste un signal qui dit :

> « Attention, cette zone devient difficile à maintenir. »

Un peu comme un aliment qui sent bizarre : **pas forcément périmé, mais il faut regarder de près.**

</div>
<div style="flex: 1; text-align: center;">

<div style="background: #e74c3c; color: white; padding: 2rem; border-radius: 12px; font-size: 3rem;">
👃
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; font-size: 0.9rem;">
« If it stinks, change it. » - Kent Beck
</div>

</div>
</div>

---

## 📚 Les code smells les plus courants (1/2)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; margin-top: 0.3rem; font-size: 0.92rem;">

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>📏 Long Method</b><br/>
Une méthode de 50 lignes qu'on scroll pour la lire.<br/>
<em>Solution</em> : Extract Method.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🏢 Large Class</b><br/>
Une classe qui fait tout (God class).<br/>
<em>Solution</em> : Extract Class.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>📋 Long Parameter List</b><br/>
Une méthode à 7 paramètres, imbuvable à l'appel.<br/>
<em>Solution</em> : Introduce Parameter Object.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>👯 Duplicated Code</b><br/>
Le même bloc copié-collé en 3 endroits.<br/>
<em>Solution</em> : Extract Method / Move Method.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🔢 Magic Numbers</b><br/>
<code>if (age > 65)</code>, <code>total *= 1.20</code>.<br/>
<em>Solution</em> : Replace Magic Number with Constant.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🌳 Nested Conditionals</b><br/>
Des <code>if</code> imbriqués sur 5 niveaux.<br/>
<em>Solution</em> : Guard Clauses, Extract Method.
</div>

</div>

---

## 📚 Les code smells les plus courants (2/2)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; margin-top: 0.3rem; font-size: 0.92rem;">

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🔌 Feature Envy</b><br/>
Une méthode de A qui manipule surtout des données de B.<br/>
<em>Solution</em> : Move Method.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🧩 Data Clumps</b><br/>
Les mêmes 3 paramètres qui voyagent ensemble partout.<br/>
<em>Solution</em> : Extract Class.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🔣 Primitive Obsession</b><br/>
<code>String email</code>, <code>int codePostal</code> partout au lieu de vrais types.<br/>
<em>Solution</em> : Replace Primitive with Object.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🔀 Switch Statements</b><br/>
Un <code>switch</code> sur un type, dupliqué en 5 endroits.<br/>
<em>Solution</em> : Replace Conditional with Polymorphism.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>💬 Comments qui expliquent le code</b><br/>
Un commentaire qui traduit ce que fait un bloc.<br/>
<em>Solution</em> : Extract Method avec un bon nom.
</div>

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c;">
<b>🏷️ Mauvais nommage</b><br/>
<code>int x, y, z</code>, <code>void doStuff()</code>.<br/>
<em>Solution</em> : Rename.
</div>

</div>

---

## 🔧 Qu'est-ce qu'un refactoring ?

<div style="background: #2c3e50; color: white; padding: 1.5rem; border-radius: 12px; font-size: 1.2rem; line-height: 1.6; margin-top: 0.5rem;">

> **Refactoring** : modifier la **structure interne** du code<br/>
> <b>sans changer son comportement observable</b>.

<div style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.8;">
Martin Fowler, <em>Refactoring: Improving the Design of Existing Code</em> (1999, 2018)
</div>

</div>

<div style="display: flex; gap: 1.5rem; margin-top: 1rem;">
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
<b>✅ Refactoring</b><br/>
Renommer une variable, extraire une méthode, bouger un champ dans une autre classe.<br/>
→ <b>Les tests existants continuent de passer.</b>
</div>

<div style="flex: 1; background: #fde8e6; padding: 1rem; border-radius: 10px;">
<b>❌ Pas un refactoring</b><br/>
Changer ce que fait une méthode, ajouter une fonctionnalité, corriger un bug.<br/>
→ Là, les tests changent (ou en deviennent rouges).
</div>
</div>

<div style="margin-top: 0.8rem; background: #e8a838; color: white; padding: 0.8rem; border-radius: 8px; text-align: center;">
🛡️ <b>Prérequis absolu</b> : une suite de tests qui couvre le comportement. Sinon vous faites du <em>rewriting</em>, pas du refactoring.
</div>

---

## 📖 Le catalogue de Fowler (70+ refactorings)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; margin-top: 0.3rem; font-size: 0.95rem;">

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🏷️ Rename</b><br/>
Renommer variable, méthode, classe. Le plus fréquent.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>✂️ Extract Method</b><br/>
Sortir un bloc dans une méthode nommée.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>📌 Inline</b><br/>
L'inverse : replacer le corps d'une méthode dans l'appelant.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>📦 Extract Class</b><br/>
Sortir un groupe de champs + méthodes dans une nouvelle classe.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>➡️ Move Method</b><br/>
Déplacer une méthode vers la classe qu'elle utilise le plus.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🎁 Introduce Parameter Object</b><br/>
Grouper des paramètres qui voyagent ensemble dans un objet.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🦎 Replace Conditional with Polymorphism</b><br/>
Un <code>switch</code> → une hiérarchie de classes.
</div>

<div style="background: #e6f0f9; padding: 0.8rem 1rem; border-radius: 8px;">
<b>🔢 Replace Magic Number with Constant</b><br/>
<code>0.2</code> → <code>TAUX_TVA</code>.
</div>

</div>

<div style="margin-top: 0.7rem; text-align: center; background: #2c3e50; color: white; padding: 0.7rem; border-radius: 8px; font-size: 0.95rem;">
Référence : <a href="https://refactoring.com/catalog/" style="color: #a0d8f8;">refactoring.com/catalog</a> - le catalogue complet en ligne.
</div>

---

## 🧪 Exemple : Extract Method

<div style="display: flex; gap: 1rem;">
<div style="flex: 1; background: #fde8e6; padding: 0.8rem; border-radius: 8px; font-size: 0.8rem;">

**Avant (smell : Long Method)**

```java
void imprimerFacture(Client c, List<Article> a) {
  // entête
  System.out.println("=== FACTURE ===");
  System.out.println("Client : " + c.nom());
  System.out.println("Date : " + LocalDate.now());

  // lignes
  for (Article art : a) {
    System.out.printf("  %s x%d : %.2f€%n",
      art.nom(), art.qte(), art.prix() * art.qte());
  }

  // total
  double t = 0;
  for (Article art : a) t += art.prix() * art.qte();
  System.out.printf("TOTAL : %.2f€%n", t * 1.20);
}
```

</div>
<div style="flex: 1; background: #e6f5ec; padding: 0.8rem; border-radius: 8px; font-size: 0.8rem;">

**Après**

```java
void imprimerFacture(Client c, List<Article> a) {
  imprimerEntete(c);
  imprimerLignes(a);
  imprimerTotal(a);
}

void imprimerEntete(Client c) {
  System.out.println("=== FACTURE ===");
  System.out.println("Client : " + c.nom());
  System.out.println("Date : " + LocalDate.now());
}

void imprimerLignes(List<Article> a) { /* ... */ }

double calculerTotalHT(List<Article> a) {
  return a.stream()
    .mapToDouble(x -> x.prix() * x.qte()).sum();
}
```

</div>
</div>

<div style="margin-top: 0.5rem; text-align: center; background: #2c3e50; color: white; padding: 0.5rem; border-radius: 6px; font-size: 0.95rem;">
Code de <b>gauche</b> : on doit tout lire pour comprendre. <b>Droite</b> : on lit <code>imprimerFacture</code> comme un sommaire.
</div>

---

## 🧪 Exemple : Replace Conditional with Polymorphism

<div style="display: flex; gap: 1rem;">
<div style="flex: 1; background: #fde8e6; padding: 0.8rem; border-radius: 8px; font-size: 0.8rem;">

**Avant (smell : Switch Statements)**

```java
class Animal {
  String type;

  String faireDuBruit() {
    switch (type) {
      case "chien":  return "Wouf !";
      case "chat":   return "Miaou !";
      case "vache":  return "Meuh !";
      case "canard": return "Coin coin !";
      default: throw new IllegalStateException();
    }
  }
}
```

Chaque nouveau type → modifier cette classe.<br/>
Un <code>switch</code> sur le type est souvent dupliqué.

</div>
<div style="flex: 1; background: #e6f5ec; padding: 0.8rem; border-radius: 8px; font-size: 0.8rem;">

**Après**

```java
abstract class Animal {
  abstract String faireDuBruit();
}

class Chien extends Animal {
  String faireDuBruit() { return "Wouf !"; }
}

class Chat extends Animal {
  String faireDuBruit() { return "Miaou !"; }
}

class Vache extends Animal {
  String faireDuBruit() { return "Meuh !"; }
}
```

Nouveau type → nouvelle classe. **Pas touche** au reste.

</div>
</div>

<div style="margin-top: 0.5rem; text-align: center; background: #2c3e50; color: white; padding: 0.5rem; border-radius: 6px; font-size: 0.95rem;">
Principe <b>Open/Closed</b> : ouvert à l'extension, fermé à la modification.
</div>

---

## 🛠️ Votre IDE fait le gros du travail

<div style="display: flex; gap: 1.5rem; margin-top: 0.5rem;">
<div style="flex: 1;">

Un refactoring **manuel** est risqué. Un oubli, un mauvais remplacement → comportement changé.

**IntelliJ IDEA** (utilisé par les pros, gratuit en Community) et **VS Code** (avec extensions Java) proposent des refactorings **automatiques et sûrs** :

- `F6` : Rename (change **toutes** les occurrences, imports inclus)
- `Ctrl+Alt+M` : Extract Method
- `Ctrl+Alt+V` : Extract Variable
- `Ctrl+Alt+F` : Extract Field
- `Ctrl+Alt+C` : Extract Constant

</div>
<div style="flex: 1;">

<div style="background: #4a90d9; color: white; padding: 1.5rem; border-radius: 12px;">

**💡 Règle pragmatique**

> Si tu peux faire le refactoring **avec un raccourci IDE**, fais-le avec. Si tu dois le faire à la main, **ajoute d'abord des tests**.

</div>

<div style="margin-top: 1rem; background: #fff3cd; padding: 1rem; border-radius: 8px;">

**Au TP4**, on abuse des raccourcis IntelliJ / VS Code.

</div>

</div>
</div>

---

## 🛡️ Characterization tests : sécuriser du legacy

<div style="display: flex; gap: 1.5rem; margin-top: 0.3rem;">
<div style="flex: 1;">

Concept de **Michael Feathers** (*Working Effectively with Legacy Code*, 2004).

> **Legacy code** = du code **sans tests**, qu'on doit faire évoluer.

**Problème** : on veut refactorer, mais sans tests on n'a pas de filet.

**Solution** : des **characterization tests** - des tests qui **décrivent le comportement actuel** du code, qu'il soit « juste » ou non.

</div>
<div style="flex: 1;">

<div style="background: #2c3e50; color: white; padding: 1.2rem; border-radius: 12px;">

**Démarche**

1. Je prends le code en entrée.
2. Je lance le code, j'observe la sortie.
3. J'écris un test qui **attend cette sortie**.
4. Le test passe - je l'ai **figé**.
5. Maintenant je peux refactorer : si un test casse, j'ai changé le comportement (donc j'ai un bug, pas un refactoring).

</div>

<div style="margin-top: 0.8rem; background: #e8a838; color: white; padding: 0.8rem; border-radius: 8px; text-align: center; font-size: 0.95rem;">
Ces tests <b>ne valident pas</b> que le code est juste - ils le <b>pinnent</b>.
</div>

</div>
</div>

---

## 🎯 Le pattern du TP4

Chaque exercice du TP4 suit le même squelette :

```mermaid
graph LR
    A[1. Lire le code<br/>smelly] --> B[2. Lire les tests<br/>de caractérisation<br/>déjà écrits]
    B --> C[3. Vérifier qu'ils<br/>passent en l'état]
    C --> D[4. Refactorer<br/>par petits pas]
    D --> E[5. Tests toujours<br/>verts à chaque pas]
    E --> F[6. Commit à<br/>chaque étape sûre]

    style A fill:#e74c3c,color:#fff
    style B fill:#e8a838,color:#fff
    style C fill:#27ae60,color:#fff
    style D fill:#4a90d9,color:#fff
    style E fill:#27ae60,color:#fff
    style F fill:#2c3e50,color:#fff
```

<div style="margin-top: 0.5rem; background: #fff3cd; padding: 1rem; border-radius: 8px; text-align: center;">
⚠️ <b>Si un test casse</b>, ne le modifiez pas pour le faire passer. Annulez votre refactoring (<code>git reset</code>, <code>Ctrl+Z</code>). Votre « refactoring » était un <b>bug</b>.
</div>

---

## 🌹 Le kata Gilded Rose

<div style="display: flex; gap: 1.5rem;">
<div style="flex: 1.2;">

**Créé par Terry Hughes, popularisé par Emily Bache.**

Un magasin vend des articles qui évoluent tous les jours :
- Articles normaux (perdent en qualité)
- Aged Brie (gagne en qualité)
- Sulfuras (immuable)
- Backstage passes (complexe)
- **Conjured** (à ajouter)

Le code source tient en **35 lignes** - mais quelles lignes. `if` imbriqués, noms cryptiques, duplication partout.

**Votre mission** :
1. Comprendre (*characterization tests*)
2. Refactorer (sans casser)
3. **Ajouter la fonctionnalité Conjured**

</div>
<div style="flex: 1;">

<div style="background: #8e44ad; color: white; padding: 1.2rem; border-radius: 12px;">

**Pourquoi ce kata est devenu un classique**

C'est exactement la situation d'un développeur qui arrive dans une entreprise :

- du code qu'il n'a pas écrit
- sans docs
- qu'il faut **modifier**
- sans **casser** l'existant

Ajouter Conjured **directement** dans le code spaghetti est très risqué. Le refactoring **d'abord** rend le changement trivial.

</div>

<div style="margin-top: 0.8rem; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; text-align: center;">
🎬 <b>Démo live en ouverture du TP4</b> (20 min).
</div>

</div>
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Clean Code - touches finales

Quelques principes transverses à retenir pour la vie.

---

## 🏕️ La règle du scout

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; font-size: 1.3rem; line-height: 1.6; text-align: center;">

> « Leave the campground cleaner than you found it. »
>
> **Laisse le campement plus propre que tu ne l'as trouvé.**

<div style="margin-top: 0.8rem; font-size: 0.95rem; opacity: 0.85;">
Adapté du scoutisme par Robert C. Martin (<em>Clean Code</em>, 2008)
</div>

</div>

<div style="margin-top: 1rem; text-align: center; font-size: 1.2rem;">
Chaque fois que vous <b>touchez</b> un fichier, vous le laissez <b>un peu mieux</b>.<br/>
Un nom plus clair, une méthode extraite, un test ajouté.
</div>

<div style="margin-top: 1rem; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
💡 <b>Effet cumulé</b> : 20 développeurs qui améliorent 2 lignes à chaque PR = la base de code s'<b>auto-nettoie</b>. Inverse du cercle vicieux de la dette technique.
</div>

---

## 🏷️ Le nommage : première victoire

<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; font-size: 1.1rem; text-align: center; margin-bottom: 0.8rem;">
« There are only <b>two hard things</b> in Computer Science: cache invalidation and <b>naming things</b>. » - Phil Karlton
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; font-size: 0.92rem;">

<div style="background: #fde8e6; padding: 0.8rem 1rem; border-radius: 8px;">

❌ `int d;`<br/>
❌ `List<Integer> list;`<br/>
❌ `void doStuff() { ... }`<br/>
❌ `boolean flag = true;`

</div>

<div style="background: #e6f5ec; padding: 0.8rem 1rem; border-radius: 8px;">

✅ `int joursRestants;`<br/>
✅ `List<Integer> ageEtudiants;`<br/>
✅ `void envoyerRappel() { ... }`<br/>
✅ `boolean estInscrit = true;`

</div>

</div>

<div style="margin-top: 0.8rem; display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.5rem; font-size: 0.9rem;">
<div style="background: #e6f0f9; padding: 0.7rem; border-radius: 8px;"><b>Classe</b> : nom commun<br/><code>Commande</code>, <code>Facture</code></div>
<div style="background: #e6f0f9; padding: 0.7rem; border-radius: 8px;"><b>Méthode</b> : verbe<br/><code>calculer</code>, <code>envoyer</code></div>
<div style="background: #e6f0f9; padding: 0.7rem; border-radius: 8px;"><b>Booléen</b> : question<br/><code>estValide</code>, <code>aPaye</code></div>
</div>

---

## 🧱 SOLID - le S : Single Responsibility

Une classe doit avoir **une seule raison de changer**.

<div style="display: flex; gap: 1rem; margin-top: 0.3rem;">
<div style="flex: 1; background: #fde8e6; padding: 0.8rem; border-radius: 8px; font-size: 0.85rem;">

**❌ Employe qui fait tout**

```java
class Employe {
  double calculerSalaire() { ... }
  void sauvegarderEnBDD() { ... }
  String genererRapportPDF() { ... }
  void envoyerEmailBulletin() { ... }
}
```

Raisons de changer : règles RH, schéma BDD, format PDF, SMTP... → **4 raisons** = trop.

</div>
<div style="flex: 1; background: #e6f5ec; padding: 0.8rem; border-radius: 8px; font-size: 0.85rem;">

**✅ Chacun son rôle**

```java
class Employe { /* données + comportement métier */ }

class CalculSalaire { ... }
class EmployeRepository { ... }
class RapportGenerator { ... }
class BulletinMailer { ... }
```

Chaque classe : **une** raison de changer.

</div>
</div>

<div style="margin-top: 0.5rem; background: #2c3e50; color: white; padding: 0.6rem; border-radius: 6px; font-size: 0.95rem; text-align: center;">
SOLID = 5 principes de Robert C. Martin. Le <b>S</b> suffit déjà à améliorer énormément votre code.
</div>

---

## 💬 Les commentaires : utiliser avec parcimonie

<div style="display: flex; gap: 1.5rem; margin-top: 0.5rem;">
<div style="flex: 1; background: #fde8e6; padding: 1rem; border-radius: 10px; font-size: 0.95rem;">

**❌ Commente pour compenser**

```java
// Vérifie si l'utilisateur a plus de 18 ans
if (u.getA() > 18) { ... }
```

→ Renomme plutôt : `if (utilisateur.estMajeur())`.

</div>
<div style="flex: 1; background: #e6f5ec; padding: 1rem; border-radius: 10px; font-size: 0.95rem;">

**✅ Commente le pourquoi**

```java
// Le SDK distant exige un id positif strict ;
// 0 provoque un NPE côté serveur.
if (id <= 0) throw ...;
```

→ Information qui ne peut **pas** être déduite du code.

</div>
</div>

<div style="margin-top: 0.8rem; background: #2c3e50; color: white; padding: 0.8rem; border-radius: 8px; text-align: center;">
<b>Règle</b> : avant d'écrire un commentaire, demandez-vous si un <b>meilleur nom</b> ou une <b>méthode extraite</b> rendrait le commentaire inutile.
</div>

---

## 📚 Les livres à lire (un jour)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; margin-top: 0.3rem; font-size: 0.95rem;">

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 Refactoring</b> (Fowler, 1999/2018)<br/>
<em>La bible. Catalogue de 70+ refactorings avec exemples.</em>
</div>

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 Clean Code</b> (Martin, 2008)<br/>
<em>Règles de nommage, fonctions, commentaires, classes.</em>
</div>

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 Test-Driven Development: By Example</b> (Beck, 2002)<br/>
<em>Le TDD expliqué par son inventeur, en 200 pages.</em>
</div>

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 Working Effectively with Legacy Code</b> (Feathers, 2004)<br/>
<em>Comment sauver du code sans tests.</em>
</div>

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 The Pragmatic Programmer</b> (Hunt & Thomas, 1999/2019)<br/>
<em>100 conseils transverses. Un classique.</em>
</div>

<div style="background: #e6f0f9; padding: 0.8rem; border-radius: 8px;">
<b>📖 The Mikado Method</b> (Ellnestam, 2014)<br/>
<em>Une méthode pour attaquer de gros refactorings.</em>
</div>

</div>

<div style="margin-top: 0.7rem; text-align: center; background: #2c3e50; color: white; padding: 0.6rem; border-radius: 8px; font-size: 0.95rem;">
💡 Commencez par <b>Clean Code</b> (chapitres 1 à 3) et <b>Refactoring</b> (chapitres 1 + 3).
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Pour la suite

TP3 demain. TP4 la semaine d'après. CC3 à la fin.

---

## 📅 Ce qui vous attend

<div style="display: flex; gap: 0.8rem; margin-top: 0.5rem;">

<div style="background: #e8a838; color: white; padding: 1rem; border-radius: 10px; flex: 1;">
<div style="font-size: 1.4rem; font-weight: bold;">🥋 TP3</div>
<div style="font-size: 0.95rem; margin-top: 0.4rem;">
5 kata en <b>pair programming</b> :<br/>
années bissextiles, tennis, employés, pagination, yahtzee.<br/><br/>
Driver / navigator, ping-pong TDD.
</div>
</div>

<div style="background: #e74c3c; color: white; padding: 1rem; border-radius: 10px; flex: 1;">
<div style="font-size: 1.4rem; font-weight: bold;">🧹 TP4</div>
<div style="font-size: 0.95rem; margin-top: 0.4rem;">
4 exercices de refactoring :<br/>
Facture (Long Method), Animal (Polymorphisme), Notification (Parameter Object), <b>Gilded Rose</b>.<br/><br/>
Tests de caractérisation fournis.
</div>
</div>

<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; flex: 1;">
<div style="font-size: 1.4rem; font-weight: bold;">💻 CC3</div>
<div style="font-size: 0.95rem; margin-top: 0.4rem;">
Mini-kata TDD <b>sur feuille</b>, 2 h.<br/><br/>
Pas d'IDE, pas de compilateur - juste la démarche TDD appliquée à un problème simple.
</div>
</div>

</div>

---

<!-- _class: lead -->

# Des questions ?

**Sébastien Nedjar**
IUT d'Aix-Marseille - Département Informatique

<div style="margin-top: 2rem; font-size: 1.1rem;">

🌐 [github.com/IUTInfoAix-R203/tp](https://github.com/IUTInfoAix-R203/tp)

📧 sebastien.nedjar@univ-amu.fr

</div>

<div style="margin-top: 2rem; background: #2c3e50; color: white; padding: 1rem 2rem; border-radius: 12px; font-size: 1.1rem;">
<b>🎯 Dès maintenant</b> : ouvrez votre IDE, tentez le <em>Rename</em> (F6 / F2), l'<em>Extract Method</em> (Ctrl+Alt+M). Le plus tôt vos doigts connaissent ces gestes, le mieux vous vivrez les TP3 et TP4.
</div>
