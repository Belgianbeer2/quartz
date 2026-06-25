---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Sérénité"
L3_valence: "positive"
L3_arousal: "très basse"
BIS_BAS: "BAS↓ BIS↓ (neutralité régulée positive)"
L1_déclencheurs: ["Besoin de Compétence générateur", "Besoin d'Appartenance générateur", "Besoin d'Autonomie générateur (tous satisfaits sans tension)"]
L2_déclencheurs: []
L4_comportements: ["Présence · Ralentissement délibéré · Ancrage · Actions depuis le centre"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🌊 Sérénité

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Sérénité]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> La Sérénité est construite quand le cerveau applique le concept 'tout est en ordre' à un affect positif à très faible arousal. Contrairement à la Fatigue (aussi BAS↓ BIS↓ mais valence négative) et à l'Accablement (phase prolongée post-sortie de fenêtre), la Sérénité est un état de régulation complète — tous les L1 sont satisfaits sans tension active. Elle accompagne souvent la sortie de l'Accablement et la restauration du budget L0. [documenté]

**Valence :** positive
**Arousal :** très basse
**Action tendency :** Présence totale · ralentissement délibéré · actions depuis le centre · conservation du calme

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — aucune menace détectée
- **BAS :** ↓ bas — pas de drive actif · pas d'objectif urgent
- **Combinaison :** BAS↓/BIS↓ avec valence positive → distinct de la Fatigue (BAS↓/BIS↓ valence négative) et de l'Accablement (même signature mais valence très négative et prolongée)
- **C'est la signature du repos régulé** — le système nerveux est en mode récupération active positive.

**Distinction des émotions proches :**
vs **[[Accablement]]** : même signature BAS↓/BIS↓ mais valence opposée. L'Accablement est un état de détresse basse activation. La Sérénité est un état de paix basse activation. La Sérénité peut être le **signal de sortie de l'Accablement**.
vs **Fatigue** : la Fatigue est aussi BAS↓/BIS↓ mais avec affect négatif et besoin urgent de récupération. La Sérénité est restaurée.
vs **[[Plénitude]]** : la Plénitude a une arousal plus élevée et souvent un déclencheur relationnel ou d'accomplissement. La Sérénité est plus silencieuse.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!success] Signaux corporels
> - **Zone de sensation :** corps entièrement détendu · absence de tension résiduelle
> - **Rythme cardiaque :** lent et régulier
> - **Respiration :** profonde, lente, régulière · naturelle
> - **Posture spontanée :** détendue · ouverte · ancrée · regard doux
> - **Sensations spécifiques :** 'tout est en ordre' · silence intérieur · légèreté sans excitation · présence totale

> [!success] Signaux cognitifs précoces
> - *"Je suis bien"* / *"C'est calme"* / *"Je suis là"*
> - Pensées rares · présence au moment actuel
> - Absence de planification anxieuse ou de rumination

> [!success] Signaux comportementaux précoces
> - Ralentissement délibéré
> - Présence totale sans distractibilité
> - Actions simples faites avec soin

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Tous les L1 | Tous les besoins fondamentaux satisfaits sans tension active → état de régulation complète · absence de menace ou d'urgence |
| **Signal** | Co-régulation | La présence de Sassa en co-régulation passive peut produire la Sérénité |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
La Sérénité est naturellement compatible avec le mastery thinking — elle n'a pas d'enjeu identitaire. Elle est difficile à maintenir sous entity thinking actif (qui crée toujours une tension).

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Aucun schéma défensif actif | La Sérénité requiert l'absence de L2 défensifs dominants |

#### L0 — Influence
La Sérénité accompagne la restauration du budget L0. Elle est à la fois le **signal** que L0 est restauré et un **état restaurateur** lui-même. C'est le signal de sortie de l'Accablement à surveiller. → [[Accablement]] §VI

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget satisfait (ou en cours de restauration) = condition de la Sérénité |
| **L3 → L0** | ascendant ✅ | Très restauratrice — le système nerveux en Sérénité récupère activement |
| **L1 → L3** | descendant | Tous les L1 générateurs satisfaits sans tension |
| **L3 → L1** | ascendant ✅ | Renforce tous les L1 générateurs silencieusement |
| **L2 → L3** | descendant | Absence de L2 défensifs dominants |
| **L3 → L2** | ascendant ✅ | La Sérénité réduit la probabilité d'activation de tous les L2 défensifs |
| **L3 → L4** | descendant | Présence · ralentissement · actions depuis le centre |
| **L4 → L3** | ascendant ✅ | Les actions depuis le centre (pas d'urgence) renforcent la Sérénité |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Créer les conditions : repos, co-présence, absence d'urgence |
| 2 · Modification | oui | Réduire les stimulations · environnement calme · Lucky, Sassa |
| 3 · Attentionnel | oui | *"Je suis là"* · ancrage corps et environnement immédiat |
| 4 · Reappraisal | non | — (la Sérénité ne se force pas) |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) + Modification (2) — créer les conditions. La Sérénité émerge quand les conditions sont réunies, elle ne se génère pas par effort.
**Signal de sortie Accablement :** quand la Sérénité apparaît, le recadrage cognitif redevient accessible. C'est le moment de reprendre les protocoles.

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
> > - [ ] [Prix à payer:: J'accepte de ne pas lancer de session depuis la Sérénité — elle mérite d'être préservée comme état de récupération]

---

## VII. Analyse à froid

> [!abstract]
> **Signal de sortie Accablement ?**
La Sérénité est l'un des signaux que le budget L0 est suffisamment restauré pour reprendre un travail cognitif. → [[Accablement]] §VI

**Conditions de la Sérénité :**
Quelles situations, personnes, moments la produisent régulièrement ? Documenter pour la convoquer intentionnellement.

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
> > - [ ] [Plan d'action:: Reconnaître la Sérénité quand elle apparaît → la nommer → la laisser durer → ne pas la rompre prématurément par l'action]

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
- [[Accablement]] · [[Plénitude]] · [[Plénitude IRL]]
- [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
- [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
