---
type: fiche_emotion
tags: [L3, émotion, soulagement, inner-mapping]
L3_nom: "Soulagement"
L3_valence: "positive-transitionnelle"
L3_arousal: "décroissante"
BIS_BAS: "BIS↓ BAS↑ transitoire"
L1_déclencheurs: ["Besoin de Contrôle satisfait", "Besoin de Compétence satisfait", "Besoin d'Appartenance satisfait"]
L2_déclencheurs: []
L4_comportements: ["Expiration longue · relâchement musculaire · sourire involontaire · baisse de vigilance"]
date: 2026-07-05
statut: documenté
---

```dataviewjs
const log = dv.page("log — Drill 02 — Rétrospective accumulation");
const nomFiche = dv.current().file.name;
if (!log || !log.entries) {
    dv.paragraph("*Aucune donnée Drill 02.*");
} else {
    const r = log.entries.filter(e => e.emotion === nomFiche);
    if (r.length === 0) { dv.paragraph("*Aucune activation Drill 02.*"); }
    else { dv.paragraph(`*${r.length} activation(s)*`); }
}
```

# 😮‍💨 Soulagement

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p = dv.current();
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.emotion).includes(p.file.name));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[emotion:: Soulagement]`*");
> ```

> [!note]- 📅 Jours concernés — O&R
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> let orPage = dv.page("📝 observation et ressentis");
> if (!orPage) {
>     dv.paragraph("*⚠️ Fichier O&R introuvable.*");
> } else {
>     let content = await dv.io.load(orPage.file.path);
>     let sections = content.split(/\n##\s+/);
>     let matches = [];
>     let dateRe = /^(\d{2}-\d{2}-\d{4})/;
>     let escaped = targetEmotion.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
>     let tagRe = new RegExp("\\[emotion::[^\\]]*" + escaped + "[^\\]]*\\]", "i");
>     for (let section of sections) {
>         let firstLine = section.split('\n')[0].trim();
>         let dateMatch = firstLine.match(dateRe);
>         if (dateMatch && tagRe.test(section)) { matches.push(dateMatch[1]); }
>     }
>     if (matches.length === 0) {
>         dv.paragraph("*Aucun O&R lié — tagger avec `[emotion:: " + targetEmotion + "]` dans l'O&R.*");
>     } else {
>         matches.sort().reverse();
>         let rows = matches.map(date => {
>             let allMR = dv.pages('"Journal/Morning routine logs/2026"').where(p => p.file.name === date + " Morning routine");
>             let mrPage = allMR.length > 0 ? allMR[0] : null;
>             return [date, mrPage ? mrPage.file.link : "*" + date + " (MR introuvable)*"];
>         });
>         dv.table(["Jour", "Morning Routine"], rows);
>     }
> }
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · Smith & Ellsworth (1985) · [[Fondements théoriques/03 — Cerveau prédictif]] · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]
> Le Soulagement est construit quand le cerveau enregistre la **résolution d'une menace active** — une tension attendue ou crainte qui ne se matérialise pas, ou une tension présente qui se lève. En termes d'appraisal (Smith & Ellsworth) : certitude qui monte soudainement + agrément qui bascule du négatif au positif + contrôle situationnel qui se restaure. [documenté]
>
> C'est une émotion **transitionnelle** : elle émerge d'un état négatif (menace, tension, BIS élevé) et ouvre sur un état positif (Satisfaction, Sérénité, Plénitude). Elle ne dure pas — le cerveau réajuste rapidement son niveau de base. [documenté — Barrett 2017]

**Valence :** positive-transitionnelle — naît d'un état négatif qui se résout
**Arousal :** décroissante — pic bref au moment de la résolution, puis descente vers le calme
**Action tendency :** expiration · relâchement · baisse de vigilance · ouverture vers l'autre

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↓ chute depuis un état élevé — la menace est levée, le système d'inhibition se désactive
- **BAS :** ↑ bref pic transitoire — les ressources libérées par la fin de la menace se redirigent
- **Combinaison :** BIS↓ + BAS↑ transitoire → fenêtre courte de restauration L0 · si non conscientisée, le cerveau réinitialise sans en tirer le bénéfice

