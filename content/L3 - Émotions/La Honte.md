---
type: fiche_emotion
tags: [L3, émotion, honte, inner-mapping]
L3_nom: "La Honte"
L3_valence: "négative"
L3_arousal: "haute"
BIS_BAS: "BIS↑↑ BAS↓"
L1_déclencheurs: ["Besoin de Compétence défensif (Intransigeance)", "Prémisses éthiques (Trahison de soi)"]
L2_déclencheurs: ["[[05 — Évaluation du soi -- Pensée binaire]]", "[[09 — Encodage de l'erreur -- Auto-flagellation]]", "[[03 — Reconstruction mémorielle -- Sélectivité mémorielle]]"]
L4_comportements: ["Retrait · Silence · Faible énergie · Évitement de la table · Off complet"]
date: 2026-06-21
statut: documenté
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const relevant=log.entries.filter(e=>e.emotion===nomFiche);if(relevant.length===0){dv.paragraph("*Aucune activation Drill 02 liée.*");}else{const fc=(f)=>{if(!f)return"#555";if(String(f).includes("Très"))return"#e74c3c";if(String(f).includes("Réduite"))return"#FF9500";return"#2ecc71";};let html="";relevant.sort((a,b)=>moment(b.d,"MM-DD-YYYY").valueOf()-moment(a.d,"MM-DD-YYYY").valueOf()).forEach(e=>{const f=String(e.fenetre||"").trim();const signaux=e.signal?String(e.signal).split("·").map(s=>s.trim()).filter(s=>s):[];html+=`<div style="border-left:3px solid ${fc(f)};padding:8px 12px;margin-bottom:8px;background:rgba(255,255,255,0.02);border-radius:0 4px 4px 0;"><div style="display:flex;justify-content:space-between;margin-bottom:6px;"><span style="color:#6edff6;font-size:12px;font-weight:bold;">${e.d||"—"}</span><span style="color:${fc(f)};font-size:11px;">Fenêtre ${f||"—"}</span></div><div style="font-size:11px;color:#888;margin-bottom:3px;">Frictions : <span style="color:#ccc;">${e.frictions||"—"}</span></div><div style="font-size:11px;color:#888;margin-bottom:3px;">Signaux : <span style="color:#BB86FC;">${signaux.join(" · ")||"—"}</span></div><div style="font-size:11px;color:#888;margin-bottom:3px;">Action : <span style="color:#ccc;">${e.action||"—"}</span></div><div style="font-size:11px;color:#888;">Résultat : <span style="color:#aaa;">${e.resultat||"—"}</span></div></div>`;});dv.paragraph(`*${relevant.length} activation(s) Drill 02*`);dv.container.createEl("div").innerHTML=html;}}
```

# 😔 La Honte

> [!note]- 📜 Sessions liées
> ```dataviewjs
> let p=dv.current();let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>dv.array(page.file.lists.emotion).includes(p.file.name));
> if(sessions.length>0)dv.list(sessions.sort(s=>s.file.name,'desc').file.link);else dv.paragraph("*Aucune session — tagger avec `[emotion:: La Honte]`*");
> ```

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · Tangney & Dearing (2002) · [[Fondements théoriques/03 — Cerveau prédictif]]
> La Honte est construite quand le cerveau applique le concept "je SUIS défaillant" à un affect négatif à haute arousal. Contrairement à la Culpabilité ("j'AI fait quelque chose de mal"), la Honte porte sur le Soi global — elle n'est pas liée à un comportement réparable mais à une identité perçue comme déficiente. C'est cette différence qui la rend si paralysante. [documenté — Tangney & Dearing 2002]

> [!abstract] ✅ La Trahison de Soi — variante spécifique · Kernis & Goldman (2006) · [[01 — Angles morts & évolutions]]
> La Trahison de soi est une forme de Honte liée à la **violation d'un engagement personnel** : le warmup est un rituel d'engagement. Le `[x] OUI` à *"Suis-je prêt à jouer ?"* est une promesse. Chaque fois que le comportement in-game s'éloigne de l'intention du warmup, la trahison de soi peut s'activer — indépendamment du résultat financier. [documenté — Alexis · session 28-05-2026]

**Valence :** négative
**Arousal :** haute — l'activation est intense même si elle produit du retrait (paradoxe)
**Action tendency :** se cacher · se retirer · évitement · paralysie

**Signature BIS/BAS :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑↑ très élevé — menace identitaire maximale, le Soi lui-même est perçu comme déficient
- **BAS :** ↓ bas — le retrait éteint le drive d'approche
- **Combinaison :** BIS fort + BAS retiré = paralysie · retrait · off complet

**Distinction fondamentale — Honte vs Culpabilité :**

| | **La Honte** | **[[Culpabilité]]** |
|---|---|---|
| **Objet** | Le Soi global ("je SUIS") | Un comportement ("j'AI fait") |
| **Message interne** | *"Je suis défaillant"* | *"J'ai mal fait X"* |
| **Action tendency** | Se cacher · retrait | Réparer · corriger |
| **Résolution possible** | Difficile — l'identité ne se répare pas facilement | Oui — l'action ferme la boucle |
| **Signal post-session** | Retrait · faible énergie · évitement | Envie de corriger |

**Distinction Honte vs Peur :** → [[Peur]]
- Peur : objet financier ("je vais perdre"), action tendency = retrait
- Honte : objet identitaire ("je SUIS défaillant"), action tendency = paralysie + évitement

---

## II. Signaux de détection — Intéroception · [[L0 — Physiologie & Budget Corporel/01 — Intéroception]]

> [!warning] Signaux corporels
> - **Zone de tension :** chaleur dans le visage et le cou · contraction thoracique · corps qui se recroqueville
> - **Rythme cardiaque :** accéléré puis qui se calme dans le retrait
> - **Respiration :** courte · superficielle · soupirs fréquents
> - **Posture spontanée :** tête baissée · épaules vers l'avant · regard qui fuit · corps replié
> - **Sensations spécifiques :** "envie de disparaître" · pesanteur · chaleur · nœud dans la gorge

> [!warning] Signaux cognitifs précoces
> - *"Je ne suis pas cette personne"* / *"J'ai encore raté"* / *"À quoi ça sert"*
> - Le remembering self reconstruit toute la session comme un échec total
> - Incapacité à nommer les moments positifs de la session

> [!warning] Signaux comportementaux précoces
> - Absence de feedback le soir de la session
> - Off complet le lendemain · "faible énergie · humeur basse"
> - Évitement de toute discussion sur la session

---

## III. Cartographie théorique

#### L1 — Besoins déclencheurs

| Mode L1 | Besoin | Mécanisme |
|---|---|---|
| **Défensif** | Besoin de Compétence (Intransigeance) | L'écart idéal-réel est interprété comme preuve de l'entité déficiente → "je ne suis pas ce joueur" |
| **Défensif** | Prémisses éthiques (Trahison de soi) | La violation de l'engagement du warmup → "je ne suis même pas fiable envers moi-même" |

> [!abstract] Le paradoxe libérateur — session 28-05-2026 [documenté]
> Reconnaître l'écart, c'est le Stratège qui regarde. Si tu vois que tu n'étais pas le Stratège — c'est lui qui a vu. Tu n'aurais pas pu nommer l'écart si l'identité n'était pas déjà là pour le mesurer. → L'écart est une **information** sur la construction identitaire, pas un verdict.

**Lien entity/mastery :** → [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- **Entity thinking** : la Honte est structurellement liée à l'entity thinking sur le Soi. "La session révèle ce que je suis vraiment."
- **Mastery thinking** : déplace de l'identité vers le processus. "La session révèle où j'en suis dans ma construction."
- **Correction structurelle** : reformuler les intentions du warmup sur l'**être** (pas le faire idéal) supprime le principal carburant de la Honte.

#### L2 — Schémas déclencheurs

| Schéma L2 | Mécanisme |
|---|---|
| Pensée binaire (L2/05) | Produit le verdict identitaire "je suis mauvais joueur" depuis un comportement déviant |
| Auto-flagellation (L2/09) | Exécute le verdict par punition — renforce la Honte en boucle |
| Sélectivité mémorielle (L2/03) | Reconstruit la session pour confirmer le verdict — efface les moments du Stratège |

#### L0 — Influence

Budget épuisé → Honte plus probable et plus intense. Le lendemain d'une session difficile, le remembering self sous budget bas produit une reconstruction encore plus biaisée. La Honte renforce l'épuisement → cercle vicieux.

---

## IV. Connexions dans l'écosystème — Bidirectionnel

| Niveau | Sens | Connexion |
|---|---|---|
| **L0 → L3** | descendant | Budget épuisé → remembering self plus biaisé → Honte plus intense · lendemain aggravé |
| **L3 → L0** | ascendant ⚠️ | BIS très actif + retrait → dépense métabolique élevée · off complet dégrade encore L0 |
| **L1 → L3** | descendant | Compétence défensif (Intransigeance) + Prémisses éthiques (Trahison de soi) |
| **L3 → L1** | ascendant ⚠️ | Répétée sans régulation → renforce "je ne suis pas fiable" → ancre la Compétence défensive |
| **L2 → L3** | descendant | Pensée binaire + Auto-flagellation + Sélectivité mémorielle la produisent et l'amplifient |
| **L3 → L2** | ascendant ⚠️ | La Honte active la Rumination (rejouer la session) et la Sélectivité mémorielle (confirmer le verdict) |
| **L3 → L4** | descendant | Retrait · off complet · évitement · silence · faible énergie |
| **L4 → L3** | ascendant ⚠️ | Le retrait amplifie la Honte (pas de feedback = pas de correction de la reconstruction biaisée) |

---

## V. Régulation — Stratégies Gross · [[Fondements théoriques/06 — Contrôle perçu & régulation émotionnelle]]

| Stratégie | Applicable | Application concrète |
|---|---|---|
| 1 · Sélection | oui | Reformuler les intentions du warmup sur l'être (pas le faire idéal) — retire le carburant |
| 2 · Modification | oui | Si retrait le lendemain : petite action concrète pour remonter sur le cheval |
| 3 · Attentionnel | oui | *"Qui est-ce que je veux être dans les 5 prochaines minutes ?"* — pas "comment je rattrape ?" |
| 4 · Reappraisal | oui | *"L'écart est une information sur ma construction — pas un verdict sur mon identité"* · *"Voir l'écart = le Stratège qui regarde"* |
| 5 · Modulation | non | — |

**Stratégie prioritaire :** Reappraisal (4) — déplacer de l'identité vers le processus. La Honte se régule par le recadrage identitaire, pas par l'action directe.
**Note L0 :** sous budget épuisé, Modification (2) d'abord — petite action concrète. Le Reappraisal est moins accessible.

**Protocoles associés :**
- [[Modèles/(modèle) - Warmup]] — reformuler l'intention sur l'être (retirer le carburant structurel)
- [[00 — Protocole In-Game]] — Bloc 2 (signal Honte/Trahison de soi)

---

## VI. Patterns documentés

> [!warning] 1. Déclencheurs
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.declencheur).forEach(i=>{let v=Array.isArray(i.declencheur)?i.declencheur:[i.declencheur];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucun déclencheur documenté.*");
> ```

