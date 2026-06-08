----
type: fiche_emotion
---
# 🧠 Fiche d'exploration : La Honte

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

> [!abstract] Honte vs Culpabilité — La distinction clinique fondamentale
> 
> La **culpabilité** et la **honte** sont souvent confondues, mais ciblent des niveaux radicalement différents de l'expérience :
> 
> | | **Culpabilité** | **Honte** |
> |---|---|---|
> | **Objet** | Un comportement spécifique | Le Soi global |
> | **Message interne** | *"J'ai mal fait X"* | *"Je SUIS défaillant"* |
> | **Impulsion** | Réparer, corriger | Se cacher, se retirer |
> | **Effet sur l'action** | Motivant | Paralysant |
> | **Signal post-session** | Envie de corriger | Retrait, faible énergie, évitement |
> 
> *Tangney & Dearing, 2002 — Shame and Guilt in Interpersonal Relationships*
> 
> → La honte explique pourquoi une mauvaise session peut générer une journée entière de retrait — là où la culpabilité seule pousserait à se remettre en mouvement.

> [!abstract] La Trahison de Soi — variante distincte
> 
> Il existe une forme particulière de honte liée à la **violation d'un engagement personnel** : la **trahison de soi**.
> 
> Elle émerge quand on brise une promesse faite à soi-même — non par rapport à une norme externe ou à autrui, mais par rapport à **sa propre parole**.
> 
> Son message intérieur : *"Si je n'arrive même pas à tenir ce que je me dis à moi-même... suis-je fiable en tant qu'agent de mes propres décisions ?"*
> 
> **Pourquoi c'est particulièrement actif dans ce système :**
> Le warmup est un **rituel d'engagement**. Le `[x] OUI` à *"Suis-je prêt à jouer ?"* est une promesse. Chaque fois que le comportement in-game s'éloigne de l'intention du warmup, la trahison de soi peut s'activer — indépendamment du résultat financier.
> 
> *Kernis & Goldman, 2006 — Authenticity and self-discrepancy*

> [!abstract] Ce que ce n'est PAS — La distinction qui change tout
> 
> L'**écart idéal-réel** est une **information** : où j'en suis dans ma construction identitaire.
> 
> La **honte** est une **réaction émotionnelle** à cet écart — une réaction qui déforme l'information et bloque l'action.
> 
> L'écart est réel et utile. La honte qui l'enveloppe est un parasite qui l'amplifie.
> 
> *→ Le travail n'est pas de supprimer l'écart. C'est de séparer l'information de la réaction émotionnelle pour voir clairement ce qu'elle dit.*
> 
> **Conséquence directe sur le warmup :**
> Une intention orientée sur le **faire idéal** crée un standard binaire : tenu / pas tenu.
> Une intention orientée sur l'**être** ne peut pas être ratée — même un seul instant de reconvocation in-game est un millimètre vers ce qu'on construit.

---


> [!abstract] Le paradoxe libérateur — et la session du 28-05
> La session du 28-05 (-$1432) illustre exactement le mécanisme : ce n'est pas la perte financière qui a causé le retrait du 29/05 — c'est la honte d'avoir dévié de l'intention du warmup. Le *remembering self* a reconstruit toute la session comme un échec d'identité, en effaçant les moments où le Stratège était présent : relire les documents plusieurs fois in-game, rester focalisé après les mains difficiles, lâcher prise sur les pertes en review.
>
> Le paradoxe : **reconnaître l'écart, c'est le Stratège qui regarde.** Si tu vois que tu n'étais pas le Stratège — c'est lui qui a vu. Tu n'aurais pas pu nommer l'écart si l'identité n'était pas déjà là pour le mesurer.
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Honte*

---

## 📊 1. Patterns de l'émotion