**Distinction des émotions proches :**
- vs **[[Satisfaction]]** : la Satisfaction vient de l'atteinte d'un objectif (BAS accompli). Le Soulagement vient de la fin d'une menace (BIS désactivé). On peut être soulagé sans avoir accompli quoi que ce soit.
- vs **[[Sérénité]]** : la Sérénité est un état stable de calme actif. Le Soulagement est une transition — il peut mener à la Sérénité mais ne l'est pas encore.
- vs **[[Plénitude]]** : la Plénitude est un état d'engagement actif depuis soi. Le Soulagement est un relâchement — l'énergie n'est pas encore orientée.

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de relâchement :** épaules qui descendent · mâchoire qui se desserre · thorax qui s'ouvre
> - **Rythme cardiaque :** ralentissement perceptible après un pic · normalisation
> - **Respiration :** expiration longue et involontaire — le corps "lâche" ce qu'il retenait
> - **Posture spontanée :** affaissement doux · fermeture des yeux · sourire involontaire
> - **Sensations spécifiques :** légèreté soudaine · chaleur diffuse · envie de s'asseoir ou de s'appuyer

> [!warning] Signaux cognitifs
> - Pensée *"c'est terminé"* / *"ça n'a pas eu lieu"* / *"c'est réglé"*
> - Baisse soudaine du volume des pensées — le DMN se calme
> - Conscience que l'on retenait quelque chose sans le savoir

> [!warning] Signal comportemental précoce
> - L'expiration longue est le signal le plus fiable — elle précède souvent la conscience émotionnelle

---

## III. Cartographie théorique

#### L1 — Besoins dont la menace vient de se lever

| L1 précédemment menacé | Contexte type de Soulagement |
|---|---|
| **Besoin de Contrôle** | Une incertitude se résout · un résultat craint ne se produit pas |
| **Besoin de Compétence** | Une tâche redoutée est accomplie · une erreur n'a pas eu les conséquences craintes |
| **Besoin d'Appartenance** | Reconnexion après Délaissement · réponse reçue après silence · conflit apaisé |
| **Prémisses éthiques** | Résolution d'une situation perçue comme injuste |

> [!important] Le Soulagement comme signal de Mentalisation accomplie
> Dans le contexte du Délaissement (chat familial, silence de la sœur), le Soulagement peut émerger quand on passe de *"ils m'ignorent"* (Dissociation) à *"ce silence appartient à leur état — pas à ma valeur"* (Mentalisation). C'est le signal que la Phase 3 du [[Protocoles/Transversaux/04 — Drill · L1 Appartenance — Bid for connection rejetée|Drill 04]] a opéré. → [[L2 - Schémas Cognitifs/01 — Mentalisation -- Dissociation]]

#### L2 — Schémas actifs

Aucun schéma L2 défensif ne produit directement le Soulagement — c'est l'**absence** d'un schéma défensif qui le permet. La levée de la Dissociation, de la Suranticipation ou de la Vision zoomée libère le Soulagement.

| Schéma levé | Soulagement possible |
|---|---|
| [[L2 - Schémas Cognitifs/01 — Mentalisation -- Dissociation\|Dissociation]] levée | Soulagement relationnel — *"il n'était pas dans mon pot"* |
| [[L2 - Schémas Cognitifs/07 — Projection temporelle -- Suranticipation\|Suranticipation]] levée | Soulagement existentiel — *"ce que je craignais ne s'est pas produit"* |
| [[L2 - Schémas Cognitifs/04 — Calibration temporelle -- Vision zoomée\|Vision zoomée]] levée | Soulagement analytique — *"ce n'était que du bruit statistique"* |

#### L0 — Influence et rôle restaurateur

> [!abstract] ✅ Fondement — McEwen (1998) · [[L0 — Physiologie & Budget Corporel/02 — Allostase]]
> La fin d'une menace déclenche une désactivation du cortisol et de l'adrénaline. Cette désactivation **restaure activement le budget L0** — le Soulagement est une fenêtre de récupération biologique. Si elle n'est pas conscientisée, le cerveau revient au niveau de base sans en tirer le bénéfice. [documenté]

