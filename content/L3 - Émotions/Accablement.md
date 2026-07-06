---
type: fiche_emotion
tags: [L3, émotion, accablement, hypoactivation, inner-mapping]
L3_nom: "Accablement"
L3_valence: "négative"
L3_arousal: "très basse"
BIS_BAS: "BAS↓ BIS↓ (récupération active)"
L1_déclencheurs: ["Tous les L1 épuisés — pas de L1 spécifique actif"]
L2_déclencheurs: []
L4_comportements: ["Retrait total · Sommeil · Inactivité · Tentatives de récupération avortées"]
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

# 😞 Accablement

> [!todo] Une phase, pas un instant
> L'Accablement est la **texture affective d'une phase d'hypoactivation prolongée** — pas une réaction à un événement identifiable, mais un état qui envahit L1 à L4 pendant que le système récupère. → [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: Accablement]`*");
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

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]] · Dantzer (2008) · [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
> L'Accablement est l'équivalent émotionnel du *sickness behavior* décrit par Dantzer (2008) — le système nerveux en mode récupération active post-sortie de fenêtre. L'affect négatif + arousal très basse = état de retrait forcé pendant la restauration du budget. Ce n'est pas de la faiblesse. C'est de la biologie. [documenté]

**Valence :** négative
**Arousal :** très basse — système en mode récupération forcée
**Action tendency :** inactivité · sommeil · retrait · évitement de tout effort cognitif

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ bas — ni les risques ni les menaces ne mobilisent (système inhibé par épuisement)
- **BAS :** ↓ bas — ni les récompenses ni les opportunités ne mobilisent
- **Combinaison :** BAS-/BIS- = Apathie motivationnelle — le système récupère plutôt que de s'activer

> [!abstract] ✅ Signature affective — Impuissance ET Culpabilité coexistantes · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §I, §VI
> Deux émotions **coexistent ou alternent** dans l'Accablement :
> - **[[Impuissance]]** — *"rien à faire"* (contrôle situationnel absent)
> - **[[Culpabilité]]** — *"je devrais pourtant pouvoir"* (contrôle tourné vers soi, orientation passée)
> C'est cette alternance sans stabilisation qui distingue l'Accablement d'une Impuissance simple.

**Distinction des émotions proches :**
- vs **[[Tristesse]]** : Tristesse = réponse à une perte identifiable. Accablement = phase prolongée sans déclencheur précis.
- vs **[[Sérénité]]** : même signature BAS-/BIS- mais valence opposée. La Sérénité est le signal de *sortie* de l'Accablement.
- vs Apathie générique : l'Apathie peut être un état stable. L'Accablement a une histoire immédiate (sortie de fenêtre récente).

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de sensation :** corps lourd dans sa totalité · membres lourds · tête lourde
> - **Rythme cardiaque :** lent · régulier · sans variation
> - **Respiration :** lente · superficielle · soupirs fréquents
> - **Posture spontanée :** corps affaissé · mouvements ralentis · démarche lente
> - **Sensations spécifiques :** "envie de rien, juste dormir" · "tout m'énerve, quart de tour" · légèreté paradoxale parfois (système qui se vide)

> [!warning] Signaux cognitifs précoces
> - *"Je ne suis pas encore sorti de mes schémas défensifs"*
> - Idéations tournées vers le pire sans déclencheur identifiable
> - Incapacité à s'engager dans une activité même agréable
> - Les tentatives de récupération semblent impossibles ("les bains m'énervent, je n'ai pas la patience")

> [!warning] Signaux comportementaux précoces
> - Retrait total de toute activité (poker, social, exercice)
> - Sommeil répété ou envie de dormir en continu
> - Irritabilité au moindre stimulus même positif

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

> L'Accablement n'est pas déclenché par un L1 spécifique — il résulte de l'épuisement de **tous les L1 simultanément** après une sortie de fenêtre (hyperactivation → bascule). Aucun besoin n'est assez restauré pour servir de levier.

#### Pourquoi le recadrage a une portée réduite ici

> [!warning] Ce n'est pas un manque d'effort · Arnsten · [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]] §III.1
> Le PFC est moins disponible pendant l'hypoactivation. Les recadrages (Gross #4) demandent précisément les ressources PFC les plus réduites à ce moment. Forcer le recadrage peut ajouter de la Culpabilité ("même ça je n'y arrive pas") — auto-entretenant l'Accablement. [documenté]

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
L'entity thinking sous Accablement amplifie : "je suis quelqu'un qui s'effondre" plutôt que "mon système est en récupération". Le mastery thinking est moins accessible — ce n'est pas le moment de le forcer.

#### L2 — Schémas déclencheurs

