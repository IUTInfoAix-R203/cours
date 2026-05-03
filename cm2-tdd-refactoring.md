---
marp: true
theme: default
paginate: true
---

<!-- _class: lead -->
<!-- _paginate: false -->

# TDD, refactoring et code propre

**R2.03 - Qualité de développement**

IUT d'Aix-Marseille - BUT Informatique, première année

<div style="display: flex; justify-content: center; gap: 9rem; margin-top: 6rem; color: #555;">
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">✅</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">TDD</div></div>
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">🥋</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">Kata</div></div>
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">🧹</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">Refactoring</div></div>
</div>

---

## Au programme de ce CM

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois axes pour transformer les bases du CM1 en <b>réflexes</b> : approfondir le TDD, pratiquer ensemble, sécuriser du legacy.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin: 3rem 0; font-size: 1.5rem;">
<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">✅</div>
<b>TDD approfondi</b><br/>
<span style="font-size: 1.3rem; opacity: 0.9;">F.I.R.S.T., stratégies de Beck, ApprovalTests</span>
</div>
<div style="background: #e8a838; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🥋</div>
<b>Kata et pair programming</b><br/>
<span style="font-size: 1.3rem; opacity: 0.9;">Driver, navigator, ping-pong</span>
</div>
<div style="background: #e74c3c; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🧹</div>
<b>Code smells et refactoring</b><br/>
<span style="font-size: 1.3rem; opacity: 0.9;">Fowler, characterization tests</span>
</div>
</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; text-align: center; font-size: 1.5rem;">
Ce CM prépare le <b>TP3 - Kata</b> et le <b>TP4 - Refactoring</b>.
</div>

---

## Où on en est

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Aujourd'hui, on <b>approfondit</b> le socle du CM1 et on prépare les <b>TP3</b>, <b>TP4</b> et la logique du <b>CC3</b>.
</p>

<!-- Ligne 1 : les 2 CMs -->
<div style="display: flex; gap: 0.5rem; margin-top: 1.5rem;">
  <div style="background: #4a90d9; color: white; padding: 1rem 1.2rem; border-radius: 10px 10px 0 0; flex: 1; text-align: center; opacity: 0.6;">
    <b>✓ CM1</b><br/><span style="font-size: 1.05rem;">Artisanat + Git + TDD intro</span>
  </div>
  <div style="background: #e8a838; color: white; padding: 1rem 1.2rem; border-radius: 10px 10px 0 0; flex: 1; text-align: center; border: 3px solid #c87d00; box-shadow: 0 4px 12px rgba(232,168,56,0.4);">
    <b>📍 CM2 (vous êtes ici)</b><br/><span style="font-size: 1.05rem;">TDD + Refactoring</span>
  </div>
</div>

<!-- Ligne 2 : les 4 TPs (légèrement espacés des CMs ci-dessus) -->
<div style="display: flex; gap: 0.5rem; margin-top: 0.4rem;">
  <div style="background: #d0e2f3; color: #2c5f8a; padding: 0.7rem; border-radius: 0 0 10px 10px; flex: 1; text-align: center; font-weight: bold; font-size: 1.05rem;">TP1</div>
  <div style="background: #d0e2f3; color: #2c5f8a; padding: 0.7rem; border-radius: 0 0 10px 10px; flex: 1; text-align: center; font-weight: bold; font-size: 1.05rem;">TP2</div>
  <div style="background: #fae5c0; color: #8a6a1f; padding: 0.7rem; border-radius: 0 0 10px 10px; flex: 1; text-align: center; font-weight: bold; font-size: 1.05rem;">TP3</div>
  <div style="background: #fae5c0; color: #8a6a1f; padding: 0.7rem; border-radius: 0 0 10px 10px; flex: 1; text-align: center; font-weight: bold; font-size: 1.05rem;">TP4</div>
</div>

<!-- Flèches convergentes TP2 + TP3 + TP4 -> CC3 -->
<div style="display: flex; gap: 0.5rem; text-align: center; font-size: 1.5rem; color: #999; margin: 0.2rem 0;">
  <div style="flex: 1;">&nbsp;</div>
  <div style="flex: 1;">↓</div>
  <div style="flex: 1;">↓</div>
  <div style="flex: 1;">↓</div>
</div>

<!-- Ligne 3 : CC3 (pleine largeur, violet plein, ligne unique) -->
<div style="background: #8e44ad; color: white; padding: 0.9rem 1rem; border-radius: 10px; text-align: center; font-weight: bold; font-size: 1.4rem;">
  🎯 CC3 — kata sur feuille (2 h) : <span style="font-weight: normal; opacity: 0.9;"> évalue les acquis de TP2 + TP3 + TP4</span>
</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem;">
<b>En CM1 on a vu <em>pourquoi</em> l'artisan prend soin de son code.</b> Aujourd'hui, on voit <b>comment il s'y prend au quotidien</b> : tester avant, refactorer souvent, nommer juste. Les gestes qui transforment l'intention en habitude.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:50%](assets/tdd-approfondi-tools.jpg)

# Partie 1 - TDD approfondi

Comment tirer le meilleur du cycle du TDD au quotidien ?

---

## 🔁 Rappel : le cycle RED-GREEN-REFACTOR

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Pour rappel : <b>3 étapes</b>, dans cet ordre, pour chaque petit comportement à ajouter.
</p>

<div style="display: grid; grid-template-columns: 1fr 0.2fr 1fr 0.2fr 1fr; gap: 0.6rem; margin-top: 1.5rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 12px; overflow: hidden; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="background: #e74c3c; color: #fff; padding: 0.6rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">1. 🔴 RED</div>
<div style="background: #fdecea; padding: 1rem; flex: 1; font-size: 1.25rem;">
J'écris <b>un seul</b> test. Il doit échouer pour la <b>bonne raison</b> : un comportement qui manque, pas une coquille de syntaxe.
</div>
</div>

<div style="display: flex; align-items: center; justify-content: center; font-size: 3rem; color: #999;">▶</div>

<div style="display: flex; flex-direction: column; border-radius: 12px; overflow: hidden; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="background: #27ae60; color: #fff; padding: 0.6rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">2. 🟢 GREEN</div>
<div style="background: #e8f6ec; padding: 1rem; flex: 1; font-size: 1.25rem;">
Je code le <b>minimum</b> pour passer. Je n'ai <b>pas</b> le droit d'anticiper sur les tests à venir.
</div>
</div>

<div style="display: flex; align-items: center; justify-content: center; font-size: 3rem; color: #999;">▶</div>

<div style="display: flex; flex-direction: column; border-radius: 12px; overflow: hidden; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="background: #4a90d9; color: #fff; padding: 0.6rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">3. 🧹 REFACTOR</div>
<div style="background: #eaf2fb; padding: 1rem; flex: 1; font-size: 1.25rem;">
Je nettoie (noms, duplication, lisibilité). La suite de tests reste <b>verte</b> en permanence.
</div>
</div>

</div>

<div style="display: flex; align-items: center; justify-content: center; gap: 0.8rem; margin-top: 1.2rem; font-size: 1.4rem; color: #555;">
<span style="font-size: 2rem;">🔁</span><span>... puis on <b>reprend en 1.</b> avec le test suivant.</span>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
La force du cycle vient de sa <b>discipline</b> : 3 étapes, dans l'ordre, à chaque tour.
</div>

---

## 💰 Pourquoi ce cycle, économiquement

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le CM1 a montré que les bugs coûtent jusqu'à <b>100×</b> plus cher quand ils sont détectés tard. Le TDD attaque la courbe <b>au moment le moins cher</b>.
</p>

<div style="display: grid; gap: 1.2rem; margin: 3.5rem 0;">

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 200px; font-size: 1.3rem; color: #555;">Développement</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.4rem; overflow: hidden; position: relative;">
<div style="background: #27ae60; width: 1%; height: 100%;"></div>
<div style="position: absolute; left: 3%; top: 50%; transform: translateY(-50%); background: #27ae60; color: white; padding: 0.2rem 0.7rem; border-radius: 999px; font-size: 1rem; font-weight: bold; box-shadow: 0 2px 6px rgba(0,0,0,0.2);">👈 le TDD agit ici</div>
</div>
<div style="width: 80px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #27ae60;">1×</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 200px; font-size: 1.3rem; color: #555;">Tests</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.4rem; overflow: hidden;">
<div style="background: #e8a838; width: 6%; height: 100%;"></div>
</div>
<div style="width: 80px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #e8a838;">6×</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 200px; font-size: 1.3rem; color: #555;">Pré-production</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.4rem; overflow: hidden;">
<div style="background: #e67e22; width: 15%; height: 100%;"></div>
</div>
<div style="width: 80px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #e67e22;">15×</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 200px; font-size: 1.3rem; color: #555;"><b>Chez le client</b></div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.4rem; overflow: hidden;">
<div style="background: #e74c3c; width: 100%; height: 100%;"></div>
</div>
<div style="width: 80px; text-align: right; font-weight: bold; font-size: 1.5rem; color: #e74c3c;">100×</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le TDD ne supprime pas le travail ; il le <b>déplace là où il coûte le moins cher</b>.
</div>

---

