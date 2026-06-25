---
type: fiche_emotion
tags: [L3, émotion, colère, inner-mapping]
L3_nom: "Colère"
L3_valence: "négative (transformable)"
L3_arousal: "haute"
BIS_BAS: "BAS↑↑ frustré · BIS↑ réactif"
L1_déclencheurs: ["Besoin de Compétence défensif", "Besoin d'Autonomie défensif"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Confabulation]]", "[[11 — Mobilisation compensatoire -- Suramplification]]"]
L4_comportements: ["Tilt · Augmentation du volume · Jeu impulsif · Étude compulsive (réaction)"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🔥 Colère

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Colère]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Carver (2001) · Barrett (2017) · [[Fondements théoriques/05 — BIS & BAS]] · [[Fondements théoriques/03 — Cerveau prédictif]]
> La Colère in-game est produite par le **BAS frustré** : le système d'approche est actif (motivation élevée, plan en cours) et un obstacle externe (variance hostile, bad beat) bloque l'avancée. La Colère est le signal que le BAS cherche un autre passage — elle a une fonction adaptatrice. La dysfonction naît quand l'impulsion de reprendre le contrôle est habillée en stratégie (Confabulation). [documenté]
>
> → Voir aussi : [[Colère IRL]] pour la version hors session (source BIS éthique)

**Valence :** négative — transformable comme la Colère IRL
**Arousal :** haute
**Action tendency :** À documenter

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ réactif — mauvais résultats = signal d'alerte
- **BAS :** ↑↑ frustré — drive bloqué par la variance → cherche un passage
- **Combinaison :** BAS frustré + BIS réactif = tension active → risque de tilt si non régulée

**Distinction des émotions proches :**
vs **[[Colère IRL]]** : in-game la source est typiquement BAS frustré (variance). IRL elle peut être BIS éthique (injustice).
vs **[[La Réactance]]** : la Réactance est plus spécifique — réponse à un obstacle perçu comme attaque directe à l'autonomie décisionnelle. La Colère est plus diffuse.
vs **[[Frustration]]** : la Frustration est le signal précoce ("bol qui se remplit"). La Colère est le stade suivant — le bol a débordé.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** mâchoire serrée · chaleur dans les épaules et les mains · tension dans le dos
> - **Rythme cardiaque :** nettement accéléré
> - **Respiration :** courte · rapide · diaphragme tendu
> - **Posture spontanée :** corps qui se redresse · tension généralisée
> - **Sensations spécifiques :** chaleur qui monte · agitation · envie d'agir immédiatement

> [!warning] Signaux cognitifs précoces
> - *"C'est n'importe quoi"* / *"À quoi ça sert de bien jouer ?"* / *"Je vais reprendre ma mise"*
> - Pensées correctives non fondées ("je dois changer quelque chose")
> - Confabulation immédiate pour justifier l'action impulsive

> [!warning] Signaux comportementaux précoces
> - Augmentation du volume ou des stakes
> - Jeu depuis l'impulsion (calls, bets non fondés)
> - Étude compulsive post-session (réaction à la colère non transformée)

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Compétence | Variance hostile = "révélation" que je ne maîtrise pas → Colère contre la situation |
| **Défensif** | Besoin d'Autonomie | Obstacle à l'action perçue comme légitime → BAS frustré |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie la Colère en traitant les bad beats comme des preuves de l'entité déficiente. La variance devient personnelle.
- **Mastery thinking** : la Colère reste informationnelle. *"La variance m'indique que je dois réguler mon état, pas changer ma stratégie."*

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Confabulation (L2/02) | Habille l'impulsion de reprendre le contrôle en "bonne décision stratégique" |
| Suramplification (L2/11) | La Colère peut déclencher l'engagement maximal défensif (jouer plus pour rattraper) |

#### L0 — Influence
Budget épuisé → seuil plus bas · plus difficile d'interrompre avant le tilt. Budget satisfait → Colère plus accessible à la régulation.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → seuil plus bas · tilt plus probable |
| **L3 → L0** | ascendant ⚠️ | Colère non régulée → dépense L0 élevée (cortisol, tension) · accélère l'épuisement |
| **L1 → L3** | descendant | Compétence + Autonomie défensifs |
| **L3 → L1** | ascendant ⚠️ | Répétée → renforce "je ne contrôle pas les résultats" → ancre la Compétence défensive |
| **L2 → L3** | descendant | Confabulation · Suramplification |
| **L3 → L2** | ascendant | Déclenche la Confabulation (justifier l'action impulsive) |
| **L3 → L4** | descendant | Tilt · augmentation volume · jeu impulsif |
| **L4 → L3** | ascendant ⚠️ | Tilt confirme la perte de contrôle → amplifie la Colère |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — |
| 2 · Modification | oui | Switch Actif · réduction du volume · pause |
| 3 · Attentionnel | oui | Drill 03 Interrupt escalade — orienter l'attention vers le processus |
| 4 · Reappraisal | oui | *"La variance n'est pas un verdict — je contrôle le processus, pas le résultat"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Modification (2) + Attentionnel (3) via Drill 03.
**Note L0 :** sous budget bas, Modification (2) uniquement — Switch Actif ou pause.

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
> > - [ ] [Prix à payer:: J'accepte que la variance n'est pas un verdict sur mon niveau]

---

## VII. Analyse à froid

> [!abstract]
> **Source BAS frustré ou tilt émotionnel ?**
Question : *"Est-ce que je change quelque chose à ma stratégie pour des raisons techniques — ou pour reprendre le contrôle ?"*
Si pour reprendre le contrôle → Colère déguisée → Confabulation active.

**Protocole associé :** [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]

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
> > - [ ] [Plan d'action:: Drill 03 si escalade détectée · Switch Actif · *"La variance n'est pas un verdict"*]

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
- [[Colère IRL]] · [[Frustration]] · [[La Réactance]]
- [[02 — Évaluation causale -- Confabulation]]
- [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]
- [[Fondements théoriques/05 — BIS & BAS]]
