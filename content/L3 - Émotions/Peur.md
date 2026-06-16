---
type: fiche_emotion
tags:
  - émotion
  - peur
  - résultats
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

# 🧠 Fiche d'exploration : Peur

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
> La peur est l'émotion de survie la plus fondamentale — elle peut s'activer via deux circuits distincts [documenté — LeDoux] :
>
> **Low road** (~12ms) : réaction viscérale immédiate avant tout traitement cognitif. Un bad beat brutal, un pot énorme perdu — la peur peut s'activer avant même de pouvoir nommer.
>
> **High road** (~300ms+) : construction progressive à partir de l'interprétation. La peur des résultats financiers opère principalement ici — elle est construite par les L2 (Vision zoomée, Sélectivité mémorielle, Pensée binaire) sur la base d'un appui L1 Résultats-dépendance.
>
> La peur construite via le high road est particulièrement piégeuse : elle *semble* rationnelle parce qu'elle est accompagnée d'un raisonnement. Mais le raisonnement est venu après — il justifie la peur, il ne la génère pas.

> [!abstract] Ce que Alexis pointe — Peur vs Honte
>
> La peur et la honte sont les deux émotions dominantes du mal-être in-game, mais elles n'ont pas le même objet :
>
> | | **Peur** | **Honte** |
> |---|---|---|
> | **Objet** | Résultat financier · variance · bad run | Déviation d'intention · qualité de jeu perçue |
> | **Trigger** | Session perdante · résultat sous les attentes | Comportement in-game qui s'éloigne du warmup |
> | **Message** | *"Je vais perdre · je ne suis pas viable"* | *"Je SUIS défaillant"* |
> | **Action tendency** | Retrait · évitement · fuite | Rumination · paralysie |
>
> **[documenté — Boussole émotionnelle]** La peur est l'appui L1 de la boucle de mal-être. Tout le travail de l'Inner Mapping vise à changer cet appui de Peur → Confiance.
>
> *Pierre progresse sur l'immunité à la peur liée aux résultats financiers — c'est un chantier de fond (L1 Résultats-dépendance).*
>
> *→ Voir cascade liée :* [[01 — Résultat négatif → Peur → Retrait]]

---

## 📊 1. Patterns de l'émotion

> [!danger] 1. Déclencheurs (Trigger)
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

> [!danger] 2. Pensées automatiques
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

> [!danger] 3. Schémas comportementaux (Réactions)
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

> [!danger] 4. Prix à payer
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
> > - [ ] [Prix à payer:: J'accepte que la variance fait partie du jeu — une session perdante n'est pas une information sur mon niveau]
> > - [ ] [Prix à payer:: J'accepte de ne pas lancer de session depuis un état de peur des résultats]

---

## 🔍 2. Travail de fond (Vrai problème)

> [!danger] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - L1 activé : Résultats-dépendance — la confiance est liée aux résultats financiers
> - L2 actifs : Vision zoomée · Sélectivité mémorielle · Pensée binaire
> ### 2. Identification de l'Objet de l'émotion
> - L'objet est financier et identitaire : *"je ne suis pas viable"* / *"le système est cassé"*
> - Distinct de la [[La Honte]] dont l'objet est la qualité de jeu perçue

---

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!danger] Recentrage Stratégique
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
> > - [ ] [Plan d'action:: Nommer la peur → identifier le L2 actif (Vision zoomée ? Pensée binaire ?) → ramener la fenêtre temporelle correcte (4-6 mois)]
> > - [ ] [Plan d'action:: Ne pas lancer de session depuis cet état — viser BE+HM d'abord]

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
- *Cascade liée :* [[01 — Résultat négatif → Peur → Retrait]]
- *L1 sous-jacent :* Résultats-dépendance (fiche à créer)
- *Lien direct :* [[🧭 Boussole émotionnelle]] — appui L1 boucle de mal-être
