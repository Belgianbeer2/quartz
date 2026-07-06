---
type: fiche_emotion
tags: [L3, émotion, frustration, inner-mapping]
L3_nom: "Frustration"
L3_valence: "négative"
L3_arousal: "moyenne-haute"
BIS_BAS: "BAS↑ bloqué BIS neutre"
L1_déclencheurs: ["Besoin d'Autonomie défensif", "Besoin de Compétence défensif"]
L2_déclencheurs: ["[[02 — Évaluation causale -- Confabulation (invente une causalité personnelle)]]"]
L4_comportements: ["Signal précoce · Pression croissante · Alimentation de la Colère si non nommée"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 😤 Frustration

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Frustration]`*");
> ```

> [!note]- 📅 Jours concernés — O&R
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> let orPage = dv.page("📝 observation et ressentis");
> if (!orPage) {
>     dv.paragraph("*⚠️ Fichier O&R introuvable.*");
> } else {
>     let content = await dv.io.load(orPage.file.path);
>     let sections = content.split(/\n##\s+/);
>     let matches = [];
>     let dateRe = /^(\d{2}-\d{2}-\d{4})/;
>     let escaped = targetEmotion.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
>     let tagRe = new RegExp("\\[emotion::[^\\]]*" + escaped + "[^\\]]*\\]", "i");
>     for (let section of sections) {
>         let firstLine = section.split('\n')[0].trim();
>         let dateMatch = firstLine.match(dateRe);
>         if (dateMatch && tagRe.test(section)) {
>             matches.push(dateMatch[1]);
>         }
>     }
>     if (matches.length === 0) {
>         dv.paragraph("*Aucun O&R lié — tagger avec `[emotion:: " + targetEmotion + "]` dans l'O&R.*");
>     } else {
>         matches.sort().reverse();
>         let rows = matches.map(date => {
>             let allMR = dv.pages('"Journal/Morning routine logs/2026"').where(p => p.file.name === date + " Morning routine"); let mrPage = allMR.length > 0 ? allMR[0] : null;
>             return [date, mrPage ? mrPage.file.link : "*" + date + " (MR introuvable)*"];
>         });
>         dv.table(["Jour", "Morning Routine"], rows);
>     }
> }
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Carver (2001) · Moukheiber (2026) · [[Fondements théoriques/05 — BIS & BAS]] · [[Sources/01 — Albert Moukheiber × Les Lueurs]]
> La Frustration est construite quand le BAS actif rencontre un obstacle externe répété. C'est un état de **BAS cherchant un passage** — pas un effondrement mais une pression. Moukheiber : la Frustration pousse le cerveau à **inventer une causalité personnelle** là où il n'y a que du bruit structurel. *"Je dois laisser paraître des tells"* n'est pas une observation — c'est une reconstruction narrative du remembering self. [documenté]
>
> **La Frustration est le bol qui se remplit [documenté — Alexis].** Nommée à temps, elle reste de l'information. Non nommée, elle alimente la Colère.

**Valence :** négative
**Arousal :** moyenne-haute — pression qui monte
**Action tendency :** À documenter

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre — pas de menace active, juste un obstacle
- **BAS :** ↑ actif + bloqué — le drive existe mais ne peut pas avancer
- **Combinaison :** BAS bloqué → pression qui monte progressivement → si non régulée → Colère

**Distinction des émotions proches :**
vs **[[Colère]]** : la Colère est le bol qui a débordé. La Frustration est le bol qui se remplit — c'est le signal précoce.
vs **[[Impuissance]]** : l'Impuissance est l'absence totale de levier (BAS↓). La Frustration a un BAS encore actif — il cherche un passage.
vs **[[La Réactance]]** : la Réactance est spécifiquement liée à une menace sur la liberté d'action. La Frustration est plus générale (tout obstacle).

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** épaules · mâchoires · chaleur légère dans le cou
> - **Rythme cardiaque :** légèrement accéléré · irrégulier parfois
> - **Respiration :** plus courte · plus tendue · soupirs contenus
> - **Posture spontanée :** corps légèrement contracté · agitation des mains
> - **Sensations spécifiques :** "bol qui se remplit" · pression croissante · sensation de "encore ça"

> [!warning] Signaux cognitifs précoces
> - *"Je dois laisser paraître des tells"* / *"Encore un bad beat"* / *"De toute façon..."*
> - Reconstruction narrative : le cerveau réécrit chaque main à travers le prisme de l'obstacle
> - Causalité personnelle inventée là où il n'y a que de la variance

> [!warning] Signaux comportementaux précoces
> - Signal précoce : tension dans les épaules perceptible
> - Jeu légèrement contracté
> - Si non nommée : transition vers la Colère

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin d'Autonomie | Obstacle à l'action naturelle → BAS frustré |
| **Défensif** | Besoin de Compétence | Variance hostile = "confirmation" que quelque chose ne fonctionne pas |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie la Frustration en inventant une causalité personnelle. "Je dois faire quelque chose de travers."
- **Mastery thinking** : maintient la Frustration comme signal neutre. "C'est de la variance — le bol se remplit, je le nomme."

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Confabulation (L2/02) | Invente une causalité personnelle pour expliquer la variance (tells imaginaires, etc.) |

#### L0 — Influence
Budget épuisé → bol se remplit plus vite · seuil de Colère plus bas. Budget satisfait → Frustration nommée reste informationnelle.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → bol se remplit plus vite · transition Colère plus rapide |
| **L3 → L0** | ascendant ⚠️ | Frustration prolongée → tension chronique → consomme L0 |
| **L1 → L3** | descendant | Autonomie + Compétence défensifs |
| **L3 → L1** | ascendant | Non nommée → renforce "je ne contrôle pas" |
| **L2 → L3** | descendant | Confabulation amplifie en inventant des causes |
| **L3 → L2** | ascendant | Déclenche la Confabulation (besoin d'explication) |
| **L3 → L4** | descendant | Signal précoce · pression · si non nommée → Colère |
| **L4 → L3** | ascendant ✅ | Nommer la Frustration interrompt le cycle → reste informationnelle |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — |
| 2 · Modification | non | — |
| 3 · Attentionnel | oui | **LA stratégie clé** : nommer *"je suis en Frustration"* avant que le bol déborde |
| 4 · Reappraisal | partiel | *"C'est de la variance — pas un tells. C'est le bol qui se remplit."* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Attentionnel (3) — nommer la Frustration est la stratégie principale. La pression physiologique est le signal à détecter.
**Note L0 :** sous budget bas, nommer est plus difficile mais encore accessible.

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
> > - [ ] [Prix à payer:: J'accepte que la variance crée une pression — le bol se remplit, je le nomme]

---

## VII. Analyse à froid

> [!abstract]
> **La pression physiologique est le vrai signal.**
La clé n'est pas dans l'histoire mentale que la Frustration génère — elle est dans la **pression physiologique qui monte**. C'est ce signal (tension épaules, chaleur, respiration) qu'il faut apprendre à reconnaître avant que le bol déborde.

**Transition vers la Colère :** si la Frustration n'est pas nommée à temps, elle alimente la Colère. Le Drill 03 est disponible pour l'interrupt d'escalade si la transition est en cours.

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
> > - [ ] [Plan d'action:: Nommer *"je suis en Frustration"* → respiration · *"c'est de la variance"* · si le bol menace de déborder : Drill 03]

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

## Note — Lien Perfectionnisme

> Le [[L2 - Schémas Cognitifs/12 — Orientation vers l'idéal -- Perfectionnisme|Perfectionnisme]] est un **upstream L2** fréquent de la Frustration :
> - Il crée un gap structurel entre vision idéale et compétences réelles
> - Chaque imprévu ou imperfection vient frapper ce gap — le bol se remplit plus vite que d'habitude
> - La Frustration issue du Perfectionnisme est particulièrement difficile à nommer tôt car elle est masquée par l'énergie de l'engagement initial

## Notes liées
- [[Colère]] · [[La Réactance]] · [[Impuissance]]
- [[02 — Évaluation causale -- Confabulation]]
- [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]
