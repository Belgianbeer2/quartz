----
type: fiche_emotion
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

# 🧠 Fiche d'exploration : La Réactance

> [!note]- 📜 Voir les sessions liées à cette émotion
> *Cliquez sur une session pour ouvrir le feedback correspondant.*
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> 
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const emotionsDansSession = page.file.lists.emotion;
>         return dv.array(emotionsDansSession).includes(targetEmotion);
>     });
> 
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```


## 🔬 0. Comprendre l'émotion

> [!abstract] ✅ Fondement — Brehm (1966, 1981) · Carver (2001)
> La **réactance** est la réponse motivationnelle à la perception d'une menace sur une liberté d'action. Brehm (1966) la définit comme une pression interne dirigée vers la *restauration* de la liberté menacée — proportionnelle à l'importance de cette liberté et à l'intensité de la menace perçue.
>
> Le mécanisme : une liberté est perçue comme menacée ou supprimée → activation d'un état motivationnel orienté vers la restauration → impulsion d'agir dans la direction bloquée, souvent avec une intensité *supérieure* à ce qu'elle aurait été sans blocage.
>
> Carver (2001) ancre ce mécanisme dans le BAS : la réactance est une réponse BAS à un obstacle — l'élan toward était actif, l'obstacle l'intensifie plutôt que de le stopper. Ce n'est pas du désespoir — c'est de l'énergie réorientée contre le blocage.
>
> *Lien L1 :* [[L1 - Structures profondes/02 — Besoin d'Autonomie]] — la réactance est l'émotion-signal que le besoin d'autonomie est entravé dans ce contexte. La liberté d'action perçue comme menacée est précisément l'autonomie décisionnelle.

> [!abstract] Ce que Moukheiber éclaire — La confabulation
> La réactance est particulièrement piégeuse parce qu'elle **utilise le vocabulaire du jeu** pour habiller une impulsion émotionnelle. *"Les propriétés de cette main sont pas mal pour reprendre l'initiative"* ressemble à de l'analyse GTO. Mais la décision de jouer a été prise avant le raisonnement — le raisonnement est venu justifier après coup.
>
> C'est ce que Moukheiber appelle *confabuler* : construire une explication rationnelle a posteriori d'une décision déjà prise émotionnellement. La main n'est pas nécessairement mauvaise — c'est sa *source* qui l'est.

> [!abstract] Les 3 marqueurs qui distinguent une justification d'une analyse
>
> **1. La sélectivité**
> Une analyse considère toutes les propriétés — pour ET contre. Une justification ne convoque que les propriétés favorables. *"Pas mal pour reprendre l'initiative"* — mais les propriétés défavorables ont-elles été pesées au même titre ? Si non : c'est un avocat de la défense, pas un analyste.
>
> **2. Le sens de la causalité**
> Dans une analyse : j'évalue → je décide. Dans une justification : je décide → je trouve des raisons. Le *"je vais reprendre l'initiative"* précède la pensée sur les propriétés de la main — pas l'inverse.
>
> **3. La vitesse et la certitude**
> Une vraie analyse génère de l'incertitude — c'est son signe de bonne santé. Une justification est rapide et certaine, parce que la conclusion est déjà là avant que le raisonnement commence. Si la pensée est arrivée vite et sans doute juste après le bluff-catch — c'est le signal.

> [!abstract] Ce que Alexis pointe
> La réactance se diagnostique avec une seule question : *"Est-ce que je joue ce coup pour optimiser mon EV ou pour reprendre le contrôle ?"*
>
> Si c'est pour reprendre le contrôle — c'est de la réactance. Et une question de test complémentaire : *"Si cet adversaire n'avait pas été agressif juste avant, est-ce que cette main m'aurait semblé jouable de la même façon ?"* Si la réponse est non — c'est de la réactance, pas de la stratégie.
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Réactance*


> [!abstract] Réactance et dimension Agon — Caillois (1958) · Carver (2001)
> La Réactance et le mode Agon partagent la même structure profonde : **un besoin que quelque chose résiste**. Ils se distinguent par leur temporalité et leur direction.
>
> | | Réactance | Agon |
> |---|---|---|
> | **Direction** | Réactive — réponse à un blocage déjà présent | Proactive — recherche délibérée d'un adversaire |
> | **Temporalité** | Se déclenche *après* la frustration | S'active *avant* ou *dès* l'identification d'un défi |
> | **Objet** | La liberté d'action perçue comme menacée | La compétence à tester contre une résistance |
> | **Émotion produite** | Impulsion de reprendre le contrôle · colère | Engagement · énergie orientée · détermination |
>
> Pour un profil Agon dominant, la Réactance peut être vue comme la *forme défensive* de ce besoin (réponse à une résistance imposée), tandis que l'Agon en est la *forme proactive* (recherche délibérée d'une résistance choisie).
>
> **Application session poker :** dans une session à -5 buyins, les deux coexistent — l'Agon s'active sur la variance comme adversaire (engagement fonctionnel) et la Réactance peut s'activer sur les bad beats spécifiques (impulsion de reprendre le contrôle). Le premier est fonctionnel. Le second bascule vers le tilt si non régulé via [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]].
>
> *→ Voir :* [[Fondements théoriques/10 — Agon · Alea · Mimicry · Ilinx]] · [[L2 - Schémas Cognitifs/11 — Mobilisation compensatoire -- Suramplification]]

---

## 📊 1. Patterns de l'émotion

> [!example] 1. Déclencheurs (Trigger)
> *Fréquence des faits bruts identifiés (In-game) :*
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> // Fonction récursive pour tout aspirer peu importe la profondeur
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> 
> dv.array(descendants).where(d => d.declencheur).forEach(i => { 
>     let vals = Array.isArray(i.declencheur) ? i.declencheur : [i.declencheur];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucun déclencheur identifié.*");
> ```

