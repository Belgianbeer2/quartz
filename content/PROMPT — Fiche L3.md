---
type: prompt_template
tags:
  - prompt
  - L3
  - template
  - inner-mapping
date: 2026-06-21
version: 1.0
---

# 📐 Template — Fiche L3 · Émotion

---

## Philosophie de la fiche

> [!abstract] Principe directeur — Barrett : affect brut + concept = émotion
> Une fiche L3 n'est pas un journal d'introspection — c'est une cartographie fonctionnelle d'un état psycho-physiologique. Elle répond à trois questions :
> 1. **Qu'est-ce que cette émotion fait** — valence, arousal, action tendency
> 2. **Comment la détecter** — signaux intéroceptifs, cognitifs, comportementaux
> 3. **Comment s'en sortir** — connexions théoriques, régulation Gross, protocoles
>
> **L'expérience personnelle ancre la fiche.** La théorie complète les patterns adjacents non encore vécus.

**Convention de sourcing :**
- `[documenté]` — issu d'une source théorique identifiée
- `[inféré depuis X]` — déduit des fondements
- `[observation personnelle — date]` — instance personnelle
- `[adjacent — non encore observé]` — pattern prédit par la théorie

**Règle de lien obligatoire :**
Chaque concept théorique cité → lien vers fiche Fondements ou `[[01 — Angles morts & évolutions]]`

- Barrett → `[[Fondements théoriques/03 — Cerveau prédictif]]`
- BIS/BAS → `[[Fondements théoriques/05 — BIS & BAS]]`
- Gross → `[[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]`
- Dweck/Entity/Mastery → `[[Fondements théoriques/09 — Mastery orientation · Entity theory]]`
- Kahneman → `[[01 — Angles morts & évolutions]]`

---

## FRONTMATTER

```yaml
---
type: fiche_emotion
tags: [L3, émotion, inner-mapping]
L3_nom: "[nom de l'émotion]"
L3_valence: "négative | positive | mixte"
L3_arousal: "haute | moyenne | basse"
BIS_BAS: "[BIS↑ BAS↓ | BIS↓ BAS↑ | BIS↑ BAS↑ | BIS↓ BAS↓]"
L1_déclencheurs: ["[L1 défensif ou générateur associé]"]
L2_déclencheurs: ["[[L2 schema typiquement impliqué]]"]
L4_comportements: ["[comportement typique généré]"]
date: YYYY-MM-DD
statut: documenté | en cours | angle mort
---
```

---