## 🚦 Les 3 lois du TDD (Uncle Bob)

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois règles formelles, énoncées par <b>Robert C. Martin</b> (Uncle Bob), pour <b>forcer la discipline du baby-step</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1.2rem; margin: 3.2rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🙅 Loi 1 — Interdit</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
Tu n'écriras <b>pas de code de production</b> tant qu'un test qui <b>échoue</b> ne l'exige.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">⏸️ Loi 2 — Limite</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
Tu n'écriras <b>pas plus de test</b> qu'il n'en faut pour échouer. Une erreur de compilation compte comme un échec.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">✋ Loi 3 — Juste assez</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
Tu n'écriras <b>pas plus de code de production</b> qu'il n'en faut pour faire passer le test qui échoue.
</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
À chaque cycle, vous alternez entre production et test toutes les <b>30 secondes à 2 minutes</b>.
</div>

---

<!-- _transition: fade -->

## 🎯 Fake it / Triangulation / Obvious : laquelle choisir ?

<style scoped>
.hidden { visibility: hidden; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
On les a vues au CM1. Voici la <b>décision rapide</b> au moment d'écrire le code de production.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎭 Fake it d'abord, toujours</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>Même si la solution semble évidente. Fake it vérifie que le <b>test</b> est juste, <b>avant</b> de se soucier du code.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em>Le test passe avec une constante en dur ? OK, il est bien formulé.</em></div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📐 Triangulation quand...</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>... le 2<sup>e</sup> ou 3<sup>e</sup> test vous <b>force</b> à généraliser. Le comportement commun émerge <em>tout seul</em>.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em>FizzBuzz : après 3 tests (1, 3, 5), la logique if/else se dessine.</em></div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">💡 Obvious seulement si...</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>... la solution <b>tient en une ligne</b> et vous ne pouvez <em>pas</em> vous tromper. <b>Le moindre doute</b> = pas obvious.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em><code>return a + b;</code> dans <code>addition(int, int)</code>.</em></div>
</div>
</div>

</div>

<div class="hidden" style="margin-top: 1rem; background: #fdecea; border-left: 5px solid #e74c3c; padding: 0.7rem 1rem; border-radius: 6px; font-size: 1.1rem;">
⚠️ <b>Anti-pattern fréquent</b> : « je sais coder ça, je passe direct en obvious ». Le test n'est jamais rouge, vous ne savez pas s'il vérifie vraiment quelque chose. <b>Fake it d'abord</b>, même 10 secondes, pour voir le test passer du rouge au vert.
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Règle simple : <b>Fake it</b> par défaut, <b>Triangulation</b> quand un seul cas ne suffit plus, <b>Obvious</b> seulement quand l'évidence est totale.
</div>

---

## 🎯 Fake it / Triangulation / Obvious : laquelle choisir ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
On les a vues au CM1. Voici la <b>décision rapide</b> au moment d'écrire le code de production.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎭 Fake it d'abord, toujours</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>Même si la solution semble évidente. Fake it vérifie que le <b>test</b> est juste, <b>avant</b> de se soucier du code.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em>Le test passe avec une constante en dur ? OK, il est bien formulé.</em></div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📐 Triangulation quand...</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>... le 2<sup>e</sup> ou 3<sup>e</sup> test vous <b>force</b> à généraliser. Le comportement commun émerge <em>tout seul</em>.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em>FizzBuzz : après 3 tests (1, 3, 5), la logique if/else se dessine.</em></div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">💡 Obvious seulement si...</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>... la solution <b>tient en une ligne</b> et vous ne pouvez <em>pas</em> vous tromper. <b>Le moindre doute</b> = pas obvious.</div>
<div style="font-size: 1rem; opacity: 0.85; margin-top: auto;">💡 <em><code>return a + b;</code> dans <code>addition(int, int)</code>.</em></div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #fdecea; border-left: 5px solid #e74c3c; padding: 0.7rem 1rem; border-radius: 6px; font-size: 1.1rem;">
⚠️ <b>Anti-pattern fréquent</b> : « je sais coder ça, je passe direct en obvious ». Le test n'est jamais rouge, vous ne savez pas s'il vérifie vraiment quelque chose. <b>Fake it d'abord</b>, même 10 secondes, pour voir le test passer du rouge au vert.
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Règle simple : <b>Fake it</b> par défaut, <b>Triangulation</b> quand un seul cas ne suffit plus, <b>Obvious</b> seulement quand l'évidence est totale.
</div>

---

## ✅ Qu'est-ce qu'un bon test ? Le principe F.I.R.S.T.

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Robert C. Martin (<em>Clean Code</em>, 2008) a énoncé <b>5 critères</b> d'un bon test, l'acronyme <b>FIRST</b>.
</p>

<div style="display: grid; grid-template-columns: repeat(5, 1fr); gap: 0.8rem; margin: 3rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.7rem 0.5rem; text-align: center; line-height: 1;">
<span style="font-size: 2.4rem; font-weight: bold;">F</span><span style="font-size: 1rem;">ast</span>
</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.8rem; flex: 1; font-size: 1.3rem;">
<b>Rapide</b> (quelques ms). On les lance des dizaines de fois par heure.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.7rem 0.5rem; text-align: center; line-height: 1;">
<span style="font-size: 2.4rem; font-weight: bold;">I</span><span style="font-size: 1rem;">ndependent</span>
</div>
<div style="background: #e8f6ec; padding: 0.7rem 0.8rem; flex: 1; font-size: 1.3rem;">
<b>Indépendants</b> entre eux. Changer l'ordre ne doit rien casser.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.7rem 0.5rem; text-align: center; line-height: 1;">
<span style="font-size: 2.4rem; font-weight: bold;">R</span><span style="font-size: 1rem;">epeatable</span>
</div>
<div style="background: #f9f5e8; padding: 0.7rem 0.8rem; flex: 1; font-size: 1.3rem;">
<b>Reproductible</b>. Pas de dépendance au réseau, à l'heure, à un fichier temporaire.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.7rem 0.5rem; text-align: center; line-height: 1;">
<span style="font-size: 2.4rem; font-weight: bold;">S</span><span style="font-size: 1rem;">elf-validating</span>
</div>
<div style="background: #fdecea; padding: 0.7rem 0.8rem; flex: 1; font-size: 1.3rem;">
<b>Auto-vérifiant</b>. Rouge ou vert, pas de « regardez le log ».
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.7rem 0.5rem; text-align: center; line-height: 1;">
<span style="font-size: 2.4rem; font-weight: bold;">T</span><span style="font-size: 1rem;">imely</span>
</div>
<div style="background: #ede5f7; padding: 0.7rem 0.8rem; flex: 1; font-size: 1.3rem;">
Écrit au <b>bon moment</b> : <b>avant</b> le code, pas après.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #fff8e1; border-left: 4px solid #e8a838; padding: 0.7rem 1rem; border-radius: 6px; font-size: 1.5rem;">
🛠️ F.I.R.S.T., c'est la <b>check-list de l'artisan</b> qui vérifie que son banc de tests reste un banc, pas un gouffre. Un test lent, fragile, dépendant des voisins, c'est un outil émoussé qu'il faut <b>affûter ou jeter</b>.
</div>

---

## 🧪 La structure AAA d'un test

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; padding: 0.9rem 1.1rem !important; }
section pre code { font-size: 0.78rem !important; line-height: 1.5 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois phases pour structurer chaque test : <b>Arrange · Act · Assert</b>. Lisible comme une phrase.
</p>

<div style="display: grid; grid-template-columns: 1fr 1.3fr; gap: 1.5rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; gap: 0.7rem;">

<div style="flex: 1; display: flex; align-items: center; gap: 0.7rem; background: #eaf2fb; border-left: 5px solid #4a90d9; padding: 0.8rem 1rem; border-radius: 8px;">
<div style="font-size: 1.6rem;">🛠️</div>
<div style="font-size: 1.4rem;"><b>Arrange</b> — préparer l'environnement, les données, les dépendances</div>
</div>

<div style="flex: 1; display: flex; align-items: center; gap: 0.7rem; background: #f9f5e8; border-left: 5px solid #e8a838; padding: 0.8rem 1rem; border-radius: 8px;">
<div style="font-size: 1.6rem;">▶️</div>
<div style="font-size: 1.4rem;"><b>Act</b> — déclencher le comportement testé (<b>une seule</b> action)</div>
</div>

<div style="flex: 1; display: flex; align-items: center; gap: 0.7rem; background: #e8f6ec; border-left: 5px solid #27ae60; padding: 0.8rem 1rem; border-radius: 8px;">
<div style="font-size: 1.6rem;">✅</div>
<div style="font-size: 1.4rem;"><b>Assert</b> — vérifier le résultat (idéalement <b>une</b> assertion principale)</div>
</div>

</div>

<div class="aaa-card" style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #2c3e50; color: #fff; padding: 0.4rem 1rem; font-size: 1.1rem; font-weight: bold;">📄 <code style="background: transparent; color: #fff;">CalculatriceTest.java</code></div>

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

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Un test <b>bien structuré</b> (AAA) et <b>bien nommé</b> se lit comme une phrase.
</div>

---

## 📝 Exemple : noms de tests parlants

<style scoped>
section pre { 
  margin: 0 !important; 
  border: none !important; 
  box-shadow: none !important; 
  border-radius: 6px !important; 
  padding: 0.7rem 0.9rem !important;
  font-size: 15px !important;
  line-height: 1.5 !important;
  transform: none !important;
  overflow-x: auto !important;
}
section pre code,
section pre code[class*="language-"] { 
  font-size: 13px !important; 
  line-height: 1.5 !important;
}
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le nom du test est sa <b>première ligne de documentation</b>. Il doit raconter le <b>quoi</b> du test et <b>quel comportement</b> est attendu.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🤦 Pas clair</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.3rem; display: flex; flex-direction: column; gap: 0.6rem;">

```java
@Test void test1()
@Test void testAdd() 
@Test void testCalc() 
@Test void bugFix12345() 
```

<div>On ne sait <b>pas ce qui est testé</b>, ni <b>quel comportement</b> est attendu.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎯 Clair</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.3rem; display: flex; flex-direction: column; gap: 0.6rem;">

```java
@Test void additionne_deux_positifs_retourne_un_positif()
@Test void additionne_zero_et_dix_retourne_dix()
@Test void montant_total_d_un_panier_negatif_leve_exception()
@Test void un_panier_vide_a_un_montant_total_de_zero()
```

<div style="margin-top: auto;">On lit le test comme une <b>spécification</b> du comportement de chaque cas.</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #fff8e1; border-left: 4px solid #e8a838; padding: 0.7rem 1rem; border-radius: 6px; font-size: 1.5rem;">
🥋 <b>Ce qu'on vise au TP3</b> : des tests qui racontent une partie, pas des numéros ou des noms génériques : <code>partie_tombe_a_egalite_apres_deux_points_partout()</code>, <code>le_serveur_gagne_la_partie_apres_quatre_points()</code>, etc.
</div>

---

## 📛 Conventions de nommage

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le <b>snake_case</b> est la norme JUnit pour la lisibilité. Trois <b>patterns</b> structurent le contenu du nom : choisissez-en un et tenez-vous-y.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin: 3.2rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">📝 Descriptif simple</div>
<div style="background: #eaf2fb; padding: 0.9rem 1rem; flex: 1; font-size: 1.4rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>Décrit le comportement <b>sans structure imposée</b>. Le plus naturel à lire.</div>
<div style="font-family: 'Courier New', Consolas, monospace; background: #fff; padding: 0.5rem; border-radius: 4px; font-size: 0.95rem; margin-top: auto;">additionne_deux_positifs_retourne_la_somme()</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">📛 should / when</div>
<div style="background: #f9f5e8; padding: 0.9rem 1rem; flex: 1; font-size: 1.4rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>Pattern <b>should_X_when_Y</b>. Très répandu en Java/Kotlin.</div>
<div style="font-family: 'Courier New', Consolas, monospace; background: #fff; padding: 0.5rem; border-radius: 4px; font-size: 0.95rem; margin-top: auto;">should_return_sum_when_adding_two_positives()</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎬 Given / When / Then</div>
<div style="background: #e8f6ec; padding: 0.9rem 1rem; flex: 1; font-size: 1.4rem; display: flex; flex-direction: column; gap: 0.6rem;">
<div>Pattern BDD : <b>given_X_<br/>when_Y_then_Z</b>. Aligne le test sur le scénario métier.</div>
<div style="font-family: 'Courier New', Consolas, monospace; background: #fff; padding: 0.5rem; border-radius: 4px; font-size: 0.95rem; margin-top: auto;">given_two_positives_when_adding_then_returns_sum()</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Pas de meilleur pattern : la <b>cohérence dans le projet</b> prime sur le style.
</div>

---

## 🥋 Grounding : ces principes sur un vrai kata

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 6px !important; padding: 0.6rem 0.8rem !important; }
section pre, section pre code, section pre code[class*="language-"] { font-size: 13px !important; line-height: 1.45 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le kata <b>Tennis</b> du TP3 illustre tout ce qu'on vient de voir. Voici les 3 premiers tests pris dans <b>leur ordre d'écriture</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🎭 Test 1 — Fake it</div>
<div style="background: #e8f6ec; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem; display: flex; flex-direction: column; gap: 0.5rem;">

```java
@Test
void debut_de_partie_est_0_0() {
  assertThat(new Tennis().score())
    .isEqualTo("0-0");
}

// Impl : return "0-0";
```

<div style="margin-top: auto;">Le test passe avec une constante. On sait que le test est <b>juste</b>.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">📐 Test 2 — Triangulation</div>
<div style="background: #f9f5e8; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem; display: flex; flex-direction: column; gap: 0.5rem;">

```java
@Test
void apres_point_serveur_15_0() {
  Tennis t = new Tennis();
  t.pointPourServeur();
  assertThat(t.score())
    .isEqualTo("15-0");
}
```

<div style="margin-top: auto;">Force à stocker un <b>état</b>. La constante ne suffit plus.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">📐 Test 3 — Triangulation</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem; display: flex; flex-direction: column; gap: 0.5rem;">

```java
@Test
void apres_2_points_serveur_30_0() {
  Tennis t = new Tennis();
  t.pointPourServeur();
  t.pointPourServeur();
  assertThat(t.score())
    .isEqualTo("30-0");
}
```

<div style="margin-top: auto;">Force une vraie <b>table</b> (0, 15, 30, 40). La logique émerge.</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Chaque test est <b>un pas</b>. La conception <b>s'invente au fur et à mesure</b>, pas avant.
</div>

---

## 🎭 La doublure de test : à quoi ça sert ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Au cinéma, le héros a une <b>doublure</b> pour les cascades. En test, on fait pareil avec les dépendances qu'on ne contrôle pas (base de données, réseau, horloge) : on les remplace par une <b>doublure de test</b> (anglais : <em>test double</em>).
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🪨 Stub / Fake</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
<b>Forcer les valeurs retournées</b> par la dépendance. On contrôle la valeur qu'elle nous <em>renvoie</em> pendant le test.<br/><br/>
<span style="opacity: 0.85; font-size: 1.4rem;">Exemple : une horloge qui retourne toujours <code>1<sup>er</sup> janvier 2026</code>.</span>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎯 Mock / Spy</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
<b>Observer l'appel</b>. On vérifie <em>comment</em> la dépendance a été utilisée (méthode, arguments, fréquence).<br/><br/>
<span style="opacity: 0.85; font-size: 1.4rem;">Exemple : vérifier qu'un service mail a bien été appelé une fois avec la bonne adresse.</span>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
<b>Isoler</b> ce qu'on ne contrôle pas, pour <b>tester</b> ce que l'on souhaite maitriser.
</div>

---

## 🪨 Le stub : forcer le retour

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 6px !important; padding: 0.6rem 0.8rem !important; }
section pre, section pre code, section pre code[class*="language-"] { font-size: 0.7rem !important; line-height: 1.45 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Un <b>stub</b> remplace une dépendance par une <b>réponse pré-définie</b>. Vous décidez ce que la dépendance retourne et vos tests deviennent <b>reproductibles</b>.
</p>

<div style="display: grid; grid-template-columns: 1.2fr 1fr; gap: 1.2rem; margin: 3.2rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold;">📄 Exemple : une horloge stub</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1;">

```java
// Production : dépend de l'horloge système
Clock horlogeStub = Clock.fixed(
    Instant.parse("2026-01-01T00:00:00Z"),
    ZoneOffset.UTC);

LocalDate date = LocalDate.now(horlogeStub);
// → toujours 2026-01-01, peu importe le jour réel
```

</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">💡 Quand l'utiliser</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.3rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>Tester un code qui dépend du <b>temps</b>, du <b>hasard</b>, d'un <b>fichier</b></li>
<li>Rendre les tests <b>reproductibles</b> (même résultat à chaque exécution)</li>
<li>Éviter d'appeler une <b>vraie</b> base de données ou un <b>vrai</b> service externe</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Un stub <b>FORCE le retour</b> de la dépendance. On ne vérifie <b>pas</b> comment elle a été appelée.
</div>

---

## 🎯 Le mock : vérifier l'appel

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 6px !important; padding: 0.6rem 0.8rem !important; }
section pre, section pre code, section pre code[class*="language-"] { font-size: 0.7rem !important; line-height: 1.45 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Un <b>mock</b> vérifie <b>comment</b> une dépendance est utilisée : <em>quelle méthode</em>, <em>avec quels arguments</em>, <em>combien de fois</em>.
</p>

<div style="display: grid; grid-template-columns: 1.2fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold;">📄 Exemple : un service mail mock (Mockito)</div>
<div style="background: #f9f5e8; padding: 0.7rem 0.9rem; flex: 1;">

```java
ServiceMail mail = mock(ServiceMail.class);
GestionnaireCommande gc 
    = new GestionnaireCommande(mail);

gc.confirmer(new Commande("alice@iut.fr"));

// On VÉRIFIE l'appel
verify(mail).envoyer(eq("alice@iut.fr"),
    contains("confirmation"));
```

</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">💡 Quand l'utiliser</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>Vérifier qu'une <b>action</b> a bien eu lieu (envoi, log, notification)</li>
<li>Tester une <b>interaction</b> entre deux composants</li>
<li>S'assurer du <b>contrat</b> entre votre code et la dépendance</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Un mock <b>VÉRIFIE l'appel</b>. La valeur de retour est secondaire.
</div>

---

## 🎭 Stub vs Mock : la synthèse

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Quatre aspects pour distinguer les deux doublures, dans un seul coup d'œil.
</p>

<div style="display: grid; grid-template-columns: 1.1fr 1.4fr 1.4fr; gap: 0.5rem; margin-top: 1.2rem; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">

<div style="background: #2c3e50; color: #fff; padding: 0.7rem 1rem; font-weight: bold; font-size: 1.2rem;">Aspect</div>
<div style="background: #4a90d9; color: #fff; padding: 0.7rem 1rem; font-weight: bold; font-size: 1.3rem; text-align: center;">🪨 Stub</div>
<div style="background: #e8a838; color: #fff; padding: 0.7rem 1rem; font-weight: bold; font-size: 1.3rem; text-align: center;">🎯 Mock</div>

<div style="background: #f5f5f5; padding: 0.8rem 1rem; font-weight: bold; font-size: 1.2rem;">But</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; font-size: 1.2rem;">Forcer le <b>retour</b></div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; font-size: 1.2rem;">Vérifier <b>l'appel</b></div>

<div style="background: #f5f5f5; padding: 0.8rem 1rem; font-weight: bold; font-size: 1.2rem;">Question</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; font-size: 1.2rem;"><em>Que renvoie X ?</em></div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; font-size: 1.2rem;"><em>Comment X est appelé ?</em></div>

<div style="background: #f5f5f5; padding: 0.8rem 1rem; font-weight: bold; font-size: 1.2rem;">Assertion porte sur</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; font-size: 1.2rem;">Le <b>résultat</b></div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; font-size: 1.2rem;">L'<b>interaction</b></div>

<div style="background: #f5f5f5; padding: 0.8rem 1rem; font-weight: bold; font-size: 1.2rem;">Exemple typique</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; font-size: 1.15rem;">Horloge fixe, base de données en mémoire</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; font-size: 1.15rem;">Service mail, logger</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Vous voulez <b>vérifier une interaction</b> → c'est un <b>mock</b>. Sinon → c'est un <b>stub</b>.
</div>

---

## 📸 ApprovalTests : quand la sortie est textuelle

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; padding: 0.7rem 0.9rem !important; }
section pre, section pre code, section pre code[class*="language-"] { font-size: 13px !important; line-height: 1.45 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Pour du code qui produit une <b>sortie complexe</b> (grille, JSON, rapport), écrire l'attendu à la main est pénible. <b>ApprovalTests</b> automatise le rituel.
</p>

<div style="display: grid; grid-template-columns: 1.2fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #2c3e50; color: #fff; padding: 0.4rem 1rem; font-size: 1.1rem; font-weight: bold;">📄 <code style="background: transparent; color: #fff;">GrilleDemineurTest.java</code></div>

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

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #17a2b8; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🔁 Le rituel d'approbation</div>
<div style="background: #e6f5f7; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.5rem;">
<ol style="margin: 0; padding-left: 1.4rem;">
<li>Je lance le test</li>
<li>La sortie va dans <code>...received.txt</code></li>
<li>Je <b>vérifie visuellement</b></li>
<li>Je renomme <code>received</code> → <code>approved</code></li>
<li>Le test compare ensuite <code>received</code> à <code>approved</code></li>
</ol>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Utilisé au <b>TP2 exercice 5</b> (Démineur) — gain énorme sur les grandes grilles ou les sorties textuelles riches.
</div>

---

## 💡 Règles pour ne pas se planter en TDD

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois pièges à éviter, trois réflexes à cultiver. Les premiers tuent le filet de sécurité, les seconds le renforcent.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🤦 Pièges à éviter</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>Écrire plusieurs tests d'affilée</b> sans coder entre. Un test écrit, un test codé.</li>
<li><b>Ajouter du code sans test qui l'exige.</b> Une branche <code>if</code> en plus = un test à écrire avant.</li>
<li><b>Sauter le REFACTOR.</b> Le cycle est à 3 étapes, pas à 2. Sinon la dette explose.</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎯 Réflexes à cultiver</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>Vérifier que le test échoue</b> avant de coder. Sinon = faux positif (un test qui passait déjà).</li>
<li><b>Commit à chaque GREEN ou REFACTOR.</b> Chaque état vert = un point de sauvegarde.</li>
<li><b>Un seul test rouge à la fois.</b> Focaliser l'attention, pas 5 rouges en parallèle.</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le TDD ne pardonne pas les <b>raccourcis</b> : chaque écart efface une garantie acquise.
</div>

---

## 📊 Pyramide des tests

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Pour rappel (CM1) : <b>3 niveaux</b> de tests, en pyramide. Plus on monte, moins on en a — et plus chaque test coûte cher.
</p>

<div style="display: grid; grid-template-columns: 1.4fr 1fr; gap: 1.5rem; margin-top: 1.5rem; align-items: center;">

<div style="display: flex; flex-direction: column; align-items: center;">

<div style="background: #e74c3c; color: #fff; padding: 1.2rem 0.8rem; width: 45%; text-align: center; border-radius: 6px 6px 0 0; font-size: 1.2rem;">E2E <span style="opacity: 0.85;">(peu)</span></div>
<div style="background: #e8a838; color: #fff; padding: 1.5rem 0.8rem; width: 65%; text-align: center; font-size: 1.3rem; border-radius: 6px 6px 0 0;">Intégration <span style="opacity: 0.85;">(moyen)</span></div>
<div style="background: #27ae60; color: #fff; padding: 1.8rem 0.8rem; width: 90%; text-align: center; font-size: 1.4rem; font-weight: bold; border-radius: 6px 6px 0 0; box-shadow: 0 0 0 3px rgba(39, 174, 96, 0.25);">Tests unitaires <span style="opacity: 0.9;">(la base, beaucoup)</span></div>

</div>

<div style="display: flex; flex-direction: column; gap: 0.8rem;">

<div style="background: #fdecea; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e74c3c; font-size: 1.15rem;">
<b>E2E</b> — toute l'application, du clic à la base. Lents, fragiles, coûteux.
</div>

<div style="background: #f9f5e8; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #e8a838; font-size: 1.15rem;">
<b>Intégration</b> — plusieurs briques ensemble (service + DB, par ex).
</div>

<div style="background: #e8f6ec; padding: 0.8rem 1rem; border-radius: 8px; border-left: 4px solid #27ae60; font-size: 1.15rem;">
<b>Unitaires</b> — une méthode, une classe, isolés. Rapides, ciblés, relancés en permanence.
</div>

</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
👉 Dans ce module, on travaille la <b>base</b> de la pyramide. C'est là que le TDD vit vraiment.
</div>

---

## 🧬 Aparté : couverture != qualité des tests

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 6px !important; padding: 0.6rem 0.8rem !important; }
section pre, section pre code, section pre code[class*="language-"] { font-size: 13px !important; line-height: 1.45 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Deux mesures qu'on confond souvent. La <b>couverture</b> répond à <em>quelles lignes ont été exécutées ?</em> La <b>qualité</b> répond à <em>les tests détectent-ils de vrais bugs ?</em>
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin: 3rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">📊 Couverture</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
Quelles <b>lignes / branches</b> ont été exécutées par la suite de tests.
<div style="opacity: 0.85; font-size: 1.3rem;">Mesurée par <b>JaCoCo</b> (plugin Maven), inline IntelliJ, etc.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎯 Qualité</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
Les tests <b>détectent-ils vraiment un bug</b> si le code est cassé ?
<div style="opacity: 0.85; font-size: 1.3rem;">Mesurée par <b>mutation testing</b> (CM2 bonus) ou par <b>lecture critique</b> (pendant la revue de code).</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
La couverture mesure <b>l'exécution</b>, pas la <b>validation</b>. Un beau 99% ne prouve rien à lui seul.
</div>

---

## 🌄 Où s'arrête le TDD ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Connaître les <b>limites</b> de l'outil, c'est déjà bien le maîtriser. Le TDD résout certains problèmes très bien mais il en laisse d'autres entiers.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎯 Ce que le TDD fait bien</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.3rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>Cadrer une <b>intention</b> avant de coder</li>
<li>Donner un <b>filet</b> pour refactorer sereinement</li>
<li>Produire une <b>documentation vivante</b> du comportement</li>
<li>Forcer un <b>découplage</b> (sinon le test devient injouable)</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🚧 Ce que le TDD ne fait PAS</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.3rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>Garantir</b> que le produit est utile pour le client</li>
<li>Remplacer la <b>revue de code</b> et le <b>pair programming</b></li>
<li>Couvrir les bugs d'<b>intégration</b>, de <b>perf</b>, d'<b>ergonomie</b></li>
<li>Dispenser de <b>penser</b> : un test tautologique passera toujours</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem;">
L'artisan connaît ses outils et leurs <b>limites</b>. Le TDD est un outil puissant pour <b>le code qui porte une logique claire</b> ; il ne remplace ni les tests d'intégration, ni la relecture humaine, ni la validation par le client qui dira si l'ouvrage correspond bien à ses exigences.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:50%](assets/kata-pair-programming.jpg)

# Partie 2 - Le kata et le pair programming

Comment on devient meilleur ? En répétant des gestes simples.

---

## 🥋 Le coding dojo : pratiquer pour apprendre

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Comment apprend-on à mieux coder ? Pas en regardant des tutos, ni en lisant des livres seul. Comme dans les arts martiaux : par la <b>pratique régulière, répétée et en groupe</b>.
</p>

<div style="display: grid; grid-template-columns: 1.2fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="background: #fff8e1; border-left: 5px solid #e8a838; padding: 0.9rem 1.1rem; border-radius: 8px; display: flex; flex-direction: column; gap: 0.5rem;">
<div style="font-size: 1.5rem; line-height: 1.5;">
💬 <em>« Si je veux apprendre le judo, je vais m'inscrire au dojo du coin et y passer une heure par semaine pendant deux ans, au bout de quoi j'aurai peut-être envie de pratiquer plus assidûment. Si je veux apprendre la programmation objet, mon employeur va me trouver une formation de trois jours à Java dans le catalogue. Cherchez l'erreur. »</em>
</div>
<div style="margin-top: auto; font-size: 1.1rem; opacity: 0.8; text-align: right;">
<b>Laurent Bossavit</b>, <em>The Leprechauns of Software Engineering</em>, 2013
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🥋 Le coding dojo</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>Origine</b> : transposition du dojo des arts martiaux à la programmation. Premiers coding dojos vers 2005 (Paris, Londres).</li>
<li><b>Forme typique</b> : 1 à 2 h, en groupe, sur un kata, avec un facilitateur.</li>
<li><b>Fréquence</b> : régulière (hebdo / mensuelle). La régularité prime sur la durée.</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le métier s'apprend par la <b>pratique régulière</b>, pas par une formation one-shot.
</div>

---

## 🥋 Qu'est-ce qu'un kata ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Dans le coding dojo, l'unité de pratique s'appelle un <b>kata</b>. Le mot vient directement des arts martiaux.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🥋 Arts martiaux</div>
<div style="background: #f9f5e8; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.25rem;">
Une <b>séquence de mouvements</b> qu'on répète jusqu'à ce que le corps l'exécute sans y penser.
<br/><br/>
On ne cherche pas à <em>vaincre un adversaire</em> : on travaille la <b>posture</b>, le <b>souffle</b>, la <b>précision</b>.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">💻 Coding kata</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.25rem;">
Un <b>petit exercice</b> qu'on refait <b>plusieurs fois</b> pour :
<ul style="margin: 0.5rem 0 0; padding-left: 1.2rem;">
<li><b>automatiser</b> des gestes (raccourcis IDE, TDD, refactoring)</li>
<li><b>essayer</b> des approches différentes</li>
<li><b>comparer</b> avec d'autres développeurs</li>
</ul>
<div style="font-size: 1rem; opacity: 0.8; margin-top: 0.6rem;">Popularisé par <b>Dave Thomas</b> (<em>The Pragmatic Programmer</em>, 2003).</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le but n'est pas de <b>résoudre le problème</b> (vous le connaissez), c'est d'améliorer <b>votre façon</b> de le résoudre. Comme un pianiste qui joue ses gammes pour <b>garder la main</b>.
</div>

---

## 🥋 Quelques kata célèbres

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
La communauté des coding dojos a accumulé un <b>répertoire</b> de kata classiques. En voici six qu'on retrouve partout — chacun éclaire un aspect différent du métier.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.8rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🔢 FizzBuzz</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Le plus <b>iconique</b> : intro TDD, branchements simples. La porte d'entrée.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🗓️ Années bissextiles</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Petit kata idéal pour travailler les <b>règles booléennes</b> imbriquées.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🎾 Tennis scoring</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Afficher le score d'un jeu de tennis. Idéal pour les <b>state machines</b>.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🎳 Bowling</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Kata classique d'<b>Uncle Bob</b>. Marquer une partie de bowling avec strikes et spares.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🎲 Yahtzee</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Scorer les combinaisons d'un jet de 5 dés. Bon terrain pour la <b>stratégie</b>.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🏪 Gilded Rose</div>
<div style="background: #eaf2fb; padding: 0.7rem 0.9rem; flex: 1; font-size: 1.1rem;">
Par <b>Emily Bache</b>. Kata de <b>refactoring</b> sur du legacy volontairement horrible.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Au <b>TP3</b>, vous en ferez <b>cinq</b> par vous-même : Années bissextiles, Tennis, Gestion employés, Pagination, Yahtzee.
</div>

---

## 🤔 Pourquoi refaire un kata qu'on sait résoudre ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le débutant croit que refaire = perdre du temps. L'expert sait que <b>chaque passage</b> apporte autre chose. Voici ce qui change au fil des répétitions.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 0.8rem; margin: 3.2rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">1<sup>re</sup> fois — la lutte</div>
<div style="background: #fdecea; padding: 0.8rem 1rem; flex: 1; font-size: 1.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.5rem;">
<div style="font-size: 4rem; line-height: 1;">😰</div>
<div>Je galère, je découvre les règles. Je code <em>quelque chose qui marche</em>.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">2<sup>e</sup> fois : l'aisance</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.5rem;">
<div style="font-size: 4rem; line-height: 1;">😅</div>
<div>Je vais plus vite, je vois les <b>pièges</b>. Je soigne le <b>nommage</b>.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">3<sup>e</sup> fois : l'aventure</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.5rem;">
<div style="font-size: 4rem; line-height: 1;">🤔</div>
<div>Je teste une <b>autre approche</b> : que du Fake it, ou que de la Triangulation.</div>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">10<sup>e</sup> fois : la maîtrise</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.5rem;">
<div style="font-size: 4rem; line-height: 1;">😎</div>
<div>Je suis <b>fluide</b>. Je peux me concentrer sur le <b>style</b>, pas le problème.</div>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Un sportif ne s'entraîne pas le jour du match. <b>Un développeur non plus.</b>
</div>

---

## 🎲 Varier les contraintes pour progresser

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Refaire un kata avec une <b>règle du jeu différente</b> force à explorer d'autres chemins.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.8rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🙅 Pas de <code style="background: rgba(255,255,255,0.2); padding: 0 0.3rem; border-radius: 3px;">if</code> / <code style="background: rgba(255,255,255,0.2); padding: 0 0.3rem; border-radius: 3px;">else</code></div>
<div style="background: #fdecea; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Force le <b>polymorphisme</b> et les <i>lookup tables</i>. Apprend à remplacer les branches par des objets.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🔁 Pas de boucles</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Force la <b>récursion</b> ou les <code style="background: rgba(0,0,0,0.05); padding: 0 0.3rem; border-radius: 3px;">Stream</code>. Apprend la programmation fonctionnelle.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📦 Pas de primitives</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Force à créer de vrais <b>objets métier</b>. Apprend <i>Tell, Don't Ask</i>.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">✂️ 4 lignes max</div>
<div style="background: #f3eaf7; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Méthodes courtes obligatoires. Apprend <b>Extract Method</b> à fond et la décomposition fine.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🤐 Silence</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
En pair, communiquer <b>uniquement</b> par le code et les tests. Apprend à l'expressivité.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #16a085; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🏓 Mute ping-pong</div>
<div style="background: #e6f5f1; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
A écrit le test, B le fait passer, <b>sans parler</b>. Apprend la rigueur TDD pure.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Une <b>contrainte arbitraire</b> transforme un kata connu en <b>nouveau terrain d'exploration</b>.
</div>

---

## 👥 Le pair programming

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Deux personnes, un clavier. Pratique née de l'<b>eXtreme Programming</b> (Kent Beck, 1996) : <b>chaque ligne</b> de code est écrite à deux.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.5rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎮 Driver</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.4rem;">
Celui qui tape. Se concentre sur le <b>comment</b> : syntaxe, IDE, faire passer le test courant.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🧭 Navigator</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.4rem;">
Celui qui pense. Se concentre sur le <b>quoi</b> : design, cas limites, lisibilité, prochaine étape.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">✅ Bénéfices</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Moins de bugs, revue de code en continu, montée en compétence croisée, <i>bus factor</i> réduit, effet antisomnolent 😴.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">⚠️ Pièges</div>
<div style="background: #fdecea; padding: 0.8rem 1rem; flex: 1; font-size: 1.3rem;">
Ce n'est <b>pas</b> "un qui code, un qui regarde son téléphone". Fatigant : <b>pauses</b> toutes les heures et rotation toutes les <b>7 à 10 min</b>.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le pair, ce n'est pas un duo regardeur / codeur. C'est <b>deux esprits qui pensent ensemble</b> au même problème.
</div>

---

## 🏓 Variante du pair programming : le ping-pong

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Variante <b>ludique</b> du pair programming : on combine pair et <b>cycle TDD strict</b>. Chacun à son tour <b>défie</b> l'autre avec un test ; l'autre doit le faire <b>passer</b>. Puis on inverse.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin: 3.8rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: white; padding: 0.5rem; text-align: center; font-size: 1.5rem; font-weight: bold;">🏓 Manche 1 : 🅰️ sert</div>
<div style="background: #f8f9fa; padding: 0.8rem; flex: 1;">

<div style="background: #fdecea; padding: 0.7rem 1rem; border-radius: 8px; font-size: 1.3rem; border-left: 5px solid #e74c3c;">
<b>🅰️ </b> écrit un <b>test</b> qui échoue 🔴
</div>

<div style="text-align: center; font-size: 1.8rem; color: #999; margin: 0.2rem 0;">⬇</div>

<div style="background: #e8f6ec; padding: 0.7rem 1rem; border-radius: 8px; font-size: 1.3rem; border-left: 5px solid #27ae60;">
<b>🅱️ </b>  fait <b>passer</b> le test 🟢
</div>

</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: white; padding: 0.5rem; text-align: center; font-size: 1.5rem; font-weight: bold;">🏓 Manche 2 : 🅱️ sert</div>
<div style="background: #f8f9fa; padding: 0.8rem; flex: 1;">

<div style="background: #fdecea; padding: 0.7rem 1rem; border-radius: 8px; font-size: 1.3rem; border-left: 5px solid #e74c3c;">
<b>🅱️ </b> écrit un <b>nouveau test</b> qui échoue 🔴
</div>

<div style="text-align: center; font-size: 1.8rem; color: #999; margin: 0.2rem 0;">⬇</div>

<div style="background: #e8f6ec; padding: 0.7rem 1rem; border-radius: 8px; font-size: 1.3rem; border-left: 5px solid #27ae60;">
<b>🅰️ </b> fait <b>passer</b> le test 🟢
</div>

</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
À chaque manche, <b>les rôles s'inversent</b> : celui qui posait la question doit maintenant y répondre. Entre les manches : <b>refactor à deux</b>.
</div>

---

## 🏓 Pourquoi faire du ping-pong ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le jeu n'est pas gratuit : cette alternance forcée produit <b>trois bénéfices</b> impossibles à obtenir en solo.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎨 Design partagé</div>
<div style="background: #f9f5e8; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
Chacun <b>devine l'intention</b> de l'autre. Le design émerge à <b>deux têtes</b>, pas une seule.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🛡️ Discipline imposée</div>
<div style="background: #f3eaf7; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
Impossible d'écrire du code <i>en douce</i> sans test : le coéquipier <b>veille</b> au cycle.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #16a085; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🔍 Tests lisibles</div>
<div style="background: #e6f5f1; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
Un test mal écrit se voit <b>tout de suite</b> : l'autre ne sait pas quoi coder.
</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
On ne peut pas tricher : le test et le code sont écrits par <b>deux personnes différentes</b>.
</div>

---

## 👨‍👩‍👧 Le mob programming

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Quand le pair programming s'étend à toute l'équipe : un seul écran, <b>tout le monde sur le même problème</b>, en même temps. Inventé par <b>Woody Zuill</b> chez Hunter Industries (~2014).
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">⚙️ Le principe</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>1 driver</b> aux mains du clavier</li>
<li><b>N navigators</b> qui dirigent à voix haute</li>
<li><b>Rotation</b> du driver toutes les 5 à 10 min</li>
<li>Tout le monde dans la <b>même pièce</b> (ou même Zoom)</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎯 À quoi ça sert</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>Problèmes <b>complexes</b> à découper en équipe</li>
<li>Démarrage d'un <b>nouveau projet</b> ou d'un module critique</li>
<li><b>Onboarding</b> rapide d'un nouvel arrivant</li>
<li>Décisions d'<b>architecture</b> partagées par tous</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
À 2 = <b>pair</b>, à 3+ = <b>mob</b>. Plus on est, plus la décision se construit en commun, au prix du débit individuel.
</div>

---

## 🏢 La pratique en entreprise

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Ces pratiques (kata, pair, mob) ne sont pas réservées à l'école. Elles sont <b>utilisées au quotidien</b> dans les équipes qui prennent au sérieux la qualité du code.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🌍 Où on les trouve</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>Équipes de <b>craftsmanship</b> : Pivotal Labs, ThoughtWorks, ekino, Octo, Zenika...</li>
<li>Projets <b>open source</b> de référence (Linux kernel, Mozilla)</li>
<li>Entreprises avec culture <b>XP / agilité forte</b></li>
<li>Hackathons et conférences (Devoxx, AgileFrance, BDX I/O...)</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🎯 Pourquoi c'est viable</div>
<div style="background: #eaf2fb; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.2rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li><b>Moins de bugs</b> : la revue est intégrée à l'écriture</li>
<li><b>Montée en compétence cross-team</b> : tout le monde apprend de tout le monde</li>
<li><b>Onboarding</b> beaucoup plus rapide</li>
<li>Réduction du <b>bus factor</b> (personne n'est seul à connaître un module)</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Apprendre par la pratique régulière, en groupe, ce n'est pas un luxe d'école mais de la <b>formation continue</b>. C'est comme ça que <b>les meilleures équipes</b> restent <b>les meilleures</b>.
</div>

---

## 🎯 Démo en ouverture du TP3

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Au début du TP3, on fera <b>20 minutes de kata live</b> en <b>mob programming</b> : tout le groupe sur le même problème, l'enseignant au clavier. Objectif : voir <b>à quoi ressemble</b> une séance TDD avant de passer en binôme sur les exercices.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🥋 Le kata retenu</div>
<div style="background: #eaf2fb; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
<b><i>Tennis scoring</i></b>, un classique du dojo :
<ul style="margin: 0.4rem 0 0 0; padding-left: 1.2rem;">
<li><b>États</b> : 0, 15, 30, 40, deuce, advantage, win</li>
<li><b>Transition</b> : marquer un point pour A ou B</li>
<li><b>Sortie</b> textuelle : <i>"Player 1 : 30 / Player 2 : 15"</i></li>
<li><b>Pièges</b> : égalité à 40-40, regagner l'avantage</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">👀 Ce que vous verrez</div>
<div style="background: #e8f6ec; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>L'enseignant reste <b>driver</b> (au clavier)</li>
<li>Le <b>navigator</b> tourne dans le groupe toutes les <b>2 min</b> au chronomètre</li>
<li>Comment une solution se construit par <b>consensus</b> du groupe</li>
<li><b>Commit</b> à chaque fin de <b>cycle TDD</b> (après le refactor)</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Après la démo, c'est <b>à vous</b> : 6 kata en binôme, vous tournez les rôles toutes les 5 à 10 minutes.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:50%](assets/refactoring-horloger.jpg)

# Partie 3 - Code smells et refactoring

Comment vivre avec du code qui marche, mais nous fait honte ?

---

## 🛠️ Refactorer, c'est entretenir ses outils

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
L'artisan ne nettoie pas ses outils par perfectionnisme. Il le fait parce que demain, <b>il s'en sert encore</b>. Remanier son code, c'est exactement ce même geste et ce même besoin mais pour un développeur qui maitrise sa dette technique.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #b8772a; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🪚 Le menuisier</div>
<div style="background: #f5e9d8; padding: 1rem 1.2rem; flex: 1; font-size: 1.5rem;">
Aiguise sa scie <b>entre deux chantiers</b>. Une lame émoussée fait perdre du temps à chaque coupe et elle peut blesser.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🍳 Le chef</div>
<div style="background: #fdecea; padding: 1rem 1.2rem; flex: 1; font-size: 1.5rem;">
Récure et aiguise ses couteaux <b>en fin de service</b>. Demain, on ne commence pas avec une cuisine sale et des couteaux émoussés.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">💻 Le développeur</div>
<div style="background: #eaf2fb; padding: 1rem 1.2rem; flex: 1; font-size: 1.5rem;">
Remanie son code <b>après chaque GREEN</b>. Pas pour faire joli mais pour <b>rester rapide</b> sur la fonctionnalité suivante tout en conservant la confiance en son code.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Le code qu'on lit cette semaine, c'est celui qu'on <b>modifiera</b> le mois prochain. Le garder propre à chaque instant garantit qu'on pourra compter sur lui quand on en aura besoin.
</div>

---

## 👃 Qu'est-ce qu'un code smell ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Terme inventé par <b>Kent Beck</b> et popularisé par <b>Martin Fowler</b> dans <i>Refactoring</i> (1999, ~20 smells catalogués). Un code smell est un <b>indice</b> que quelque chose ne va pas, pas un bug ni une erreur de compilation.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🚨 Un signal, pas une alarme</div>
<div style="background: #fdecea; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
Le code <b>compile</b>, les tests <b>passent</b>, l'utilisateur ne voit rien. Mais quand on essaie de le <b>modifier</b>, ça résiste : la zone va devenir pénible pour les développeurs.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 0rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🍞 Comme un aliment qui sent</div>
<div style="background: #f9f5e8; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
<b>Pas forcément périmé</b>, mais il faut <b>regarder de près</b>. Le smell est un signal d'enquête, pas une condamnation.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📏 Un vocabulaire partagé</div>
<div style="background: #eaf2fb; padding: 1rem 1.2rem; flex: 1; font-size: 1.4rem;">
<i>Long Method</i>, <i>Magic Number</i>, <i>Duplicated Code</i>... un <b>nom commun</b> qui rend les revues de code plus rapides : pas besoin de réexpliquer le problème à chaque fois.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
<i>"If it stinks, change it."</i> &nbsp; - &nbsp; <b>Kent Beck</b>
</div>

---

## 📚 Les smells qu'on va surtout rencontrer au TP4

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Fowler en référence une vingtaine. Voici les <b>6 smells</b> que vous croiserez au TP4, chacun avec son refactoring associé.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.8rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📏 Long Method</div>
<div style="background: #fdecea; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Une méthode de 50 lignes qu'on doit scroller pour la lire.<br/>
<b>→ Extract Method</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🏢 Large Class</div>
<div style="background: #f3eaf7; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Une classe qui fait <b>trop de choses</b> à la fois.<br/>
<b>→ Extract Class</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📋 Long Parameter List</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Une méthode à <b>7 paramètres</b>, imbuvable à l'appel.<br/>
<b>→ Introduce Parameter Object</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #c19a3a; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">👯 Duplicated Code</div>
<div style="background: #f5f0dc; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Le même bloc <b>copié-collé</b> en 3 endroits.<br/>
<b>→ Extract Method / Move Method</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🔢 Magic Numbers</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
<code style="background: rgba(0,0,0,0.05); padding: 0 0.3rem; border-radius: 3px;">if (age &gt; 65)</code>, <code style="background: rgba(0,0,0,0.05); padding: 0 0.3rem; border-radius: 3px;">total *= 1.20</code>.<br/>
<b>→ Replace Magic Number with Constant</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🔀 Switch Statements</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Un <code style="background: rgba(0,0,0,0.05); padding: 0 0.3rem; border-radius: 3px;">switch</code> sur un type, <b>dupliqué</b> en 5 endroits.<br/>
<b>→ Replace Conditional with Polymorphism</b>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Un smell n'est pas une <b>faute</b>, c'est un <b>signal</b> qu'une zone va devenir pénible à modifier.
</div>

---

## 🔧 Qu'est-ce qu'un refactoring ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le mot <i>refactoring</i> (en français : <b>remaniement</b>) est utilisé à toutes les sauces. La définition est plus <b>exigeante</b> qu'on ne le croit :
</p>

<div style="background: #fff8e1; border-left: 5px solid #e8a838; padding: 1rem 1.2rem; border-radius: 6px; margin-top: 0.8rem; font-size: 1.5rem;">
💬 <i>"Modifier la <b>structure interne</b> du code <b>sans changer son comportement observable</b>."</i><br/>
<span style="font-size: 1.2rem;">- <b>Martin Fowler</b>, <i>Refactoring: Improving the Design of Existing Code</i> (1999, 2018)</span>
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">✅ C'est un refactoring</div>
<div style="background: #e8f6ec; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
Renommer une variable, extraire une méthode, déplacer un champ dans une autre classe.<br/>
<b>→ Les tests existants continuent de passer.</b>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🙅 Pas un refactoring</div>
<div style="background: #fdecea; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
Changer ce que fait une méthode, ajouter une fonctionnalité, corriger un bug.<br/>
<b>→ Là, les tests changent (ou deviennent rouges).</b>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
🛡️ Prérequis absolu : une <b>suite de tests</b> qui couvre le comportement. Sinon, c'est de la <b>réécriture</b> (<i>rewriting</i>), pas un <b>remaniement</b> (<i>refactoring</i>).
</div>

---

## 📖 Le catalogue de Fowler (70+ refactorings)

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Fowler a normalisé ce vocabulaire : <b>70+ transformations</b> cataloguées, chacune avec son <b>nom</b>, son <b>contexte d'usage</b> et sa <b>procédure pas-à-pas</b>. Tout est en ligne sur <a href="https://refactoring.com/catalog/" style="color: #4a90d9;">refactoring.com/catalog</a>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 0.8rem; margin: 4rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🏷️ Rename</div>
<div style="background: #eaf2fb; padding: 0.9rem 1rem; flex: 1; font-size: 1.3rem;">
Le plus fréquent. Pour un <b>nom plus juste</b>, qui révèle l'intention.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">✂️ Extract Method</div>
<div style="background: #f3eaf7; padding: 0.9rem 1rem; flex: 1; font-size: 1.3rem;">
Découper une <b>longue méthode</b> en plus petites, chacune avec une intention claire.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">📦 Extract Class</div>
<div style="background: #f9f5e8; padding: 0.9rem 1rem; flex: 1; font-size: 1.3rem;">
Sortir un <b>sous-ensemble cohérent</b> de la classe trop chargée dans sa propre classe.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🦎 Polymorphism</div>
<div style="background: #e8f6ec; padding: 0.9rem 1rem; flex: 1; font-size: 1.3rem;">
Remplacer un <code style="background: rgba(0,0,0,0.05); padding: 0 0.3rem; border-radius: 3px;">switch</code> sur un type par des <b>sous-classes</b>.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Au TP4, vous pratiquerez ces <b>4 grands classiques</b> avec l'aide de votre IDE.
</div>

---

## 🧪 Exemple : Extract Method

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; background: transparent !important; padding: 0.4rem 0.2rem !important; }
section pre, section pre code, section pre code[class*="language-"] { background: transparent !important; font-size: 0.55rem !important; line-height: 1.25 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
On découpe une longue méthode en plusieurs petites, chacune nommée d'après son <b>intention</b>. Le code racine devient un <b>sommaire</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.5rem; margin-top: 0.8rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🦴 Avant : Long Method</div>
<div style="background: #fdecea; padding: 0.6rem 0.9rem; flex: 1; font-size: 0.85rem;">

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
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">✨ Après : intentions nommées</div>
<div style="background: #e8f6ec; padding: 0.6rem 0.9rem; flex: 1; font-size: 0.85rem;">

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

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Avant il falait <b>tout lire</b> pour comprendre, après, on lit <code>imprimerFacture</code> comme un <b>sommaire</b>.
</div>

---

## 🧪 Exemple : Replace Conditional with Polymorphism

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; background: transparent !important; padding: 0.4rem 0.2rem !important; }
section pre, section pre code, section pre code[class*="language-"] { background: transparent !important; font-size: 0.45rem !important; line-height: 1.25 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
On remplace un <code>switch</code> sur un <b>type</b> par une <b>hiérarchie de sous-classes</b>. Chaque branche devient une méthode dans sa sous-classe.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.8rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">🦴 Avant : Switch Statements</div>
<div style="background: #fdecea; padding: 0.6rem 0.9rem; flex: 1;">

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

<p style="font-size: 1.1rem; margin: 0.3rem 0 0 0;">Chaque nouveau type oblige à <b>rouvrir</b> cette classe. Le <code>switch</code> est souvent <b>dupliqué</b> ailleurs (parler, manger, dormir...).</p>

</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.4rem; font-weight: bold; text-align: center;">✨ Après : Polymorphisme</div>
<div style="background: #e8f6ec; padding: 0.6rem 0.9rem; flex: 1;">

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

<p style="font-size: 1.1rem; margin: 0.3rem 0 0 0;">Nouveau type = <b>nouvelle classe</b>. On ne touche <b>pas à l'existant</b>.</p>

</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Principe <b>Open/Closed</b> : ouvert à l'<b>extension</b> (ajouter une classe), fermé à la <b>modification</b> (ne pas toucher l'existant).
</div>

---

## 🛠️ Votre IDE fait le gros du travail

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Un refactoring <b>manuel</b> est risqué : un oubli, un remplacement raté → le comportement change. L'IDE fait le travail à votre place, <b>sans erreur</b>. Au TP4, on abuse de deux raccourcis dans le <b>Codespace VS Code</b> (extension Java Red Hat).
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">⌨️ <kbd>Ctrl+.</kbd> &nbsp; Quick Fix + Refactor</div>
<div style="background: #eaf2fb; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
Menu <b>contextuel</b> selon ce que touche le curseur :
<ul style="margin: 0.4rem 0 0 0; padding-left: 1.2rem;">
<li><i>Extract to method</i> / <i>constant</i> / <i>variable</i></li>
<li><i>Move</i>, <i>Inline</i></li>
<li><i>Add unimplemented methods</i></li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🏷️ <kbd>F2</kbd> &nbsp; Rename</div>
<div style="background: #e8f6ec; padding: 1rem 1.2rem; flex: 1; font-size: 1.3rem;">
Renomme <b>partout</b> en un coup : déclaration, usages, imports, Javadoc.<br/><br/>
Le refactoring le plus <b>fréquent</b>, et celui pour lequel l'IDE est <b>indispensable</b>.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
💡 Si l'IDE sait faire le refactoring : <b>laissez-le</b> faire. Si vous devez le faire à la main : <b>ajoutez d'abord des nouveaux tests</b>.
</div>

<div style="margin-top: 0.5rem; font-size: 1rem; color: #666; text-align: center;">
<em>IntelliJ IDEA propose les mêmes refactorings avec <kbd>Ctrl+Alt+M</kbd>, <kbd>Ctrl+Alt+V</kbd>, <kbd>Shift+F6</kbd>...</em>
</div>

---

## 🛡️ Characterization tests : sécuriser du legacy

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Concept de <b>Michael Feathers</b> (<i>Working Effectively with Legacy Code</i>, 2004). <b>Legacy</b> = code <b>sans tests</b> qu'on doit faire évoluer. Sans filet, pas de refactoring en sécurité.
</p>

<div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 0.6rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem; font-size: 1.4rem; font-weight: bold; text-align: center;">1. 🔍 Observer</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Lancer le code sur des entrées variées, <b>noter</b> ce qu'il sort.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem; font-size: 1.4rem; font-weight: bold; text-align: center;">2. ✍️ Figer</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Écrire un test qui <b>attend exactement cette sortie</b>, juste ou pas.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem; font-size: 1.4rem; font-weight: bold; text-align: center;">3. ✅ Verrouiller</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Le test passe : le comportement actuel est <b>fixé</b>, vous avez un filet.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem; font-size: 1.4rem; font-weight: bold; text-align: center;">4. 🔧 Refactorer</div>
<div style="background: #f3eaf7; padding: 0.8rem 1rem; flex: 1; font-size: 1.2rem;">
Si un test casse : vous avez <b>changé le comportement</b>, donc créé un bug.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Ces tests ne valident pas que le code est <b>juste</b>. Ils le <b>pinnent</b>. C'est à dire qu'ils figent ce qui sort, pour que le refactoring n'introduise pas de régression.
</div>

---

## 🛡️ Exemple : un code opaque à caractériser

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; background: transparent !important; padding: 0.4rem 0.2rem !important; }
section pre, section pre code, section pre code[class*="language-"] { background: transparent !important; font-size: 0.8rem !important; line-height: 1.35 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Une méthode <code>fraisPort</code> empile <b>5 règles</b> qui s'additionnent, s'écrasent, se multiplient. Impossible de prédire le résultat <i>juste en lisant</i>.
</p>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12); margin-top: 1rem;">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🦴 Le code legacy (en production, pas un seul test)</div>
<div style="background: #fdecea; padding: 0.8rem 1.2rem;">

