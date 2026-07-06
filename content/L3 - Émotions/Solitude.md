---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Solitude"
L3_valence: "négative"
L3_arousal: "basse"
BIS_BAS: "BAS↓ BIS neutre-bas"
L1_déclencheurs: ["Besoin d'Appartenance défensif (manque structurel)"]
L2_déclencheurs: ["[[01 — Mentalisation -- Dissociation (peut amplifier la Solitude par projection négative)]]"]
L4_comportements: ["Retrait · Réduction des activités sociales · Introspection · Compensation par l'hyperactivité (fuite)"]
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

# 🌒 Solitude

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Solitude]`*");
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
> La Solitude est construite quand le cerveau applique le concept 'absence de lien' à un affect négatif à faible arousal. Contrairement au Délaissement (connexion refusée dans une relation existante), la Solitude est une absence structurelle de connexion disponible — pas un rejet, mais un vide. [documenté — Williams 2001 · Barrett 2017]

**Valence :** négative
**Arousal :** basse
**Action tendency :** Retrait · réduction des activités sociales · recherche de connexion différée

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre-bas — pas de menace active, absence de signal positif
- **BAS :** ↓ bas — drive d'approche réduit faute de cible disponible
- **Combinaison :** BAS/BIS tous deux bas → apathie douce · état de récupération isolée
- **Distinction vs Délaissement :** le Délaissement active le BIS (connexion refusée = menace). La Solitude n'active pas le BIS — il n'y a pas de refus, juste une absence.

**Distinction des émotions proches :**
vs **[[Délaissement]]** : le Délaissement est une connexion refusée dans une relation existante (BIS activé). La Solitude est l'absence structurelle de connexion (BIS neutre). Plus facile à traiter car pas de dimension relationnelle blessante.
vs **[[Accablement]]** : l'Accablement est une phase post-sortie de fenêtre envahissant L1-L4. La Solitude est plus ciblée sur le manque relationnel.
vs **Tristesse** : la Tristesse répond à une perte identifiable. La Solitude peut exister sans événement déclencheur précis.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de sensation :** vide dans la poitrine · légèreté paradoxale (absence de stimulation)
> - **Rythme cardiaque :** ralenti, régulier
> - **Respiration :** lente, profonde, régulière
> - **Posture spontanée :** corps légèrement affaissé · regard interne · mouvements ralentis
> - **Sensations spécifiques :** 'le silence pèse' · absence de stimulation extérieure · sentiment d'être dans une bulle

> [!warning] Signaux cognitifs précoces
> - *"Il n'y a personne"* / *"Je suis seul"* (factuel, pas accusateur)
> - Pensées qui cherchent quelqu'un à qui parler
> - Silence interne plus présent que d'habitude

> [!warning] Signaux comportementaux précoces
> - Consultation des contacts sans envoyer de message
> - Augmentation du temps d'écran comme substitut de connexion
> - Ralentissement général des activités

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin d'Appartenance | Isolement géographique (Siem Reap) + barrière linguistique + contexte poker solitaire → absence structurelle de connexion spontanée |
| **Contexte** | Besoin de Co-régulation (L0/03) | L'absence de co-régulation sociale disponible → budget L0 se restaure moins bien → Solitude amplifie les autres états négatifs |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : peut amplifier la Solitude en interprétant l'absence de connexion comme un signal sur sa propre valeur relationnelle. *"Je suis seul parce que je ne suis pas quelqu'un avec qui on a envie de passer du temps."*
- **Mastery thinking** : traite la Solitude comme une contrainte contextuelle. *"Je suis seul parce que mes conditions de vie créent un isolement structurel — pas parce que je manque de valeur relationnelle."*

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Dissociation (L2/01) | Peut amplifier la Solitude en construisant des interactions imaginaires négatives avec des personnes absentes |

#### L0 — Influence
La Solitude réduit la co-régulation sociale disponible → le budget L0 se restaure moins bien. Cercle possible : Solitude → L0 plus épuisé → états négatifs amplifiés → plus difficile de chercher connexion. → [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → Solitude plus intense (co-régulation encore plus nécessaire) |
| **L3 → L0** | ascendant ⚠️ | Absence de co-régulation → budget se restaure moins bien · risque de cercle vicieux |
| **L1 → L3** | descendant | Besoin d'Appartenance défensif (manque structurel) → Solitude |
| **L3 → L1** | ascendant | Solitude prolongée → peut renforcer l'Appartenance défensive |
| **L2 → L3** | descendant | Dissociation peut amplifier par projections négatives sur les absents |
| **L3 → L2** | ascendant | La Solitude peut activer Confabulation (construire des narrative sur pourquoi on est seul) |
| **L3 → L4** | descendant | Retrait · hyperactivité de fuite · consultation des contacts |
| **L4 → L3** | ascendant ✅ | Micro-connexion (message, appel court) réduit la Solitude |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Planifier des micro-connexions régulières (appel famille, contact Alexis) |
| 2 · Modification | oui | Co-présence physique avec Sassa même sans interaction intense |
| 3 · Attentionnel | partiel | Orienter vers les connexions disponibles plutôt que vers l'absence |
| 4 · Reappraisal | oui | *"Je suis seul par contrainte contextuelle — pas par manque de valeur relationnelle"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) + Modification (2) — la Solitude se résout par la connexion, pas par la réflexion.
**Note L0 :** sous budget bas, Modification (2) d'abord — co-présence physique même passive.

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
> > - [ ] [Prix à payer:: J'accepte que l'isolement géographique crée une Solitude structurelle — ce n'est pas un jugement sur ma valeur relationnelle]

---

## VII. Analyse à froid

> [!abstract]
> **Solitude structurelle ou construite ?**
*"Est-ce que je suis seul parce que les conditions créent cet isolement — ou est-ce que je construis cette Solitude en me retirant activement ?"*

**Co-régulation disponible ?**
Sassa est présente. La co-présence passive (même sans conversation intense) est de la co-régulation. → [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]

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
> > - [ ] [Plan d'action:: Identifier une micro-connexion accessible (message, appel court) → agir dessus plutôt que de rester dans la Solitude]

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
- [[Délaissement]] · [[Accablement]]
- [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
- [[L1 - Structures profondes/03 — Besoin d'Appartenance]]