> [!warning] 2. Pensées automatiques
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.pensee).forEach(i=>{let v=Array.isArray(i.pensee)?i.pensee:[i.pensee];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)sorted.forEach(e=>dv.el("blockquote",`« <i>${e[0]}</i> » <strong>(x${e[1]})</strong>`));
> else dv.paragraph("*Aucune pensée documentée.*");
> ```

> [!warning] 3. Réactions
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);let counts={};
> dv.array(desc).where(d=>d.reaction).forEach(i=>{let v=Array.isArray(i.reaction)?i.reaction:[i.reaction];v.forEach(x=>{counts[x]=(counts[x]||0)+1;});});
> let sorted=Object.entries(counts).sort((a,b)=>b[1]-a[1]);
> if(sorted.length>0)dv.list(sorted.map(e=>`${e[0]} **(x${e[1]})**`));else dv.paragraph("*Aucune réaction documentée.*");
> ```

> [!warning] 4. Prix à payer
> ```dataviewjs
> let p=dv.current();let items=dv.pages('"Journal/Session/Feedback/2026"').file.lists.where(l=>l.emotion==p.file.name);
> let gD=(i)=>{let r=[];if(i.children){i.children.forEach(c=>{r.push(c);r.push(...gD(c));});}return r;};
> let desc=items.flatMap(gD);
> let ingame=dv.array(desc).where(c=>c["Prix à payer"]&&!c.completed);
> let local=p.file.lists.where(l=>l["Prix à payer"]&&!l.completed);
> if(ingame.length>0||local.length>0)dv.taskList([...ingame,...local],false);else dv.paragraph("*Aucun prix actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer
> > - [ ] [Prix à payer:: J'accepte que l'écart entre mon intention de warmup et mon comportement in-game est une information sur ma construction — pas un verdict sur mon identité]
> > - [ ] [Prix à payer:: J'accepte que le lendemain d'une session difficile, le retrait et la faible énergie sont des signaux de Honte à nommer — pas des vérités définitives sur mes capacités]

---

## VII. Analyse à froid

> [!abstract]
> **L'intention du warmup crée-t-elle un standard binaire ?**
> Si l'intention est orientée sur le **faire idéal** → standard binaire : tenu / pas tenu → carburant de la Honte. Si l'intention est orientée sur l'**être** → pas de standard binaire → un instant de reconvocation = avancement.
>
> **Ce qu'il faut distinguer :**
> L'écart idéal-réel est une **information** (où j'en suis dans ma construction). La Honte est une **réaction émotionnelle** à cet écart. La Honte déforme l'information et bloque l'action. L'écart est utile. La Honte qui l'enveloppe est un parasite.
>
> **Session du 28-05-2026 [documenté] :** la perte financière (-$1432) n'a pas causé le retrait du 29/05. La Honte d'avoir dévié de l'intention du warmup l'a causé. Le remembering self a effacé les moments du Stratège (relire les documents, rester focalisé, lâcher prise) pour reconstruire un "échec total".

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
> > - [ ] [Plan d'action:: In-game — si Honte fire : nommer → "qui est-ce que je veux être dans les 5 prochaines minutes ?" (pas "comment je rattrape ?")]
> > - [ ] [Plan d'action:: Warmup — reformuler l'intention sur l'être, pas le faire idéal]
> > - [ ] [Plan d'action:: Lendemain difficile — nommer le retrait comme signal Honte + petite action concrète]

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
- [[Culpabilité]] — distinction fondamentale identité vs comportement
- [[05 — Évaluation du soi -- Pensée binaire]] · [[09 — Encodage de l'erreur -- Auto-flagellation]]
- [[03 — Reconstruction mémorielle -- Sélectivité mémorielle]]
- [[Fondements théoriques/09 — Mastery orientation · Entity theory]]
- [[L1 - Structures profondes/01 — Besoin de Compétence]]
- [[00 — Protocole In-Game]] · [[Modèles/(modèle) - Warmup]]
- *Fiche créée le 30-05-2026 — session 28-05-2026 (-$1432)*
