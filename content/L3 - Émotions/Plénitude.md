---
type: fiche_emotion
tags: [L3, émotion, plénitude, inner-mapping]
L3_nom: "Plénitude"
L3_valence: "positive"
L3_arousal: "moyenne-haute"
BIS_BAS: "BAS↑ BIS↓"
L1_déclencheurs: ["Tous les L1 générateurs actifs"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Analyse fondée]]", "[[05 — Évaluation du soi -- Évaluation graduée]]"]
L4_comportements: ["Fold facile · Décisions libres · Lâcher prise FOMO · Engagement depuis soi"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# ✨ Plénitude

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Plénitude]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · Moukheiber (2026) · [[Fondements théoriques/03 — Cerveau prédictif]] · [[Sources/01 — Albert Moukheiber × Les Lueurs]]
> La Plénitude est un **état**, pas une destination permanente. Le cerveau fonctionne autour d'une baseline — chercher à la maintenir indéfiniment est contre la biologie. Elle a un pic, puis on revient à la moyenne. Sa valeur n'est pas dans sa durée — c'est dans ce qu'elle **révèle** : fold facilement sur les lignes difficiles, pas de précipitation, lâcher prise sur le FOMO du leaderboard. Ces comportements sont les données sur le meilleur jeu possible. [documenté — Moukheiber 2026]

> [!abstract] La double fonction [documenté — Alexis]
> **En session :** ancrer. Documenter les *comportements* (pas l'état) : *"Qu'est-ce que je fais concrètement quand je suis en plénitude ?"* → données qui alimentent les reconvocations du Stratège.
>
> **Post-session difficile :** contrebalancer. Les sessions en plénitude sont la **preuve datée que le Stratège existe et est accessible**. Quand la honte dit *"tu n'es pas cette personne"* — les sessions en plénitude disent le contraire.

**Valence :** positive
**Arousal :** moyenne-haute — présence active et engagée
**Action tendency :** jouer depuis soi · fold facile · décisions libres · lâcher prise

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — aucune menace détectée
- **BAS :** ↑ actif — engagement depuis l'identité, pas de l'anxiété
- **Combinaison :** Stratège actif — configuration optimale

**Distinction des émotions proches :**
vs **[[Certitude]]** : la Certitude est plus ciblée (une décision). La Plénitude est plus diffuse (un état de session entier).
vs **[[Satisfaction]]** : la Satisfaction est post-effort (boucle fermée). La Plénitude est dans le mouvement lui-même.
vs **[[Sérénité]]** : la Sérénité a une arousal très basse. La Plénitude est plus active.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!success] Signaux corporels
> - **Zone de sensation :** légèreté générale · chaleur diffuse dans la poitrine · corps ouvert
> - **Rythme cardiaque :** régulier · stable · pas accéléré
> - **Respiration :** profonde · régulière · naturelle
> - **Posture spontanée :** corps ouvert · épaules en arrière · regard stable et direct
> - **Sensations spécifiques :** *"présence totale + absence de résistance"* · le cerveau n'est pas en train de prouver ou de combattre

> [!success] Signaux cognitifs précoces
> - *"Je joue depuis moi"* / *"Je veux jouer cette main"*
> - Les fold difficiles semblent faciles
> - Pas de questionnement sur l'image projetée

> [!success] Signaux comportementaux précoces
> - Fold facile sur les lignes difficiles
> - Pas de précipitation sur les timebanks
> - Lâcher prise sur le FOMO du leaderboard

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Tous les L1 | Tous les besoins fondamentaux satisfaits → Plénitude · engagement depuis l'identité |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Mastery thinking** : permet la Plénitude stable. Jouer depuis ce qu'on construit, pas de ce qu'on prouve.
- **Entity thinking** : transforme la Plénitude en Piédestal. *"Aujourd'hui je suis en forme — je dois saisir ça."*

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Analyse fondée (L2/02 générateur) | Décisions depuis l'évaluation → Plénitude |
| Évaluation graduée (L2/05 générateur) | Absence de verdict binaire → liberté d'action → Plénitude |

