---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Satisfaction"
L3_valence: "positive"
L3_arousal: "basse-moyenne"
BIS_BAS: "BAS neutre BIS↓"
L1_déclencheurs: ["Besoin de Compétence générateur (accomplissement)"]
L2_déclencheurs: ["[[09 — Encodage de l'erreur -- Ancrage par compréhension (pôle générateur)]]"]
L4_comportements: ["Consolidation · Ancrage · Clôture · Documentation"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# ✨ Satisfaction

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Satisfaction]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> La Satisfaction est construite quand le cerveau applique le concept 'j'ai accompli ce que je voulais accomplir' à un affect positif à arousal basse-moyenne. Contrairement à la Plénitude (plus profonde, moins liée à un accomplissement précis) et à l'Enthousiasme (avant l'action), la Satisfaction vient après — c'est la fermeture de boucle positive. [documenté]

**Valence :** positive
**Arousal :** basse-moyenne
**Action tendency :** Consolidation de l'acquis · ancrage · documentation · clôture propre

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — aucune menace, système d'inhibition désactivé
- **BAS :** neutre — la boucle est fermée, pas de nouveau drive actif
- **Combinaison :** Boucle fermée · repos actif · restauration L0
- **Note :** la Satisfaction est légèrement restauratrice — la fermeture de boucle réduit la charge cognitive de l'incertitude non résolue.

**Distinction des émotions proches :**
vs **[[Plénitude]]** : la Plénitude est plus profonde et moins liée à un accomplissement spécifique. La Satisfaction est plus ciblée et plus liée à une action terminée.
vs **Enthousiasme** : l'Enthousiasme précède l'action. La Satisfaction la suit.
vs **Certitude** : la Certitude est dans le moment de la décision. La Satisfaction est dans l'après.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!success] Signaux corporels
> - **Zone de sensation :** légèreté générale · muscles relâchés · chaleur diffuse dans la poitrine
> - **Rythme cardiaque :** normal · régulier
> - **Respiration :** profonde et lente · soupirs de relâchement
> - **Posture spontanée :** corps ouvert · détendu · léger recul
> - **Sensations spécifiques :** sentiment de 'c'est fait' · légèreté des épaules · absence de tension résiduelle

> [!success] Signaux cognitifs précoces
> - *"C'est bien"* / *"J'ai fait ce que je voulais faire"* / *"Ça valait le coup"*
> - Absence de questionnement sur ce qui aurait pu être différent
> - Ancrage naturel dans ce qui a été accompli

> [!success] Signaux comportementaux précoces
> - Arrêt naturel de l'activité
> - Documentation de ce qui a bien fonctionné
> - Transition fluide vers autre chose

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Besoin de Compétence | Accomplissement perçu comme croissance → boucle fermée positivement |
| **Générateur** | Besoin d'Autonomie | Action faite depuis soi · pas d'obligation → Satisfaction authentique |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Mastery thinking** : Satisfaction stable et durable. *"J'ai bien fait ce que je voulais faire — c'est de l'information sur ce qui fonctionne."*
- **Entity thinking** : Satisfaction instable. *"J'ai bien joué = je suis bon joueur."* → dépend du résultat suivant → fragile.

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Ancrage par compréhension (L2/09 générateur) | La Satisfaction suit l'encodage sain d'une erreur ou d'un apprentissage |

#### L0 — Influence
La Satisfaction est restauratrice — la fermeture de boucle réduit la charge cognitive. Contrairement à d'autres états positifs, elle ne demande pas beaucoup de L0 pour être accessible.

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget même modéré → Satisfaction accessible (fermeture de boucle peu coûteuse) |
| **L3 → L0** | ascendant ✅ | Restauratrice — fermeture de boucle réduit la charge cognitive |
| **L1 → L3** | descendant | Besoin de Compétence générateur (accomplissement) |
| **L3 → L1** | ascendant ✅ | Renforce 'je suis capable d'accomplir ce que je commence' |
| **L2 → L3** | descendant | Ancrage par compréhension (L2/09 générateur) |
| **L3 → L2** | ascendant ✅ | La Satisfaction réduit le besoin de Rumination ou d'Auto-flagellation |
| **L3 → L4** | descendant | Consolidation · documentation · clôture |
| **L4 → L3** | ascendant ✅ | La documentation de ce qui a bien fonctionné renforce la Satisfaction |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Créer le rituel de clôture (feedback post-session) qui permet la Satisfaction |
| 2 · Modification | non | — |
| 3 · Attentionnel | oui | *"Qu'est-ce qui a bien fonctionné dans cette session ?"* |
| 4 · Reappraisal | non | — (la Satisfaction ne se force pas, elle se récolte) |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) — créer le rituel de clôture. La Satisfaction arrive quand on prend le temps de nommer ce qui a bien fonctionné.
**Note L0 :** accessible même sous budget modéré.

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
> > - [ ] [Prix à payer:: J'accepte de prendre le temps de nommer ce qui a bien fonctionné — même après une session difficile]

---

## VII. Analyse à froid

> [!abstract]
> **La Satisfaction se documente.**
Ce qui distingue la Satisfaction durable de la satisfaction fugitive : la documentation. Les sessions en Satisfaction sont la preuve datée que le Stratège existe et est accessible. → [[Plénitude]] §Alexis pointe

Question : *"Qu'est-ce que j'ai accompli aujourd'hui qui mérite d'être nommé ?"*

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
> > - [ ] [Plan d'action:: Question pivot en feedback : 'Quels moments du Stratège étaient présents ?' → nommer → fermer la boucle]

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
- [[Plénitude]] · [[Certitude]]
- [[09 — Encodage de l'erreur -- Auto-flagellation]]
- [[L1 - Structures profondes/01 — Besoin de Compétence]]
