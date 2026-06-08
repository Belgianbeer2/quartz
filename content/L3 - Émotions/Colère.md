---
type: fiche_emotion
---
# 🧠 Fiche d'exploration : Colère

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


## 📊 1. Patterns de l'émotion

> [!danger] 1. Déclencheurs (Trigger)
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

> [!danger] 2. Pensées automatiques
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

> [!danger] 3. Schémas comportementaux (Réactions)
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

> [!danger] 4. Prix à payer
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

> [!danger] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - 
> ### 2. Identification de l'Objet de l'émotion
> - 

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!danger] Recentrage Stratégique
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
> > - [ ] [Plan d'action:: test]
> > - [ ] 

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
à implémenter dans la session du [[(03-30-2026) Feedback - finesse technique et lucidité ingame]]

> [!example] *Cartographie émotionnelle & Action* 
> *💡 Raccourcis : Colère, Frustration, Doute, Dépis , Sur-confiance, Certitude.*
> *(Note : Tu peux en taper de nouvelles, elles s'ajouteront automatiquement au Dashboard !)*
> 
> **Émotions & Fondements**
>  - [emotion:: Colère] ➡️ [fondement:: perfectionnisme]
>  - [emotion:: Colère] ➡️ [fondement:: refus de l'erreur]
>  - [emotion:: Colère] ➡️ [fondement:: intransigeance]
>  - [emotion:: Colère] ➡️ [fondement::exemplarité]
>
> **Plan d'action**
> > - [ ] ➡️[Plan d'action:: relecture des prix à payer]
> > - [ ] ➡️[Plan d'action:: faire un travail de fond mindset à chaud]
> 
> **Prix à payer**
> > - [ ] ➡️[Prix à payer:: arrêter la session et être frusté de ne pas faire de la performance]
> > - [ ] ➡️[Prix à payer:: passer par un inconfort physiologique important]
> 
> **J'accepte ?**
> - [ ] ✅ Oui 
> - [x] ❌ Non