> [!abstract] 1. Déclencheurs (Trigger)
> *Fréquence des faits bruts identifiés (In-game) :*
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
> 
> dv.array(descendants).where(d => d.declencheur).forEach(i => { 
>     let vals = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur identifié.*");
> ```

> [!abstract] 2. Pensées automatiques
> *Fréquence des histoires mentales récurrentes :*
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
> 
> dv.array(descendants).where(d => d.pensee).forEach(i => { 
>     let vals = Array.isArray(i.pensee) ? i.pensee : [i.pensee];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) {
>     sorted.forEach(e => { dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`); });
> } else {
>     dv.paragraph("*Aucune pensée enregistrée.*");
> }
> ```

> [!abstract] 3. Schémas comportementaux (Réactions)
> *Fréquence des réactions identifiées :*
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
> 
> dv.array(descendants).where(d => d.reaction).forEach(i => { 
>     let vals = Array.isArray(i.reaction) ? i.reaction : [i.reaction];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction identifiée.*");
> ```

> [!abstract] 4. Prix à payer
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
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix à payer actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer à froid
> > - [ ] [Prix à payer:: J'accepte que l'écart entre mon intention de warmup et mon comportement in-game est une information sur ma construction — pas un verdict sur mon identité]
> > - [ ] [Prix à payer:: J'accepte que ressentir de la honte post-session ne signifie pas que je suis la honte]
> > - [ ] [Prix à payer:: J'accepte que le lendemain d'une session difficile, le retrait et la faible énergie sont des signaux de honte à nommer — pas des vérités définitives sur mes capacités]

---

## 🔍 2. Travail de fond (Vrai problème)

> [!abstract] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - L'intention de session orientée sur le **faire idéal** crée un standard binaire implicite : tenu / pas tenu. Ne pas le tenir active la honte.
> - Plus l'intention est haute (idéale, orientée vers le Stratège parfait), plus l'écart potentiel est grand — et plus la honte est intense quand la session dévie.
> - Quand le warmup devient un **contrat à honorer** plutôt qu'un **compas d'orientation**, il génère la trahison de soi si le comportement in-game s'en éloigne.
> 
> ### 2. Identification de l'Objet de l'émotion
> - L'objet n'est pas la session ni le résultat financier. L'objet est **l'image de soi comme Stratège de la performance durable**.
> - In-game, ne pas respecter son sens de session = evidence perçue que *"je ne suis pas encore cette personne."*
> - La correction structurelle : reformuler l'intention sur l'**être** (pas le faire) supprime le carburant principal de la honte.

---

## 🛡️ 3. Protocole de Recentrage : Plans d'action adaptés

> [!abstract] Recentrage Stratégique
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
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan d'action actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action à froid
> > - [ ] [Plan d'action:: Quand la honte fire in-game (je réalise que j'ai dévié de mon intention) : nommer ("honte") → demander "qui est-ce que je veux être dans les 5 prochaines minutes ?" — pas "comment je rattrape mon intention initiale ?"]
> > - [ ] [Plan d'action:: Reformuler les intentions de warmup sur l'être, pas le faire, pour retirer le carburant de la honte avant même de lancer les tables]
> > - [ ] [Plan d'action:: Le lendemain d'une session difficile : si je suis en retrait, nommer que c'est un signal de honte — pas une vérité sur mes capacités. Une petite action concrète pour remonter sur le cheval.]

---

## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
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
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
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
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

---

## 📝 Notes de suivi & Coaching
- *Fiche créée le 30-05-2026 — Origine : session 2 du 28-05-2026 (-$1432). Honte post-session (retrait le 29/05 — off complet, faible énergie, humeur basse, pas de performance). Call Alexis 29-05-2026 : identification du schéma FAIRE vs ÊTRE comme carburant structurel de la honte.*
- *Lien direct : [[00 — Protocole In-Game]] — Bloc 2 mis à jour avec le signal Honte / Trahison de soi*
- *Lien direct : [[00_Warmup]] — Prix à payer récurrents mis à jour*
