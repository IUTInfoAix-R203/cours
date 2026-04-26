---
marp: true
theme: default
paginate: true
---

<!-- _class: lead -->
<!-- _paginate: false -->

# Artisanat logiciel, qualité et Git avancé

**R2.03 - Qualité de développement**

IUT d'Aix-Marseille - BUT Informatique, première année

<div style="display: flex; justify-content: center; gap: 9rem; margin-top: 6rem; color: #555;">
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">🔀</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">Git</div></div>
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">✅</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">TDD</div></div>
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">🥋</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">Kata</div></div>
<div style="text-align: center;"><div style="font-size: 6.5rem; opacity: 0.8;">🧹</div><div style="font-size: 1.3rem; font-weight: 400; letter-spacing: 0.03em; color: #888;">Refactoring</div></div>
</div>

---

## Le module R2.03 en un coup d'oeil

<style scoped>
blockquote { font-size: 1rem; margin-bottom: 0; }
</style>

> Apprendre à produire du code **propre**, **testé**, **relu** et **maintenable**. Passer de "ça marche sur ma machine" à un vrai réflexe professionnel.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin-top: 2rem;">
<div style="background: #4a90d9; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2rem;">🔀</div>
<div style="font-size: 1.6rem; font-weight: bold; margin-top: 0.4rem;">Git professionnel</div>
<div style="font-size: 1.05rem; margin-top: 0.4rem; opacity: 0.95;">Rebase, cherry-pick, PR, review</div>
</div>

<div style="background: #27ae60; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2rem;">✅</div>
<div style="font-size: 1.6rem; font-weight: bold; margin-top: 0.4rem;">TDD baby-steps</div>
<div style="font-size: 1.05rem; margin-top: 0.4rem; opacity: 0.95;">RED → GREEN → REFACTOR</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2rem;">🥋</div>
<div style="font-size: 1.6rem; font-weight: bold; margin-top: 0.4rem;">Kata &amp; pair programming</div>
<div style="font-size: 1.05rem; margin-top: 0.4rem; opacity: 0.95;">Driver, navigator, ping-pong</div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2rem;">🧹</div>
<div style="font-size: 1.6rem; font-weight: bold; margin-top: 0.4rem;">Refactoring</div>
<div style="font-size: 1.05rem; margin-top: 0.4rem; opacity: 0.95;">Code smells et transformations de Fowler</div>
</div>

</div>

---

## Organisation du module

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.4rem; border-radius: 12px; text-align: center;">
<div style="font-size: 1.8rem; font-weight: bold;">CM1</div>
<div style="margin-top: 0.3rem;">Artisanat + Git + TDD intro</div>
<div style="margin-top: 0.8rem; background: rgba(255,255,255,0.18); border-radius: 8px; padding: 0.6rem; font-weight: bold;">→ TP1 Git + TP2 TDD</div>
</div>
<div style="background: #e8a838; color: white; padding: 1.4rem; border-radius: 12px; text-align: center;">
<div style="font-size: 1.8rem; font-weight: bold;">CM2</div>
<div style="margin-top: 0.3rem;">TDD avancé + refactoring</div>
<div style="margin-top: 0.8rem; background: rgba(255,255,255,0.18); border-radius: 8px; padding: 0.6rem; font-weight: bold;">→ TP3 Kata + TP4 Refactoring</div>
</div>
</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 10px; text-align: center; font-size: 1.1rem;">
Chaque CM prépare les <b>gestes concrets</b> mis en pratique dans les TP qui suivent.
</div>

<div style="margin-top: 1.5rem; display: flex; justify-content: space-between; align-items: flex-start; padding: 0 0.5rem; position: relative;">

<div style="position: absolute; top: 0.6rem; left: 3%; right: 3%; height: 3px; background: #bdc3c7; border-radius: 2px; z-index: 0;"></div>

<div style="flex: 1; text-align: center; position: relative; z-index: 1;">
<div style="width: 14px; height: 14px; background: #4a90d9; border: 3px solid white; border-radius: 50%; margin: 0 auto; box-shadow: 0 0 0 2px #4a90d9;"></div>
<div style="margin-top: 0.4rem; font-size: 0.8rem; color: #888;">Sem. 1 · 27 avril</div>
<div style="font-weight: bold; color: #4a90d9; margin-top: 0.1rem;">CM1</div>
</div>

<div style="flex: 1.2; text-align: center; position: relative; z-index: 1;">
<div style="width: 14px; height: 14px; background: #e8a838; border: 3px solid white; border-radius: 50%; margin: 0 auto; box-shadow: 0 0 0 2px #e8a838;"></div>
<div style="margin-top: 0.4rem; font-size: 0.8rem; color: #888;">Sem. 2 · 4 mai</div>
<div style="font-weight: bold; color: #e8a838; margin-top: 0.1rem;">CM2 + TP1 + TP2</div>
</div>

<div style="flex: 1; text-align: center; position: relative; z-index: 1;">
<div style="width: 14px; height: 14px; background: #27ae60; border: 3px solid white; border-radius: 50%; margin: 0 auto; box-shadow: 0 0 0 2px #27ae60;"></div>
<div style="margin-top: 0.4rem; font-size: 0.8rem; color: #888;">Sem. 3 · 11 mai</div>
<div style="font-weight: bold; color: #27ae60; margin-top: 0.1rem;">TP3</div>
</div>

<div style="flex: 1; text-align: center; position: relative; z-index: 1;">
<div style="width: 14px; height: 14px; background: #e74c3c; border: 3px solid white; border-radius: 50%; margin: 0 auto; box-shadow: 0 0 0 2px #e74c3c;"></div>
<div style="margin-top: 0.4rem; font-size: 0.8rem; color: #888;">Sem. 4 · 18 mai</div>
<div style="font-weight: bold; color: #e74c3c; margin-top: 0.1rem;">TP4</div>
</div>

<div style="flex: 1; text-align: center; position: relative; z-index: 1;">
<div style="width: 14px; height: 14px; background: #2c3e50; border: 3px solid white; border-radius: 50%; margin: 0 auto; box-shadow: 0 0 0 2px #2c3e50;"></div>
<div style="margin-top: 0.4rem; font-size: 0.8rem; color: #888;">18 juin</div>
<div style="font-weight: bold; color: #2c3e50; margin-top: 0.1rem;">CC3</div>
</div>

</div>

---

## Évaluation

<p style="font-size : 1.5rem;">
Trois notes, un objectif : vérifier que vous <b>maîtrisez des gestes de métier</b>, pas juste que votre code tourne.
</p>

<div style="display: flex; gap: 1.5rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">📝</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC1</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Autograding de TP2, TP3, TP4</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 10</div>
</div>
<div style="background: #e8a838; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">🤝</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC2</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Participation et qualité des reviews</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 10</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.8rem 1.2rem; border-radius: 12px; flex: 1; text-align: center;">
<div style="font-size: 3.5rem; margin-bottom: 0.5rem;">💻</div>
<div style="font-weight: bold; font-size: 1.5rem;">CC3</div>
<div style="margin-top: 0.5rem; opacity: 0.9;">Mini-kata TDD sur feuille (2 h, sans outils)</div>
<div style="margin-top: 0.5rem; font-weight: bold; font-size: 1.2rem; background: rgba(255,255,255,0.2); border-radius: 6px; padding: 0.2rem;">coeff. 40</div>
</div>
</div>

<div style="display: flex; height: 2rem; border-radius: 8px; overflow: hidden; margin-top: 1.2rem;">
<div style="background: #4a90d9; flex: 10; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">17%</div>
<div style="background: #e8a838; flex: 10; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">17%</div>
<div style="background: #e74c3c; flex: 40; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.7rem; font-weight: bold;">66%</div>
</div>

