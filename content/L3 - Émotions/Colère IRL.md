---
type: fiche_emotion
tags:
  - L3
  - colère
  - inner-mapping
  - BAS
  - BIS
  - appraisal
date: 2026-06-15
BIS_BAS_source: "BAS frustré · BIS réactif · Prémisses éthiques"
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

# 🧠 Fiche  : La Colère


## 🔬 0. Comprendre l'émotion

> [!abstract] ✅ Deux sources de Colère — Carver (2001) · Smith & Ellsworth (1985)
> La Colère IRL n'a pas une seule origine. Deux mécanismes distincts peuvent la produire, et leur distinction change le levier de régulation :
>
> **Source 1 — BAS frustré** (Carver 2001 — [[Fondements théoriques/05 — BIS & BAS]] §V.2) : le système d'approche est actif (motivation élevée, plan en cours), et un obstacle *externe* bloque l'avancée de façon répétée. La Colère est ici le signal que le BAS cherche un autre passage. Le contrôle *self/autre* est attribué à l'obstacle — c'est l'évaluation qui génère l'émotion.
>
> **Source 2 — BIS/Prémisses éthiques** : un événement active un concept moral préchargé (injustice, violation de consentement, bourreau impuni — [[L1 - Structures profondes/04 — Prémisses éthiques]]) sans nécessairement que le BAS soit actif. La Colère ici signale une violation de valeurs, pas un obstacle à une approche. Le contrôle est attribué à un agent extérieur perçu comme responsable.
>
> **Pourquoi cette distinction compte pour la régulation :**
> - Source 1 → levier = rediriger le BAS (changer d'objet d'approche, ou recadrer l'obstacle)
> - Source 2 → levier = distinguer ce sur quoi j'ai du contrôle (ma réponse) de ce sur quoi je n'en ai pas (l'injustice elle-même) — contrôle secondaire ([[L1 - Structures profondes/05 — Besoin de contrôle]])

> [!abstract] ✅ Mécanisme de la transformation — Gross (1998) · Smith & Ellsworth (1985)
> Le niveau 3 d'Alexis ("je la transforme en levier de détermination") a maintenant un mécanisme documenté dans [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §IV-V :
>
> Colère et Détermination partagent la même énergie (effort anticipé élevé, BAS actif). Ce qui les distingue : *où* le contrôle/la responsabilité est perçu — sur l'obstacle extérieur (Colère) vs sur mon propre processus/mes valeurs (Détermination). La transformation n'est pas un "calmant" — c'est une **redirection du contrôle perçu**, sans changer l'énergie mobilisée. C'est un *reappraisal* (changement cognitif, Gross #4) — la stratégie la plus documentée pour ce type de transformation.

> [!abstract] Ce que Moukheiber éclaire
> La fiche IRL illustre un mécanisme précis : le discours interne explosif (*"je vais les défoncer"*, *"je vais tout faire péter"*) et la réaction réelle (stratégie de l'autruche) sont **opposés**. Ce n'est pas une contradiction — c'est le fonctionnement normal du cerveau sous impuissance.
>
> Quand on n'a aucun pouvoir sur une situation, le cerveau génère une **histoire d'agentivité** pour compenser. *"Je vais tout faire péter"* n'est pas un plan — c'est une illusion de contrôle produite pour rendre la situation supportable. La stratégie de l'autruche est la réaction *réelle* ; le discours explosif est la réaction *narrative*. L'écart entre les deux, c'est exactement ce que Moukheiber montre : le *soi narratif* et le *soi comportemental* ne coïncident pas sous pression.

> [!abstract] Ce que Alexis pointe — Les 3 niveaux de traitement
> La colère n'est pas irrationnelle quand le trigger touche aux valeurs fondamentales (liberté, autodétermination). Elle est **cohérente** avec qui tu es. Le travail n'est pas de l'effacer — c'est de la traverser :
>
> 1. **Je la subis** — le trigger crée l'impuissance, l'émotion déborde.
> 2. **Je la gère** — stratégie de l'autruche, faire des choses à conséquences limitées le temps de s'apaiser.
> 3. **Je la transforme** — la valeur (liberté, autodétermination) devient **levier de détermination** : *"je joue pour construire l'indépendance qui me permettra d'aider les gens qui m'importent."*
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Colère*

---

## 📊 1. Patterns de l'émotion

> [!danger] **1. Déclencheurs (Trigger)**
> *Fréquence des faits bruts identifiés (In-game) :*
> - Le beau père de Sassa, qui est enfermé en prison injustement est sur le point de mourir. Il est mal nourrit, incapable de bouger et mal traité par les officiers (injustices)

> [!danger] **2. Pensées automatiques**
>*Fréquence des histoires mentales récurrentes :*
> - "j'aurais préféré ne pas être au courant"
> - "je vais les défoncer"
> - "Je vais tout faire pêter"
> 

> [!danger] **3. Schémas comportementaux (Réactions)**
>*Fréquence des réactions identifiées :*
>- Stratégie de l'autruche
>	- faire des choses qui ont des conséquences limités (le temps que je m'appaise)
>

> [!danger] **4. Prix à payer de rester dans l'illusion de la Colère**
> - [ ] [Prix à payer:: me faire guider par mes émotion (ne plus être le conducteur de mon corps)]
> - [ ] [Prix à payer:: ]
## 🔍 2. Travail de fond (Vrai problème)

> [!danger] **Analyse à froid (Hors session)**
> ### 1. A quoi le trigger fait-il écho ?
> - injustice + impuissance
> 	Pourquoi ça importe pour moi ?
> 	- je veux que les gens puissent vivre librement
> 	- Je veux que les gens puissent s'auto-déterminé
> ### 2. Qu'est-ce que j'en fais ?
> *1. je la subis. 2. Je la gère (stratégie) 3. Je la transforme (je crée un levier de détermination)*
> 	- Comment je transforme toutes ces valeur humaine pour en faire qqch d'utile et non qqch qui me bouffe ?
> >**Dépolarisation sur l'injustice**
## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!danger] **Recentrage Stratégique**
> - [ ] [Plan d'action:: Rubber ducké]
>
## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
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
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
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

>
---

## Notes liées
- [[Fondements théoriques/05 — BIS & BAS]] §V.2
- [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]] §IV-V
- [[L1 - Structures profondes/04 — Prémisses éthiques]]
- [[L1 - Structures profondes/05 — Besoin de contrôle]]
- [[L3 - Émotions/Accablement]]
