---
type: fiche_emotion
tags: [L3, émotion, anxiété-évaluation, inner-mapping]
L3_nom: "Anxiété d'évaluation"
L3_valence: "négative"
L3_arousal: "moyenne-haute"
BIS_BAS: "BIS↑ BAS neutre"
L1_déclencheurs: ["Besoin de Compétence défensif", "Besoin d'Appartenance défensif"]
L2_déclencheurs: ["[[01 — Mentalisation -- Dissociation]]"]
L4_comportements: ["Jeu d'image · Ajustement anticipatoire · Décisions EV-dégradées · Modélisation du reg"]
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

# 🧠 Anxiété d'évaluation

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Anxiété d'évaluation]`*");
> ```

> [!note]- 📅 Jours concernés — O&R 
>```dataviewjs 
> let p = dv.current();
> let targetEmotion = p.file.name;
> 
> let orPage = dv.page("📝 observation et ressentis");
> if (!orPage) {
>     dv.paragraph("*⚠️ Fichier O&R introuvable.*");
> } else {
>     let content = await dv.io.load(orPage.file.path);
> 
>     // Découpe par sections ## DATE
>     let sections = content.split(/\n##\s+/);
>     let matches = [];
> 
>     let dateRe = /^(\d{2}-\d{2}-\d{4})/;
>     // Escape les caractères spéciaux du nom de la fiche pour le regex
>     let escaped = targetEmotion.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
>     // Matche l'émotion n'importe où dans une liste de valeurs : [emotion:: A, B, C]
>     let tagRe = new RegExp("\\[emotion::[^\\]]*" + escaped + "[^\\]]*\\]", "i");
> 
>     for (let section of sections) {
>         let firstLine = section.split('\n')[0].trim();
>         let dateMatch = firstLine.match(dateRe);
>         if (dateMatch && tagRe.test(section)) {
>             matches.push(dateMatch[1]);
>         }
>     }
> 
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

> [!abstract] ✅ Fondement — Barrett (2017) · Moukheiber (2026) · [[Fondements théoriques/03 — Cerveau prédictif]] · [[Sources/01 — Albert Moukheiber × Les Lueurs]]
> L'anxiété d'évaluation est construite quand le cerveau applique le concept "je suis observé et jugé par quelqu'un de compétent" à un affect négatif à arousal moyenne-haute. Ce n'est pas une menace financière ou physique — c'est une menace sur **l'image de soi dans le regard d'un pair qualifié**. [documenté]

> [!abstract] ✅ Son véhicule cognitif : la Dissociation · [[01 — Mentalisation -- Dissociation]]
> L'anxiété d'évaluation transite souvent par la Dissociation — la projection dans la tête de l'observateur. L'émotion n'est pas toujours nommable directement. Elle se détecte par le comportement qu'elle génère : ajustement de stratégie avant toute main contre le reg. [documenté — observation personnelle]

**Valence :** négative
**Arousal :** moyenne-haute — vigilance accrue sans activation explosive
**Action tendency :** jeu d'image · ajustement anticipatoire · décisions EV-dégradées

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ actif — menace identitaire (regard compétent = risque d'être "démasqué")
- **BAS :** neutre — pas d'élan particulier, mais le BIS oriente les décisions
- **Combinaison :** BIS dominant → inhibition de l'action naturelle → jeu contracté ou jeu d'image

**Distinction des émotions proches :**
- vs **[[Peur]]** : la Peur a un objet financier/existentiel. L'Anxiété d'évaluation a un objet identitaire et social (le regard).
- vs **[[Honte]]** : la Honte est après-coup ("je SUIS défaillant"). L'Anxiété d'évaluation est anticipatoire ("il va voir que je suis défaillant").

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** poitrine légèrement comprimée · gorge légèrement serrée · épaules qui remontent
> - **Rythme cardiaque :** légèrement accéléré · régulier mais plus rapide
> - **Respiration :** légèrement retenue · plus courte · moins profonde
> - **Posture spontanée :** corps légèrement contracté · regard qui surveille la table adverse
> - **Sensations spécifiques :** vigilance accrue · sentiment d'être "exposé" · difficulté à se concentrer sur la main

> [!warning] Signaux cognitifs précoces
> - *"Il me voit"* / *"Il pense que je joue mal"* / *"Qu'est-ce qu'il pense de ce play ?"*
> - Construction mentale de ce que l'adversaire perçoit — avant toute action réelle
> - Questionnement sur l'image projetée plutôt que sur l'EV de la décision

> [!warning] Signaux comportementaux précoces
> - Ajustement de stratégie contre le reg **avant** d'avoir joué une main contre lui
> - Modélisation des conclusions du reg depuis un pot où il n'est pas impliqué
> - Conduire plus vite devant un observateur perçu comme compétent *(IRL)*

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Compétence | Le regard d'un pair qualifié peut "démasquer" l'entité — menace identitaire directe |
| **Défensif** | Besoin d'Appartenance | Le regard du reg = évaluation de la place dans la communauté des joueurs compétents |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : le regard du reg est traité comme juge de l'entité. Un mauvais play "révèle" l'entité déficiente.
- **Mastery thinking** : le regard du reg est neutre — il joue ses mains, il n'est probablement pas en train de te regarder.

> [!abstract] Ce que Moukheiber éclaire [inféré]
> L'observateur fantasmé est la version pathologique d'un mécanisme social normal. Le reg multi-tableur n'a probablement pas traité cette main. Le cerveau continue de gérer le risque évaluatif même quand l'observateur n'est pas réellement en train d'observer. [inféré — Moukheiber 2026 · [[Sources/01 — Albert Moukheiber × Les Lueurs]]]

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Dissociation (L2/01) | **C'est le véhicule principal** — la projection dans la tête de l'observateur est la Dissociation en action. L'Anxiété d'évaluation est l'émotion sous-jacente à la Dissociation. |

#### L0 — Influence

Budget épuisé → DMN plus actif → Dissociation plus fréquente → Anxiété d'évaluation plus probable. Sous L0 satisfait, la question de réalité ("est-il dans ce pot ?") est plus accessible.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → DMN plus actif → Dissociation → Anxiété d'évaluation plus probable |
| **L3 → L0** | ascendant ⚠️ | Vigilance accrue soutenue → activation prolongée → coût métabolique modéré |
| **L1 → L3** | descendant | Compétence défensif + Appartenance défensif |
| **L3 → L1** | ascendant ⚠️ | Répétée → renforce "les autres peuvent voir mes failles" → ancre la Compétence défensive |
| **L2 → L3** | descendant | Dissociation (L2/01) la produit directement |
| **L3 → L2** | ascendant | L'Anxiété d'évaluation alimente la Dissociation en boucle |
| **L3 → L4** | descendant | Jeu d'image · ajustement anticipatoire · décisions EV-dégradées |
| **L4 → L3** | ascendant ⚠️ | Décisions depuis l'image confirment qu'on joue sous regard → renforce l'anxiété |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Ancrage corporel au warmup si Dissociation/Anxiété d'évaluation détectée |
| 2 · Modification | non | — |
| 3 · Attentionnel | oui | **Question de réalité** : *"Est-il dans ce pot ? Combien de tables joue-t-il ?"* |
| 4 · Reappraisal | oui | *"Je joue ce coup depuis moi — pas pour l'image que je projette"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Attentionnel (3) — question de réalité. Simple, rapide, interrompt le circuit.
**Note L0 :** sous budget bas, ancrage corporel (1) avant la question de réalité.

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
> > - Identification d'un reg compétent à la table *(in-game)*
> > - Bluff créatif amené au showdown en présence d'un reg *(in-game)*
> > - Play créatif dans un pot où le reg est spectateur *(in-game)*
> > - Présence d'un observateur qualifié *(IRL — scooter Siem Reap)*

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
> > [!note]- Réactions documentées à froid
> > - Ajustement anticipatoire de la stratégie avant toute main contre le reg *(in-game)*
> > - Modélisation des conclusions du reg depuis un pot où il n'est pas impliqué *(in-game)*
> > - Conduire plus vite devant des touristes *(IRL)*

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
> > - [ ] [Prix à payer:: J'accepte de jouer contre un adversaire imaginaire plutôt que contre la main devant moi]
> > - [ ] [Prix à payer:: J'accepte que mes fréquences soient distordues par une menace qui n'existe probablement pas]

---

## VII. Analyse à froid

> [!abstract]
> **L'observateur est-il réel ?**
> - Question de réalité : *"Est-il dans ce pot ?"* Si non → observateur fantasmé à 100%.
> - Si oui : *"Combien de tables joue-t-il ?"* Si plus de 4 → il n'a probablement pas traité cette main.
>
> **Ce qui est réel vs construit :**
> Réel : le reg est à la table. Construit : il me surveille, il tire des conclusions sur mon identité de joueur depuis cette main.

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
> > - [ ] [Plan d'action:: Question de réalité — *"Est-il dans ce pot ?"* → sinon : observateur fantasmé]
> > - [ ] [Plan d'action:: Nommer : "anxiété d'évaluation" → *"Depuis qui est-ce que je joue ce coup ?"*]

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
- [[01 — Mentalisation -- Dissociation]] — pattern cognitif véhiculant cette émotion
- [[Anxiété]] — index des formes d'anxiété
- [[Honte]] — distinction anticipatoire vs après-coup
- [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- *Fiche créée le 04-06-2026*