```java
double fraisPort(double poids, boolean express, String pays) {
  double frais = 5;
  if (poids > 1) frais += 2;
  if (poids > 5) frais = 15;
  if (express) frais *= 1.5;
  if (pays.equals("FR")) frais -= 1;
  return frais;
}
```

</div>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Combien coûte un colis de <b>6 kg en express vers la France</b> ? <b>Personne ne sait</b> sans le lancer.
</div>

---

## 🛡️ Exemple : pinner le comportement avec des tests

<style scoped>
section pre { margin: 0 !important; border: none !important; box-shadow: none !important; border-radius: 0 !important; background: transparent !important; padding: 0.4rem 0.2rem !important; }
section pre, section pre code, section pre code[class*="language-"] { background: transparent !important; font-size: 0.85rem !important; line-height: 1.4 !important; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
On <b>lance</b> la méthode avec des entrées variées, on <b>note</b> ce qu'elle retourne, on <b>colle</b> les valeurs dans des <code>assertEquals</code>. On n'invente rien : on copie ce que la prod fait <b>déjà</b>.
</p>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12); margin-top: 1rem;">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🛡️ 5 tests qui figent les sorties observées</div>
<div style="background: #e8f6ec; padding: 0.8rem 1.2rem;">

```java
@Test void colis_leger_FR()       { assertEquals(4.0,  fraisPort(0.5, false, "FR")); }
@Test void colis_2kg_FR()         { assertEquals(6.0,  fraisPort(2.0, false, "FR")); }
@Test void colis_6kg_FR()         { assertEquals(14.0, fraisPort(6.0, false, "FR")); }
@Test void colis_6kg_express_FR() { assertEquals(21.5, fraisPort(6.0, true,  "FR")); }
@Test void colis_2kg_express_DE() { assertEquals(10.5, fraisPort(2.0, true,  "DE")); }
```

