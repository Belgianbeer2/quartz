---
type: schema_L2
tags: [L2, schema, perfectionnisme, ambition, mastery, inner-mapping]
L2_neutre: "Orientation vers l'idéal"
pôle_défensif: "Perfectionnisme"
pôle_générateur: "Ambition"
L1_déclencheurs: ["Besoin de Compétence", "Besoin de Contrôle", "Besoin d'Autonomie"]
émotions_produites: ["Frustration", "Honte", "Culpabilité"]
stratégies_Gross: ["4 · Reappraisal", "3 · Déploiement attentionnel", "1 · Sélection"]
entity_mastery: "les deux"
date: 2026-06-28
statut: documenté
---

```dataviewjs
let p = dv.current();
let targetPattern = p["pôle_défensif"] || p.file.name;
let sessions = dv.pages('"Journal/Session/Feedback/2026"')
    .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
if (sessions.length > 0) {
    dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
} else {
    dv.paragraph(`*Aucune session — tagger avec \`[pattern:: ${targetPattern}]\`*`);
}
```

# 🎯 L2 — Orientation vers l'idéal · Ambition / Perfectionnisme

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p = dv.current();
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes("Perfectionnisme"));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph(`*Aucune session — tagger avec \`[pattern:: Perfectionnisme]\`*`);
> ```

---

## I. L'opération neutre — Orientation vers l'idéal

> [!abstract] ✅ Fondement — Dweck (1986, 1999) · [[Fondements théoriques/09 — Mastery orientation · Entity theory]] · Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> L'**orientation vers l'idéal** est la capacité du cerveau à générer une représentation cible d'un output et à s'y référer pour guider l'action. En termes de cerveau prédictif (Barrett), c'est une **erreur de prédiction volontairement entretenue** : le gap entre l'état actuel et l'état cible génère un signal moteur qui dirige l'action.
>
> Fonctionnellement : Input (état actuel) → représentation de l'idéal → évaluation du gap → action corrective. Ce cycle est universel et adaptatif — sans idéal, pas de direction.

**Définition fonctionnelle :** génération d'une représentation cible + évaluation continue du gap entre état actuel et état idéal → signal orientant l'action.

**Ancrage théorique :** Dweck (1999) distingue deux façons d'utiliser un idéal : comme *boussole d'apprentissage* (mastery) ou comme *standard de valeur identitaire* (entity). C'est cette différence d'utilisation — pas l'idéal lui-même — qui détermine le pôle activé. → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]

**Modulation par L0 :** Budget plein → gap traité comme information sur le prochain geste. Budget épuisé → gap traité comme verdict sur la valeur personnelle. L'entity thinking est le médiateur : il s'active préférentiellement sous L0 réduit. → [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]

**Universalité :** Se représenter un idéal est nécessaire à tout apprentissage, toute création, toute ambition. L'opération n'est pas problématique en soi — c'est son **couplage à l'identité** qui produit le pôle défensif.

---

## II. Cartographie des pôles — Toutes expressions possibles

> **Méthode :** les instances personnelles documentées (juin 2026, Alexis 04-20-2026) sont les ancres. Les expressions adjacentes sont déduites des mêmes mécanismes L1 × entity/mastery × L0.

### A. Pôle défensif — Perfectionnisme

*Expression sous appui L1 défensif et/ou entity thinking*

> **Rappel architectural :** un L2 défensif est une opération cognitive mobilisée *au service* d'un L1 défensif menacé. Le L1 actif détermine la *direction* de la distorsion. Ici : l'idéal ne dirige plus — il juge.

---

**Expression 1 — Gap compétences/vision (L1 Compétence menacé)**

- **L1 actif :** [[L1 - Structures profondes/01 — Besoin de Compétence|Besoin de Compétence]] en mode défensif
  *Ce qui est menacé :* l'efficacité perçue — si le gap entre la vision idéale et les compétences actuelles est visible, la compétence est exposée comme insuffisante
- **Mécanisme L1→L2 :** le Besoin de Compétence menacé active l'entity thinking (Dweck) : l'idéal devient un *standard de ce qu'on devrait être capable de produire*. Le gap n'est plus une étape d'apprentissage — il est une preuve de déficit de compétence. Chaque imperfection en cours de tâche vient frapper ce gap, qui s'accumule plutôt que de s'encoder comme information.
- **Condition déclenchante :** L0 moyen ou bas + domaine où les compétences sont en construction (≠ automatisées) + entity thinking activé + engagement sur une tâche nouvelle ou complexe
- **Lien entity thinking :** nécessaire. Sans entity thinking, le gap reste informatif et processuel. Avec entity thinking, le gap devient un verdict : *"je devrais être capable de faire ça parfaitement"* → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Output typique :** visualisation du produit fini parfait dès l'engagement, avant même les premières compétences construites · chaque imprévu frappe le gap plutôt que d'être traité isolément · Frustration cumulée → Honte · parfois abandon ou sur-investissement défensif
- **L3 générée :** [[L3 - Émotions/Frustration]] · [[Honte]]
- **Statut :** observation personnelle — juin 2026 (balade Lucky, étude, création environnement Siem Reap)

---

**Expression 2 — Contrôle identitaire par la maîtrise technique (L1 Contrôle menacé)**

- **L1 actif :** [[L1 - Structures profondes/05 — Besoin de contrôle|Besoin de Contrôle]] en mode défensif
  *Ce qui est menacé :* le levier sur les outcomes — en contexte de haute variance (poker) ou d'imprévus (quotidien), le contrôle sur les résultats est absent. La maîtrise technique devient le seul levier disponible.
- **Mécanisme L1→L2 :** le Besoin de Contrôle menacé par l'absence de levier sur les résultats cherche un substitut — *"si ma technique est parfaite, la variance seule est responsable"*. L'idéal technique devient une stratégie de contrôle de l'identité : atteindre le parfait protège contre la responsabilité des outcomes non contrôlés.
- **Condition déclenchante :** contexte à haute variance + L0 moyen + Besoin de Contrôle activé (bad run, imprévus accumulés)
- **Lien entity thinking :** renforce — si la compétence est fixe, la perfectionner à 100% est la seule protection contre un verdict négatif sur l'entité
- **Output typique :** étude compulsive post-erreur · standard technique irréaliste · Culpabilité sur les erreurs dans les zones supposément maîtrisées
- **L3 générée :** [[L3 - Émotions/Culpabilité]] · [[Honte]]
- **Statut :** documenté — Alexis 04-20-2026

---

**Expression 3 — Idéal comme contrainte de l'expression autonome (L1 Autonomie menacé)**

- **L1 actif :** [[L1 - Structures profondes/02 — Besoin d'Autonomie|Besoin d'Autonomie]] en mode défensif
  *Ce qui est menacé :* agir depuis soi — l'idéal parfait devient une norme externe intégrée qui remplace l'expression authentique
- **Mécanisme L1→L2 :** la vision idéale est internalisée comme standard normatif (≠ aspirationnel). Agir depuis soi devient impossible : chaque choix est évalué par rapport à l'idéal plutôt que depuis ses propres valeurs. La créativité spontanée est bloquée par la question *"est-ce que ça correspond à l'idéal ?"*
- **Condition déclenchante :** contexte de création ou d'expression + validation externe recherchée + L0 moyen
- **Lien entity thinking :** l'idéal parfait est traité comme une entité fixe qui juge l'expression — pas comme une direction évolutive
- **Output typique :** blocage créatif · validation-seeking avant d'agir · Anxiété d'évaluation · plays non exécutés par peur de ne pas être "à la hauteur"
- **L3 générée :** [[L3 - Émotions/Anxiété d'évaluation]]
- **Statut :** inféré depuis L1 Autonomie + [[L2 - Schémas Cognitifs/01 — Mentalisation -- Dissociation|Dissociation]] (adjacent non encore formellement documenté)

---

### B. Pôle générateur — Ambition

*Expression sous appui L1 générateur et/ou mastery thinking*

---

**Expression 1 — Boussole aspirationnelle (L1 Compétence satisfait)**

- **Condition :** [[L1 - Structures profondes/01 — Besoin de Compétence|Besoin de Compétence]] en mode générateur + L0 satisfait + mastery thinking actif
- **Mécanisme :** l'idéal est traité comme une *direction* et non comme un *standard de valeur*. Le gap vision/réalité génère de la curiosité et informe le prochain geste plutôt que de menacer l'identité. Chaque imperfection est encodée comme donnée de processus.
- **Lien mastery thinking :** nécessaire — c'est le mastery thinking qui maintient l'idéal comme boussole. Sans lui, tout gap risque de basculer en verdict. → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Output typique :** plaisir du défi · curiosité face aux gaps · plaisir de l'apprentissage indépendant du résultat · progression visible
- **L3 générée :** [[L3 - Émotions/Curiosité]] · [[L3 - Émotions/Satisfaction]] · [[L3 - Émotions/Plénitude]]
- **Statut :** inféré depuis les dépolarisations accomplies (voir [[L1 - Structures profondes/01 — Besoin de Compétence]]) · partiellement observé

---

**Expression 2 — Engagement depuis ses valeurs (L1 Autonomie satisfait)**

- **Condition :** [[L1 - Structures profondes/02 — Besoin d'Autonomie|Besoin d'Autonomie]] en mode générateur + L0 satisfait
- **Mécanisme :** l'idéal est défini depuis ses propres valeurs plutôt qu'un standard externe intégré. La créativité peut s'exprimer librement car l'évaluation se fait depuis soi, pas depuis une norme.
- **Lien mastery thinking :** l'idéal est évolutif et co-construit avec l'expérience — pas fixé a priori
- **Output typique :** expression créative spontanée · plays exécutés depuis ses reads sans validation-seeking · Plénitude IRL
- **L3 générée :** [[L3 - Émotions/Plénitude IRL]] · [[L3 - Émotions/Satisfaction]]
- **Statut :** adjacent — observé ponctuellement · à documenter

---

## III. Instances personnelles documentées

| Date | Contexte | Expression activée | Émotion produite | Source |
|---|---|---|---|---|
| Juin 2026 | Balade avec Lucky · étude · création environnement Siem Reap | Expression 1 — Gap compétences/vision | Frustration → Honte | Observation personnelle |
| 04-20-2026 | Session poker haute énergie | Expression 2 — Contrôle identitaire par maîtrise | Honte · Colère | Documenté — Alexis |
| En cours | Travail sur le vault Inner Mapping | Expression 1 + Expression 3 | Frustration · Anxiété d'évaluation | Observation — non encore datée |

---

## IV. Connexions dans l'écosystème L0→L4

| Niveau | Sens | Connexion |
|---|---|---|
| **Opération neutre → L0** | intrinsèque | Coût de base faible — générer une représentation cible est une opération courante du cerveau prédictif. Coût nul en mode boussole. |
| **L0 → L2** | descendant | Budget plein → gap informatif (pôle générateur accessible). Budget moyen → entity thinking plus probable. Budget épuisé → entity thinking quasi-systématique → Perfectionnisme presque garanti. → [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]] |
| **L2(défensif) → L0** | ascendant ⚠️ | Le Perfectionnisme consomme du budget L0 : chaque évaluation du gap génère une erreur de prédiction non résolue → activation prolongée → coût allostatique accumulé. Effet boule de neige sur L0. → [[L0 — Physiologie & Budget Corporel/02 — Allostase]] |
| **L2(générateur) → L0** | ascendant ✅ | L'Ambition en mode boussole est neutre sur L0 (coût de l'opération sans charge émotionnelle) · sous conditions favorables, la progression perçue restaure légèrement le budget via satisfaction. |
| **L1 → L2** | descendant | Besoin de Compétence menacé → Expression 1 · Besoin de Contrôle menacé → Expression 2 · Besoin d'Autonomie menacé → Expression 3 |
| **L2(défensif) → L1** | ascendant ⚠️ | Chaque activation du Perfectionnisme renforce la prédiction entity : *"je devrais être capable de faire ça parfaitement"* → renforce le mode défensif du Besoin de Compétence · affaiblit la confiance dans le mode générateur |
| **L2(générateur) → L1** | ascendant ✅ | Chaque activation de l'Ambition en mode boussole entraîne la prédiction mastery → renforce le mode générateur du Besoin de Compétence · consolide l'autonomie d'expression |
| **L2 associés** | latéral | [[L2 - Schémas Cognitifs/05 — Évaluation du soi -- Pensée binaire\|Pensée binaire]] (véhicule — rend le gap infranchissable) · [[L2 - Schémas Cognitifs/09 — Encodage de l'erreur -- Auto-flagellation\|Auto-flagellation]] (punit le gap) · [[L2 - Schémas Cognitifs/06 — Évaluation de l'enjeu -- Piédestal\|Piédestal]] (cousin — enjeu de la situation vs standard d'output) |
| **L3 produites** | descendant | Pôle défensif → [[L3 - Émotions/Frustration]] · [[Honte]] · [[L3 - Émotions/Culpabilité]] · [[L3 - Émotions/Anxiété d'évaluation]] · Pôle générateur → [[L3 - Émotions/Curiosité]] · [[L3 - Émotions/Satisfaction]] · [[L3 - Émotions/Plénitude]] |
| **L4 comportements** | descendant | Défensif : abandon précoce · sur-investissement compulsif · étude post-erreur · paralysie créative · Générateur : engagement soutenu · itération rapide · documentation des gaps |

**Distinction des schémas proches :**

| Schéma | Objet | Mécanisme |
|---|---|---|
| **Perfectionnisme** | Standard d'output attendu | *"Je devrais être capable de produire ça parfaitement"* |
| **Piédestal** | Enjeu de la situation | *"Cette session / cet événement est unique — je ne peux pas le rater"* |
| **Pensée binaire** | Verdict identitaire | *"Parfait ou nul — pas de graduations"* — est le véhicule du Perfectionnisme |
| **Auto-flagellation** | Encodage de l'erreur | Punit le gap créé par le Perfectionnisme |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Définir explicitement la "version suffisamment bonne" avant de commencer — pas la version parfaite · ne pas s'engager sur une tâche depuis un état Perfectionnisme détecté au warmup sans ajustement préalable |
| 2 · Modification | partiel | Réduire la portée de la tâche si Perfectionnisme détecté en cours — passer du produit final à la prochaine étape concrète |
| **3 · Attentionnel** | oui | **Ramener à la prochaine étape concrète — pas au produit fini** · *"Quelle est ma prochaine action ici — pas mon produit final ?"* |
| **4 · Reappraisal** | oui | **Recadrer le gap comme information de processus** · *"Cette imperfection est une étape — pas un verdict sur ce que je suis"* |
| 5 · Modulation | oui | Nommer *"je suis en mode Perfectionnisme"* — la métacognition interrompt partiellement le cycle |

**Stratégie prioritaire :** Reappraisal (4) — recadrer l'imperfection comme étape. C'est l'intervention la plus stable car elle traite directement le couplage idéal/identité.

**Note L0 :** sous budget épuisé, le Reappraisal (4) devient moins accessible (PFC réduit). Préférer Modulation (5) — nommer le pattern — puis Sélection (1) — réduire la portée si possible.

---

## VI. Signaux de détection

> [!warning] Le pattern Perfectionnisme est actif quand...
> - Visualisation spontanée du **produit fini parfait** dès l'engagement — avant même les premières compétences construites
> - **Contraction physique** au premier imprévu ou à la première imperfection (tension, soupir, décrochage)
> - Les **imprévus s'accumulent** plutôt que d'être traités isolément — le bol se remplit plus vite qu'en mode normal
> - **Comparaison systématique** entre ce que l'on produit et ce que l'on devrait produire
> - Difficulté à **continuer sans valider** l'étape précédente
>
> **Question de détection :** *"Est-ce que je visualise mon produit fini parfait ou ma prochaine étape concrète ?"*

---

## VII. Protocoles d'interruption

> [!tip] En contexte · Interrupt
> 1. Nommer : *"Je suis en mode Perfectionnisme"*
> 2. Ramener à la prochaine étape : *"Quelle est mon action concrète maintenant — pas mon produit final ?"*

> [!tip] Avant l'engagement
> Définir verbalement ou par écrit la "version suffisamment bonne" avant de commencer. Fixer une intention de processus, pas de résultat : *"Je veux apprendre X dans cette session — pas produire le parfait."*

> [!tip] Post-session · Review
> Observer : le gap vision/réalité s'est-il activé ? Quel L1 était menacé ? Documenter dans Section III.
> Reformuler chaque imperfection notée en information de processus : *"Ça m'apprend que..."*

> [!tip] Si L0 épuisé
> Modulation uniquement — nommer le pattern sans chercher à le recadrer immédiatement. Réduire la portée de la tâche. Protocoles L0 prioritaires.

---

## VIII. Suivi en session

```dataviewjs
let p = dv.current();
let targetPattern = p["pôle_défensif"] || p.file.name;
let sessions = dv.pages('"Journal/Session/Feedback/2026"')
    .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