<div style="margin-top: 0.8rem; font-size: 1.2rem; color: #666; text-align: center;">
TP1 Git : mise à niveau, non noté. Le plus gros coefficient porte sur le <b>raisonnement TDD</b>, pas sur la vitesse de frappe.
</div>

---

## Environnement de travail
<p style="font-size : 1.5rem;">
Tout le module se fait sur <b>GitHub Codespaces</b> dans votre navigateur sans installation :
</p>
<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1.5rem;">
<div style="background: #e8a838; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">☕</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Java 25</div>
</div>
<div style="background: #27ae60; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🧪</div>
<div style="font-weight: bold; margin-top: 0.3rem;">JUnit 6 + AssertJ</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">📦</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Maven (via mvnw)</div>
</div>
<div style="background: #4a90d9; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🔀</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Git + gh CLI</div>
</div>
<div style="background: #8e44ad; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">🤖</div>
<div style="font-weight: bold; margin-top: 0.3rem;">Copilot Chat</div>
</div>
<div style="background: #17a2b8; color: white; padding: 1.2rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.5rem;">📊</div>
<div style="font-weight: bold; margin-top: 0.3rem;">ApprovalTests</div>
</div>
</div>

<div style="background: #2c3e50; color: white; padding: 1rem 2rem; border-radius: 10px; text-align: center; margin-top: 1rem; font-size: 1.5rem;">
🌐 Dépôt étudiant : <a href="https://github.com/IUTInfoAix-R203/tp" style="color: #a0d8f8;">github.com/IUTInfoAix-R203/tp</a>
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:40%](assets/artisan-menuisier.jpg)

# Partie 1 - Artisanat logiciel

Pourquoi on parle de "qualité" ?

---

## 🔨 Qu'est-ce que l'artisanat logiciel ?

<p style="font-size : 1.5rem;">
Un <b>artisan meunuisier</b> livre une table <b>bien finie</b>, robuste, belle, facile à réparer. Un <b>artisan logiciel</b> livre du code qui doit être :
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 1rem; margin: 3rem 0;">

<div style="background: #4a90d9; color: white; padding: 1.2rem 0.8rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.5rem;">📖</div>
<div style="font-size: 1.3rem; font-weight: bold; margin-top: 0.3rem;">Lisible</div>
<div style="font-size: 1.1rem; margin-top: 0.3rem; opacity: 0.95;">par un autre humain</div>
</div>

<div style="background: #27ae60; color: white; padding: 1.2rem 0.8rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.5rem;">✅</div>
<div style="font-size: 1.3rem; font-weight: bold; margin-top: 0.3rem;">Testé</div>
<div style="font-size: 1.1rem; margin-top: 0.3rem; opacity: 0.95;">pour éviter les régressions</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.2rem 0.8rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.5rem;">🔧</div>
<div style="font-size: 1.3rem; font-weight: bold; margin-top: 0.3rem;">Simple</div>
<div style="font-size: 1.1rem; margin-top: 0.3rem; opacity: 0.95;">à modifier quand les besoins évoluent</div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.2rem 0.8rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.5rem;">👥</div>
<div style="font-size: 1.3rem; font-weight: bold; margin-top: 0.3rem;">Relu</div>
<div style="font-size: 1.1rem; margin-top: 0.3rem; opacity: 0.95;">par des pairs avant fusion</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem 1.5rem; border-radius: 10px; font-size: 1.5rem; text-align: left;">
Le <b>"Software Craftsmanship"</b> est mouvement né dans les années 2000, en réaction à l'industrialisation du monde du logiciel qui pressait les développeurs à livrer vite au détriment de la qualité.
</div>

---

## 🔨 Le manifeste de l'artisanat logiciel (2009)

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
✊ Snowbird, Utah, décembre 2008 — en écho au Manifeste Agile de 2001, 4 principes, toujours sur le même modèle : <b>non seulement X, mais aussi Y</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">

<div style="background: #4a90d9; color: white; padding: 1.2rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.4rem; opacity: 0.75;">Non seulement du logiciel qui marche,</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;"><span style="font-size: 2rem; vertical-align: middle; margin-right: 0.3rem;">⚒️</span> mais aussi du logiciel bien conçu.</div>
</div>

<div style="background: #27ae60; color: white; padding: 1.2rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.4rem; opacity: 0.75;">Non seulement répondre au changement,</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;"><span style="font-size: 2rem; vertical-align: middle; margin-right: 0.3rem;">📈</span> mais aussi ajouter de la valeur régulièrement.</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.2rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.4rem; opacity: 0.75;">Non seulement des individus et des interactions,</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;"><span style="font-size: 2rem; vertical-align: middle; margin-right: 0.3rem;">🤝</span> mais aussi une communauté de professionnels.</div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.2rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.4rem; opacity: 0.75;">Non seulement collaborer avec le client,</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;"><span style="font-size: 2rem; vertical-align: middle; margin-right: 0.3rem;">🏛️</span> mais aussi des partenariats productifs.</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem;">
💡 <b>L'idée à retenir</b> : le manifeste ne <b>rejette pas</b> l'agilité, il la <b>complète</b>. Les processus agiles ne suffisent pas : il faut aussi une exigence sur la <b>qualité du code</b> lui-même.
</div>

---

## 📉 Pourquoi c'est important : le coût des bugs

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Plus un bug est détecté <b>tard</b>, plus il coûte cher à corriger. Ordre de grandeur (<a href="https://staff.emu.edu.tr/alexanderchefranov/Documents/CMPE412/Boehm1981%20COCOMO.pdf" style="color: inherit;">Boehm, 1981</a>) :
</p>

<div style="display: flex; gap: 2rem; margin-top: 0.8rem; align-items: center;">
<div style="flex: 1.3;">

<div style="display: grid; gap: 2.6rem;">

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 190px; font-size: 1.5rem; color: #555;">Développement</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.5rem; overflow: hidden;">
<div style="background: #27ae60; width: 1%; height: 100%;"></div>
</div>
<div style="width: 70px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #27ae60;">1x</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 190px; font-size: 1.5rem; color: #555;">Tests</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.5rem; overflow: hidden;">
<div style="background: #e8a838; width: 6%; height: 100%;"></div>
</div>
<div style="width: 70px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #e8a838;">6x</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 190px; font-size: 1.5rem; color: #555;">Pré-production</div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.5rem; overflow: hidden;">
<div style="background: #e67e22; width: 15%; height: 100%;"></div>
</div>
<div style="width: 70px; text-align: right; font-weight: bold; font-size: 1.3rem; color: #e67e22;">15x</div>
</div>

<div style="display: flex; align-items: center; gap: 0.8rem;">
<div style="width: 190px; font-size: 1.5rem; color: #555;"><b>Chez le client</b></div>
<div style="flex: 1; background: #eee; border-radius: 6px; height: 2.5rem; overflow: hidden;">
<div style="background: #e74c3c; width: 100%; height: 100%;"></div>
</div>
<div style="width: 70px; text-align: right; font-weight: bold; font-size: 1.5rem; color: #e74c3c;">100x</div>
</div>

</div>

</div>
<div style="flex: 1;">

<div style="background: #e74c3c; color: white; padding: 1.3rem 1.5rem; border-radius: 12px; font-size: 1.4rem;">
<div style="font-size: 1.5rem; font-weight: bold; margin-bottom: 0.6rem;">💥 Knight Capital (2012)</div>
Un bug de déploiement sur un système de trading a fait perdre <b>440 M$ en 45 minutes</b>.<br/><br/>
Conséquence : <b>Faillite !</b><br/><br/> Cause : un drapeau mal réinitialisé dans un module obsolète.
</div>

</div>
</div>

<div style="margin-top: 2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem;">
➡️ La qualité du code n'est pas un luxe d'esthète : c'est une question de <b>survie économique</b>.
</div>

---

## 💳 La dette technique

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Métaphore de <b>Ward Cunningham</b> (1992) : écrire du code sale pour livrer vite, c'est comme <b>emprunter</b> de l'argent. Ça aide à court terme — mais il faut <b>rembourser</b>, <b>avec intérêts</b>.
</p>

