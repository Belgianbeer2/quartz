---
type: fiche_emotion
tags:
  - émotion
  - impuissance
  - contrôle
  - inner-mapping
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

# 🧠 Fiche d'exploration : Impuissance

> [!note]- 📜 Voir les sessions liées à cette émotion
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const emotionsDansSession = page.file.lists.emotion;
>         return dv.array(emotionsDansSession).includes(targetEmotion);
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```

---

## 🔬 0. Comprendre l'émotion

> [!abstract] Ce que Moukheiber éclaire
> L'impuissance est l'émotion déclenchée quand le cerveau perçoit l'absence totale de levier sur une situation. Sa caractéristique principale : elle génère immédiatement une **réponse compensatoire**.
>
> **[documenté]** Quand on n'a aucun pouvoir sur une situation, le cerveau génère une histoire d'agentivité pour compenser. Le discours interne explosif (*"je vais tout faire péter"*) et la réaction réelle (stratégie de l'autruche) sont opposés — ce n'est pas une contradiction, c'est le fonctionnement normal du cerveau sous impuissance. Le *soi narratif* et le *soi comportemental* ne coïncident pas sous pression.
>
> In-game, l'impuissance prend une forme différente : la perte du contrôle sur les résultats (variance) est vécue comme une absence de levier — alors que le seul levier disponible est le processus. La tentative de *reprendre* le contrôle là où il n'y en a pas génère la Réactance, la Colère, et dans les cas extrêmes la Surchauffe cognitive.

> [!abstract] Ce que Alexis pointe — L'impuissance comme émotion sous-jacente
>
> L'impuissance est rarement nommée seule — elle est le **carburant émotionnel** d'autres émotions plus visibles :
>
> | Émotion de surface | Impuissance sous-jacente |
> |---|---|
> | [[La Réactance]] | Impuissance face à l'agressivité adverse → reprendre le contrôle |
> | [[Colère IRL]] | Impuissance face à l'injustice → discours explosif |
> | [[04 — Surchauffe cognitive → Colère → Impulsivité]] | Impuissance face à la fatigue + chaleur → réécriture des corrélations |
>
> **Les 3 niveaux de traitement [documenté — Alexis, Colère IRL] :**
> 1. **Je la subis** — l'impuissance déborde, génère la réaction de surface
> 2. **Je la gère** — stratégie d'apaisement, actions à conséquences limitées
> 3. **Je la transforme** — identifier la valeur touchée (liberté, autodétermination) → levier de détermination
>
> *→ Voir aussi :* [[Colère IRL]] — Section 0, et [[Être et Faire — Réconciliation Moukheiber × Alexis]]

---

## 📊 1. Patterns de l'émotion

> [!warning] 1. Déclencheurs (Trigger)
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.declencheur).forEach(i => {
>     let vals = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur identifié.*");
> ```

> [!warning] 2. Pensées automatiques
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.pensee).forEach(i => {
>     let vals = Array.isArray(i.pensee) ? i.pensee : [i.pensee];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) { sorted.forEach(e => { dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`); }); }
> else dv.paragraph("*Aucune pensée enregistrée.*");
> ```

> [!warning] 3. Schémas comportementaux (Réactions)
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> dv.array(descendants).where(d => d.reaction).forEach(i => {
>     let vals = Array.isArray(i.reaction) ? i.reaction : [i.reaction];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction identifiée.*");
> ```

> [!warning] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix à payer actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer à froid
> > - [ ] [Prix à payer:: J'accepte que la variance n'est pas un levier — le seul levier est le processus]
> > - [ ] [Prix à payer:: J'accepte que tenter de reprendre le contrôle là où il n'existe pas génère la Réactance et la Colère]

---

## 🔍 2. Travail de fond (Vrai problème)

> [!warning] *Analyse à froid (Hors session)*
> ### 1. Quelle valeur est touchée ?
> - Liberté · autodétermination · contrôle sur son environnement
> - Identifier la valeur précise permet de transformer l'impuissance en levier (niveau 3)
> ### 2. Impuissance objective vs perçue ?
> - Objective : aucun levier réel disponible (variance, tiers)
> - Perçue : un levier existe (le processus, la décision) mais l'impuissance le masque

---

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!warning] Recentrage Stratégique
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); }
>     return results;
> };
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan d'action actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action à froid
> > - [ ] [Plan d'action:: Nommer l'impuissance → identifier quelle émotion de surface elle alimente (Réactance ? Colère ?) → consulter la fiche correspondante]
> > - [ ] [Plan d'action:: Identifier la valeur touchée → transformer en levier de détermination (niveau 3)]

---

## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let results = []; if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); } return results; };
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> let getDescendants = (item) => { let results = []; if (item.children) { item.children.forEach(child => { results.push(child); results.push(...getDescendants(child)); }); } return results; };
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

---

## 📝 Notes de suivi & Coaching
- *Émotion sous-jacente de :* [[La Réactance]] · [[Colère IRL]] · [[04 — Surchauffe cognitive → Colère → Impulsivité]]
- *Lien direct :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] — les 3 niveaux subir/gérer/transformer