</div>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Sans ces tests, refactorer ce genre de cascade = <b>roulette russe</b> avec la production. Avec ces tests, on s'assure que le comportement reste identique.
</div>

---

## 🎯 Le pattern du TP4

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Chaque exercice du TP4 suit le même squelette, avec <b>deux familles de tests</b> complémentaires : un filet anti-régression et un filet qui certifie le geste.
</p>

<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.8rem; margin: 1rem 0; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">1. 📖 Lire</div>
<div style="background: #fdecea; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Survoler le code <i>smelly</i> sans chercher à <b>tout</b> comprendre. Repérer les zones qui semblent <b>bizarres</b> (longues, dupliquées, opaques).
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">2. ✅ Vérifier</div>
<div style="background: #e8f6ec; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Lancer les <b>caractérisations</b>. Toutes vertes ? On a un point de départ stable. Une qui échoue ? On corrige <b>avant</b> de toucher au reste.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">3. 🔍 Identifier</div>
<div style="background: #f9f5e8; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Choisir <b>un seul</b> smell à traiter (Long Method, Magic Number...) et le refactoring associé du catalogue Fowler.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">4. 🔧 Refactorer</div>
<div style="background: #eaf2fb; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Appliquer le refactoring via l'IDE (<kbd>Ctrl+.</kbd> / <kbd>F2</kbd>). Lancer les tests <b>à chaque pas</b>. Caract verte ? On continue. Rouge ? On annule.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #16a085; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">5. 🔓 Débloquer</div>
<div style="background: #e6f5f1; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Retirer les <code>@Disabled</code> des tests de structure que le refactoring vient de <b>rendre vrais</b>. Ils passent : le geste est <b>fait</b>.
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #8e44ad; color: #fff; padding: 0.5rem 0.8rem; font-size: 1.4rem; font-weight: bold; text-align: center;">6. 💾 Commit</div>
<div style="background: #f3eaf7; padding: 0.8rem 1rem; flex: 1; font-size: 1.15rem;">
Commit dès que <b>tous</b> les tests passent. Petits commits = retour arrière facile. Message clair : <code>refactor: extract calculerTotalHT</code>.
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.4rem;">
⚠️ Si une caractérisation casse : <b>ne la modifiez pas</b>. Annulez la dernière transformation.
</div>

