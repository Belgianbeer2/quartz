----
type: fiche_emotion
---
# 🧠 Fiche d'exploration : La Réactance

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


## 🔬 0. Comprendre l'émotion

> [!abstract] Ce que Moukheiber éclaire — La confabulation
> La réactance est particulièrement piégeuse parce qu'elle **utilise le vocabulaire du jeu** pour habiller une impulsion émotionnelle. *"Les propriétés de cette main sont pas mal pour reprendre l'initiative"* ressemble à de l'analyse GTO. Mais la décision de jouer a été prise avant le raisonnement — le raisonnement est venu justifier après coup.
>
> C'est ce que Moukheiber appelle *confabuler* : construire une explication rationnelle a posteriori d'une décision déjà prise émotionnellement. La main n'est pas nécessairement mauvaise — c'est sa *source* qui l'est.

> [!abstract] Les 3 marqueurs qui distinguent une justification d'une analyse
>
> **1. La sélectivité**
> Une analyse considère toutes les propriétés — pour ET contre. Une justification ne convoque que les propriétés favorables. *"Pas mal pour reprendre l'initiative"* — mais les propriétés défavorables ont-elles été pesées au même titre ? Si non : c'est un avocat de la défense, pas un analyste.
>
> **2. Le sens de la causalité**
> Dans une analyse : j'évalue → je décide. Dans une justification : je décide → je trouve des raisons. Le *"je vais reprendre l'initiative"* précède la pensée sur les propriétés de la main — pas l'inverse.
>
> **3. La vitesse et la certitude**
> Une vraie analyse génère de l'incertitude — c'est son signe de bonne santé. Une justification est rapide et certaine, parce que la conclusion est déjà là avant que le raisonnement commence. Si la pensée est arrivée vite et sans doute juste après le bluff-catch — c'est le signal.

> [!abstract] Ce que Alexis pointe
> La réactance se diagnostique avec une seule question : *"Est-ce que je joue ce coup pour optimiser mon EV ou pour reprendre le contrôle ?"*
>
> Si c'est pour reprendre le contrôle — c'est de la réactance. Et une question de test complémentaire : *"Si cet adversaire n'avait pas été agressif juste avant, est-ce que cette main m'aurait semblé jouable de la même façon ?"* Si la réponse est non — c'est de la réactance, pas de la stratégie.
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Réactance*

---

## 📊 1. Patterns de l'émotion

> [!example] 1. Déclencheurs (Trigger)
> *Fréquence des faits bruts identifiés (In-game) :*
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> // Fonction récursive pour tout aspirer peu importe la profondeur
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

> [!example] 2. Pensées automatiques
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

> [!example] 3. Schémas comportementaux (Réactions)
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

> [!example] 4. Prix à payer
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
> > - [ ] [Prix à payer:: ]

## 🔍 2. Travail de fond (Vrai problème)

> [!example] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - 
> ### 2. Identification de l'Objet de l'émotion
> - 

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!example] Recentrage Stratégique
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
> > - [ ] [Plan d'action:: ]

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

## 📝 Notes de suivi & Coaching
-