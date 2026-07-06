---
type: fiche_emotion
tags: [L3, émotion, agacement, inner-mapping]
L3_nom: "Agacement"
L3_valence: "négative"
L3_arousal: "basse-moyenne"
BIS_BAS: "BIS↑léger BAS neutre"
L1_déclencheurs: ["Besoin d'Autonomie (léger — empiètement sur l'espace de concentration)"]
L2_déclencheurs: []
L4_comportements: ["Gestes secs · Évitement de l'irritant · Décision précipitée (si in-game)"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log = dv.page("log — Drill 02 — Rétrospective accumulation");
const nomFiche = dv.current().file.name;
if (!log || !log.entries) {
    dv.paragraph("*Aucune donnée Drill 02.*");
} else {
    const relevant = log.entries.filter(e => e.emotion === nomFiche);
    if (relevant.length === 0) {
        dv.paragraph("*Aucune activation Drill 02 liée à cette émotion pour l'instant.*");
    } else {
        const fenetreColor = (f) => {
            if (!f) return "#555";
            if (String(f).includes("Très")) return "#e74c3c";
            if (String(f).includes("Réduite")) return "#FF9500";
            return "#2ecc71";
        };
        let html = "";
        relevant.sort((a, b) => moment(b.d, "MM-DD-YYYY").valueOf() - moment(a.d, "MM-DD-YYYY").valueOf()
        ).forEach(e => {
            const f = String(e.fenetre || "").trim();
            const signaux = e.signal ? String(e.signal).split("·").map(s => s.trim()).filter(s => s) : [];
            html += `<div style="border-left:3px solid ${fenetreColor(f)};padding:8px 12px;margin-bottom:8px;background:rgba(255,255,255,0.02);border-radius:0 4px 4px 0;">
                <div style="display:flex;justify-content:space-between;margin-bottom:6px;">
                    <span style="color:#6edff6;font-size:12px;font-weight:bold;">${e.d || "—"}</span>
                    <span style="color:${fenetreColor(f)};font-size:11px;">Fenêtre ${f || "—"}</span>
                </div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Frictions : <span style="color:#ccc;">${e.frictions || "—"}</span></div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Signaux : <span style="color:#BB86FC;">${signaux.join(" · ") || "—"}</span></div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Action : <span style="color:#ccc;">${e.action || "—"}</span></div>
                <div style="font-size:11px;color:#888;">Résultat : <span style="color:#aaa;">${e.resultat || "—"}</span></div>
            </div>`;
        });
        dv.paragraph(`*${relevant.length} activation(s) Drill 02 liée(s)*`);
        dv.container.createEl("div").innerHTML = html;
    }
}
```

# 😒 Agacement

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Agacement]`*");
> ```

> [!note]- 📅 Jours concernés — O&R 
>```dataviewjs 
> let p = dv.current();
> let targetEmotion = p.file.name;
> 
> let orPage = dv.page("📝 observation et ressentis");
> if (!orPage) { dv.paragraph("*⚠️ Fichier O&R introuvable.*"); return; }
> 
> let content = await dv.io.load(orPage.file.path);
> 
> // Découpe par sections ## DATE (gère le double espace)
> let sections = content.split(/\n##\s+/);
> let matches = [];
> 
> let dateRe = /^(\d{2}-\d{2}-\d{4})/;
> // Escape les caractères spéciaux du nom de la fiche pour le regex
> let escaped = targetEmotion.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
> let tagRe = new RegExp("\\[emotion::[^\\]]*" + escaped + "[^\\]]*\\]", "i");
> 
> for (let section of sections) {
>     let firstLine = section.split('\n')[0].trim();
>     let dateMatch = firstLine.match(dateRe);
>     if (dateMatch && tagRe.test(section)) {
>         matches.push(dateMatch[1]);
>     }
> }
> 
> if (matches.length === 0) {
>     dv.paragraph("*Aucun O&R lié — tagger avec `[emotion:: " + targetEmotion + "]` dans l'O&R.*");
>     return;
> }
> 
> matches.sort().reverse();
> let rows = matches.map(date => {
>     let allMR = dv.pages('"Journal/Morning routine logs/2026"').where(p => p.file.name === date + " Morning routine"); let mrPage = allMR.length > 0 ? allMR[0] : null;
>     return [date, mrPage ? mrPage.file.link : "*" + date + " (MR introuvable)*"];
> });
> dv.table(["Jour", "Morning Routine"], rows);
> ```
---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> L'Agacement est construit quand le cerveau applique le concept "quelque chose me dérange" à un affect négatif à faible arousal, en réponse à un **irritant environnemental répété**. Ce n'est pas un objectif bloqué (ce serait la Frustration) — c'est un stimulus non désiré persistant qui consomme de l'attention sans raison valable. Le cerveau cherche à éliminer l'irritant, pas à atteindre un objectif. [documenté — inféré depuis Barrett 2017]

**Valence :** négative
**Arousal :** basse-moyenne — tension légère, pas d'explosion

**Deux lectures à toujours distinguer :**

> [!warning] Lecture 1 — Agacement standalone
> L'irritant existe réellement et a une cause neutre (bruit, chaleur, adversaire lent). Le budget L0 est normal. L'Agacement est une réponse proportionnée à un stimulus non désiré.
> → Stratégie : retirer l'irritant ou modifier l'environnement.

> [!warning] Lecture 2 — Agacement comme signal L0
> *"Tout m'énerve, quart de tour"* [documenté — Accablement 11-13/06/2026] — le seuil de tolérance aux irritants s'est effondré. Des stimuli normalement anodins (Lucky qui aboie, la chaleur, un adversaire lent) déclenchent une réaction disproportionnée. C'est le budget L0 qui parle, pas l'irritant.
> → Stratégie : traiter L0, pas l'irritant.

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ léger — signal d'intrusion non désirée dans l'espace de concentration
- **BAS :** neutre — pas d'objectif actif bloqué (sinon ce serait la Frustration)
- **Combinaison :** BIS léger sans BAS frustré → irritation légère sans élan vers l'action

**Distinction des émotions proches :**

| | **Agacement** | **[[Frustration]]** |
|---|---|---|
| **Mécanisme** | Irritant externe non désiré | Objectif actif bloqué par un obstacle |
| **BAS** | Neutre | ↑ actif + bloqué |
| **Arousal** | Basse-moyenne | Moyenne-haute |
| **Objet** | Stimulus non désiré (bruit, chaleur, lenteur) | Résultat non atteint (variance, bad beat) |
| **Action tendency** | Retirer/éviter l'irritant | Trouver un autre passage |

vs **[[Colère]]** : l'Agacement est en dessous de la Frustration dans la hiérarchie d'activation. Agacement < Frustration < Colère en intensité. Si non régulé, l'Agacement peut monter vers la Frustration puis la Colère.

vs **[[Doute]]** : le Doute a un BIS léger sur une incertitude interne (processuelles). L'Agacement a un BIS léger sur un irritant externe.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** légère tension dans les épaules et la nuque · front légèrement plissé · mâchoire qui se serre imperceptiblement
> - **Rythme cardiaque :** normal à très légèrement accéléré
> - **Respiration :** légèrement retenue · légère tension dans le diaphragme
> - **Posture spontanée :** légère raideur · gestes qui deviennent plus secs
> - **Sensations spécifiques :** "ça frotte" · légère hypersensibilité aux stimuli · impression que tout prend plus d'espace qu'il ne le devrait

> [!warning] Signaux cognitifs précoces
> - *"Encore ce son"* / *"Pourquoi il met autant de temps ?"* / *"Lucky, ça suffit"*
> - Attention qui se divise malgré soi entre la tâche et l'irritant
> - Si L0 bas : *"Tout m'énerve"* / *"Je n'ai pas la patience"*

> [!warning] Signaux comportementaux précoces
> - Gestes qui deviennent plus secs (clic de souris, frappe clavier)
> - Regarder vers la source de l'irritant de façon répétée
> - In-game : légère accélération de la prise de décision sans raison technique

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Léger défensif** | Besoin d'Autonomie | L'irritant empiète sur l'espace de concentration ou d'action sans consentement → BIS léger |
| **Signal L0** | — (pas de L1 spécifique) | Quand L0 est épuisé, le seuil de tolérance à tous les irritants s'effondre → l'Agacement n'est pas causé par un L1 mais par l'épuisement du substrat |

> [!abstract] L'Agacement comme proxy L0 · [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
> La corrélation est documentée : plus le budget L0 est épuisé, plus le seuil d'agacement est bas. *"Quart de tour"* = proxy indirect d'un L0 critique.
> **Règle pratique :** si l'intensité de l'Agacement est disproportionnée à la source → ce n'est pas l'irritant qu'il faut traiter, c'est L0.

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- L'Agacement standalone est peu lié à l'entity/mastery — c'est pré-cognitif.
- Sous entity thinking actif, l'Agacement peut basculer vers la Frustration plus vite : *"il me ralentit intentionnellement"* (confabulation de l'irritant en obstacle personnel).

#### L2 — Schémas déclencheurs

Aucun L2 défensif spécifique ne déclenche l'Agacement — il est typiquement pré-cognitif. Mais l'Agacement peut activer la Confabulation (L2/02) si le cerveau cherche une explication personnelle à l'irritant.

#### L0 — Influence

**C'est la connexion principale.** L'Agacement n'est pas seulement influencé par L0 — il peut **révéler** l'état de L0.

**Contexte Siem Reap spécifique :**
- Chaleur → seuil d'agacement plus bas · impact cognitif direct (→ [[01 — Angles morts & évolutions]] : impact de la chaleur sur les capacités cognitives)
- Lucky qui aboie → irritant prévisible · gérable par modification (Drill 01 baseline : noter comme signal L0 si réaction disproportionnée)
- Bruit de la rue · connexion Internet instable · adversaires lents → irritants structurels à anticiper

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → seuil d'agacement effondré · "quart de tour" · hypersensibilité généralisée |
| **L3 → L0** | ascendant ⚠️ | Agacement soutenu → légère consommation attentionnelle · si non régulé → montée vers Frustration → dépense L0 accélérée |
| **L1 → L3** | descendant | Autonomie léger (empiètement sur l'espace de concentration) |
| **L3 → L1** | ascendant | Rarement — l'Agacement ne renforce pas durablement les L1 sauf s'il monte en Frustration |
| **L2 → L3** | descendant | — (pré-cognitif dans la plupart des cas) |
| **L3 → L2** | ascendant | Peut activer la Confabulation (inventer une raison personnelle à l'irritant) |
| **L3 → L4** | descendant | Gestes secs · évitement · décision précipitée in-game |
| **L4 → L3** | ascendant ✅ | Retirer l'irritant (casque, fermer la porte) → réduit l'Agacement directement |

**Cascade typique sous L0 bas :**
Chaleur + Lucky + adversaire lent → Agacement disproportionné → non nommé → Frustration → Colère → tilt

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Anticiper les irritants prévisibles avant la session (casque, ventilateur, heure calme) |
| 2 · Modification | oui | **LA stratégie principale** : retirer ou réduire l'irritant directement · fermer la porte · mettre le casque · changer de pièce |
| 3 · Attentionnel | oui | *"Est-ce que cet irritant m'affecte vraiment — ou est-ce mon L0 qui m'hypersensibilise ?"* |
| 4 · Reappraisal | partiel | *"Cet agacement disproportionné est un signal L0 — pas un problème réel avec [l'irritant]"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire selon la lecture :**
- **Agacement standalone** → Modification (2) — retirer l'irritant. Simple, efficace.
- **Agacement signal L0** → Attentionnel (3) d'abord pour identifier → puis traitement L0 (Drill 01 baseline, repos, hydratation)

**Note L0 :** si l'Agacement est disproportionné à la source → ne pas traiter l'irritant, traiter L0.

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
> > [!note]- Déclencheurs documentés à froid
> > - Lucky qui aboie pendant une session
> > - Chaleur de Siem Reap
> > - Adversaire lent (timebank systématique)
> > - Connexion Internet instable
> > - Bruit de la rue
> > - *"Les bains m'énervent, je n'ai pas la patience"* [documenté — Accablement 11-13/06/2026 = signal L0 critique]

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
> > - [ ] [Prix à payer:: J'accepte que Lucky, la chaleur et les adversaires lents font partie de mon environnement — je les anticipe plutôt que les subis]
> > - [ ] [Prix à payer:: J'accepte qu'un agacement disproportionné est un signal L0 — pas un problème réel avec l'irritant]

---

## VII. Analyse à froid

> [!abstract]
> **Question pivot — standalone ou signal L0 ?**
> *"Est-ce que cet irritant me dérange normalement à cette intensité — ou est-ce que ma réaction est disproportionnée à sa cause ?"*
> - Proportionnée → Agacement standalone → retirer l'irritant
> - Disproportionnée → signal L0 → traiter L0 d'abord
>
> **Corrélation documentée :**
> L0 satisfait → Lucky qui aboie = nuisance mineure.
> L0 épuisé → Lucky qui aboie = "quart de tour".
> L'irritant n'a pas changé. Le budget a changé.
>
> **Irritants structurels à anticiper dans le contexte Siem Reap :**
> La chaleur · Lucky · le bruit de la rue ne vont pas disparaître. Les stratégies Gross 1-2 (anticipation + modification) sont plus efficaces que de les subir et d'essayer de les réguler in-game.

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
> > - [ ] [Plan d'action:: Identifier la lecture (standalone vs signal L0) → si disproportionné : Drill 01 baseline]
> > - [ ] [Plan d'action:: Irritants structurels (chaleur, Lucky, bruit) : casque + ventilateur + heure calme — anticiper avant la session]
> > - [ ] [Plan d'action:: In-game : si agacement détecté → vérifier si décision suivante est accélérée sans raison technique]

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

---

## Notes liées
- [[Frustration]] — distinction : BAS bloqué vs irritant externe
- [[Accablement]] — *"quart de tour"* comme signal L0 critique
- [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
- [[01 — Angles morts & évolutions]] — impact de la chaleur sur les capacités cognitives
- [[Protocoles/Transversaux/log — Drill 01 — Baseline]] — noter l'agacement disproportionné comme signal L0
