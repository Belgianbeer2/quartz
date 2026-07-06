---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Enthousiasme"
L3_valence: "positive"
L3_arousal: "haute"
BIS_BAS: "BAS↑↑ BIS↓"
L1_déclencheurs: ["Besoin de Compétence générateur", "Besoin d'Autonomie générateur"]
L2_déclencheurs: ["[[06 — Évaluation de l'enjeu -- Piédestal (précurseur potentiel si enjeu monte)]]"]
L4_comportements: ["Engagement immédiat · Partage · Créativité · Augmentation du volume (risque Piédestal)"]
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

# ⚡ Enthousiasme

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Enthousiasme]`*");
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
> L'Enthousiasme est construit quand le cerveau applique le concept 'je suis emballé' à un affect positif à haute arousal. C'est une émotion d'élan pur — moins ciblée que la Détermination, moins stable que la Certitude. Sa particularité : elle peut basculer vers le Piédestal si l'enjeu perçu monte avec elle. [documenté]

**Valence :** positive
**Arousal :** haute
**Action tendency :** Engagement immédiat · partage · créativité · augmentation du volume (risque à surveiller)

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — inhibition réduite, élan maximal
- **BAS :** ↑↑ très actif — drive d'approche fort et diffus
- **Combinaison :** BAS dominant fort → état d'élan pur · risque de Piédestal si l'enjeu gonfle avec l'Enthousiasme

**Distinction des émotions proches :**
vs **[[Détermination]]** : la Détermination est ciblée sur un objectif précis. L'Enthousiasme est plus diffus — engagement de surface haute mais sans cible unique.
vs **[[Certitude]]** : la Certitude est ancrée et stable. L'Enthousiasme est excité et moins stable.
vs **Piédestal (L2/06)** : l'Enthousiasme est l'état L3. Le Piédestal est le L2 défensif qui peut être déclenché par l'Enthousiasme quand l'enjeu perçu monte.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!success] Signaux corporels
> - **Zone de sensation :** énergie diffuse dans tout le corps · légèreté des membres
> - **Rythme cardiaque :** accéléré
> - **Respiration :** plus rapide · ample
> - **Posture spontanée :** corps ouvert · regard animé · sourire spontané · mouvement
> - **Sensations spécifiques :** envie de bouger · de parler · de commencer immédiatement

> [!success] Signaux cognitifs précoces
> - *"C'est génial"* / *"Je veux commencer tout de suite"* / *"Ça va être super"*
> - Pensées rapides qui sautent d'une idée à l'autre
> - Plans qui se forment avant même d'évaluer

> [!success] Signaux comportementaux précoces
> - Lancement immédiat sans préparation
> - Partage spontané avec l'entourage
> - Augmentation du volume ou des tables (signal d'alerte Piédestal)

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Générateur** | Besoin de Compétence | Opportunité perçue comme alignée avec la croissance → élan pur |
| **Générateur** | Besoin d'Autonomie | Initiative libre → engagement sans contrainte → Enthousiasme |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Mastery thinking** : l'Enthousiasme reste un état productif. L'élan est utilisé sans besoin de 'ne pas gâcher'.
- **Entity thinking** : transforme l'Enthousiasme en Piédestal. *"Aujourd'hui je suis en forme — je dois saisir ça."* → enjeu monte → anxiété → contre-performance. → [[06 — Évaluation de l'enjeu -- Piédestal]]

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Piédestal (L2/06) | L'Enthousiasme peut déclencher le Piédestal si entity thinking est actif : *"aujourd'hui est une opportunité unique à ne pas rater"* |

#### L0 — Influence
L'Enthousiasme peut masquer un L0 bas sous adrénaline. Vérifier si l'énergie est réelle (budget satisfait) ou compensatoire (budget épuisé + adrénaline).

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget satisfait = Enthousiasme durable · Budget épuisé + adrénaline = faux Enthousiasme |
| **L3 → L0** | ascendant ⚠️/✅ | Enthousiasme calibré → énergisant · Enthousiasme excessif → épuisement accéléré |
| **L1 → L3** | descendant | Compétence + Autonomie générateurs |
| **L3 → L1** | ascendant ✅ | Renforce 'je peux m'engager pleinement' |
| **L2 → L3** | descendant | — |
| **L3 → L2** | ascendant ⚠️ | Peut déclencher le Piédestal si entity thinking actif |
| **L3 → L4** | descendant | Engagement immédiat · partage · augmentation du volume |
| **L4 → L3** | ascendant ✅ | L'engagement productif renforce l'Enthousiasme |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Warmup avant de lancer : nommer l'Enthousiasme · évaluer le risque Piédestal |
| 2 · Modification | oui | Réduire les tables si Enthousiasme très élevé — éviter la surexposition |
| 3 · Attentionnel | oui | *"Je joue depuis moi — pas pour l'image de cet élan"* |
| 4 · Reappraisal | oui | *"Cet Enthousiasme est une ressource, pas une opportunité unique à saisir absolument"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Sélection (1) en warmup — nommer l'Enthousiasme et évaluer le risque Piédestal avant de lancer.
**Note L0 :** vérifier si l'énergie est réelle (L0 satisfait) ou adrénaline compensatoire (L0 bas).

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
> > - [ ] [Prix à payer:: J'accepte que l'Enthousiasme est une ressource — pas une opportunité unique à ne pas rater]

---

## VII. Analyse à froid

> [!abstract]
> **Enthousiasme ou début de Piédestal ?**
Question pivot : *"Est-ce que cet élan me donne envie de jouer — ou est-ce que je sens que je 'dois' saisir cette opportunité ?"*
- Envie de jouer → Enthousiasme → ressource
- Devoir saisir → Piédestal → risque → [[06 — Évaluation de l'enjeu -- Piédestal]]

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
> > - [ ] [Plan d'action:: Nommer l'Enthousiasme au warmup → évaluer risque Piédestal → lancer depuis l'identité, pas depuis l'élan]

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
- [[Détermination]] · [[Certitude]]
- [[06 — Évaluation de l'enjeu -- Piédestal]]
- [[L1 - Structures profondes/01 — Besoin de Compétence]]