<div style="display: flex; align-items: center; gap: 0.6rem; margin: 2rem 0;">

<div style="flex: 1; background: #27ae60; color: white; padding: 1.1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 3rem;">⚡</div>
<div style="font-weight: bold; font-size: 1.6rem; margin-top: 0.2rem;">Livrer vite</div>
<div style="font-size: 1.4rem; opacity: 0.9; margin-top: 0.3rem;">gain court terme</div>
</div>

<div style="font-size: 2rem; color: #888;">→</div>

<div style="flex: 1; background: #e8a838; color: white; padding: 1.1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 3rem;">💳</div>
<div style="font-weight: bold; font-size: 1.6rem; margin-top: 0.2rem;">Dette accumulée</div>
<div style="font-size: 1.4rem; opacity: 0.9; margin-top: 0.3rem;">coût caché</div>
</div>

<div style="font-size: 2rem; color: #888;">→</div>

<div style="flex: 1; background: #e74c3c; color: white; padding: 1.1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 3rem;">🐌</div>
<div style="font-weight: bold; font-size: 1.6rem; margin-top: 0.2rem;">Ralentissement</div>
<div style="font-size: 1.4rem; opacity: 0.9; margin-top: 0.3rem;">perte long terme</div>
</div>

</div>

<div style="margin: 1.2rem 0; font-size: 1.5rem; font-weight: bold;">
Quand la dette augmente :
</div>

<div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 1rem; margin-top: 0.6rem;">
<div style="background: #2c3e50; color: white; padding: 1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.2rem;">⏳</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem;">Les features sont plus lentes à livrer</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.2rem;">🐛</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem;">Les bugs se multiplient en production</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.2rem;">😩</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem;">L'équipe se sent démotivée</div>
</div>
<div style="background: #2c3e50; color: white; padding: 1rem 0.8rem; border-radius: 10px; text-align: center;">
<div style="font-size: 2.2rem;">💀</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem;">Le projet finit par mourir</div>
</div>
</div>

---

## 🛠️ Les 4 gestes de l'artisan du logiciel

<p style="font-size: 1.5rem; margin-top: -0.7rem;">
Derrière chaque pilier du module, un <b>geste métier</b> que pratique l'artisan, pas juste un outil technique.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">

<div style="background: #4a90d9; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">🔀 Laisser une trace</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9; font-style: italic;">Comme le menuisier qui date et signe ses ouvrages : on doit pouvoir revenir, comprendre, reprendre.</div>
<div style="margin-top: 0.5rem; font-size: 1.3rem; background: rgba(255,255,255,0.15); padding: 0.4rem 0.7rem; border-radius: 6px;">Git avancé, branches, PR, review <span style="opacity: 0.8;">→ TP1</span></div>
</div>

<div style="background: #27ae60; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">✅ Essayer avant de livrer</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9; font-style: italic;">Comme la table qu'on essaie sur l'établi avant de la remettre au client : l'outil doit fonctionner avant de quitter l'atelier.</div>
<div style="margin-top: 0.5rem; font-size: 1.3rem; background: rgba(255,255,255,0.15); padding: 0.4rem 0.7rem; border-radius: 6px;">TDD, RED-GREEN-REFACTOR <span style="opacity: 0.8;">→ TP2</span></div>
</div>

<div style="background: #e8a838; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">🥋 Répéter pour apprendre</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9; font-style: italic;">Comme l'apprenti qui refait cent fois le même geste : la main retient ce que la tête oublie.</div>
<div style="margin-top: 0.5rem; font-size: 1.3rem; background: rgba(255,255,255,0.15); padding: 0.4rem 0.7rem; border-radius: 6px;">Kata, pair programming, ping-pong <span style="opacity: 0.8;">→ TP3</span></div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">🧹 Entretenir ses outils</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9; font-style: italic;">Comme le chef qui aiguise ses couteaux en fin de service : demain on s'en resservira, autant qu'ils coupent.</div>
<div style="margin-top: 0.5rem; font-size: 1.3rem; background: rgba(255,255,255,0.15); padding: 0.4rem 0.7rem; border-radius: 6px;">Refactoring, code smells, Fowler <span style="opacity: 0.8;">→ TP4</span></div>
</div>

</div>

---

## 🧭 Pourquoi ce module compte tout de suite

<div style="background: #eef2f7; border-left: 6px solid #2c3e50; padding: 1.1rem 1.4rem; border-radius: 8px; margin-top: 1rem; font-size: 1.5rem;">
<b style="color: #2c3e50;">SAÉ 2.01 - Développement d'une application :</b>
Vous allez coder <b>en équipe</b>, <b>sur plusieurs semaines</b>, un projet réel. Les gestes de R2.03 - historique propre, tests, refactoring, review - y deviennent immédiatement utiles.
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin: 2rem 0;">
<div style="background: #4a90d9; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.2rem;">🔀</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;">Git</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.95;">pour collaborer sans se marcher dessus</div>
</div>
<div style="background: #27ae60; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.2rem;">✅</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;">Tests</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.95;">pour modifier sans paniquer</div>
</div>
<div style="background: #e74c3c; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.2rem;">🧹</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.3rem;">Refactoring</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.95;">pour garder le projet vivable</div>
</div>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2.2rem; vertical-align: middle; margin-right: 0.4rem;">🎯</span> Ce qu'on voit ici n'est pas "pour plus tard" : c'est ce qui rend un projet d'équipe tenable.
</div>

---

## 🎯 Compétences BUT visées

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois apprentissages critiques du <a href="https://cache.media.education.gouv.fr/file/SP4-MESRI-26-5-2022/14/6/spe617_annexe15_1426146.pdf" style="color: inherit;"><b>PN BUT Informatique 2022</b> (annexe 15)</a> sont couverts ici.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1rem;">

<div style="background: #4a90d9; color: white; padding: 1.4rem 1.2rem; border-radius: 12px;">
<div style="font-size: 2.4rem;">📐</div>
<div style="font-weight: bold; font-size: 2rem; margin-top: 0.2rem;">AC11.02</div>
<div style="font-size: 1.5rem; margin-top: 0.5rem; font-weight: bold;">Élaborer des conceptions simples</div>
<div style="margin-top: 0.7rem; font-size: 1.4rem; opacity: 0.9;">Compétence 1<br/><em>Développer des applications informatiques simples</em></div>
</div>

<div style="background: #27ae60; color: white; padding: 1.4rem 1.2rem; border-radius: 12px;">
<div style="font-size: 2.4rem;">🧪</div>
<div style="font-weight: bold; font-size: 2rem; margin-top: 0.2rem;">AC11.03</div>
<div style="font-size: 1.5rem; margin-top: 0.5rem; font-weight: bold;">Faire des essais et évaluer leurs résultats</div>
<div style="margin-top: 0.7rem; font-size: 1.4rem; opacity: 0.9;">Compétence 1<br/><em>Développer des applications informatiques simples</em></div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.4rem 1.2rem; border-radius: 12px;">
<div style="font-size: 2.4rem;">🔀</div>
<div style="font-weight: bold; font-size: 2rem; margin-top: 0.2rem;">AC15.02</div>
<div style="font-size: 1.5rem; margin-top: 0.5rem; font-weight: bold;">Mettre en place les outils de gestion de projet</div>
<div style="margin-top: 0.7rem; font-size: 1.4rem; opacity: 0.9;">Compétence 5<br/><em>Identifier les besoins métiers et techniques des clients</em></div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Mots-clés officiels du PN : <b>Qualité</b>, <b>Test</b>, <b>Gestion de version</b>. C'est exactement le coeur de ce module.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:50%](assets/git-archives.jpg)

# Partie 2 - Git professionnel

Retour aux bases, puis les concepts avancés qui changent la vie.

