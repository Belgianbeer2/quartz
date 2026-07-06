---
type: fiche_emotion
tags: [L3, émotion, culpabilité, inner-mapping]
L3_nom: "Culpabilité"
L3_valence: "négative"
L3_arousal: "moyenne"
BIS_BAS: "BIS↑ BAS↑ (réparation)"
L1_déclencheurs: ["Prémisses éthiques défensif", "Besoin de Compétence défensif (Intransigeance)"]
L2_déclencheurs: ["[[09 — Encodage de l'erreur -- Auto-flagellation]]", "[[03 — Reconstruction mémorielle -- Sélectivité mémorielle]]"]
L4_comportements: ["Réparation · Compensation · Évitement · Sur-engagement compensatoire"]
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

# 😔 Culpabilité

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p = dv.current();
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.emotion).includes(p.file.name));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[emotion:: Culpabilité]`*");
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
> La Culpabilité est construite quand le cerveau applique le concept "j'ai fait quelque chose de mal" à un affect négatif lié à une action passée propre. Contrairement à la [[Honte]] qui porte sur l'identité ("je SUIS mauvais"), la Culpabilité porte sur le comportement ("j'AI fait quelque chose de mal"). Cette distinction est fondamentale : elle change l'action tendency et le levier de régulation. [documenté]

> [!abstract] ✅ Fondement — Neff (2003, 2011) · [[Fondements théoriques/07 — Self-compassion]]
> Neff distingue la culpabilité fonctionnelle (signal d'alignement avec ses valeurs, oriente vers la réparation) de la culpabilité toxique (se confond avec la Honte, produit de la rumination sans réparation). La culpabilité fonctionnelle est en réalité adaptative — elle indique que les valeurs sont actives. [documenté]

**Valence :** négative
**Arousal :** moyenne — moins intense que la Colère, plus insistante que l'Impuissance
**Action tendency :** réparation, compensation, confession, évitement (si toxique)

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ élevé — violation d'un standard interne perçue → système d'inhibition actif
- **BAS :** ↑ actif sur la réparation — l'élan vers la réparation est une activation BAS sur un objectif de correction. La culpabilité fonctionnelle mobilise, elle ne paralyse pas.
- **Combinaison :** Tension active BIS↑/BAS↑ — énergie disponible mais orientée vers un objectif précis (réparer)

**Distinction fondamentale — Culpabilité vs Honte :**

| | **Culpabilité** | **[[Honte]]** |
|---|---|---|
| **Objet** | Un comportement ("j'AI fait") | L'identité ("je SUIS") |
| **Action tendency** | Réparation · compensation | Retrait · cachement |
| **Question générée** | "Qu'est-ce que je peux faire ?" | "Qu'est-ce que je suis ?" |
| **Résolution possible** | Oui — l'action répare | Difficile — l'identité ne se répare pas facilement |
| **Lien entity thinking** | Amplifie vers la Honte si ET actif | ET nécessaire à la Honte |

> [!warning] La Culpabilité toxique
> Quand la Culpabilité est amplifiée par l'entity thinking, elle glisse vers la Honte : "j'ai fait une erreur" → "je SUIS quelqu'un qui fait des erreurs" → boucle de Rumination sans réparation possible. C'est ce glissement qui la rend dysfonctionnelle — pas la culpabilité elle-même. → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** poitrine — sensation de poids ou de compression · estomac — nœud ou vide
> - **Rythme cardiaque :** légèrement accéléré ou irrégulier (moins intense que la Colère ou la Peur)
> - **Respiration :** légèrement superficielle · soupirs fréquents
> - **Posture spontanée :** tête légèrement baissée · épaules en avant · regard qui évite
> - **Sensations spécifiques :** pesanteur diffuse · sentiment d'insistance ("ça revient") sans explosion

> [!warning] Signaux cognitifs précoces
> - *"J'aurais dû..."* / *"Je n'aurais pas dû..."* — formulation passée centrée sur l'action
> - *"C'est ma faute"* — attribution interne, distincte du blâme externe
> - Rejouer mentalement l'événement pour identifier où "ça a dérapé"
> - Pensées de réparation : "comment je pourrais arranger ça ?"

> [!warning] Signaux comportementaux précoces
> - Tendance à vouloir réparer immédiatement (parfois avant d'avoir bien évalué)
> - Tendance à l'évitement de la personne ou du contexte associé
> - Sur-engagement compensatoire : travailler plus, faire plus, pour "effacer" la faute

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Prémisses éthiques | Violation d'un standard moral ou d'un engagement → signal que les valeurs sont trahies |
| **Défensif** | Besoin de Compétence (Intransigeance) | Erreur traitée comme trahison de ses propres exigences → "j'aurais dû faire mieux" |
| **Défensif** | Besoin d'Appartenance | Ne pas avoir été présent, disponible ou utile pour quelqu'un qui compte → trahison du lien |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : amplifie la Culpabilité vers la Honte. "J'ai fait une erreur" → "je SUIS quelqu'un qui fait des erreurs" → glissement identitaire → Rumination sans réparation
- **Mastery thinking** : maintient la Culpabilité dans sa forme fonctionnelle. L'erreur est traitée comme de l'information sur le processus → réparation possible → apprentissage

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme de production |
|---|---|
| [[09 — Encodage de l'erreur -- Auto-flagellation]] | L'Auto-flagellation peut naître de la Culpabilité ou la produire — boucle réciproque |
| [[03 — Reconstruction mémorielle -- Sélectivité mémorielle]] | Sous état négatif, la reconstruction sélectionne les moments "où j'ai failli" → amplifie la Culpabilité |
| [[10 -- Traitement mémoriel -- Rumination]] | La Culpabilité toxique se transforme en Rumination si non résolue → amplifie encore |

#### L0 — Influence du budget corporel

Sous budget L0 épuisé, la Culpabilité est plus difficile à maintenir dans sa forme fonctionnelle — le glissement vers la Honte (et la Rumination) est plus probable car le PFC est moins disponible pour le reappraisal. Le "j'ai fait" glisse vers "je suis" sans résistance cognitive.

**Contextes poker spécifiques :**
- Culpabilité après une erreur technique connue → risque Auto-flagellation
- Culpabilité de ne pas avoir travaillé assez → risque de Procrastination Productive compensatoire
- Culpabilité post-session gagnante ("j'aurais dû jouer plus") → forme paradoxale, liée au Piédestal

**Contextes IRL :**
- Culpabilité liée à l'isolement géographique (ne pas être présent pour la famille) → triple activation Appartenance + Éthique + Compétence
- Culpabilité liée aux difficultés financières et leur impact sur Sassa → activation Éthique + Appartenance

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → glissement Culpabilité fonctionnelle → Honte plus probable · PFC moins disponible pour maintenir le reappraisal |
| **L3 → L0** | ascendant ⚠️ | Culpabilité insistante → activation BIS chronique → consomme L0 · Culpabilité fonctionnelle résolue → légèrement restauratrice (fermeture de boucle) |
| **L1 → L3** | descendant | Prémisses éthiques défensif + Compétence défensif (Intransigeance) + Appartenance défensif |
| **L3 → L1** | ascendant | Répétée sans résolution → renforce l'Intransigeance ("je dois toujours faire mieux") · Résolue par réparation → renforce les Prémisses éthiques génératives |
| **L2 → L3** | descendant | Auto-flagellation · Sélectivité mémorielle · Rumination la produisent ou l'amplifient |
| **L3 → L2** | ascendant | La Culpabilité active la Rumination (rejouer l'événement) et peut déclencher l'Auto-flagellation |
| **L3 → L4** | descendant | Réparation · compensation · évitement · sur-engagement compensatoire |
| **L4 → L3** | ascendant | L4 réparation ferme la boucle → réduit la Culpabilité · L4 évitement maintient la boucle ouverte → amplifie |

**Distinction avec émotions proches :**
- vs **[[Honte]]** : Honte = identité ("je SUIS"), Culpabilité = comportement ("j'AI fait"). La Honte est plus résistante à la régulation — elle ne se résout pas par la réparation comportementale.
- vs **[[Impuissance]]** : l'Impuissance n'a pas d'agent interne ("rien à faire"). La Culpabilité a un agent interne ("c'est moi qui ai fait"). La Culpabilité fonctionnelle a un levier — la réparation.
- vs **[[Accablement]]** : l'Accablement est une phase prolongée BAS-/BIS-, sans déclencheur identifiable. La Culpabilité est une réponse à un événement précis, avec un agent interne.

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | partiel | Différer l'analyse de la "faute" quand L0 est épuisé — le glissement vers la Honte est trop probable |
| 2 · Modification | oui | Action de réparation concrète — ferme la boucle Culpabilité plus efficacement que le reappraisal seul |
| 3 · Attentionnel | partiel | *"Qu'est-ce que je peux faire ?"* — orienter vers l'action plutôt que vers le verdict |
| 4 · Reappraisal | oui | *"J'ai fait une erreur sur ce comportement — pas sur ce que je suis"* · Mastery frame : l'erreur est de l'information |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Modification (2) — la réparation concrète est le levier le plus direct de la Culpabilité fonctionnelle. Elle ferme la boucle là où le reappraisal seul peut tourner en rond.
**Note L0 :** sous budget épuisé, le Reappraisal est moins fiable. Action de réparation minimale + co-régulation sociale d'abord.

**Protocoles associés :**
- [[Protocoles/Transversaux/01 — Drill · L1 Besoin de contrôle — Contrôle secondaire]] — distinguer ce qui est réparable de ce qui ne l'est pas

---

## VI. Patterns documentés

> [!note] 1. Déclencheurs
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.declencheur).forEach(i => { let v = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur documenté.*");
> ```
> > [!note]- Déclencheurs documentés à froid
> > - Erreur technique sur spot connu *(in-game)*
> > - Ne pas avoir assez travaillé avant une session *(IRL)*
> > - Ne pas être disponible pour Sassa dans un moment difficile *(IRL)*
> > - Session gagnante avec volume réduit ("j'aurais dû jouer plus") *(in-game)*
> > - Isolement géographique qui impacte les relations familiales *(IRL)*