---

## 🌹 Le kata Gilded Rose

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Créé par <b>Terry Hughes</b>, popularisé par <b>Emily Bache</b>. Un classique : <b>35 lignes</b> de code spaghetti à comprendre et faire évoluer <b>sans rien casser</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e8a838; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🛍️ Le magasin</div>
<div style="background: #f9f5e8; padding: 1rem 1.2rem; flex: 1; font-size: 1.2rem;">
Chaque jour, les articles évoluent selon leur type :
<ul style="margin: 0.4rem 0 0 0; padding-left: 1.2rem;">
<li><b>Articles normaux</b> : perdent en qualité</li>
<li><b>Aged Brie</b> : gagne en qualité avec le temps</li>
<li><b>Sulfuras</b> : immuable, légendaire</li>
<li><b>Backstage passes</b> : règle complexe</li>
<li><b>Conjured</b> 🆕 : à <b>ajouter</b></li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #4a90d9; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">🎯 Votre mission</div>
<div style="background: #eaf2fb; padding: 1rem 1.2rem; flex: 1; font-size: 1.2rem;">
<ol style="margin: 0; padding-left: 1.4rem;">
<li><b>Comprendre</b> le code via des <i>characterization tests</i></li>
<li><b>Refactorer</b> sans casser une seule caractérisation</li>
<li><b>Ajouter Conjured</b> sur le code propre</li>
</ol>
<p style="margin: 0.5rem 0 0 0;">L'<code>if</code> imbriqué qui faisait peur est devenu <b>trivial</b> à étendre.</p>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
La <b>situation typique</b> en entreprise : du code qu'on n'a pas écrit, sans docs, à faire évoluer. <b>Refactoring d'abord</b>, feature ensuite. 🎬 Démo live au TP4.
</div>

