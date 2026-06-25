---
type: fiche_emotion
tags: [L3, émotion, réactance, inner-mapping, BAS, autonomie]
L3_nom: "La Réactance"
L3_valence: "négative"
L3_arousal: "haute"
BIS_BAS: "BAS↑↑ BIS neutre"
L1_déclencheurs: ["Besoin d'Autonomie défensif"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Confabulation]]"]
L4_comportements: ["Play depuis l'impulsion · Jeu agressif non fondé · Tilt d'orgueil"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# ⚡ La Réactance

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: La Réactance]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Brehm (1966, 1981) · Carver (2001) · [[Fondements théoriques/05 — BIS & BAS]] · [[Fondements théoriques/10 — Agon · Alea · Mimicry · Ilinx]]
> La Réactance est la réponse motivationnelle à la **perception d'une menace sur une liberté d'action**. Carver (2001) ancre ce mécanisme dans le BAS : la Réactance est une réponse BAS à un obstacle — l'élan toward était actif, l'obstacle l'**intensifie** plutôt que de le stopper. Ce n'est pas du désespoir — c'est de l'énergie réorientée contre le blocage. [documenté]

> [!abstract] ✅ La Confabulation comme véhicule · [[02 — Évaluation causale -- Confabulation]]
> La Réactance est particulièrement piégeuse parce qu'elle utilise le vocabulaire du jeu pour habiller une impulsion. *"Les propriétés de cette main sont pas mal pour reprendre l'initiative"* ressemble à de l'analyse GTO. Mais la décision était prise avant le raisonnement. **3 marqueurs [documenté — Moukheiber · Alexis] :**
> 1. **Sélectivité** — seules les propriétés favorables sont convoquées
> 2. **Causalité inversée** — la décision précède l'évaluation
> 3. **Vitesse et certitude** — rapide et certain = suspect

**Valence :** négative
**Arousal :** haute — drive intense vers la restauration de la liberté
**Action tendency :** reprendre le contrôle · agir dans la direction bloquée avec intensité supérieure

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre — ce n'est pas une menace, c'est un blocage
- **BAS :** ↑↑ très actif + intensifié par l'obstacle — l'élan est amplifié par le blocage
- **Combinaison :** BAS dominant fort → impulsion d'action immédiate

> [!abstract] Réactance vs Agon · [[Fondements théoriques/10 — Agon · Alea · Mimicry · Ilinx]]
>
> | | Réactance | Agon |
> |---|---|---|
> | Direction | Réactive — réponse à un blocage déjà présent | Proactive — recherche délibérée d'un adversaire |
> | Émotion produite | Impulsion de reprendre le contrôle | Engagement · détermination |
>
> Pour un profil Agon dominant, la Réactance peut être vue comme la forme défensive de ce besoin.

**Distinction des émotions proches :**
vs **[[Frustration]]** : la Frustration est générale (tout obstacle). La Réactance est spécifique — la liberté d'action **décisionnelle** est menacée.
vs **[[Colère]]** : la Colère peut suivre la Réactance si non régulée. La Réactance est plus spécifique à l'autonomie décisionnelle.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** plexus solaire · tension dans la poitrine · envie d'agir
> - **Rythme cardiaque :** accéléré · intense
> - **Respiration :** courte et rapide
> - **Posture spontanée :** corps légèrement en avant · prêt à agir
> - **Sensations spécifiques :** impatience musculaire · énergie dirigée · *"je dois agir maintenant"*

> [!warning] Signaux cognitifs précoces
> - *"Je vais reprendre l'initiative"* / *"Je dois répondre"* / *"C'est GTO d'être agressif ici"*
> - Le raisonnement arrive **après** la décision — justification post-hoc
> - Certitude rapide (sans incertitude résiduelle) → signal de confabulation

