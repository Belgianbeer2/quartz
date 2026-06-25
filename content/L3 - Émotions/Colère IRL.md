---
type: fiche_emotion
tags: [L3, émotion, colère, inner-mapping, BAS, BIS]
L3_nom: "Colère IRL"
L3_valence: "négative (transformable)"
L3_arousal: "haute"
BIS_BAS: "BAS↑↑ frustré (Source 1) · BIS↑ éthique (Source 2)"
L1_déclencheurs: ["Prémisses éthiques", "Besoin d'Autonomie défensif"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Confabulation]]"]
L4_comportements: ["Discours explosif (narratif) · Stratégie de l'autruche (réel) · Levier de détermination (transformé)"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🔥 Colère IRL

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Colère IRL]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Deux sources de Colère — Carver (2001) · Smith & Ellsworth (1985) · [[Fondements théoriques/05 — BIS & BAS]] · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
> La Colère IRL n'a pas une seule origine. Deux mécanismes distincts peuvent la produire :
>
> **Source 1 — BAS frustré** (Carver 2001) : le système d'approche est actif, et un obstacle externe bloque l'avancée. La Colère est le signal que le BAS cherche un autre passage. → levier = rediriger le BAS.
>
> **Source 2 — BIS/Prémisses éthiques** : un événement active un concept moral préchargé (injustice, violation de consentement) sans que le BAS soit nécessairement actif. → levier = distinguer ce sur quoi on a du contrôle.
>
> **Mécanisme de transformation [documenté — Alexis]** : Colère et Détermination partagent la même énergie (BAS actif élevé). Ce qui les distingue : où le contrôle est perçu — sur l'obstacle (Colère) vs sur mon processus (Détermination). La transformation est un **reappraisal** (Gross #4) — redirection du contrôle perçu, sans changer l'énergie. [documenté — Gross 1998 · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §IV-V]

**Valence :** négative — mais transformable
**Arousal :** haute — énergie mobilisée intense
**Action tendency :** reprendre le contrôle · discours explosif (narratif) · stratégie de l'autruche (réel)

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **Source 1 :** BAS↑↑ + obstacle = frustration → Colère BAS frustré
- **Source 2 :** BIS↑ éthique (injustice activée) + impuissance → Colère BIS éthique
- **Note importante :** les deux sources peuvent coexister dans le même événement

> [!abstract] Ce que Moukheiber éclaire · [[Sources/01 — Albert Moukheiber × Les Lueurs]]
> Le discours interne explosif (*"je vais les défoncer"*) et la réaction réelle (stratégie de l'autruche) sont **opposés**. Ce n'est pas une contradiction — c'est le fonctionnement normal sous impuissance. Le cerveau génère une histoire d'agentivité pour compenser. Le *soi narratif* et le *soi comportemental* ne coïncident pas sous pression. [documenté]

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** mâchoire serrée · chaleur diffuse dans les épaules et la poitrine · mains qui se serrent
> - **Rythme cardiaque :** nettement accéléré
> - **Respiration :** plus courte · plus rapide · tension dans le diaphragme
> - **Posture spontanée :** corps qui se redresse · tension dans le cou · regard intense
> - **Sensations spécifiques :** chaleur qui monte · agitation · énergie qui cherche une sortie

> [!warning] Signaux cognitifs précoces
> - *"J'aurais préféré ne pas être au courant"* / *"je vais les défoncer"* / *"je vais tout faire péter"*
> - Discours interne explosif sans plan réel associé
> - Ruminition sur l'injustice ou l'obstacle

> [!warning] Signaux comportementaux précoces
> - Stratégie de l'autruche (faire des choses à conséquences limitées)
> - Isolement · silence · évitement du sujet

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Prémisses éthiques | Violation d'un standard moral → Colère BIS éthique (injustice, violation de liberté) |
| **Défensif** | Besoin d'Autonomie | BAS actif + obstacle → Colère BAS frustré (liberté d'action bloquée) |