if (sessions.length > 0) {
    dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
} else {
    dv.paragraph(`*Aucune session — tagger avec \`[pattern:: ${targetPattern}]\`*`);
}
```

> [!note]- 📅 Jours concernés — O&R
> ```dataviewjs
> let p = dv.current();
> let targetPattern;
> if (p["pôle_défensif"]) {
>     targetPattern = p["pôle_défensif"];
> } else {
>     let nameParts = p.file.name.split(" -- ");
>     targetPattern = nameParts.length > 1 ? nameParts[nameParts.length - 1] : p.file.name;
> }
> let orPage = dv.page("📝 observation et ressentis");
> if (!orPage) {
>     dv.paragraph("*⚠️ Fichier O&R introuvable.*");
> } else {
>     let content = await dv.io.load(orPage.file.path);
>     let sections = content.split(/\n##\s+/);
>     let matches = [];
>     let dateRe = /^(\d{2}-\d{2}-\d{4})/;
>     let escaped = targetPattern.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
>     let tagRe = new RegExp("\\[pattern::[^\\]]*" + escaped + "[^\\]]*\\]", "i");
>     for (let section of sections) {
>         let firstLine = section.split('\n')[0].trim();
>         let dateMatch = firstLine.match(dateRe);
>         if (dateMatch && tagRe.test(section)) {
>             matches.push(dateMatch[1]);
>         }
>     }
>     if (matches.length === 0) {
>         dv.paragraph("*Aucun O&R lié — tagger avec `[pattern:: " + targetPattern + "]` dans l'O&R.*");
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

## Sources

[^1]: Dweck, C.S. (1986). *Motivational processes affecting learning.* American Psychologist, 41(10), 1040–1048.
[^2]: Dweck, C.S. (1999). *Self-Theories: Their Role in Motivation, Personality, and Development.* Psychology Press.
[^3]: Barrett, L.F. (2017). *How Emotions Are Made.* Houghton Mifflin.
[^4]: Gross, J.J. (1998). *Antecedent- and response-focused emotion regulation.* Journal of Personality and Social Psychology, 74(1), 224–237.

---

## Notes liées

- [[00 — Index Schémas]] · [[L2 - Schémas Cognitifs/00 — Index Schémas]]
- [[L1 - Structures profondes/01 — Besoin de Compétence]] · [[L1 - Structures profondes/05 — Besoin de contrôle]] · [[L1 - Structures profondes/02 — Besoin d'Autonomie]]
- [[L2 - Schémas Cognitifs/05 — Évaluation du soi -- Pensée binaire]] · [[L2 - Schémas Cognitifs/09 — Encodage de l'erreur -- Auto-flagellation]] · [[L2 - Schémas Cognitifs/06 — Évaluation de l'enjeu -- Piédestal]]
- [[L3 - Émotions/Frustration]] · [[Honte]] · [[L3 - Émotions/Culpabilité]]
- [[Fondements théoriques/09 — Mastery orientation · Entity theory]] · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

---

## CHECKLIST DE COHÉRENCE

- [x] Chaque expression défensive nomme explicitement le L1 actif et ce qui est menacé
- [x] Le mécanisme L1→L2 est formulé pour chaque expression
- [x] Les instances personnelles sont présentes et géolocalisées
- [x] Les expressions adjacentes prédites par la théorie sont documentées
- [x] Chaque expression est distinguée par son mécanisme précis
- [x] Le lien entity thinking est explicite dans chaque expression défensive
- [x] Le lien mastery thinking est explicite dans les expressions génératives
- [x] Les stratégies Gross sont identifiées avec stratégie prioritaire nommée
- [x] La modulation par L0 est documentée (activation normale ET condition dégradée)
- [x] Le coût de base de l'opération neutre (→L0 intrinsèque) est documenté
- [x] Le coût métabolique du pôle défensif (L2défensif→L0) est documenté
- [x] L'effet net du pôle générateur sur L0 est documenté
- [x] Le renforcement de L1 défensif par répétition est documenté
- [x] Le renforcement de L1 générateur par répétition est documenté
- [x] La distinction avec les L2 proches est clarifiée
- [x] Les connexions L0/L1/L3/L4 sont toutes renseignées dans les deux sens
- [x] Pas de contradiction interne avec les fondements
- [x] Chaque référence théorique citée est liée vers sa fiche Fondements
