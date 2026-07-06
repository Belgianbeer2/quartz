---
type: fiche_emotion
tags: [L3, émotion, délaissement, appartenance, inner-mapping]
L3_nom: "Délaissement"
L3_valence: "négative"
L3_arousal: "haute (blessure sociale) puis basse (retrait)"
BIS_BAS: "BIS↑ BAS↓"
L1_déclencheurs: ["Besoin d'Appartenance défensif"]
L2_déclencheurs: ["[[01 — Mentalisation -- Dissociation]]", "[[02 — Évaluation causale -- Confabulation]]"]
L4_comportements: ["Retrait · Stratégie de l'autruche · Questionnement relationnel"]
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

# 🌑 Délaissement

> **Distinct de :**
> - *Solitude* — absence structurelle de lien. Ici le lien existe, mais on est à sa périphérie.
> - *Abandon* — rupture totale. Ici c'est le *sidelining* — présent mais mis sur le carreau.
> - *Rejet* — exclusion active. Ici souvent passif, non intentionnel — ce qui le rend plus insidieux.
>
> **Déclencheur type :** le "vu" sans réponse dans le chan familial après un message qui cherchait une interaction.

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Délaissement]`*");
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

> [!abstract] ✅ Fondement — Williams (2001) · Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> L'ostracisme social — être ignoré même brièvement — active les mêmes zones cérébrales que la douleur physique (Williams 2001). Le "vu" sans réponse est une micro-forme d'ostracisme. L'effet est mesurable en quelques secondes, indépendamment de l'intention. [documenté]
>
> Barrett : le même signal peut construire des émotions très différentes selon le concept appliqué — *"ils sont occupés"* vs *"je suis mis sur le carreau"*. La précision du nommage — **délaissement** plutôt qu'abandon — change le plan d'action que le cerveau génère. [documenté — [[Fondements théoriques/03 — Cerveau prédictif]]]

**Valence :** négative
**Arousal :** haute initialement (blessure sociale) puis basse (retrait)
**Action tendency :** retrait · stratégie de l'autruche · questionnement sur la relation

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ actif — connexion refusée = menace sociale
- **BAS :** ↓ bas — le drive de connexion s'effondre après le rejet perçu
- **Combinaison :** BIS fort + BAS retiré → blessure sociale + retrait

> [!abstract] Bid for Connection → Délaissement · [[L1 - Structures profondes/03 — Besoin d'Appartenance]] §I.3
> Le Délaissement peut se construire par accumulation de **bids for connection** non-reçues.
> **Spécificité profil haut NFC** : offrir de l'aide est l'expression du mode d'engagement le plus intense. Un refus active simultanément 3 L1 : Appartenance + Compétence + Autonomie → intensité disproportionnée. [documenté]

**Distinction des émotions proches :**
vs **[[Solitude]]** : la Solitude est une absence structurelle de lien (BIS neutre). Le Délaissement est une connexion refusée dans une relation existante (BIS activé). Plus douloureux.
vs **[[Tristesse]]** : la Tristesse répond à une perte identifiable. Le Délaissement peut exister sans rupture réelle — juste un silence.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de sensation :** creux dans la poitrine · estomac noué · légère pesanteur
> - **Rythme cardiaque :** légèrement irrégulier puis ralenti
> - **Respiration :** courte puis ralentie · soupirs
> - **Posture spontanée :** corps légèrement replié · envie de se retirer
> - **Sensations spécifiques :** vide relationnel · *"je suis à la périphérie"*

> [!warning] Signaux cognitifs précoces
> - *"Je suis mis sur le carreau"* / *"Est-ce que je compte vraiment ici ?"* / *"Pourquoi je suis parrain si..."*
> - Construction d'une narrative de rejet depuis un événement ponctuel
> - Remise en question de la relation entière depuis un signal isolé

> [!warning] Signaux comportementaux précoces
> - Consultation des messages sans répondre
> - Retrait de la conversation
> - Stratégie de l'autruche (activités à conséquences limitées)

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin d'Appartenance | Connexion refusée dans une relation existante → signal sur la place dans le groupe |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : le "vu" est traité comme révélation définitive sur la place dans la relation. *"Je suis mis sur le carreau parce que je ne compte pas assez."*
- **Mastery thinking** : le "vu" est traité comme un signal sur cet événement précis. *"Ils sont probablement occupés — ce n'est pas un jugement sur la relation."*

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Dissociation (L2/01) | Interprète le "vu" comme rejet intentionnel — l'observateur est fantasmé dans sa réaction |
| Confabulation (L2/02) | Sélectionne les données qui confirment le rejet (*"ils s'envoient des photos entre eux"*) |

#### L0 — Influence

Budget épuisé → co-régulation moins disponible → Délaissement plus probable et plus intense. Sassa présente = ressource de co-régulation même passive.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → co-régulation réduite → Délaissement plus intense |
| **L3 → L0** | ascendant ⚠️ | BIS actif → légère consommation L0 · retrait réduit la co-régulation disponible |
| **L1 → L3** | descendant | Besoin d'Appartenance défensif |
| **L3 → L1** | ascendant ⚠️ | Répété → renforce "je suis à la périphérie" |
| **L2 → L3** | descendant | Dissociation · Confabulation l'amplifient |
| **L3 → L2** | ascendant | Déclenche la Dissociation (construire la réaction imaginée de l'autre) |
| **L3 → L4** | descendant | Retrait · stratégie de l'autruche · questionnement relationnel |
| **L4 → L3** | ascendant ⚠️ | Le retrait amplifie le Délaissement (pas de reconnexion = erreur de prédiction non résolue) |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — |
| 2 · Modification | oui | Micro-connexion (message court, appel) · co-présence avec Sassa |
| 3 · Attentionnel | oui | *"Ce 'vu' est-il intentionnel ? Quelle est la contrainte structurelle réelle ?"* |
| 4 · Reappraisal | oui | Nommer *"délaissement"* (pas "abandon") · distinguer contrainte structurelle (distance) vs jugement relationnel |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Reappraisal (4) — nommer précisément + distinguer contrainte structurelle vs jugement relationnel.
**Note L0 :** sous budget bas, Modification (2) d'abord — micro-connexion disponible.

**Protocole associé :** [[Protocoles/Transversaux/04 — Drill · L1 Appartenance — Bid for connection rejetée]]

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
> > [!note]- Déclencheur documenté
> > - Le "vu" sans réponse dans le chan familial après un message qui cherchait une interaction

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
> > - [ ] [Prix à payer:: J'accepte que la distance crée une asymétrie réelle — ce n'est pas un jugement sur la relation]
> > - [ ] [Prix à payer:: J'accepte que le "vu" n'est probablement pas intentionnel — c'est de l'inattention, pas du rejet]

---

## VII. Analyse à froid

> [!abstract]
> **Ce qui se passe réellement :**
> - L2 Dissociation : le "vu" est interprété comme rejet intentionnel — alors que c'est probablement de l'inattention.
> - L2 Confabulation : sélection des données qui confirment (*"ils s'envoient des photos entre eux"*)
>
> **Ce qui est réel vs construit :**
> Réel : la distance (Cambodge / Europe) crée une asymétrie structurelle dans les échanges spontanés.
> Construit : *"Je suis mis sur le carreau"* comme conclusion permanente depuis un signal ponctuel.

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
> > - [ ] [Plan d'action:: Nommer précisément — délaissement, pas abandon]
> > - [ ] [Plan d'action:: Identifier le L2 actif — Dissociation ou Confabulation ?]
> > - [ ] [Plan d'action:: Micro-connexion disponible (Sassa, message court)]

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
- [[Solitude]] · [[Tristesse]] · [[Impuissance]]
- [[01 — Mentalisation -- Dissociation]] · [[02 — Évaluation causale -- Confabulation]]
- [[L1 - Structures profondes/03 — Besoin d'Appartenance]] §I.3
- [[L0 — Physiologie & Budget Corporel/03 — Co-régulation sociale]]
- [[Protocoles/Transversaux/04 — Drill · L1 Appartenance — Bid for connection rejetée]]