**Signal pratique :** conscientiser le Soulagement — le nommer, le respirer, le laisser durer 30-60 secondes — multiplie son effet restaurateur sur L0.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget suffisant → Soulagement accessible · Budget très épuisé → Soulagement émoussé ou absent (le système de menace reste hyperactif) |
| **L3 → L0** | ascendant ✅ | Soulagement conscientisé → désactivation du cortisol · restauration active du budget L0 |
| **L1 → L3** | descendant | Résolution d'un L1 menacé → Soulagement proportionnel à l'intensité de la menace précédente |
| **L3 → L1** | ascendant ✅ | Soulagement consolide *"ce besoin peut être satisfait"* → renforce la prédiction générative du L1 |
| **L2 → L3** | descendant | Levée d'un schéma défensif → Soulagement (Mentalisation, levée de la Suranticipation) |
| **L3 → L3** | transitif | Soulagement → si conscientisé → Satisfaction ou Sérénité · si non conscientisé → retour au niveau de base sans bénéfice |
| **L3 → L4** | descendant | Expiration · relâchement · baisse de vigilance · ouverture relationnelle |

---

## V. Régulation — Cadre positif · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

> Le Soulagement étant une émotion à valence positive, l'objectif n'est pas de le réguler à la baisse mais de **l'entretenir et de le laisser se consolider**. → [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle#VIII. Régulation des états positifs — cadre alternatif à Gross]]

| Dimension | Contenu |
|---|---|
| **Conditions d'accès** | Résolution réelle d'une menace active · ou recadrage cognitif (Mentalisation, levée de Suranticipation) qui lève la menace perçue |
| **Conditions de maintien** | Nommer l'émotion · respirer consciemment · lui accorder 30-60 secondes avant de reprendre · ne pas se replonger immédiatement dans le suivant |
| **Risques de dérive** | Réinitialisation rapide sans bénéfice (le cerveau revient au niveau de base trop vite) · Euphorie brève si BAS spike fort → risque de Piédestal · Retour de la tension si la résolution était partielle |
| **Protection** | *"Je me laisse soulager."* · Expiration consciente · Nommer : *"C'est du Soulagement"* |

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
> > - Lâcher prise sur le Délaissement après Phase 3 Drill 04 *(IRL — juillet 2026)*
> > - Résolution d'une incertitude sur Lucky *(IRL)*

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

---

## VII. Analyse à froid

> [!abstract]
> **Le Soulagement est une fenêtre — pas une destination.**
> Il ouvre un espace de 30 à 90 secondes où le budget L0 se restaure activement. Non conscientisé, il disparaît sans laisser de trace. Conscientisé, il peut se consolider en Satisfaction (si une tâche était en jeu) ou en Sérénité (si c'était une menace relationnelle).
>
> **Dans le contexte du Délaissement :** le Soulagement après la Phase 3 du Drill 04 est le signal que la Mentalisation a opéré. *"Ce silence appartient à leur état"* a remplacé *"ils m'ignorent"*. C'est une petite victoire qui mérite d'être nommée — pas avalée et oubliée.
>
> **Risque principal :** reprendre immédiatement le rythme après le Soulagement sans laisser le système nerveux autonome compléter sa désactivation. Le cerveau revient à son niveau de base en quelques minutes — pas en quelques secondes.

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
> > - [ ] [Plan d'action:: Nommer *"c'est du Soulagement"* · expiration consciente · laisser 30-60 secondes avant de reprendre]
> > - [ ] [Plan d'action:: Identifier ce qui vient après : Satisfaction · Sérénité · ou retour de tension si résolution partielle]

---

## IX. Archives

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let archives=dv.array([...desc,...p.file.lists]).where(c=>c.completed&&c["Plan d'action"]);
> if(archives.length>0)dv.taskList(archives,false);else dv.paragraph("*Aucune action archivée.*");
> ```

---

## Notes liées
- [[Satisfaction]] · [[Sérénité]] · [[Plénitude]] — états vers lesquels le Soulagement peut transiter
- [[L3 - Émotions/Délaissement]] — contexte fréquent de déclenchement
- [[L2 - Schémas Cognitifs/01 — Mentalisation -- Dissociation]] — schéma dont la levée produit le Soulagement relationnel
- [[Protocoles/Transversaux/04 — Drill · L1 Appartenance — Bid for connection rejetée]] — Phase 3 comme déclencheur
- [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §VIII
- [[L0 — Physiologie & Budget Corporel/02 — Allostase]]