---

## 🌄 Où s'arrête le refactoring ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Refactorer a un <b>coût</b> : du temps, un risque résiduel, une PR à relire. C'est une <b>décision</b>, pas un automatisme. Comment savoir si ça vaut le coup ?
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">✅ Ça vaut le coup quand...</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>vous <b>allez toucher</b> cette zone dans les prochains mois</li>
<li>le smell <b>ralentit</b> concrètement une feature ou un bug fix</li>
<li>les <b>tests</b> prouvent que rien ne casse</li>
<li>c'est <b>l'endroit précis</b> où vous intervenez</li>
</ul>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold; text-align: center;">⚠️ C'est un piège quand...</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1; font-size: 1.4rem;">
<ul style="margin: 0; padding-left: 1.2rem;">
<li>le code <b>marche</b>, est <b>stable</b>, personne ne le touche</li>
<li>vous le faites juste parce que <i>"c'est pas joli"</i></li>
<li>il n'y a <b>pas de tests</b> : vous allez casser</li>
<li>vous refactorez <b>et</b> ajoutez une feature en même temps</li>
</ul>
</div>
</div>

</div>

<div style="margin-top: 1rem; background: #fff8e1; border-left: 5px solid #e8a838; padding: 0.9rem 1.2rem; border-radius: 6px; font-size: 1.5rem;">
🛠️ L'artisan qui retourne son atelier <b>les jours</b> où il ne travaille plus, il range. On justifie un refactoring par un <b>bénéfice concret à venir</b>, pas par un idéal d'esthétique.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Quelques gestes à garder