> [!note] 2. Pensées automatiques
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.pensee).forEach(i => { let v = Array.isArray(i.pensee) ? i.pensee : [i.pensee]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) sorted.forEach(e => dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!note] 3. Réactions
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.reaction).forEach(i => { let v = Array.isArray(i.reaction) ? i.reaction : [i.reaction]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!note] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let ingame = dv.array(desc).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: J'accepte que cette erreur est de l'information sur mon processus — pas un verdict sur ce que je suis]
> > - [ ] [Prix à payer:: J'accepte que la réparation possible vaut mieux que la rumination sur ce qui ne l'est pas]
> > - [ ] [Prix à payer:: J'accepte que la distance géographique crée des contraintes réelles sur ma disponibilité — ce n'est pas un jugement sur ma valeur relationnelle]

---

## VII. Analyse à froid — Travail de fond

> [!abstract] *À remplir hors état émotionnel activé*
>
> **1. Est-ce de la Culpabilité ou de la Honte ?**
> Question pivot : *"Est-ce que je pense à ce que j'ai fait — ou à ce que je suis ?"*
> - "J'ai fait une erreur sur ce spot" → Culpabilité → réparable
> - "Je suis quelqu'un qui fait des erreurs" → Honte → travail de fond différent → [[Honte]]
>
> **2. Est-ce réparable ?**
> - Oui → identifier l'action de réparation la plus petite possible → agir → fermer la boucle
> - Non → distinguer ce qui est hors contrôle → Drill 01 (contrôle secondaire)
>
> **3. À quoi la valeur touchée renvoie-t-elle ?**
> [Identifier la valeur ou l'engagement que l'action a trahi — Prémisses éthiques, Appartenance, Compétence]