> [!example] 2. Pensées automatiques
> *Fréquence des histoires mentales récurrentes :*
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> 
> dv.array(descendants).where(d => d.pensee).forEach(i => { 
>     let vals = Array.isArray(i.pensee) ? i.pensee : [i.pensee];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) {
>     sorted.forEach(e => { dv.el("blockquote", `« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`); });
> } else {
>     dv.paragraph("*Aucune pensée enregistrée.*");
> }
> ```

> [!example] 3. Schémas comportementaux (Réactions)
> *Fréquence des réactions identifiées :*
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let counts = {};
> 
> dv.array(descendants).where(d => d.reaction).forEach(i => { 
>     let vals = Array.isArray(i.reaction) ? i.reaction : [i.reaction];
>     vals.forEach(v => { counts[v] = (counts[v] || 0) + 1; });
> });
> 
> let sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
> if (sorted.length > 0) dv.list(sorted.map(e => `${e[0]} **(x${e[1]})**`));
> else dv.paragraph("*Aucune réaction identifiée.*");
> ```

> [!example] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix à payer actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer à froid
> > - [ ] [Prix à payer:: ]

## 🔍 2. Travail de fond (Vrai problème)

> [!example] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - 
> ### 2. Identification de l'Objet de l'émotion
> - 

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!example] Recentrage Stratégique
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan d'action actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action à froid
> > - [ ] [Plan d'action:: ]

## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

## 📝 Notes de suivi & Coaching

*L1 entravé :* [[L1 - Structures profondes/02 — Besoin d'Autonomie]]
*L2 lié :* [[L2 - Schémas Cognitifs/02 — Évaluation causale -- Confabulation]]
*Connexion Agon :* [[Fondements théoriques/10 — Agon · Alea · Mimicry · Ilinx]]
*Connexion L1 :* [[L1 - Structures profondes/01 — Besoin de Compétence]] — mode Agon §I.3
*Protocole associé :* [[Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt d'escalade]]