## BLOC DATAVIEWJS — DRILL 02 (à placer en tête de fichier, avant le titre H1)

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
        relevant.sort((a, b) =>
            moment(b.d, "MM-DD-YYYY").valueOf() - moment(a.d, "MM-DD-YYYY").valueOf()
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

---

## STRUCTURE DE LA FICHE

---

# [Emoji] [Nom de l'émotion]

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p = dv.current();
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.emotion).includes(p.file.name));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph(`*Aucune session — tagger avec \`[emotion:: ${p.file.name}]\`*`);
> ```

---

### I. L'émotion — Définition fonctionnelle

**Ce bloc répond à :** qu'est-ce que cette émotion fait, structurellement ?

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> [Définition de l'émotion dans le cadre de la théorie des émotions construites : affect brut (valence + arousal) + concept appliqué = émotion spécifique. Expliquer pourquoi le cerveau construit *cette* émotion dans ce contexte précis.]

**Valence :** [positive | négative | mixte]
**Arousal :** [haute | moyenne | basse — état d'activation physiologique]
**Action tendency :** [tendance à l'action générée — ce que l'émotion pousse à faire]

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** [↑ élevé | ↓ bas | neutre] — [explication : quelle menace est détectée ou non]
- **BAS :** [↑ élevé | ↓ bas | neutre] — [explication : quelle opportunité/récompense est activée ou bloquée]
- **Combinaison :** [Stratège | Piédestal | Tension active | Retrait | Fatigue | Autre]

**Distinction des émotions proches :**
[Si risque de confusion avec d'autres L3 — clarifier la différence précise]

---

### II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

**Ce bloc répond à :** comment détecter cette émotion *avant* qu'elle soit cognitivement nommée ?

> [!warning] Signaux corporels *(intéroception — voie de détection la plus précoce)*
> - **Zone de tension :** [où dans le corps — poitrine, gorge, mâchoire, ventre, épaules...]
> - **Rythme cardiaque :** [accéléré | ralenti | normal | irrégulier]
> - **Respiration :** [superficielle | bloquée | profonde | accélérée]
> - **Posture spontanée :** [contraction | ouverture | effondrement | rigidité]
> - **Sensations spécifiques :** [chaleur | froid | pesanteur | légèreté | nœud | vide...]

> [!warning] Signaux cognitifs précoces *(pensées automatiques typiques)*
> - [Phrase ou pattern de pensée typiquement associé à cette émotion avant qu'elle soit nommée]
> - [Ex : "de toute façon", "j'aurais dû", "ça va forcément", "c'est ma faute"...]

> [!warning] Signaux comportementaux précoces *(premières tendances à l'action)*
> - [Premier comportement que l'émotion génère — avant intervention consciente]

---

### III. Cartographie théorique

**Ce bloc répond à :** d'où vient cette émotion dans l'écosystème L0→L4 ?

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | [Besoin menacé] | [Comment la menace sur ce besoin produit cette émotion] |
| **Générateur** | [Besoin satisfait] | [Comment la satisfaction de ce besoin produit cette émotion — si applicable] |

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
[Comment l'entity thinking ou le mastery thinking module l'intensité ou la durée de cette émotion]

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme de production |
|---|---|
| [[L2 schema]] | [Comment ce schema produit typiquement cette émotion] |

#### L0 — Influence du budget corporel

[Comment le niveau de budget L0 module l'intensité, la durée, ou la fréquence de cette émotion]

---

### IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | [Comment le budget corporel module l'intensité de cette émotion] |
| **L3 → L0** | ascendant ⚠️/✅ | [Impact de cette émotion sur le budget L0 — consomme ou restaure ?] |
| **L1 → L3** | descendant | [Quels L1 déclenchent cette émotion] |
| **L3 → L1** | ascendant | [Répétée, cette émotion renforce ou affaiblit quels L1 ?] |
| **L2 → L3** | descendant | [Quels schémas L2 produisent typiquement cette émotion] |
| **L3 → L2** | ascendant | [Cette émotion active-t-elle en retour certains L2 ?] |
| **L3 → L4** | descendant | [Quels comportements cette émotion génère-t-elle typiquement ?] |
| **L4 → L3** | ascendant | [Les comportements associés renforcent-ils ou régulent-ils cette émotion ?] |

**Distinction des émotions proches :**
[Tableau comparatif si nécessaire]

---

### V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

> Rappel — les 5 stratégies de Gross (1998), de l'amont vers l'aval :
> 1. Sélection de situation · 2. Modification de situation · 3. Déploiement attentionnel · 4. Reappraisal · 5. Modulation de la réponse

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui/non/partiel | |
| 2 · Modification | oui/non/partiel | |
| 3 · Attentionnel | oui/non/partiel | |
| 4 · Reappraisal | oui/non/partiel | |
| 5 · Modulation | oui/non/partiel | |

**Stratégie prioritaire :** [laquelle est la plus accessible et la plus stable pour cette émotion]
**Note L0 :** [quelle stratégie reste disponible sous budget épuisé]

**Protocoles associés :**
- [Drill concerné si applicable — ex : Drill 01, 03, 04]

---

### VI. Patterns documentés

> [!note] 1. Déclencheurs
> *Instances documentées en session et IRL :*
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let r = []; if (item.children) { item.children.forEach(c => { r.push(c); r.push(...getDescendants(c)); }); } return r; };
> let desc = items.flatMap(getDescendants);
> let counts = {};
> dv.array(desc).where(d => d.declencheur).forEach(i => { let v = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur]; v.forEach(x => { counts[x] = (counts[x] || 0) + 1; }); });
> let sorted = Object.entries(counts).sort((a,b) => b[1]-a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur documenté — tagger avec `[declencheur:: X]`*");
> ```
> > [!note]- ➕ Déclencheurs documentés à froid
> > [Déclencheurs observés hors session si non capturés par DataviewJS]

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
> else dv.paragraph("*Aucune pensée documentée — tagger avec `[pensee:: X]`*");
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
> else dv.paragraph("*Aucune réaction documentée — tagger avec `[reaction:: X]`*");
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
> > - [ ] [Prix à payer:: ]

---

### VII. Analyse à froid — Travail de fond

> [!abstract] *À remplir hors état émotionnel activé*
>
> **1. À quoi le déclencheur fait-il écho ?**
> [Quelle valeur, quel besoin, quel schéma L1 est touché ?]
>
> **2. Ce qui est réel vs construit**
> [Distinguer la contrainte réelle de la narrative L2 construite depuis l'état émotionnel]
>
> **3. Lien entity/mastery dans ce contexte**
> [Comment l'orientation entity ou mastery module l'expérience de cette émotion ici]

---

### VIII. Plan d'action — Recentrage stratégique

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
> > - [ ] [Plan d'action:: ]

---

### IX. Archives

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
[^1]: [Référence principale]

## Notes liées
- [[00 — Protocole In-Game]]
- [L1 déclencheurs] · [L2 schemas associés] · [L4 comportements]
- [Protocoles associés]

---

## CHECKLIST DE COHÉRENCE

- [ ] Valence, arousal, action tendency documentés
- [ ] BIS/BAS mapping explicite avec lien vers fiche 05
- [ ] Signaux intéroceptifs documentés (zone, rythme, respiration, posture)
- [ ] Signaux cognitifs précoces documentés
- [ ] L1 déclencheurs avec mécanisme explicite
- [ ] L2 → L3 connexions documentées
- [ ] Table bidirectionnelle complète (L0/L1/L2/L3/L4)
- [ ] Stratégies Gross identifiées avec note L0 épuisé
- [ ] Distinction avec émotions proches clarifiée
- [ ] Lien entity/mastery documenté
- [ ] Règle de lien obligatoire respectée pour chaque référence théorique
- [ ] DataviewJS Drill 02 en tête de fichier
- [ ] DataviewJS sessions liées présent
