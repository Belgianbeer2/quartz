---
type: fiche_emotion
tags: [L3, émotion, impuissance, contrôle, inner-mapping]
L3_nom: "Impuissance"
L3_valence: "négative"
L3_arousal: "basse-moyenne"
BIS_BAS: "BAS↓ BIS neutre-bas"
L1_déclencheurs: ["Besoin de Contrôle défensif", "Besoin d'Autonomie défensif"]
L2_déclencheurs: ["[[07 — Projection temporelle -- Suranticipation (projette l'impuissance dans le futur)]]"]
L4_comportements: ["Discours compensatoire (narratif) · Stratégie de l'autruche (réel) · Réactance · Colère de surface"]
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

# 😶 Impuissance

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Impuissance]`*");
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

> [!abstract] ✅ Fondement — Moukheiber (2026) · Barrett (2017) · [[Sources/01 — Albert Moukheiber × Les Lueurs]] · [[Fondements théoriques/03 — Cerveau prédictif]]
> L'Impuissance est construite quand le cerveau perçoit l'absence totale de levier sur une situation. Sa caractéristique : elle génère immédiatement une **réponse compensatoire** — le cerveau produit une histoire d'agentivité (*"je vais tout faire péter"*) pour compenser l'absence de contrôle réel. Le soi narratif et le soi comportemental ne coïncident pas. [documenté]
>
> **L'Impuissance comme émotion sous-jacente [documenté — Alexis] :** elle est souvent le carburant d'émotions plus visibles.

| Émotion de surface | Impuissance sous-jacente |
|---|---|
| [[La Réactance]] | Impuissance face à l'agressivité adverse → reprendre le contrôle |
| [[Colère IRL]] | Impuissance face à l'injustice → discours explosif |
| [[Frustration]] | Impuissance face à la variance répétée |

**Valence :** négative
**Arousal :** basse-moyenne — épuisement face à l'absence de levier
**Action tendency :** À documenter

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** neutre-bas — pas de menace active, absence de signal
- **BAS :** ↓ bas — drive qui s'effondre face à l'absence de levier
- **Combinaison :** BAS↓/BIS neutre = apathie orientée vers l'absence de contrôle (distinct de l'Accablement qui touche tous les domaines)

**Distinction des émotions proches :**
vs **[[Accablement]]** : l'Impuissance est ponctuelle (réponse à un événement identifiable). L'Accablement est une phase prolongée post-épuisement systémique.
vs **[[Frustration]]** : la Frustration a un BAS encore actif. L'Impuissance est le BAS qui s'effondre.
vs **[[Déception]]** : la Déception est un résultat manqué. L'Impuissance est l'absence totale de levier.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** corps lourd · épaules basses · mains ouvertes (abandon)
> - **Rythme cardiaque :** ralenti · régulier
> - **Respiration :** courte · superficielle · soupirs
> - **Posture spontanée :** corps qui s'affaisse · regard vers le bas ou vague
> - **Sensations spécifiques :** "rien à faire" · paralysie légère · sensation de vide

> [!warning] Signaux cognitifs précoces
> - *"Rien à faire"* / *"Je vais tout faire péter"* (compensatoire) / *"La variance va me ruiner"*
> - Discours explosif sans plan réel → illusion de contrôle pour rendre la situation supportable
> - Projection : *"ça va continuer comme ça"*

> [!warning] Signaux comportementaux précoces
> - Stratégie de l'autruche (actions à conséquences limitées)
> - Tentative de reprendre le contrôle là où il n'y en a pas (→ Réactance)
> - Retrait · silence

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Contrôle | Absence de levier = violation directe du besoin de contrôle → Impuissance |
| **Défensif** | Besoin d'Autonomie | L'action souhaitée est impossible → le BAS s'effondre |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie l'Impuissance en la traitant comme révélation de l'entité déficiente. *"Je ne contrôle pas parce que je suis mauvais."*
- **Mastery thinking** : maintient l'Impuissance comme contrainte contextuelle. *"Cette situation n'a pas de levier — ça n'est pas un jugement sur moi."*

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Suranticipation (L2/07) | L'Impuissance projette vers le futur → "ça va continuer comme ça" (Expr. 3 catastrophiste) |

#### L0 — Influence
Budget épuisé → Impuissance plus intense et plus difficile à sortir. Sous L0 bas, le niveau 3 (transformation) est quasi-inaccessible.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → Impuissance plus intense |
| **L3 → L0** | ascendant ⚠️ | Impuissance non régulée → légère dépense L0 |
| **L1 → L3** | descendant | Besoin de Contrôle + Autonomie défensifs |
| **L3 → L1** | ascendant | Répétée → renforce "je n'ai pas de contrôle" |
| **L2 → L3** | descendant | Suranticipation projette l'Impuissance dans le futur |
| **L3 → L2** | ascendant | Déclenche la Confabulation (histoire d'agentivité compensatoire) |
| **L3 → L4** | descendant | Discours explosif (compensatoire) · stratégie de l'autruche · Réactance |
| **L4 → L3** | ascendant ✅ | Identifier la valeur touchée → transformer en levier réduit l'Impuissance |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | partiel | Ne pas tenter de reprendre le contrôle là où il n'y en a pas |
| 2 · Modification | oui | Stratégie de l'autruche (niveau 2) · s'éloigner du stimulus si possible |
| 3 · Attentionnel | oui | *"Quelle est la valeur touchée ici ?"* → identifier pour transformer |
| 4 · Reappraisal | oui | Redirection : *"Le seul levier ici est mon processus — pas le résultat"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Attentionnel (3) → Reappraisal (4) : identifier la valeur touchée → transformer en levier.
**Les 3 niveaux :** 1. Je la subis · 2. Je la gère (autruche) · 3. Je la transforme (levier de détermination)
**Note L0 :** sous budget bas, niveau 2 uniquement. La transformation requiert du PFC disponible.

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
> > - [ ] [Prix à payer:: J'accepte que la variance n'est pas un levier — le seul levier est mon processus]

---

## VII. Analyse à froid

> [!abstract]
> **Impuissance objective ou perçue ?**
- Objective : aucun levier réel disponible (variance, tiers)
- Perçue : un levier existe (processus, décision) mais l'Impuissance le masque

**Quelle valeur est touchée ?**
Liberté · autodétermination · contrôle sur son environnement. Identifier la valeur précise permet la transformation (niveau 3) : la valeur devient levier de [[Détermination]].

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
> > - [ ] [Plan d'action:: Nommer l'Impuissance → quelle émotion de surface alimente-t-elle (Réactance ? Colère ?) → identifier la valeur touchée → transformer en levier]

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
- [[La Réactance]] · [[Colère IRL]] · [[Frustration]] · [[Accablement]]
- [[07 — Projection temporelle -- Suranticipation]]
- [[L1 - Structures profondes/05 — Besoin de contrôle]]