---

## 🔀 Ce que vous savez déjà (plus ou moins bien)

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Au S1, vous avez utilisé Git. Vérifiez avec moi :
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 0.8rem;">
<div style="background: #27ae60; color: white; padding: 1rem 1.2rem; border-radius: 12px; font-size: 1.5rem;">
<div style="font-size: 1.6rem; font-weight: bold;">✅ Je sais</div>
<ul style="margin: 0.4rem 0 0 0; padding-left: 1.2rem; line-height: 1.6;">
<li><code style="font-size: 0.95em;">git clone</code>, <code style="font-size: 0.95em;">add</code>, <code style="font-size: 0.95em;">commit</code>, <code style="font-size: 0.95em;">push</code></li>
<li>Créer une branche</li>
<li>Ouvrir un fork sur GitHub</li>
<li>😭 Pleurer quand un collègue écrase mes modifications</li>
<li>😭😭 Pleurer encore plus quand j'ai un conflit de fusion</li>
</ul>
</div>
<div style="background: #e74c3c; color: white; padding: 1rem 1.2rem; border-radius: 12px; font-size: 1.5rem;">
<div style="font-size: 1.6rem; font-weight: bold;">🤔 Je ne sais pas (encore)</div>
<ul style="margin: 0.4rem 0 0 0; padding-left: 1.2rem; line-height: 1.6;">
<li>Écrire un message de commit lisible 6 mois plus tard</li>
<li>Intégrer une branche proprement (rebase vs merge)</li>
<li>Rattraper un commit perdu sans paniquer</li>
<li>Relire sérieusement la PR d'un pair</li>
</ul>
</div>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.8rem 1.2rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
La moitié de ce TP1 corrige les mauvaises habitudes du S1. L'autre moitié, ce qui fait la différence en équipe.
</div>

---

## 🔀 Rappel express : le modèle Git

<div style="text-align: center; margin-top: 0.5rem;">
<img src="assets/git-model.svg" alt="Modèle Git : branches et commits" style="width: 50%;" />
</div>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Il vous suffit de retenir <b>3 concepts</b> pour suivre le reste du cours :
</p>

<div style="display: flex; gap: 1rem; margin-top: 2rem;">
<div style="background: #4a90d9; color: white; padding: 1rem 1.2rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2.2rem;">📸</div>
<div style="font-size: 1.5rem; font-weight: bold; margin-top: 0.2rem;">Commit</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9;">une photo du projet à un instant donné</div>
</div>
<div style="background: #27ae60; color: white; padding: 1rem 1.2rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2.2rem;">🌱</div>
<div style="font-size: 1.5rem; font-weight: bold; margin-top: 0.2rem;">Branche</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9;">une étiquette mobile qui avance avec vos commits</div>
</div>
<div style="background: #e8a838; color: white; padding: 1rem 1.2rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2.2rem;">📍</div>
<div style="font-size: 1.5rem; font-weight: bold; margin-top: 0.2rem;">HEAD</div>
<div style="font-size: 1.4rem; margin-top: 0.3rem; opacity: 0.9;">l'endroit où vous êtes en train de travailler</div>
</div>
</div>

---

## 📝 Pourquoi un bon message de commit ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le message que vous écrivez <b>aujourd'hui</b> sera relu par <b>quelqu'un d'autre</b> (ou vous-même) dans 6 mois, pour comprendre pourquoi telle ligne a été écrite.
</p>

<div style="display: flex; gap: 1.5rem; margin: 3rem 0;">

<div style="flex: 1; background: #e74c3c; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">🙅 Mauvais messages</div>
<pre style="background: transparent; padding: 0.5rem 0; font-size: 1.2rem; margin-top: 0.5rem; line-height: 1.6; color: white; border: none; box-shadow: none;">
wip
fix
trucs
ca marche enfin putain
update file</pre>
</div>

<div style="flex: 1; background: #27ae60; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">✅ Bons messages</div>
<pre style="background: transparent; padding: 0.5rem 0; font-size: 1.2rem; margin-top: 0.5rem; line-height: 1.6; color: white; border: none; box-shadow: none;">feat(auth): ajoute login via OAuth Google
fix(cart): corrige le total quand la remise est 0
docs(readme): detaille l'installation locale
refactor(facture): extrait appliquerTVA</pre>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2rem; vertical-align: middle; margin-right: 0.4rem;">🎯</span> Un message clair aujourd'hui = l'origine d'un bug est retrouvé en 30 secondes dans 6 mois.
</div>

---

## 📝 Le format Conventional Commits

<p style="font-size: 1.5rem; margin-top: -1.3rem;">
Un standard universel pour structurer vos messages et rendre votre historique lisible par tous.
</p>

<div style="text-align: center; margin-top: 1.2rem; background: #f5f7fa; border: 2px dashed #bdc3c7; padding: 1.2rem; border-radius: 10px; font-family: monospace; font-size: 1.6rem;">
<b>&lt;type&gt;</b>(<b>&lt;scope&gt;</b>) : <b>&lt;description&gt;</b>
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-top: 1.2rem;">

<div style="background: #4a90d9; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">✨</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">feat</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">nouvelle fonctionnalité</div>
</div>

<div style="background: #e74c3c; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">🐛</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">fix</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">correction de bug</div>
</div>

<div style="background: #17a2b8; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">📝</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">docs</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">documentation</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">♻️</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">refactor</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">réorganisation sans changer le comportement</div>
</div>

<div style="background: #27ae60; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">✅</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">test</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">ajout ou fix de tests</div>
</div>

<div style="background: #8e44ad; color: white; padding: 1.2rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 2.4rem;">🔧</div>
<div style="font-family: monospace; font-size: 1.6rem; font-weight: bold; margin-top: 0.3rem;">chore</div>
<div style="font-size: 1.4rem; opacity: 0.95; margin-top: 0.3rem;">maintenance, config, outils</div>
</div>

</div>

---

## 🔄 GitHub Flow : le workflow en 4 étapes

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Le workflow standard en équipe, proposé par <b>Scott Chacon</b> (GitHub, 2011). Simple : une seule branche de référence (<code>main</code>) et des branches éphémères par fonctionnalité.
</p>

<div style="display: flex; gap: 1rem; margin-top: 1rem;">
<div style="background: #4a90d9; color: white; padding: 0.9rem 0.6rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2rem;">🌱</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;">1. Branche</div>
<div style="font-size: 1.3rem; margin-top: 0.2rem; opacity: 0.9;">une par fonctionnalité</div>
</div>
<div style="background: #e8a838; color: white; padding: 0.9rem 0.6rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2rem;">📸</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;">2. Commits</div>
<div style="font-size: 1.3rem; margin-top: 0.2rem; opacity: 0.9;">atomiques + Conventional</div>
</div>
<div style="background: #8e44ad; color: white; padding: 0.9rem 0.6rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2rem;">🔍</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;">3. Pull Request</div>
<div style="font-size: 1.3rem; margin-top: 0.2rem; opacity: 0.9;">dès qu'on est prêt à montrer</div>
</div>
<div style="background: #27ae60; color: white; padding: 0.9rem 0.6rem; border-radius: 10px; flex: 1; text-align: center;">
<div style="font-size: 2rem;">✅</div>
<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;">4. Merge</div>
<div style="font-size: 1.3rem; margin-top: 0.2rem; opacity: 0.9;">après review</div>
</div>
</div>


<div style="text-align: center; margin-top: 0.8rem;">
<img src="assets/github-flow.svg" alt="GitHub Flow : main, feature branch, PR, review, merge" style="width: 55%;" />
</div>

<div style="margin-top: -1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2rem; vertical-align: middle; margin-right: 0.4rem;">🎯</span> Règle d'or : <b>jamais de commit direct sur <code>main</code></b>. Tout passe par une PR.
</div>

---

