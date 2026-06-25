---
type: fiche_emotion
tags: [L3, émotion, plénitude-IRL, inner-mapping]
L3_nom: "Plénitude IRL"
L3_valence: "positive"
L3_arousal: "moyenne"
BIS_BAS: "BAS↑ BIS↓"
L1_déclencheurs: ["Besoin d'Appartenance générateur", "Besoin de Compétence générateur (utilité)"]
L2_déclencheurs: []
L4_comportements: ["Contemplation · Ralentissement · Introspection · Présence totale"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🌿 Plénitude IRL

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Plénitude IRL]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · Moukheiber (2026) · [[Fondements théoriques/03 — Cerveau prédictif]] · [[Sources/01 — Albert Moukheiber × Les Lueurs]]
> La Plénitude IRL partage avec la [[Plénitude]] le signal commun : **présence totale + absence de résistance**. Le cerveau n'est pas en train de prouver quelque chose ni de combattre quelque chose. La différence est dans le déclencheur : la Plénitude IRL naît de la connexion relationnelle (empathie, utilité, vulnérabilité partagée), pas de la performance technique. [documenté]

> [!abstract] La Plénitude IRL nourrit la Plénitude in-game [documenté — Alexis]
> La connexion empathique, le sentiment d'utilité — ces états construisent **l'être** en dehors de la table. Ce que le Stratège est dans la vie se transfère à la table : un homme qui se sent utile et connecté joue depuis une identité pleine, pas depuis un vide à combler par la performance. → [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]

**Valence :** positive
**Arousal :** moyenne — présence active mais calme, ralentissement du temps perçu
**Action tendency :** contemplation · ralentissement · introspection · partage de vulnérabilités

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — aucune menace, espace sécurisé
- **BAS :** ↑ actif — drive de connexion satisfait
- **Combinaison :** BAS/BIS équilibrés → co-régulation sociale active → restaure L0

**Distinction des émotions proches :**
vs **[[Plénitude]]** : Plénitude in-game est dans l'engagement technique. Plénitude IRL est dans la connexion relationnelle.
vs **[[Sérénité]]** : la Sérénité est plus silencieuse et moins relationnelle. La Plénitude IRL requiert une présence à l'autre.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!success] Signaux corporels
> - **Zone de sensation :** chaleur dans la poitrine · légèreté générale · corps ouvert et détendu
> - **Rythme cardiaque :** lent et régulier
> - **Respiration :** profonde · naturelle · lente
> - **Posture spontanée :** corps ouvert · regard doux · épaules décontractées
> - **Sensations spécifiques :** ralentissement du temps perçu · *"je suis là"* · absence de résistance

> [!success] Signaux cognitifs précoces
> - Verbalisation spontanée des ressentis en discours interne
> - *"Ça m'importe"* / *"Je suis utile ici"*
> - Pensées qui restent dans le moment présent (pas de projection ni de rumination)

> [!success] Signaux comportementaux précoces
> - Contemplation · regarder plutôt qu'agir
> - Ralentissement du rythme de vie
> - Introspection avec discours interne bienveillant

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Besoin d'Appartenance | Connexion authentique · empathie · vulnérabilité partagée → sentiment de compter pour l'autre |
| **Générateur** | Besoin de Compétence (utilité) | Sentiment de s'être rendu utile pour quelque chose d'important → compétence dans le domaine relationnel |

**Lien entity/mastery :**
La Plénitude IRL est naturellement compatible avec le mastery thinking — il n'y a pas d'enjeu identitaire. Elle est difficile à maintenir sous entity thinking (qui crée toujours une tension sur ce qu'on est perçu comme étant).

#### L2 — Schémas

Aucun L2 défensif n'est actif pendant la Plénitude IRL — c'est sa caractéristique principale.

#### L0 — Influence

La Plénitude IRL est restauratrice via la co-régulation sociale. → [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
Elle a des **conditions d'existence** : discipline sur l'exposition au stress, disponibilité relationnelle.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget satisfait = condition d'accès (la co-régulation nécessite une disponibilité) |
| **L3 → L0** | ascendant ✅ | Co-régulation sociale → restaure L0 · Fredrickson (Broaden-and-Build) → [[Fondements théoriques/07 — Self-compassion]] |
| **L1 → L3** | descendant | Appartenance + Compétence générateurs |
| **L3 → L1** | ascendant ✅ | Renforce tous les L1 générateurs · renforce "je suis une ressource pour ceux qui comptent" |
| **L2 → L3** | descendant | Aucun L2 défensif actif |
| **L3 → L2** | ascendant ✅ | Réduit la probabilité d'activation des L2 défensifs |
| **L3 → L4** | descendant | Contemplation · ralentissement · présence · partage |
| **L4 → L3** | ascendant ✅ | La présence active à l'autre renforce la Plénitude IRL |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

> La Plénitude IRL est un état à **créer les conditions** d'accès, pas à réguler.

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Discipline sur l'exposition au stress · créer des espaces de connexion authentique |
| 2 · Modification | oui | Co-présence de Sassa · moments de connexion réelle |
| 3 · Attentionnel | non | — |
| 4 · Reappraisal | non | — |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) — créer les conditions (protéger les espaces de connexion).
**Prix à payer :** sortir de cette bulle vient avec une frustration. C'est de la biologie, pas un signe que c'était faux.

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
> > [!note]- Déclencheurs documentés
> > - Sentiment de s'être rendu utile pour quelque chose d'important pour une personne chère
> > - Connexion empathique sur les vulnérabilités · questionnement sur la vie

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
> > [!note]- Réactions documentées
> > - Contemplation · ralentissement du rythme de vie · introspection avec discours interne

> [!success] 4. Prix à payer
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Prix à payer"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Prix à payer"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: J'accepte que ce que je pense avoir été utile ne l'est peut-être pas pour la personne en face]
> > - [ ] [Prix à payer:: J'accepte que sortir de cette bulle vient souvent avec une frustration — c'est de la biologie]
> > - [ ] [Prix à payer:: J'accepte que entretenir cet état demande une discipline sur l'exposition au stress]

---

## VII. Analyse à froid

> [!abstract]
> **Conditions d'existence :**
> Quelles situations, personnes, moments produisent régulièrement la Plénitude IRL ? Documenter pour la cultiver intentionnellement.
>
> **Le transfert :**
> La Plénitude IRL nourrit directement la Plénitude in-game via le renforcement de l'identité. Un homme qui se sent utile et connecté joue depuis une identité pleine — pas depuis un vide à combler par la performance.

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
> > - [ ] [Plan d'action:: Documenter les conditions d'existence de cet état — construire la base de reconvocation]

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
- [[Plénitude]] · [[Sérénité]] · [[Certitude]]
- [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
- [[L1 - Structures profondes/03 — Besoin d'Appartenance]]