> [!warning] Signaux comportementaux précoces
> - Bet/raise depuis l'impulsion plutôt que depuis l'analyse
> - Bluff-catch ou bluff non fondé après une séquence agressive adverse
> - Décision qui change si on se demande : *"Si cet adversaire n'avait pas été agressif, aurais-je joué cette main ?"*

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin d'Autonomie | Liberté d'action perçue comme menacée → BAS s'intensifie contre l'obstacle |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : l'adversaire agressif est traité comme un test de l'entité. La Réactance devient identitaire : *"si je ne réponds pas, je perds mon image de joueur dur".*
- **Mastery thinking** : l'adversaire agressif est juste de l'information sur le range. Pas besoin de répondre identitairement.

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Confabulation (L2/02) | **Véhicule principal** — habille l'impulsion de reprendre le contrôle en analyse GTO |

#### L0 — Influence

Budget épuisé → seuil de déclenchement plus bas · confabulation moins détectable. Sous L0 bas : règle — si rapide + certain + suit une émotion → fold.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → seuil plus bas · confabulation moins détectable |
| **L3 → L0** | ascendant ⚠️ | BAS intensifié → coût métabolique · dépense L0 |
| **L1 → L3** | descendant | Besoin d'Autonomie défensif |
| **L3 → L1** | ascendant ⚠️ | Répétée → renforce "je dois toujours répondre" → ancre l'Autonomie défensive |
| **L2 → L3** | descendant | — (la Réactance déclenche la Confabulation) |
| **L3 → L2** | ascendant | Déclenche immédiatement la Confabulation (habiller l'impulsion) |
| **L3 → L4** | descendant | Play depuis l'impulsion · jeu agressif non fondé |
| **L4 → L3** | ascendant ⚠️ | Si le play non fondé réussit → renforce la Réactance comme stratégie |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — |
| 2 · Modification | oui | Timebank délibéré — ralentir la décision |
| 3 · Attentionnel | oui | *"Est-ce que je joue ce coup pour optimiser l'EV ou pour reprendre le contrôle ?"* |
| 4 · Reappraisal | oui | *"Si cet adversaire n'avait pas été agressif, aurais-je joué cette main ?"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Attentionnel (3) — la question de diagnostic. Simple, rapide, accessible in-game.
**Note L0 :** sous budget bas — si rapide + certain + suit une émotion → fold par défaut.

**Protocole associé :** [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]

---

## VI. Patterns documentés

> [!note] 1. Déclencheurs
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.declencheur).forEach(i=>{let v=Array.isArray(i.declencheur)?i.declencheur:[i.declencheur];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucun déclencheur documenté.*");
> ```
> > [!note]- Instance documentée
> > - Bluff-catch → *"Les propriétés de cette main sont pas mal pour reprendre l'initiative"* [observation personnelle]

> [!note] 2. Pensées automatiques
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.pensee).forEach(i=>{let v=Array.isArray(i.pensee)?i.pensee:[i.pensee];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)sorted.forEach(e=>dv.el("blockquote",`« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!note] 3. Réactions
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.reaction).forEach(i=>{let v=Array.isArray(i.reaction)?i.reaction:[i.reaction];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!note] 4. Prix à payer
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Prix à payer"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Prix à payer"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: ]

---

## VII. Analyse à froid

> [!abstract]
> **La question de diagnostic [documenté — Alexis] :**
> *"Est-ce que je joue ce coup pour optimiser mon EV ou pour reprendre le contrôle ?"*
> *"Si cet adversaire n'avait pas été agressif juste avant, est-ce que cette main m'aurait semblé jouable ?"*
> Si la réponse est non → Réactance, pas stratégie.

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
> > - [ ] [Plan d'action:: *"Est-ce que je joue pour l'EV ou pour reprendre le contrôle ?"* → fold si Réactance]
> > - [ ] [Plan d'action:: Si rapide + certain + suite d'une émotion → fold par défaut]

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
- [[Fondements théoriques/05 — BIS & BAS]] · [[Fondements théoriques/10 — Agon · Alea · Mimicry · Ilinx]]
- [[02 — Évaluation causale -- Confabulation]]
- [[L1 - Structures profondes/02 — Besoin d'Autonomie]]
- [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]