Trois habitudes simples pour la suite : ranger un peu, nommer mieux, commenter moins.

---

## 🏕️ La règle du scout

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; font-size: 1.3rem; line-height: 1.6; text-align: center;">

> "Leave the campground cleaner than you found it."
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

<div style="margin-top: 1rem; background: #fff8e1; border-left: 4px solid #e8a838; padding: 0.8rem 1rem; border-radius: 6px; font-size: 1.5rem;">
🛠️ C'est <b>le geste de l'artisan qui range son atelier</b> avant de partir. Pas pour la démonstration, pas pour la photo - parce que demain matin il veut retrouver un atelier où il peut travailler vite. La règle du scout appliquée au code, c'est la même économie : l'artisan soigne son environnement parce que <em>c'est là qu'il vit</em>.
</div>

<div style="margin-top: 0.8rem; background: #e6f5ec; padding: 1rem; border-radius: 10px;">
💡 <b>Effet cumulé</b> : 20 développeurs qui améliorent 2 lignes à chaque PR = la base de code s'<b>auto-nettoie</b>. Inverse du cercle vicieux de la dette technique.
</div>

---

## 🏷️ Le nommage : première victoire

<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; font-size: 1.1rem; text-align: center; margin-bottom: 0.8rem;">
"There are only <b>two hard things</b> in Computer Science: cache invalidation and <b>naming things</b>." - Phil Karlton
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

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Pour la suite