#### L0 — Influence

Budget satisfait = condition quasi-nécessaire. La Plénitude peut nourrir L0 en retour (fermeture de boucles).

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget satisfait = condition de la Plénitude |
| **L3 → L0** | ascendant ✅ | Légèrement restauratrice — moins de coût de décision, pas de tension |
| **L1 → L3** | descendant | Tous les L1 générateurs |
| **L3 → L1** | ascendant ✅ | Renforce tous les L1 générateurs silencieusement |
| **L2 → L3** | descendant | Analyse fondée · Évaluation graduée |
| **L3 → L2** | ascendant ✅ | Réduit la probabilité d'activation de tous les L2 défensifs |
| **L3 → L4** | descendant | Fold facile · décisions libres · engagement depuis soi |
| **L4 → L3** | ascendant ✅ | Les comportements du Stratège documentés alimentent les reconvocations futures |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

> La Plénitude est un état à **cultiver et protéger**, pas à réguler.

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Créer les conditions : L0 satisfait + warmup ancré avant de lancer |
| 2 · Modification | oui | Si Piédestal détecté : nommer avant que l'enjeu monte |
| 3 · Attentionnel | oui | *"Je joue depuis moi — pas pour l'image de cette forme"* |
| 4 · Reappraisal | oui | Si Piédestal : *"Cet état est une ressource — pas une opportunité unique à ne pas rater"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) — créer les conditions au warmup.
**Risque principal :** glissement vers le [[06 — Évaluation de l'enjeu -- Piédestal]] si entity thinking s'active sur la haute énergie.

---

## VI. Patterns documentés

> [!success] 1. Déclencheurs
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.declencheur).forEach(i=>{let v=Array.isArray(i.declencheur)?i.declencheur:[i.declencheur];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucun déclencheur documenté.*");
> ```

> [!success] 2. Pensées automatiques
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.pensee).forEach(i=>{let v=Array.isArray(i.pensee)?i.pensee:[i.pensee];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)sorted.forEach(e=>dv.el("blockquote",`« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!success] 3. Réactions
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.reaction).forEach(i=>{let v=Array.isArray(i.reaction)?i.reaction:[i.reaction];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!success] 4. Prix à payer *(pour conserver la Plénitude)*
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Prix à payer"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Prix à payer"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: J'accepte que la Plénitude a un pic puis revient à la baseline — ce n'est pas un échec]
> > - [ ] [Prix à payer:: J'accepte que sortir de cette session en Plénitude vient souvent avec une frustration]

---

## VII. Analyse à froid

> [!abstract]
> **Documenter les comportements, pas l'état :**
> *"Qu'est-ce que je fais concrètement quand je suis en Plénitude ?"*
> → fold facile · décisions sans débat interne · lâcher prise FOMO · timebank détendu
> Ces comportements sont les données qui alimentent les reconvocations futures du Stratège.
>
> **Risque Piédestal :**
> Si la Plénitude génère une pensée "ne pas gâcher" → Piédestal activé → nommer immédiatement. → [[06 — Évaluation de l'enjeu -- Piédestal]]

---

## VIII. Plan d'action

> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Plan d'action"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Plan d'action"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun plan actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action
> > - [ ] [Plan d'action:: Documenter les comportements spécifiques de cette session en Plénitude → base de reconvocation]

---

## IX. Archives

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let archives=dv.array([...desc,...p.file.lists]).where(c=>c.completed&&c["Prix à payer"]);
> if(archives.length>0)dv.taskList(archives,false);else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let archives=dv.array([...desc,...p.file.lists]).where(c=>c.completed&&c["Plan d'action"]);
> if(archives.length>0)dv.taskList(archives,false);else dv.paragraph("*Aucune action archivée.*");
> ```

## Notes liées
- [[Plénitude IRL]] · [[Certitude]] · [[Satisfaction]] · [[Sérénité]]
- [[06 — Évaluation de l'enjeu -- Piédestal]] — risque de glissement
- [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
