---
type: fiche_emotion
tags:
  - émotion
  - délaissement
  - appartenance
  - inner-mapping
---
# 🧠 Fiche d'exploration : Délaissement

> **Distinct de :**
> - *Solitude* — absence de lien. Ici le lien existe, mais on est à sa périphérie.
> - *Abandon* — rupture totale. Ici c'est le *sidelining* — présent mais mis sur le carreau.
> - *Rejet* — exclusion active. Ici c'est souvent passif, non intentionnel — ce qui le rend plus insidieux.
>
> **Déclencheur type :** le "vu" sans réponse dans le chan familial après un message qui cherchait une interaction. Être vu, exactement — et rien.

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p = dv.current();
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.emotion).includes(p.file.name));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[emotion:: Délaissement]`*");
> ```

---

## 🔬 0. Comprendre l'émotion

> [!abstract] Ce que la recherche éclaire
> **[documenté — Williams 2001]** L'ostracisme social — être ignoré ou exclu même brièvement — active les mêmes zones cérébrales que la douleur physique. Le "vu" sans réponse est une micro-forme d'ostracisme : la présence est reconnue, la connexion refusée. L'effet est mesurable en quelques secondes.
>
> Ce qui le rend particulièrement douloureux : c'est *non intentionnel* dans la majorité des cas. La personne qui envoie le "vu" n'a probablement pas pensé à blesser. Le cerveau, lui, traite ça comme un signal social négatif — indépendamment de l'intention.

> [!abstract] Lecture LFB — affect vs émotion
> **[documenté — Barrett 2017]** Le même signal (pas de réponse dans un groupe familial) peut construire des émotions très différentes selon le concept appliqué : *"ils sont occupés"* vs *"je suis mis sur le carreau"* vs *"je suis à la périphérie"*. La précision du nommage — **délaissement** plutôt qu'abandon — change le plan d'action que le cerveau génère.

> [!abstract] Ce que Alexis pointe — Besoin d'Appartenance
> Le délaissement est le signal direct que le **besoin d'appartenance** (SDT — Deci & Ryan) est entravé dans ce contexte précis. Non pas dans toutes les relations — mais dans ce groupe spécifique, depuis cette position géographique (Cambodge / Europe).
>
> L'entrave est **structurelle** autant qu'émotionnelle : la distance rend la connexion spontanée difficile. Ce n'est pas un jugement sur la relation — c'est une contrainte réelle.
>
> *→ Voir :* [[L1 — Structures profondes/03 — Besoin d'Appartenance]]

---

## 📊 1. Patterns de l'émotion

> [!info] 1. Déclencheurs (Trigger)
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.declencheur).forEach(i => { let v = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur documenté.*");
> ```

> [!info] 2. Pensées automatiques
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.pensee).forEach(i => { let v = Array.isArray(i.pensee) ? i.pensee : [i.pensee]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) sorted.forEach(e => dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!info] 3. Réactions
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.reaction).forEach(i => { let v = Array.isArray(i.reaction) ? i.reaction : [i.reaction]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!info] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let ingame = dv.array(desc).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: J'accepte que la distance crée une asymétrie réelle dans les échanges — ce n'est pas un jugement sur la relation]
> > - [ ] [Prix à payer:: J'accepte que le "vu" n'est probablement pas intentionnel — c'est de l'inattention, pas du rejet]
> > - [ ] [Prix à payer:: Je me permets de nommer le délaissement sans en faire une conclusion sur ma place dans la famille]

---

## 🔍 2. Travail de fond

> [!info] Analyse à froid
>
> ### Ce qui se passe réellement
> - **L2 Mentalisation -- Dissociation** : le "vu" est interprété comme rejet intentionnel — alors que c'est probablement de l'inattention. L'observateur est fantasmé dans sa réaction.
> - **L2 Évaluation causale -- Confabulation** : sélection des données qui confirment (*"ils s'envoient des photos entre eux"*) pour construire un récit cohérent depuis l'état émotionnel présent.
>
> ### Ce qui est réel vs construit
> **Réel :** La distance (Cambodge / Europe) crée une asymétrie structurelle dans les échanges spontanés. C'est une contrainte concrète, pas une mesure de la valeur de la relation.
>
> **Construit :** *"Je suis mis sur le carreau"* comme conclusion permanente depuis un événement ponctuel. La question sur le parrainage (*"pourquoi je suis parrain si..."*) est construite depuis cet état — pas depuis une analyse froide de la relation.

---

## 🛡️ 3. Protocole de Recentrage

> [!info] Recentrage Stratégique
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let ingame = dv.array(desc).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action
> > - [ ] [Plan d'action:: Nommer l'émotion précisément — délaissement, pas abandon]
> > - [ ] [Plan d'action:: Identifier le L2 actif — Dissociation ou Confabulation ?]
> > - [ ] [Plan d'action:: Distinguer la contrainte structurelle (distance) du jugement relationnel (je ne compte pas)]
> > - [ ] [Plan d'action:: Résister à la stratégie de l'autruche — le retrait amplifie le délaissement]

---

## 🗄️ Archives

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let archives = dv.array([...desc, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let archives = dv.array([...desc, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

---

## 📝 Notes

- *L2 liés :* [[Mentalisation -- Dissociation]] · [[Évaluation causale -- Confabulation]]
- *L3 secondaires :* [[Colère_IRL]] · [[Impuissance]]
- *L1 entravé :* [[L1 — Structures profondes/03 — Besoin d'Appartenance]]
- *Comportement associé :* stratégie de l'autruche (L4)