Le prochain cap est simple : mettre ces gestes en pratique, d'abord à deux, puis sur du legacy.

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
6 exercices de refactoring : Facture (Extract Method), CalculPrix (Magic Number), Menu (Extract Class), Animal (Polymorphisme), ServiceNotification (Parameter Object), <b>Gilded Rose</b>.<br/><br/>
Caractérisation <b>active et verte</b> + tests de structure <code>@Disabled</code> à débloquer.
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
<b>🎯 Dès maintenant</b> : dans votre Codespace, essayez <code>F2</code> pour renommer un identifiant, puis sélectionnez quelques lignes et lancez <code>Ctrl+.</code> → <em>Extract to method</em>. Le plus tôt vos doigts connaissent ces deux gestes, le mieux vous vivrez les TP3 et TP4.
</div>

<div style="margin-top: 1.2rem; background: #fff8e1; border-left: 4px solid #e8a838; padding: 0.9rem 1rem; border-radius: 6px; font-size: 1.5rem;">
🛠️ <b>L'artisan, au fond, c'est vous.</b> Le CM1 a posé le <em>pourquoi</em> - du code dont on peut être fier, qu'on n'a pas peur de relire dans six mois. Ce CM2 a posé les <em>gestes</em> - tester avant, refactorer souvent, nommer juste, ranger en partant. À partir du TP3, le seul objectif est que ces gestes deviennent des <b>réflexes</b>. On n'aiguise pas sa scie le jour où on doit couper la planche ; on l'aiguise la veille.
</div>
