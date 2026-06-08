----
type: fiche_emotion
---
# 🧠 Fiche d'exploration : Plénitude

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

> [!abstract] Ce que Moukheiber éclaire
> La plénitude est un **état**, pas une destination permanente. Le cerveau fonctionne autour d'une baseline émotionnelle — chercher à la maintenir indéfiniment est une quête contre la biologie. Elle a un pic, puis on revient à la moyenne. C'est pour ça que le prix à payer documenté (*"je peux être déçu si les résultats s'inversent"*) est réel et prévisible : pas un échec, un retour mécanique à la baseline.
>
> Sa valeur n'est pas dans sa durée — c'est dans ce qu'elle **révèle** : fold facilement sur les lignes difficiles, pas de précipitation, lâcher prise sur le FOMO du leaderboard. Ces comportements sont des données sur le meilleur jeu possible — pas un état à préserver.

> [!abstract] Ce que Alexis pointe — La double fonction
> La plénitude a deux usages distincts :
>
> **En session :** ancrer. Documenter les *comportements* (pas l'état) : *"Qu'est-ce que je fais concrètement quand je suis en plénitude ?"* → ce sont les données qui alimentent les futures reconvocations du Stratège.
>
> **Post-session difficile :** contrebalancer. Les sessions en plénitude sont la **preuve datée que le Stratège existe et est accessible**. Quand la honte dit *"tu n'es pas cette personne"* — les sessions en plénitude disent le contraire, avec date et métriques.
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Plénitude*

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

> [!example] 4. Prix à payer de continuer la session
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
.