---

## VIII. Plan d'action — Recentrage stratégique

> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let ingame = dv.array(desc).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action
> > - [ ] [Plan d'action:: Nommer l'émotion précisément — Culpabilité, pas Honte. Identifier ce qui est réparable.]
> > - [ ] [Plan d'action:: Action de réparation minimale → fermer la boucle]
> > - [ ] [Plan d'action:: Si irréparable → Drill 01 mode post-situationnel]
> > - [ ] [Plan d'action:: Test : "Est-ce que je dirais ça à quelqu'un que j'estime qui aurait fait la même chose ?"]

---

## IX. Archives

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let archives = dv.array([...desc, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let archives = dv.array([...desc, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

---

## Sources

[^1]: Neff, K.D. (2003). Self-compassion. *Self and Identity*, 2(2). → [[Fondements théoriques/07 — Self-compassion]]
[^2]: Barrett, L.F. (2017). *How Emotions Are Made*. → [[Fondements théoriques/03 — Cerveau prédictif]]
[^3]: Tangney, J.P. & Dearing, R.L. (2002). *Shame and Guilt*. Guilford Press. → [[01 — Angles morts & évolutions]]

## Notes liées
- [[Honte]] — distinction fondamentale identité vs comportement
- [[Impuissance]] — différence agent interne vs absence de levier
- [[Accablement]] — différence état prolongé vs réaction événementielle
- [[09 — Encodage de l'erreur -- Auto-flagellation]]
- [[Fondements théoriques/07 — Self-compassion]]
- [[L1 - Structures profondes/04 — Prémisses éthiques]]
- [[Protocoles/Transversaux/01 — Drill · L1 Besoin de contrôle — Contrôle secondaire]]