Aucun L2 spécifique ne déclenche l'Accablement — il émerge de l'épuisement systémique post-cascade.

#### L0 — Influence

L'Accablement **est** un état L0. Il émerge directement de la sortie de fenêtre. Les protocoles pertinents sont les protocoles L0 : repos sans culpabilité, behavioral activation minimal, lumière, micro-contact social. Le recadrage redevient accessible **après** la restauration partielle du budget.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | L'Accablement **est** un état L0 — il émerge directement de l'épuisement post-sortie de fenêtre |
| **L3 → L0** | ascendant ✅ | Signal que L0 est en cours de restauration · respecter la phase = restauration plus rapide |
| **L1 → L3** | descendant | Tous les L1 épuisés → Accablement (pas de L1 spécifique) |
| **L3 → L1** | ascendant | Sortie de l'Accablement restaure progressivement les L1 — dans l'ordre inversé de leur coût métabolique |
| **L2 → L3** | descendant | Pas de L2 déclencheur — l'Accablement précède les L2 |
| **L3 → L2** | ascendant ⚠️ | Sous Accablement, les L2 défensifs (Rumination, Sélectivité mémorielle) peuvent se mettre en route avec peu de carburant |
| **L3 → L4** | descendant | Retrait total · sommeil · inactivité · tentatives de récupération avortées |
| **L4 → L3** | ascendant ✅ | Repos sans culpabilité + behavioral activation minimal → restaure L0 → sortie de l'Accablement |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | non | — (pas de sélection possible dans cet état) |
| 2 · Modification | oui | **LA stratégie principale** : repos sans culpabilité · behavioral activation minimal · lumière · micro-contact social |
| 3 · Attentionnel | non | PFC indisponible |
| 4 · Reappraisal | non | PFC indisponible — forcer le recadrage ajoute de la Culpabilité |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Modification (2) — protocoles L0 uniquement. Les drills cognitifs (Drill 01, Protocole Lucidité) ne sont **pas** appropriés pendant l'Accablement.
**Note L0 :** l'Accablement *est* un état L0. Pas de protocoles cognitifs. Repos → micro-contact social → reprise progressive.

**Signal de sortie :** apparition de la [[Sérénité]] ou de la [[Curiosité]] → le recadrage redevient accessible à ce moment.

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
> > [!note]- Instance documentée 11-13/06/2026
> > Trois jours suivant un collapse. Signature : *"envie de rien, juste dormir"* · *"tout m'énerve, quart de tour"* · idéations vers le pire · tentative SPA impossible · *"les bains m'énervent, je n'ai pas la patience"*. Sortie le 14/06 après repos (sommeil répété, arrêt caféine). → [[Synthèse — Collapse du 10-06]]

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
> > - [ ] [Prix à payer:: J'accepte que le repos sans culpabilité est la seule action utile pendant l'Accablement — pas les drills]
> > - [ ] [Prix à payer:: J'accepte que forcer le recadrage pendant l'Accablement ajoute de la Culpabilité et ralentit la sortie]

---

## VII. Analyse à froid

> [!abstract]
> **Proxy de détection : transition Impuissance ponctuelle → Accablement**
> - Durée : plus de 24h d'inactivité généralisée ?
> - Domaines touchés : le retrait touche-t-il à la fois le poker, le social et le corps ?
> - Origine : y a-t-il eu une sortie de fenêtre récente (cascade ou hyperactivation prolongée) ?
>
> **Signal de sortie à observer :** l'apparition de la [[Sérénité]] ou d'une [[Curiosité]] légère — c'est le moment où le recadrage redevient accessible. Documenter ici quand ce signal apparaît pour affiner le proxy.
>
> **Ce qui reste à approfondir :**
> - [ ] Proxy observable pour la transition Impuissance ponctuelle → Accablement (durée ? domaines ?)
> - [ ] Drill 02 adapté pour détecter la *sortie* de l'Accablement (pas seulement la prévention)

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
> > - [ ] [Plan d'action:: Protocoles L0 uniquement : repos sans culpabilité · behavioral activation minimal · lumière · micro-contact social (Sassa)]
> > - [ ] [Plan d'action:: Attendre le signal de sortie (Sérénité ou Curiosité légère) avant tout travail cognitif]

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
- [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
- [[Fondements théoriques/05 — BIS & BAS]] §II
- [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §I, §VI
- [[Impuissance]] · [[Culpabilité]] · [[Sérénité]]
- [[Synthèse — Collapse du 10-06 et direction Inner Mapping]]
- [[Protocoles/Transversaux/02 — Drill · L0 Fenêtre d'activation — Rétrospective accumulation]]