## 🔍 Pull Request : une conversation

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Une PR n'est pas un formulaire administratif. C'est une <b>invitation à discuter</b> du code que vous proposez d'intégrer à la branche <code>main</code>.
</p>

<div style="font-weight: bold; font-size: 1.5rem; margin-top: 1.2rem;">Ce qu'elle permet :</div>

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 1rem; margin-top: 0.6rem;">

<div style="background: #4a90d9; color: white; padding: 1.1rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 3.6rem;">🗣️</div>
<div style="font-weight: bold; font-size: 1.7rem; margin-top: 0.3rem;">Comprendre</div>
<div style="font-size: 1.5rem; opacity: 0.9; margin-top: 0.2rem;">votre intention</div>
</div>

<div style="background: #e8a838; color: white; padding: 1.1rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 3.6rem;">❓</div>
<div style="font-weight: bold; font-size: 1.7rem; margin-top: 0.3rem;">Questionner</div>
<div style="font-size: 1.5rem; opacity: 0.9; margin-top: 0.2rem;">vos choix de conception</div>
</div>

<div style="background: #17a2b8; color: white; padding: 1.1rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 3.6rem;">🤖</div>
<div style="font-weight: bold; font-size: 1.7rem; margin-top: 0.3rem;">Vérifier</div>
<div style="font-size: 1.5rem; opacity: 0.9; margin-top: 0.2rem;">tests, qualité, conventions</div>
</div>

<div style="background: #27ae60; color: white; padding: 1.1rem 1rem; border-radius: 12px; text-align: center;">
<div style="font-size: 3.6rem;">📝</div>
<div style="font-weight: bold; font-size: 1.7rem; margin-top: 0.3rem;">Documenter</div>
<div style="font-size: 1.5rem; opacity: 0.9; margin-top: 0.2rem;">l'historique des décisions</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2.6rem; vertical-align: middle; margin-right: 0.4rem;">💡</span> Une PR qui vaut le coup : <b>un diff ciblé qui se lit, un contexte qui se comprend</b>.
</div>

---

## 🔍 Comment faire une bonne review ?

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Reviewer, ce n'est pas dire "oui". C'est <b>lire le code avec les yeux d'un collègue dans 6 mois</b>, et mettre son nom en face de ce qui partira en prod.
</p>

<div style="display: flex; gap: 1.5rem; margin-top: 1rem; align-items: stretch;">

<div style="flex: 1; background: #8e44ad; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.6rem; font-weight: bold;"><span style="font-size: 2rem; vertical-align: middle; margin-right: 0.4rem;">✅</span> Checklist d'une bonne review</div>
<ul style="margin-top: 0.5rem; padding-left: 1.3rem; font-size: 1.3rem; line-height: 1.7;">
<li>Le code est-il <b>lisible</b> ?</li>
<li>Les <b>noms de variable</b> sont-ils parlants ?</li>
<li>Y a-t-il des <b>tests</b> ? Passent-ils ?</li>
<li>Pas de <code>TODO</code> / <code>FIXME</code> orphelins ?</li>
<li>La PR ne fait-elle qu'<em>une seule</em> chose ?</li>
</ul>
</div>

<div style="flex: 1; background: #e74c3c; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">
<div style="font-size: 1.6rem; font-weight: bold;"><span style="font-size: 2.6rem; vertical-align: middle; margin-right: 0.4rem;">🙅</span> Ce qui n'est PAS une review</div>
<ul style="margin-top: 0.5rem; padding-left: 1.3rem; font-size: 1.3rem; line-height: 1.7;">
<li><b>"LGTM"</b> sans lire le diff</li>
<li>Approuver <b>sans tester</b> la branche en local</li>
<li>Commenter les <b>fautes de frappe</b>, jamais le fond</li>
<li>Valider sans attendre <b>la validation du CI</b></li>
<li>Bloquer la PR sur un <b>détail subjectif</b> (style personnel)</li>
</ul>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2rem; vertical-align: middle; margin-right: 0.4rem;">🎯</span> Une bonne review prend <b>15 minutes</b>. Un bug en prod prend <b>15 heures</b>.
</div>

---

## 🤖 Review automatique par Copilot

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Dans vos Codespaces, <b>Copilot Code Review</b> peut commenter automatiquement une PR ouverte. Utile, mais ne remplace pas une vraie revue.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin-top: 1rem; align-items: stretch;">

<div style="background: #27ae60; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">

<div style="font-size: 1.4rem; font-weight: bold; margin-top: 0.2rem;"> <span style="font-size: 2.2rem;">👁️</span> Ce qu'il fait bien</div>
<ul style="margin-top: 0.5rem; padding-left: 1.3rem; font-size: 1.4rem; line-height: 1.7;">
<li>Détecter les fautes de frappe</li>
<li>Signaler les noms confus</li>
<li>Proposer des simplifications</li>
<li>Trouver des bugs</li>
</ul>
</div>

<div style="background: #e74c3c; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">

<div style="font-size: 1.4rem; font-weight: bold; margin-top: 0.2rem;"><span style="font-size: 2.2rem;">⚠️</span> Ses limites</div>
<ul style="margin-top: 0.5rem; padding-left: 1.3rem; font-size: 1.4rem; line-height: 1.7;">
<li>Ne comprend pas toujours l'intention métier</li>
<li>Peut suggérer des choses hors sujet</li>
<li>Peut <b>halluciner</b> un code faux qui semble bon</li>
<li>Ne peut pas trouver tous les bugs</li>
</ul>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
<span style="font-size: 2rem; vertical-align: middle; margin-right: 0.4rem;">💡</span> <b>Copilot suggère</b> mais c'est <b>un humain qui décide.</b> Une vraie review commence par comprendre l'intention du contributeur et de vérifier qu'elle est correctement mise en oeuvre dans le code.
</div>

---

<!-- _transition: fade -->

## 🔀 `git merge` — avant la fusion