**Les 3 niveaux de traitement [documenté — Alexis] :**
1. **Je la subis** — le trigger crée l'impuissance, l'émotion déborde
2. **Je la gère** — stratégie de l'autruche, actions à conséquences limitées
3. **Je la transforme** — la valeur (liberté, autodétermination) → **levier de détermination**

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
La transformation (niveau 3) est plus accessible sous mastery thinking — l'énergie est redirigée vers le processus plutôt que vers le verdict sur l'obstacle.

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Confabulation (L2/02) | Peut habiller l'impulsion de Colère en stratégie — *"je dois riposter pour me respecter"* |

#### L0 — Influence

Budget épuisé → seuil de déclenchement plus bas · transformation plus difficile. Sous L0 bas, le niveau 3 (transformation) est quasi-inaccessible.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → seuil plus bas · intensité plus élevée · transformation plus difficile |
| **L3 → L0** | ascendant ⚠️ | Colère non régulée → coût métabolique élevé (cortisol, tension) · dépense L0 |
| **L1 → L3** | descendant | Prémisses éthiques + Autonomie défensif |
| **L3 → L1** | ascendant ✅ | Transformée en Détermination → renforce les valeurs comme moteur plutôt que comme source de souffrance |
| **L2 → L3** | descendant | Confabulation peut amplifier en habillant la Colère en "logique" |
| **L3 → L2** | ascendant | La Colère active la Confabulation (justifier l'impulsion) |
| **L3 → L4** | descendant | Discours explosif (narratif) · stratégie de l'autruche · Détermination (si transformée) |
| **L4 → L3** | ascendant ✅ | La transformation en levier réduit durablement la Colère |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — |
| 2 · Modification | oui | Stratégie de l'autruche (niveau 2) — actions à conséquences limitées · s'éloigner du stimulus |
| 3 · Attentionnel | partiel | *"Quelle est la valeur touchée ici ?"* → identifier pour transformer |
| 4 · Reappraisal | oui | Redirection du contrôle perçu : obstacle → mon processus · Colère → Détermination |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Reappraisal (4) — redirection du contrôle perçu. Nécessite que L0 soit partiellement restauré (niveau 2 d'abord si L0 bas).
**Note L0 :** sous budget épuisé, Modification (2) en premier. La transformation (Reappraisal) vient après.

---

## VI. Patterns documentés

> [!warning] 1. Déclencheurs
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.declencheur).forEach(i=>{let v=Array.isArray(i.declencheur)?i.declencheur:[i.declencheur];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucun déclencheur documenté.*");
> ```
> > [!note]- Instance documentée
> > - Le beau-père de Sassa, emprisonné injustement, sur le point de mourir · maltraitance · impuissance totale

> [!warning] 2. Pensées automatiques
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.pensee).forEach(i=>{let v=Array.isArray(i.pensee)?i.pensee:[i.pensee];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)sorted.forEach(e=>dv.el("blockquote",`« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!warning] 3. Réactions
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.reaction).forEach(i=>{let v=Array.isArray(i.reaction)?i.reaction:[i.reaction];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!warning] 4. Prix à payer
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Prix à payer"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Prix à payer"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: me faire guider par mes émotions (ne plus être le conducteur de mon corps)]

---

## VII. Analyse à froid

> [!abstract]
> **Quelle source est active — BAS frustré ou BIS éthique ?**
> - BAS frustré : un obstacle bloque quelque chose que je voulais. Levier = rediriger le BAS.
> - BIS éthique : une valeur est violée. Levier = distinguer ce que je contrôle de ce que je ne contrôle pas.
>
> **Comment transformer la valeur touchée en levier ?**
> *"Je joue pour construire l'indépendance qui me permettra d'aider les gens qui m'importent."*
> La valeur (liberté, autodétermination) devient le moteur plutôt que la source de souffrance. → Dépolarisation sur l'injustice (sujet de travail avec Alexis)

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
> > - [ ] [Plan d'action:: Identifier la source (BAS frustré ou BIS éthique) → adapter le levier]
> > - [ ] [Plan d'action:: Niveau 2 d'abord si L0 bas → niveau 3 (transformation) quand restauré]

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
- [[Fondements théoriques/05 — BIS & BAS]] §V.2
- [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §IV-V
- [[L1 - Structures profondes/04 — Prémisses éthiques]] · [[L1 - Structures profondes/05 — Besoin de contrôle]]
- [[Détermination]] · [[Impuissance]]
