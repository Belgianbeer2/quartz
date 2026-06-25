---
type: fiche_emotion
tags: [L3, émotion, peur, résultats, inner-mapping]
L3_nom: "Peur"
L3_valence: "négative"
L3_arousal: "haute"
BIS_BAS: "BIS↑↑ BAS↓"
L1_déclencheurs: ["Besoin de Compétence défensif (Résultats-dépendance)"]
L2_déclencheurs: ["[[04 — Calibration temporelle -- Vision zoomée]]", "[[03 — Reconstruction mémorielle -- Sélectivité mémorielle]]", "[[05 — Évaluation du soi -- Pensée binaire]]"]
L4_comportements: ["Retrait · Évitement · Ne pas lancer de session · Étude compulsive"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 😨 Peur

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Peur]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — LeDoux (1996) · Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]] · [[Fondements théoriques/04 — Voie rapide & voie lente]]
> La Peur s'active via deux circuits :
> **Low road** (~12ms) : réaction viscérale immédiate avant tout traitement cognitif. Un bad beat brutal peut déclencher la Peur avant même de pouvoir nommer.
> **High road** (~300ms+) : construction progressive à partir de l'interprétation. La Peur des résultats financiers opère principalement ici — construite par les L2 (Vision zoomée, Sélectivité mémorielle, Pensée binaire). [documenté — LeDoux · [[Fondements théoriques/04 — Voie rapide & voie lente]]]
>
> La Peur construite via le high road semble rationnelle (elle s'accompagne d'un raisonnement) mais le raisonnement vient après — il justifie la Peur, il ne la génère pas.

**Valence :** négative
**Arousal :** haute — activation du système de menace
**Action tendency :** retrait · évitement · fuir la situation menaçante

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑↑ très actif — menace financière/identitaire détectée → inhibition forte
- **BAS :** ↓ bas — le retrait éteint le drive d'approche
- **Combinaison :** BIS dominant → paralysie · retrait · ne pas lancer

**Distinction Peur vs Honte [documenté — Alexis] :**

| | **Peur** | **[[La Honte]]** |
|---|---|---|
| **Objet** | Résultat financier · variance · bad run | Qualité de jeu perçue · identité |
| **Trigger** | Session perdante · résultat sous les attentes | Comportement in-game déviant |
| **Message** | *"Je vais perdre · je ne suis pas viable"* | *"Je SUIS défaillant"* |
| **Action tendency** | Retrait · évitement · fuite | Rumination · paralysie |

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** gorge serrée · poitrine comprimée · estomac noué
> - **Rythme cardiaque :** accéléré · irrégulier
> - **Respiration :** courte · superficielle · retenue
> - **Posture spontanée :** corps contracté · légère tendance à l'effacement
> - **Sensations spécifiques :** vigilance accrue · "quelque chose ne va pas" · tension diffuse

> [!warning] Signaux cognitifs précoces
> - *"Je vais perdre"* / *"Le système est cassé"* / *"Je ne suis pas viable"*
> - Reconstruction biaisée de la session : seules les pertes sont mémorisées
> - Vision zoomée active : 3-5 sessions = "tendance"

> [!warning] Signaux comportementaux précoces
> - Ne pas lancer la session prévue
> - Consulter obsessionnellement les résultats récents
> - Étude compulsive compensatoire

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Compétence (Résultats-dépendance) | La confiance est liée aux résultats financiers → mauvais résultats = menace identitaire + financière |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : les résultats *révèlent* la compétence → un bad run révèle une entité déficiente → Peur amplifiée.
- **Mastery thinking** : les résultats sont de la variance → la Peur des résultats diminue structurellement avec l'ancrage mastery.

#### L2 — Schémas déclencheurs (triple activation)

| Schéma L2 | Mécanisme |
|---|---|
| Vision zoomée (L2/04) | 3-5 sessions = tendance → "le système est cassé" |
| Sélectivité mémorielle (L2/03) | Reconstruit la session comme echec total → confirme la Peur |
| Pensée binaire (L2/05) | Produit le verdict identitaire "je ne suis pas viable" → amplifie la Peur |

#### L0 — Influence

Budget épuisé → BIS encore plus actif → Peur plus intense. Sous L0 bas, ne pas consulter les résultats récents. → [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → BIS encore plus actif → Peur plus intense |
| **L3 → L0** | ascendant ⚠️ | Peur chronique → activation HPA → dépense L0 |
| **L1 → L3** | descendant | Compétence défensif (Résultats-dépendance) |
| **L3 → L1** | ascendant ⚠️ | Répétée → renforce "mes résultats définissent ma valeur" |
| **L2 → L3** | descendant | Vision zoomée + Sélectivité mémorielle + Pensée binaire (triple activation) |
| **L3 → L2** | ascendant | La Peur active la Sélectivité mémorielle (confirmer la menace) |
| **L3 → L4** | descendant | Retrait · ne pas lancer · évitement |
| **L4 → L3** | ascendant ⚠️ | Le retrait confirme la menace (pas de session = pas de réfutation) |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Ne pas lancer de session depuis cet état · attendre BE + HM |
| 2 · Modification | non | — |
| 3 · Attentionnel | oui | *"Sur quelle fenêtre est-ce que j'évalue ça ?"* — ramener 4-6 mois |
| 4 · Reappraisal | oui | *"La variance n'est pas un verdict — 3 sessions ne suffisent pas à conclure"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Attentionnel (3) — ramener la fenêtre temporelle correcte.
**Note L0 :** sous budget bas, Sélection (1) uniquement — ne pas lancer, ne pas analyser les résultats.

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
> > - [ ] [Prix à payer:: J'accepte que la variance fait partie du jeu — une session perdante n'est pas une information sur mon niveau]
> > - [ ] [Prix à payer:: J'accepte de ne pas lancer de session depuis un état de Peur des résultats]

---

## VII. Analyse à froid

> [!abstract]
> **L1 actif :** Résultats-dépendance — la confiance est liée aux résultats financiers, pas au processus.
> **L2 actifs :** Vision zoomée · Sélectivité mémorielle · Pensée binaire — triple activation.
> **L'objet :** financier et identitaire : *"je ne suis pas viable"* / *"le système est cassé"* — distinct de la [[La Honte]] dont l'objet est la qualité de jeu perçue.
>
> **La Peur est l'appui L1 de la boucle de mal-être [documenté — Boussole émotionnelle].** Tout le travail de l'Inner Mapping vise à changer cet appui de Peur → Confiance.

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
> > - [ ] [Plan d'action:: Nommer la Peur → identifier le L2 actif (Vision zoomée ? Pensée binaire ?) → ramener la fenêtre temporelle correcte (4-6 mois)]
> > - [ ] [Plan d'action:: Ne pas lancer de session depuis cet état — viser BE+HM d'abord]

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
- [[La Honte]] — distinction Peur (objet financier) vs Honte (objet identitaire)
- [[04 — Calibration temporelle -- Vision zoomée]] · [[03 — Reconstruction mémorielle -- Sélectivité mémorielle]]
- [[05 — Évaluation du soi -- Pensée binaire]]
- [[Fondements théoriques/04 — Voie rapide & voie lente]]
- [[01 — Résultat négatif → Peur → Retrait]] · [[🧭 Boussole émotionnelle]]