<style scoped>
h2 { view-transition-name: titre-integration; }
.git-diagram img { view-transition-name: git-diagram; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Vos commits sur la branche <code>ma-feature</code> sont prêts à être partagés. Voici la première façons de les intégrer à la branche <code>main</code> : <code>git merge</code>.
</p>

<div class="git-diagram" style="text-align: center; margin-top: 3rem;">
<img src="assets/git-before.svg" alt="Situation initiale : main A-B-C, ma-feature avec D non fusionné" style="width: 55%; max-width: 550px;" />
</div>

<div style="margin-top: 4rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.4rem; text-align: center;">
<span style="font-size: 1.8rem; vertical-align: middle; margin-right: 0.4rem;">🕐</span> <b>Situation initiale</b> : la branche <code>main</code> continue d'avancer (commit C) pendant que la branche <code>ma-feature</code> travaille sur D puis sur E.
</div>

---

## 🔀 `git merge` — après la fusion

<style scoped>
h2 { view-transition-name: titre-integration; }
.git-diagram img { view-transition-name: git-diagram; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Vos commits sur la branche <code>ma-feature</code> sont prêts à être partagés. Voici la première façons de les intégrer à la branche <code>main</code> : <code>git merge</code>. Après cette opération un nouveau commit de merge fait la jointure entre les deux branches.
</p>

<div class="git-diagram" style="text-align: center; margin-top: 1rem;">
<img src="assets/git-merge.svg" alt="git merge : branche fusionnée via commit de merge M" style="width: 55%; max-width: 550px;" />
</div>

<div style="display: flex; gap: 1.5rem; margin-top: 1rem; align-items: stretch;">

<div style="flex: 1; background: #27ae60; color: white; padding: 1rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">✅ Avantages</div>
<ul style="margin-top: 0.4rem; padding-left: 1.2rem; font-size: 1.4rem; line-height: 1.6;">
<li>Préserve l'<b>historique réel</b> du travail</li>
<li>Les SHA des commits restent <b>stables</b> (partageables sans risque)</li>
</ul>
</div>

<div style="flex: 1; background: #e74c3c; color: white; padding: 1rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">⚠️ Inconvénients</div>
<ul style="margin-top: 0.4rem; padding-left: 1.2rem; font-size: 1.4rem; line-height: 1.6;">
<li>Crée un <b>commit de merge</b> en plus</li>
<li>Historique "<b>en arête de poisson</b>", plus difficile à relire</li>
</ul>
</div>

</div>

---

<!-- _transition: fade -->

## 🔀 `git rebase` — avant le rebase

<style scoped>
h2 { view-transition-name: titre-integration; }
.git-diagram img { view-transition-name: git-diagram; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Vos commits sur la branche <code>ma-feature</code> sont prêts à être partagés. Voici la seconde façons de les intégrer à la branche <code>main</code> : <code>git rebase</code>.
</p>

<div class="git-diagram" style="text-align: center; margin-top: 4rem;">
<img src="assets/git-before.svg" alt="Situation initiale : main A-B-C, ma-feature avec D" style="width: 55%; max-width: 550px;" />
</div>

<div style="margin-top: 2.2rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.4rem; text-align: center;">
<span style="font-size: 1.8rem; vertical-align: middle; margin-right: 0.4rem;">🕐</span> <b>Même situation initiale</b> : on part de <code>main</code> = A-B-C et <code>ma-feature</code> = D-E.
</div>

---

## 🔀 `git rebase` — après le rebase

<style scoped>
h2 { view-transition-name: titre-integration; }
.git-diagram img { view-transition-name: git-diagram; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Vos commits sur la branche <code>ma-feature</code> sont prêts à être partagés. Voici la seconde façons de les intégrer à la branche <code>main</code> : <code>git rebase</code>. Le rebase <b>rejoue</b> les commits D et E sur la pointe de <code>main</code>. D et E devienent D' et E' : même contenu, mais nouveau commit avec un nouveau SHA.
</p>

<div class="git-diagram" style="text-align: center; margin-top: 4rem;">
<img src="assets/git-rebase.svg" alt="git rebase : branche rejouée linéairement sur main" style="width: 55%; max-width: 550px;" />
</div>

<div style="display: flex; gap: 1.5rem; margin-top: 1rem; align-items: stretch;">

<div style="flex: 1; background: #27ae60; color: white; padding: 1rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">✅ Avantages</div>
<ul style="margin-top: 0.4rem; padding-left: 1.2rem; font-size: 1.4rem; line-height: 1.6;">
<li>Historique totalement <b>linéaire</b>, lisible comme une histoire</li>
<li>Pas de commit de merge parasite</li>
</ul>
</div>

<div style="flex: 1; background: #e74c3c; color: white; padding: 1rem 1.3rem; border-radius: 12px;">
<div style="font-size: 1.5rem; font-weight: bold;">⚠️ Inconvénients</div>
<ul style="margin-top: 0.4rem; padding-left: 1.2rem; font-size: 1.4rem; line-height: 1.6;">
<li><b>Réécrit les commits</b> : nouveaux SHA</li>
<li>Dangereux sur une branche <b>déjà partagée</b> avec d'autres</li>
</ul>
</div>

</div>

---

## ⚖️ La règle d'or pour choisir entre merge et rebase

<div style="background: #2c3e50; color: white; padding: 2rem; border-radius: 12px; text-align: center; font-size: 1.7rem; margin-top: 2rem;">
<b>Rebase</b> tes commits <b>tant que la branche n'est pas partagée </b>.<br/>
<b>Merge</b> dès qu'elle est <b>partagée</b> avec d'autres personnes.
</div>

<div style="margin-top: 1.5rem; font-size: 1.5rem; text-align: center;">
<b>Pourquoi ?</b> Le rebase <b>change les SHAs</b>. Si ton coéquipier a déjà basé du travail sur ta branche publique, ton rebase lui fait <b>perdre ses commits</b>.
</div>

<div style="display: flex; gap: 1.5rem; margin-top: 1.5rem; align-items: stretch;">
<div style="flex: 1; background: #27ae60; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">

<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;"><span style="font-size: 2rem;">✅</span> OK</div>
<div style="font-size: 1.4rem; margin-top: 0.4rem;">Je rebase ma branche personnelle <code>feat-login</code> avant de créer une PR.</div>
</div>
<div style="flex: 1; background: #e74c3c; color: white; padding: 1.2rem 1.4rem; border-radius: 12px;">

<div style="font-weight: bold; font-size: 1.5rem; margin-top: 0.2rem;"><span style="font-size: 2rem;">💀</span> Danger</div>
<div style="font-size: 1.4rem; margin-top: 0.4rem;">Je rebase <code>main</code> (partagée par toute l'équipe).</div>
</div>
</div>

---

## ✏️ Rebase interactif : nettoyer l'historique


<p style="font-size: 1.5rem;"><code>git rebase -i HEAD~3</code> ouvre un éditeur qui liste les 3 derniers commits, un par ligne, avec une action modifiable devant chacun.</p>

<div style="display: grid; grid-template-columns: 1.1fr 1fr; gap: 1.5rem; margin-top: 0.5rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; box-shadow: 0 2px 6px rgba(0,0,0,0.15);">
<div style="background: #2c3e50; color: #fff; padding: 0.4rem 1rem; font-size: 1.4rem; font-weight: bold; border-radius: 10px 10px 0 0;">📝 Éditeur ouvert par <code style="background:transparent;color:#fff;">rebase -i</code></div>
<pre style="background: #1e1e1e; color: #e8e8e8; margin: 0; padding: 0.8rem 1rem; font-size: 1.4rem; line-height: 1.35; border: none; box-shadow: none; font-family: 'Courier New', Consolas, monospace; white-space: pre; border-radius: 0 0 10px 10px;">pick a1b2c3 wip
pick d4e5f6 maj
pick g7h8i9 fix typo
&#35; Rebase ...
&#35; p, pick   = use commit
&#35; r, reword = edit message
&#35; s, squash = meld into previous
&#35; f, fixup  = like squash, no msg
&#35; d, drop   = remove commit</pre>
</div>

<div style="background: #fff; border: 2px solid #4a90d9; border-radius: 10px; overflow: hidden; display: flex; flex-direction: column;">
<div style="background: #4a90d9; color: #fff; padding: 0.4rem 1rem; font-size: 1.4rem; font-weight: bold;">🎯 3 actions utiles au quotidien</div>
<div style="padding: 0.8rem 1rem; font-size: 1.4rem; line-height: 1.6;">

- **`reword`** — corriger un message de commit
- **`squash`** / **`fixup`** — fusionner les petits commits de travail
- **`drop`** — retirer un commit indésirable

</div>
</div>

</div>

<div style="background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; margin-top: 1rem; text-align: center; font-size: 1.5rem;">
<b>reword</b> + <b>squash</b> + <b>drop</b> : 95% des cas d'usage.
</div>

---

## ✏️ Rebase interactif : exemple concret

<p style="font-size: 1.5rem;">Cinq commits de travail accumulés au fil de la journée, à fusionner en un seul commit propre prêt pour la PR.</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; align-items: stretch; margin: 3rem 0;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #e74c3c; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold;">🤦 Avant</div>
<pre style="background: #1e1e1e; color: #e8e8e8; margin: 0; padding: 0.8rem 1rem; font-size: 1.4rem; line-height: 1.4; border: none !important; box-shadow: none !important; border-radius: 0 !important; font-family: 'Courier New', Consolas, monospace; white-space: pre; flex: 1;">a1b2c3 wip
d4e5f6 maj
g7h8i9 fix typo
h1j2k3 oh j'avais oublié un test
m4n5o6 deuxième essai</pre>
<div style="background: #fdecea; padding: 0.9rem 1rem; font-size: 1.15rem;">L'historique est illisible. Que s'est-il vraiment passé ?</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #27ae60; color: #fff; padding: 0.5rem 1rem; font-size: 1.5rem; font-weight: bold;">🎯 Après rebase interactif</div>
<pre style="background: #1e1e1e; color: #e8e8e8; margin: 0; padding: 0.8rem 1rem; font-size: 1.4rem; line-height: 1.4; border: none !important; box-shadow: none !important; border-radius: 0 !important; font-family: 'Courier New', Consolas, monospace; white-space: pre-wrap; word-break: break-all; flex: 1;">x7y8z9 feat(auth): ajoute login OAuth Google</pre>
<div style="background: #e8f6ec; padding: 0.9rem 0.9rem; font-size: 1.15rem;">Le message est clair. On sait ce qui a été ajouté et <b>pourquoi</b>.</div>
</div>

</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Refaire son historique avant la PR, c'est un acte de <b>respect</b> envers le relecteur.
</div>

---

<!-- _transition: fade -->

## 🍒 `cherry-pick` — avant

<style scoped>
h2 { view-transition-name: titre-cherry; }
.git-diagram-cherry img { view-transition-name: git-diagram-cherry; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Sur une branche expérimentale <code>exp</code>, le commit <code>D</code> contient un correctif utile. Vous voulez <b>juste ce commit-là</b> sur <code>main</code>, sans embarquer <code>C</code> ni <code>E</code>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1.1fr; gap: 2rem; align-items: center; margin-top: 2rem;">

<div style="font-size: 1.5rem;">

**Le besoin :**

- Récupérer **uniquement D** sur `main`
- Laisser `C` et `E` sur `exp` (encore en cours)
- Sans `merge` (qui rapatrierait tout)
- Sans `rebase` (qui réécrirait `exp`)

</div>

<div class="git-diagram-cherry" style="text-align: center;">
<img src="assets/git-cherry-pick-before.svg" alt="Situation initiale : main A-B, exp C-D-E avec D mis en valeur" style="width: 100%; max-width: 500px;" />
</div>

</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 0.9rem 1.2rem; border-radius: 8px; font-size: 1.5rem; text-align: center;">
🕐 <b>Situation initiale</b> : <code>main</code> = A-B, <code>exp</code> = C-D-E.
</div>

---

## 🍒 `cherry-pick` — après

<style scoped>
h2 { view-transition-name: titre-cherry; }
.git-diagram-cherry img { view-transition-name: git-diagram-cherry; }
</style>

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
<code>cherry-pick</code> <b>copie</b> le commit <code>D</code> sur la pointe de <code>main</code>. Il devient <code>D'</code> : même contenu, mais nouveau commit avec un <b>nouveau SHA</b>.
</p>

<div style="display: grid; grid-template-columns: 1fr 1.1fr; gap: 2rem; align-items: center; margin-top: 2rem;">

<div>

<pre style="margin: 0; padding: 0.9rem 1.1rem; font-size: 1.5rem; line-height: 1.4; border: none !important; box-shadow: none !important; border-radius: 8px !important; font-family: 'Courier New', Consolas, monospace; white-space: pre;">git checkout main
git cherry-pick D</pre>

<div style="margin-top: 1rem; font-size: 1.5rem;">

`exp` reste **intacte** : C, D et E sont toujours là pour continuer la branche expérimentale plus tard.

</div>

</div>

<div class="git-diagram-cherry" style="text-align: center;">
<img src="assets/git-cherry-pick-after.svg" alt="git cherry-pick : commit D copié sur main en D'" style="width: 100%; max-width: 500px;" />
</div>

</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
⚠️ Cherry-pick <b>copie</b> le commit : vous récupérez l'idée, pas le même SHA.
</div>

---

## 🆘 Outil de secours : reflog

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Vous tapez <code>git reset --hard HEAD~5</code> et réalisez que vous venez d'effacer 5 commits. <b>Pas de panique</b> : Git garde une mémoire locale de tous vos déplacements.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin-top: 1.5rem; align-items: stretch;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #2c3e50; color: #fff; padding: 0.4rem 1rem; font-size: 1.5rem; font-weight: bold;">1️⃣ Lister les déplacements</div>
<pre style="background: #1e1e1e; color: #e8e8e8; margin: 0; padding: 0.8rem 1rem; font-size: 1.3rem; line-height: 1.4; border: none !important; box-shadow: none !important; border-radius: 0 !important; font-family: 'Courier New', Consolas, monospace; white-space: pre; flex: 1;">$ git reflog
a1b2c3 HEAD@{0}: reset: moving to HEAD~5
g7h8i9 HEAD@{1}: commit: feat: ajoute X  ← ici !
d4e5f6 HEAD@{2}: commit: wip
...</pre>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.18);">
<div style="background: #27ae60; color: #fff; padding: 0.4rem 1rem; font-size: 1.5rem; font-weight: bold;">2️⃣ Revenir au commit perdu</div>
<pre style="background: #1e1e1e; color: #e8e8e8; margin: 0; padding: 0.8rem 1rem; font-size: 1.3rem; line-height: 1.4; border: none !important; box-shadow: none !important; border-radius: 0 !important; font-family: 'Courier New', Consolas, monospace; white-space: pre; flex: 1;">$ git reset --hard g7h8i9
HEAD is now at g7h8i9 feat: ajoute X
✅ Vos commits sont récupérés.</pre>
</div>

</div>

<div style="margin-top: 1.5rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
<code>reflog</code> est votre <b>filet de sécurité</b> : tant qu'un commit a existé localement, il reste récupérable pendant ~30 jours.
</div>

---

## ⚠️ Commandes destructrices et leurs alternatives

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Certaines commandes Git détruisent du travail <b>sans demander confirmation</b>. Pour chacune, il existe une variante équivalente qui refuse d'écraser silencieusement.
</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; margin-top: 1.2rem;">

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.4rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">💀 Dangereux</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1;">
<code style="font-size: 1.3rem; color: #c0392b; font-weight: bold;">git reset --hard</code><br/>
<span style="font-size: 1.1rem;">Perd toutes les modifications non commitées.</span>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.4rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🛡️ Plus sûr</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1;">
<code style="font-size: 1.3rem; color: #1e8449; font-weight: bold;">git reset</code><br/>
<span style="font-size: 1.1rem;">Déstage sans toucher au contenu (mode <code>--mixed</code> par défaut).</span>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #e74c3c; color: #fff; padding: 0.4rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">💀 Dangereux</div>
<div style="background: #fdecea; padding: 0.9rem 1.1rem; flex: 1;">
<code style="font-size: 1.3rem; color: #c0392b; font-weight: bold;">git push --force</code><br/>
<span style="font-size: 1.1rem;">Écrase la branche distante, même si un collègue a poussé entre-temps.</span>
</div>
</div>

<div style="display: flex; flex-direction: column; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 6px rgba(0,0,0,0.12);">
<div style="background: #27ae60; color: #fff; padding: 0.4rem 1rem; font-size: 1.3rem; font-weight: bold; text-align: center;">🛡️ Plus sûr</div>
<div style="background: #e8f6ec; padding: 0.9rem 1.1rem; flex: 1;">
<code style="font-size: 1.3rem; color: #1e8449; font-weight: bold;">git push --force-with-lease</code><br/>
<span style="font-size: 1.1rem;">Refuse le push si quelqu'un a poussé entre-temps pour ne pas perdre son travail.</span>
</div>
</div>

</div>

<div style="margin-top: 1.2rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
Règle de survie : <b>privilégiez toujours la variante qui refuse d'écraser silencieusement</b>.
</div>

---

## 🎬 Démo live : rebase d'une branche sur main

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Cycle complet en direct : <b>brancher, commiter, rebaser, pousser sans casser le travail des autres</b>. Posez vos questions pendant la démo.
</p>

<div style="display: grid; grid-template-columns: repeat(2, 1fr); grid-template-rows: repeat(3, auto); grid-auto-flow: column; gap: 0.6rem 1.2rem; margin-top: 1rem;">

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">1</span>
<span>Clone <code>IUTInfoAix-R203/tp1</code> dans un Codespace</span>
</div>

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">2</span>
<span>Création de la branche <code>feat-exemple</code> + deux commits</span>
</div>

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">3</span>
<span>Deux commits sur <code>main</code> pour simuler le travail d'un collègue</span>
</div>

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">4</span>
<span>Rebase sur <code>main</code> : <code>git rebase origin/main</code></span>
</div>

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">5</span>
<span>Visualisation : <code>git log --oneline --graph --all</code></span>
</div>

<div style="display: flex; align-items: flex-start; gap: 0.7rem; font-size: 1.5rem;">
<span style="background: #4a90d9; color: #fff; width: 1.8rem; height: 1.8rem; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; font-weight: bold; flex-shrink: 0;">6</span>
<span>Push sécurisé : <code>git push --force-with-lease</code></span>
</div>

</div>

<div style="margin-top: 1.2rem; background: #fdecea; border: 2px solid #e74c3c; padding: 0.8rem 1.1rem; border-radius: 8px; font-size: 1.5rem;">
<b style="color: #c0392b;">⚠️ Mise en scène pédagogique</b> — je vais volontairement simuler un commit mal formé pour montrer comment le rebase interactif le corrige. <b>Ne reproduisez pas ce style en vrai.</b>
</div>

<div style="margin-top: 1rem; background: #2c3e50; color: white; padding: 1rem; border-radius: 8px; text-align: center; font-size: 1.5rem;">
👁️ Observez : l'historique de <code>main</code> reste <b>linéaire</b> et <b>lisible</b> avant et après le push.
</div>

---

## 🔗 De l'historique propre au code qui tient

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Git assure la <b>trace</b> propre de votre travail. Mais une belle histoire ne garantit pas que <b>le code actuel marche</b>. Il vous faut l'autre moitié du métier.
</p>

<div style="display: flex; align-items: stretch; justify-content: center; gap: 1.2rem; margin-top: 3rem;">

<div style="flex: 1; max-width: 320px; background: #4a90d9; color: white; padding: 1.5rem 1rem; border-radius: 14px; text-align: center; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="font-size: 3.5rem; line-height: 1;">🔀</div>
<div style="font-size: 1.8rem; font-weight: bold; margin-top: 0.5rem;">Git</div>
<div style="font-size: 1.2rem; opacity: 0.95; margin-top: 0.3rem;">la trace propre du travail</div>
</div>

<div style="display: flex; align-items: center; font-size: 3rem; color: #555; font-weight: bold;">+</div>

<div style="flex: 1; max-width: 320px; background: #27ae60; color: white; padding: 1.5rem 1rem; border-radius: 14px; text-align: center; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="font-size: 3.5rem; line-height: 1;">✅</div>
<div style="font-size: 1.8rem; font-weight: bold; margin-top: 0.5rem;">Tests</div>
<div style="font-size: 1.2rem; opacity: 0.95; margin-top: 0.3rem;">l'ouvrage qui tient</div>
</div>

<div style="display: flex; align-items: center; font-size: 3rem; color: #555; font-weight: bold;">=</div>

<div style="flex: 1.1; max-width: 360px; background: #e8a838; color: white; padding: 1.5rem 1rem; border-radius: 14px; text-align: center; box-shadow: 0 3px 8px rgba(0,0,0,0.15);">
<div style="font-size: 3.5rem; line-height: 1;">🔨</div>
<div style="font-size: 1.8rem; font-weight: bold; margin-top: 0.5rem;">Artisan</div>
<div style="font-size: 1.2rem; opacity: 0.95; margin-top: 0.3rem;">le geste complet</div>
</div>

</div>

<div style="margin-top: 3rem; background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center; font-size: 1.5rem;">
Vérifier son ouvrage <b>à chaque geste</b>, pas à la livraison. C'est là qu'intervient le <b>TDD</b>.
</div>

---

<!-- _class: lead -->
<!-- _header: "" -->
<!-- _footer: "" -->

![bg left:50%](assets/tdd-climbing.jpg)

# Partie 3 - Introduction au TDD

Quand tester un logiciel vous aidera à mieux le concevoir !

---

## 🐛 Le problème du code "ça marche sur ma machine"

<p style="font-size: 1.5rem; margin-top: -0.3rem;">
Trois situations qu'on a toutes et tous vécues, et qui ont <b>une seule cause profonde</b>.
</p>

<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-top: 1rem;">

<div style="background: #f9f5e8; border-left: 5px solid #e8a838; padding: 0.9rem 1rem; border-radius: 8px; font-size: 1.5rem;">
<div style="margin-top: 0.3rem;"><span style="font-size: 2rem; line-height: 1;">📦</span> Vous livrez un projet qui marchait chez vous, et il <b>plante</b> chez le prof.</div>
</div>

<div style="background: #f9f5e8; border-left: 5px solid #e8a838; padding: 0.9rem 1rem; border-radius: 8px; font-size: 1.5rem;">
<div style="margin-top: 0.3rem;"><span style="font-size: 2rem; line-height: 1;">🔄</span> Vous corrigez un bug et un <b>autre</b> que vous aviez résolu il y a 3 jours <b>réapparaît</b>.</div>
</div>

<div style="background: #f9f5e8; border-left: 5px solid #e8a838; padding: 0.9rem 1rem; border-radius: 8px; font-size: 1.5rem;">
<div style="margin-top: 0.3rem;"><span style="font-size: 2rem; line-height: 1;">😰</span> Vous modifiez une fonction en ayant <b>peur</b> que ça casse ailleurs.</div>
</div>

</div>

<div style="margin-top: 2rem; background: #2c3e50; color: white; padding: 1.2rem; border-radius: 10px; text-align: center; font-size: 1.5rem;">
La cause profonde : <b>aucun filet de sécurité</b> qui vous prévient quand vous cassez quelque chose, vous n'avez aucune assurance que votre logiciel continue à fonctionner comme attendu.
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

Au TP2, Copilot est configuré comme **tuteur TDD** : il peut aider à raisonner, mais pas court-circuiter la démarche.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
<div style="background: #27ae60; color: white; padding: 1rem; border-radius: 10px;">
<b>✅ Ce que Copilot fera</b>
<ul style="margin-top: 0.3rem;">
<li>Expliquer un concept TDD</li>
<li>Vous orienter vers la Javadoc</li>
<li>Vous aider à débloquer une impasse</li>
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
Copilot est un <b>tuteur</b> pendant les TP ; au contrôle, vos réflexes doivent être les vôtres.
</div>

---

<!-- _class: lead -->

# Ce qu'on fait maintenant

Le prochain cap est simple : mettre en pratique les deux moitiés du cours d'aujourd'hui.

**🔀 TP1 - Git avancé** (~2h, non noté)
Historique lisible, PR, review, intégration propre.

**✅ TP2 - TDD** (~4h, noté)
Cycle RED-GREEN-REFACTOR, fake-it, triangulation, ApprovalTests.

<div style="margin-top: 1rem; background: #fff8e1; border-left: 4px solid #e8a838; padding: 0.8rem 1rem; border-radius: 6px; font-size: 1rem;">
🎯 <b>Dès le prochain TP</b> : écrivez des commits relisibles, ouvrez une PR comme une vraie conversation, et laissez toujours un test vous dire quand vous avez cassé quelque chose.
</div>

<div style="margin-top: 1rem; text-align: center;">
👉 Lien Classroom : [github.com/IUTInfoAix-R203/tp](https://github.com/IUTInfoAix-R203/tp)
</div>

---

<!-- _class: lead -->

# À suivre : CM2 - TDD avancé et refactoring

On y approfondira le TDD, on découvrira les kata en pair programming, et on préparera le refactoring du TP4.
