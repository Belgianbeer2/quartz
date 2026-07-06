---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Déception"
L3_valence: "négative"
L3_arousal: "basse-moyenne"
BIS_BAS: "BAS↓ BIS neutre"
L1_déclencheurs: ["Besoin de Compétence défensif (si rattaché à l'identité)"]
L2_déclencheurs: ["[[04 — Calibration temporelle -- Vision zoomée]]", "[[05 — Évaluation du soi -- Pensée binaire]]"]
L4_comportements: ["Retrait temporaire · Réévaluation des attentes · Abandon potentiel"]
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
# 😔 Déception

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Déception]`*");
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
> La Déception est construite quand le cerveau applique le concept 'l'objectif attendu n'est pas atteint' à un affect négatif à arousal basse. Contrairement à la Frustration (obstacle présent bloquant le BAS), la Déception est rétrospective — l'objectif était possible, il ne s'est pas réalisé. [documenté]

**Valence :** négative
**Arousal :** basse-moyenne
**Action tendency :** Retrait temporaire · réévaluation des attentes · éventuellement abandon si non régulée

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre — pas de menace active
- **BAS :** ↓ bas — signal que l'objectif attendu n'est pas atteint · élan qui retombe
- **Combinaison :** BAS qui se retire sans inhibition externe — fermeture de boucle négative

**Distinction des émotions proches :**
vs **[[Frustration]]** : la Frustration a un obstacle présent qui bloque (BAS actif + obstacle = énergie réactive). La Déception est une boucle fermée négativement — pas d'obstacle, juste l'absence du résultat attendu.
vs **[[Peur]]** : la Peur anticipe une menace future. La Déception constate un manque passé.
vs **[[Honte]]** : la Honte porte sur l'identité. La Déception porte sur un résultat spécifique — plus réparable si mastery thinking actif.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** épaules qui tombent · estomac creux · légère pesanteur thoracique
> - **Rythme cardiaque :** légèrement ralenti
> - **Respiration :** soupirs fréquents · ralentissement général
> - **Posture spontanée :** épaules en avant · regard vers le bas
> - **Sensations spécifiques :** pesanteur douce · 'tout à l'air plat'

> [!warning] Signaux cognitifs précoces
> - *"C'est dommage"* / *"J'aurais pu"* / *"Je pensais que ça allait marcher"*
> - Réévaluation spontanée de ce qui aurait pu être différent
> - Comparaison entre l'attendu et le réel

> [!warning] Signaux comportementaux précoces
> - Réduction d'activité temporaire · retrait léger
> - Réévaluation silencieuse des attentes
> - Tentation d'abandon si entity thinking actif

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Compétence | Résultat manqué traité comme révélation de l'entité → glissement vers la Honte |
| **Générateur** | Besoin de Compétence | Résultat manqué traité comme information sur le processus → réévaluation calibrée |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie la Déception vers la Honte. "Ce résultat révèle que je ne suis pas ce joueur."
- **Mastery thinking** : maintient la Déception comme information. "Ce résultat me dit que quelque chose dans mon processus n'a pas fonctionné — qu'est-ce que ça m'apprend ?"

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Vision zoomée (L2/04) | La déception sur une session est amplifiée si évaluée sur la mauvaise fenêtre temporelle |
| Pensée binaire (L2/05) | Produit un verdict identitaire depuis la Déception si entity thinking actif |

#### L0 — Influence
Budget épuisé → Déception plus intense et plus longue à récupérer. Budget satisfait → Déception plus légère, réévaluation plus accessible.

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → Déception plus intense · récupération plus lente |
| **L3 → L0** | ascendant ⚠️ | Déception persistante → légère dépense L0 via affect négatif chronique |
| **L1 → L3** | descendant | Besoin de Compétence défensif → amplifie vers Honte · générateur → réévaluation |
| **L3 → L1** | ascendant | Répétée sans régulation → peut renforcer la Compétence défensive |
| **L2 → L3** | descendant | Vision zoomée · Pensée binaire |
| **L3 → L2** | ascendant | La Déception peut activer la Rumination (rejouer ce qui aurait pu se passer autrement) |
| **L3 → L4** | descendant | Retrait · réévaluation · abandon potentiel |
| **L4 → L3** | ascendant | Le retrait temporaire peut permettre la récupération · l'abandon renforce la Déception |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Ne pas analyser la session sous état très dégradé |
| 2 · Modification | partiel | Changement d'environnement physique |
| 3 · Attentionnel | oui | *"Sur quelle fenêtre est-ce que j'évalue ce résultat ?"* |
| 4 · Reappraisal | oui | *"Ce résultat est de l'information sur mon processus — pas un verdict sur ce que je suis"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Reappraisal (4) — déplacer de l'identité vers le processus.
**Note L0 :** sous budget bas, Sélection (1) d'abord — ne pas analyser.

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
> > - [ ] [Prix à payer:: J'accepte que ce résultat est de l'information — pas un verdict]

---

## VII. Analyse à froid

> [!abstract]
> **Déception ou Honte ?**
Question pivot : *"Est-ce que je suis déçu du résultat — ou déçu de ce que je suis ?"*
- Résultat → Déception → traitable par réévaluation et ajustement
- Identité → Honte → traitement différent → [[Honte]]

**Quelle était l'attente initiale ?**
La Déception révèle toujours une attente. Quelle était-elle ? Était-elle calibrée ?

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
> > - [ ] [Plan d'action:: Nommer la Déception précisément → distinguer Déception (résultat) vs Honte (identité) → identifier une chose concrète à faire différemment]

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
- [[Honte]] · [[Frustration]] · [[Peur]]
- [[04 — Calibration temporelle -- Vision zoomée]] · [[05 — Évaluation du soi -- Pensée binaire]]
