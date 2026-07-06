---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "Tristesse"
L3_valence: "négative"
L3_arousal: "basse"
BIS_BAS: "BAS↓ BIS neutre"
L1_déclencheurs: ["Besoin d'Appartenance (perte relationnelle)", "Prémisses éthiques (perte de sens)"]
L2_déclencheurs: ["[[03 — Reconstruction mémorielle -- Sélectivité mémorielle (reconstruit pour confirmer la perte)]]"]
L4_comportements: ["Retrait · Ralentissement · Introspection · Recherche de sens · Pleurs"]
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

# 🌧️ Tristesse

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Tristesse]`*");
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
> La Tristesse est construite quand le cerveau applique le concept 'une perte s'est produite' à un affect négatif à faible arousal. Contrairement à l'Accablement (phase prolongée post-sortie de fenêtre), la Tristesse est une réponse adaptative à une perte identifiable — relationnelle, de sens, ou d'espoir. Elle signale que quelque chose d'important est absent ou perdu. [documenté]

**Valence :** négative
**Arousal :** basse
**Action tendency :** Retrait · ralentissement · introspection · recherche de sens · pleurs comme régulation

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre — pas de menace active
- **BAS :** ↓ bas — le drive d'approche se retire face à la perte
- **Combinaison :** BAS/BIS tous deux bas, avec valence négative (distinct de la Sérénité qui est aussi BAS↓/BIS↓ mais positive)
- **Note :** la Tristesse est adaptative. Elle signale la valeur de ce qui est perdu. Réprimer la Tristesse coûte plus cher métaboliquement qu'y faire face.

**Distinction des émotions proches :**
vs **[[Accablement]]** : l'Accablement est une phase prolongée post-sortie de fenêtre envahissant L1-L4, sans déclencheur précis. La Tristesse a un déclencheur identifiable (une perte) et une durée plus limitée.
vs **[[Déception]]** : la Déception porte sur un résultat manqué. La Tristesse porte sur une perte réelle (relation, sens, espoir).
vs **[[Solitude]]** : la Solitude est un manque structurel de connexion. La Tristesse répond à une perte identifiable.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** poitrine et gorge · sensation de poids · yeux humides ou lourds
> - **Rythme cardiaque :** ralenti
> - **Respiration :** lente · profonde · parfois entrecoupée
> - **Posture spontanée :** corps légèrement affaissé · épaules en avant · regard interne
> - **Sensations spécifiques :** pesanteur générale · 'quelque chose manque' · besoin de calme

> [!warning] Signaux cognitifs précoces
> - *"Ça me manque"* / *"Ce n'est plus là"* / *"C'était important"*
> - Pensées qui reviennent à ce qui est perdu
> - Absence de projection vers le futur (différent de la Peur qui anticipe)

> [!warning] Signaux comportementaux précoces
> - Ralentissement général
> - Retrait des activités externes
> - Besoin de calme et d'espace
> - Pleurs comme régulation naturelle

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs
| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| — | Besoin d'Appartenance | Perte relationnelle → signal que ce lien avait de la valeur |
| — | Prémisses éthiques | Perte de sens, de direction ou d'alignement avec ses valeurs |
| — | Besoin de Compétence | Perte d'une capacité ou d'un objectif important |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie la Tristesse. *"Cette perte révèle que je ne méritais pas ce que j'avais."* Glissement vers la Honte.
- **Mastery thinking** : permet de traverser la Tristesse. *"Cette perte montre que ça avait de la valeur pour moi — c'est de l'information sur ce qui compte."*

#### L2 — Schémas déclencheurs
| Schéma L2 | Mécanisme |
|---|---|
| Sélectivité mémorielle (L2/03) | Sous Tristesse, le remembering self reconstruit pour confirmer et amplifier la perte |

#### L0 — Influence
La Tristesse consomme modérément L0 mais est aussi partiellement restauratrice si elle peut être vécue pleinement (les pleurs régulent le système nerveux). Réprimer la Tristesse coûte plus cher que l'exprimer.

---

## IV. Connexions dans l'écosystème — Bidirectionnel
| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → Tristesse plus difficile à traverser · risque de glissement vers Accablement |
| **L3 → L0** | ascendant ✅/⚠️ | Tristesse vécue pleinement → légèrement restauratrice (pleurs régulent SNV) · Tristesse réprimée → coûteuse |
| **L1 → L3** | descendant | Appartenance défensive (perte relationnelle) · Prémisses éthiques (perte de sens) |
| **L3 → L1** | ascendant | Révèle ce qui a de la valeur → peut renforcer les L1 générateurs si traversée |
| **L2 → L3** | descendant | Sélectivité mémorielle amplifie |
| **L3 → L2** | ascendant | La Tristesse peut activer la Rumination |
| **L3 → L4** | descendant | Retrait · ralentissement · introspection |
| **L4 → L3** | ascendant ✅ | Le ralentissement délibéré permet la traversée naturelle |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Créer un espace pour traverser la Tristesse plutôt que la fuir |
| 2 · Modification | oui | Co-présence de Sassa · environnement calme · pas de stimulation intense |
| 3 · Attentionnel | non | Ne pas détourner — la Tristesse se traverse, pas s'évite |
| 4 · Reappraisal | partiel | Après coup : *"Cette Tristesse révèle ce qui a de la valeur pour moi"* |
| 5 · Modulation | oui | Les pleurs sont une stratégie de modulation adaptative — ne pas les réprimer |

**Stratégie prioritaire :** Sélection (1) + Modulation (5) — créer l'espace et laisser la Tristesse se traverser naturellement.
**Note L0 :** la Tristesse sous L0 très épuisé peut glisser vers l'Accablement. Priorité à L0 d'abord.

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
> > - [ ] [Prix à payer:: J'accepte que la Tristesse révèle ce qui a de la valeur pour moi — la traverser est plus économique que la réprimer]

---

## VII. Analyse à froid

> [!abstract]
> **Tristesse ou Accablement ?**
Question pivot : *"Y a-t-il une perte identifiable — ou est-ce un état diffus sans cause précise ?"*
- Perte identifiable → Tristesse → traitable par traversée
- État diffus → Accablement → traitement L0 d'abord → [[Accablement]]

**Ce que la Tristesse révèle :** elle indique toujours ce qui a de la valeur. Quelle est la perte ? Quelle valeur révèle-t-elle ?

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
> > - [ ] [Plan d'action:: Créer l'espace pour traverser la Tristesse → identifier ce qui est perdu → distinguer Tristesse (perte identifiable) vs Accablement (état prolongé sans déclencheur)]

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
- [[Accablement]] · [[Solitude]] · [[Déception]]
- [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
- [[L1 - Structures profondes/03 — Besoin d'Appartenance]]
