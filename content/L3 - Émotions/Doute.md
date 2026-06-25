---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Doute"
L3_valence: "mixte"
L3_arousal: "basse-moyenne"
BIS_BAS: "BIS↑léger BAS neutre"
L1_déclencheurs: ["Besoin de Compétence (défensif si paralysant / générateur si calibré)"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Confabulation (absence de doute = signal de confabulation)]]", "[[05 — Évaluation du soi -- Pensée binaire (amplifie le Doute paralysant)]]"]
L4_comportements: ["Questionnement · Vérification · Ralentissement décisionnel · Immobilisation (si paralysant)"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🌫️ Doute

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Doute]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> Le Doute est construit quand le cerveau applique le concept 'je ne suis pas sûr' à un état d'incertitude. Il a une forme **fonctionnelle** (Doute calibré — signal de santé analytique, signe que le Système 2 est actif) et une forme **dysfonctionnelle** (Doute paralysant — amplifié par l'entity thinking sur la compétence). La différence n'est pas dans l'incertitude elle-même, mais dans ce que le cerveau en fait. [documenté]

**Valence :** mixte
**Arousal :** basse-moyenne
**Action tendency :** Vérification · questionnement · ralentissement décisionnel (fonctionnel) · immobilisation (paralysant)

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ léger — signal d'incertitude détectée · invite à la prudence
- **BAS :** neutre — pas d'élan particulier
- **Combinaison :** BIS léger sans BAS fort → pause décisionnelle
- **Note :** Le Doute fonctionnel est exactement ça — un BIS léger qui invite à vérifier. Le Doute paralysant est ce même BIS amplifié par l'entity thinking.

**Distinction des émotions proches :**
vs **[[Anxiété d'évaluation]]** : l'Anxiété d'évaluation a un objet précis (le regard d'un pair compétent). Le Doute porte sur sa propre décision ou compétence, indépendamment du regard.
vs **[[Peur]]** : la Peur anticipe une menace future. Le Doute est centré sur le processus présent.
vs **[[Impuissance]]** : l'Impuissance est l'absence totale de levier. Le Doute a un levier — la vérification.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** légère tension dans la gorge · poitrine indécise
> - **Rythme cardiaque :** normal à légèrement irrégulier
> - **Respiration :** légèrement suspendue · pauses entre les inspirations
> - **Posture spontanée :** tête légèrement penchée · regard qui cherche · hésitation musculaire
> - **Sensations spécifiques :** sensation d'être 'entre deux' · pas d'élan clair

> [!warning] Signaux cognitifs précoces
> - *"Je ne sais pas"* / *"Et si..."* / *"Est-ce que c'est la bonne décision ?"*
> - Pensées qui tournent autour d'un choix sans se résoudre
> - Recherche de confirmation ou de preuve supplémentaire

> [!warning] Signaux comportementaux précoces
> - Pause avant d'agir
> - Demande de validation externe (si paralysant)
> - Questionnement approfondi (si fonctionnel)

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Besoin de Compétence | Doute calibré = signal d'analyse honnête. "Je ne suis pas encore sûr — il me manque une information." |
| **Défensif** | Besoin de Compétence | Doute paralysant = entity thinking sur la compétence. "Le Doute révèle que je ne suis pas capable." |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Mastery thinking** : le Doute est un signe de santé analytique. *"L'incertitude résiduelle est normale — elle me dit de vérifier."* → Doute fonctionnel.
- **Entity thinking** : le Doute devient une menace identitaire. *"Si je doute, c'est que je ne suis pas vraiment compétent."* → Doute paralysant.

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Confabulation (L2/02) | **L'absence de Doute** dans une décision rapide est le signal de confabulation. La Certitude immédiate post-impulsion = suspect. |
| Pensée binaire (L2/05) | Amplifie le Doute paralysant : "Si je doute = je suis mauvais" |

#### L0 — Influence
Budget épuisé → Doute paralysant plus probable. Le PFC moins disponible rend la distinction fonctionnel/paralysant plus difficile à faire. Sous L0 bas → si doute intense, fold par défaut.

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → Doute paralysant plus probable |
| **L3 → L0** | ascendant ⚠️ | Doute paralysant prolongé → coût PFC élevé · consomme L0 |
| **L1 → L3** | descendant | Compétence défensif → Doute paralysant · Compétence générateur → Doute calibré |
| **L3 → L1** | ascendant | Doute répété non résolu → renforce la Compétence défensive |
| **L2 → L3** | descendant | L'absence de Doute signale la Confabulation · la Pensée binaire amplifie le Doute paralysant |
| **L3 → L2** | ascendant | Le Doute fonctionnel peut interrompre la Confabulation |
| **L3 → L4** | descendant | Vérification · ralentissement · immobilisation |
| **L4 → L3** | ascendant ✅ | La vérification résout le Doute fonctionnel |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | partiel | Sous L0 bas : règle "si doute intense → fold" — pas d'analyse |
| 2 · Modification | non | — |
| 3 · Attentionnel | oui | *"Qu'est-ce qui manque pour décider ?"* — orienter vers l'information manquante |
| 4 · Reappraisal | oui | *"Ce Doute est un signal d'analyse — pas un verdict sur ma compétence"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Reappraisal (4) pour le Doute paralysant · Attentionnel (3) pour le Doute fonctionnel.
**Note L0 :** sous budget bas, fold par défaut si Doute intense.

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
> > - [ ] [Prix à payer:: J'accepte que l'incertitude résiduelle est un signe d'analyse honnête — pas de faiblesse]

---

## VII. Analyse à froid

> [!abstract]
> **Doute fonctionnel ou paralysant ?**
Question pivot : *"Est-ce que je doute parce qu'il me manque une information — ou parce que le Doute lui-même me semble menaçant ?"*
- Manque d'info → Doute fonctionnel → vérifier
- Menace identitaire → Doute paralysant → Reappraisal → *"ce Doute est normal"*

**Rappel : l'absence de Doute dans une décision rapide est suspecte.** → [[02 — Évaluation causale -- Confabulation]]

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
> > - [ ] [Plan d'action:: Nommer le Doute → identifier s'il est fonctionnel (manque d'info) ou paralysant (entity thinking) → agir sur la cause]

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
- [[Peur]] · [[Anxiété d'évaluation]] · [[Impuissance]]
- [[02 — Évaluation causale -- Confabulation]] · [[05 — Évaluation du soi -- Pensée binaire]]
