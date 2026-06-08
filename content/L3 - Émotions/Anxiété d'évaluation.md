---
type: fiche_emotion
tags:
  - anxiété
  - évaluation
  - regard-autrui
  - performance
  - émotions
---

# 🧠 Fiche d'exploration : Anxiété d'évaluation

> [!note]- 📜 Voir les sessions liées à cette émotion
> *Cliquez sur une session pour ouvrir le feedback correspondant.*
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> 
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const emotionsDansSession = page.file.lists.emotion;
>         return dv.array(emotionsDansSession).includes(targetEmotion);
>     });
> 
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```

---

## 🔬 0. Comprendre l'émotion

> [!abstract] Définition
>
> L'anxiété d'évaluation est la forme d'anxiété déclenchée par la **perception d'être observé et jugé par un observateur compétent**. Elle est orientée vers l'avenir : elle anticipe un jugement négatif, une exploitation, une perte de statut ou de réputation dans le regard de quelqu'un qui a les capacités de nous évaluer.
>
> Elle se distingue des autres formes d'anxiété par son objet spécifique : ce n'est pas une menace financière, physique ou existentielle — c'est une menace sur **l'image de soi dans le regard d'un pair qualifié**.

> [!abstract] Son véhicule cognitif : la Dissociation
>
> L'anxiété d'évaluation ne se ressent pas toujours directement. Elle transite souvent par le pattern cognitif de la **Dissociation** — la projection dans la tête de l'observateur, la construction de ce qu'il pense, l'ajustement comportemental en réponse à ce modèle imaginé.
>
> **[documenté — observation personnelle]** Dans les trois formes identifiées, l'émotion sous-jacente est la même : anticiper un jugement de compétence par un pair.
>
> *→ Voir :* [[Dissociation]] *— pattern cognitif véhiculant cette émotion*

> [!abstract] Ce que Moukheiber éclaire
>
> **[inféré de son cadre]** Si l'identité se construit socialement, alors le regard des pairs compétents a un poids particulier dans cette construction. L'anxiété d'évaluation est la réponse émotionnelle au risque de voir cette construction fragilisée — être "vu" comme moins compétent qu'on ne se perçoit, par quelqu'un qui a les moyens de l'évaluer correctement.
>
> **[inféré de son cadre]** L'observateur fantasmé (le reg multi-tableur qui n'a pas vu la main) est la version pathologique de ce mécanisme social normal : le cerveau continue de gérer le risque évaluatif même quand l'observateur n'est pas réellement en train d'observer.

> [!abstract] Ce que Alexis pointe
>
> **[inféré de son cadre]** L'anxiété d'évaluation est incompatible avec "être avant d'agir" : quand elle est active, on agit *pour* une image projetée plutôt que *depuis* son identité. Le Stratège joue depuis lui-même — l'anxiété d'évaluation fait jouer depuis le regard imaginé d'un adversaire compétent.
>
> **[extrapolé — à valider avec Alexis]** Le travail de fond sur cette émotion passe probablement par le renforcement de la certitude identitaire : plus le Stratège est solidement construit et accessible, moins le regard extérieur — réel ou fantasmé — peut déstabiliser le jeu.

---

## 📊 1. Patterns de l'émotion

> [!note] 1. Déclencheurs (Trigger)
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
>
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
>
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.declencheur).forEach(i => {
>     let vals = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur identifié.*");
> ```
>
> > [!note]- Déclencheurs documentés (hors session)
> > - Identification d'un reg compétent à la table *(in-game)*
> > - Présence d'un observateur perçu comme qualifié pour évaluer *(IRL — scooter Siem Reap)*
> > - Bluff créatif amené au showdown en présence d'un reg *(in-game)*
> > - Play créatif dans un pot où le reg est spectateur *(in-game)*

> [!note] 2. Pensées automatiques
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
>
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
>
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.pensee).forEach(i => {
>     let vals = Array.isArray(i.pensee) ? i.pensee : [i.pensee];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) {
>     sorted.forEach(e => { dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`); });
> } else {
>     dv.paragraph("*Aucune pensée enregistrée.*");
> }
> ```

> [!note] 3. Schémas comportementaux (Réactions)
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
>
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
>
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.reaction).forEach(i => {
>     let vals = Array.isArray(i.reaction) ? i.reaction : [i.reaction];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction identifiée.*");
> ```
>
> > [!note]- Réactions documentées (hors session)
> > - Ajustement anticipatoire de la stratégie avant toute main contre le reg *(in-game)*
> > - Modélisation des conclusions du reg depuis un pot où il n'est pas impliqué *(in-game)*
> > - Conduire plus vite en scooter devant des touristes perçus comme observateurs *(IRL)*

> [!note] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
>
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
>
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix à payer actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer à froid
> > - [ ] [Prix à payer:: J'accepte de jouer contre un adversaire imaginaire plutôt que contre la main devant moi]
> > - [ ] [Prix à payer:: J'accepte que mes fréquences soient distordues par une menace qui n'existe probablement pas]

---

## 🔍 2. Travail de fond (Vrai problème)

> [!note] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - L'anxiété d'évaluation s'active sur la perception d'un observateur **compétent** — pas n'importe quel regard, mais un regard qualifié pour détecter les failles.
> - **[observation personnelle]** L'observateur est souvent fantasmé : le reg multi-table et n'a probablement pas vu la main. Le touriste regardait peut-être ailleurs. L'émotion tourne sans ancrage réel.
>
> ### 2. Identification de l'objet de l'émotion
> - L'objet n'est pas la perte financière ni la défaite technique. L'objet est **l'image de soi comme joueur compétent dans le regard d'un pair qualifié**.
> - In-game, elle produit des décisions orientées vers la gestion de cette image plutôt que vers l'EV optimal.

---

## 🛡️ 3. Protocole de Recentrage

> [!note] Recentrage Stratégique
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
>
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
>
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan d'action actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action à froid
> > - [ ] [Plan d'action:: Question de réalité — est-il seulement dans ce pot ? Si non : observateur fantasmé. Si oui : combien de tables joue-t-il ? Si plus de 4 : il n'a probablement pas traité cette main.]
> > - [ ] [Plan d'action:: Nommer l'émotion : "anxiété d'évaluation" — puis demander "depuis qui est-ce que je joue ce coup ?"]

---

## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

---

## 📝 Notes de suivi & Coaching
- *Fiche créée le 04-06-2026 — Identifiée comme émotion sous-jacente au pattern Dissociation.*
- *Lien direct :* [[Dissociation]] *— pattern cognitif véhiculant cette émotion*
- *Lien direct :* [[Anxiété]] *— index des formes d'anxiété documentées*

---

## 📎 Sources

[^1]: Observation personnelle documentée le 04-06-2026. Voir aussi [[Dissociation]] pour les exemples détaillés.
