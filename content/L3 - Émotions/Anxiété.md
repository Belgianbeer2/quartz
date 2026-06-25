---
type: fiche_emotion_index
tags: [L3, émotion, anxiété, index, inner-mapping]
L3_nom: "Anxiété"
L3_valence: "négative"
L3_arousal: "variable selon la forme"
BIS_BAS: "BIS↑ (variable) BAS neutre-bas"
date: 2026-06-21
statut: index
---
```dataviewjs
const log=dv.page("log — Drill 02 — Rétrospective accumulation");const nomFiche=dv.current().file.name;
if(!log||!log.entries){dv.paragraph("*Aucune donnée Drill 02.*");}else{const r=log.entries.filter(e=>e.emotion===nomFiche);if(r.length===0){dv.paragraph("*Aucune activation Drill 02.*");}else{dv.paragraph(`*${r.length} activation(s)*`);}}
```

# 🧠 Anxiété — Index

---

## I. L'émotion — Définition fonctionnelle

> [!abstract] ✅ Fondement — Barrett (2017) · [[Fondements théoriques/03 — Cerveau prédictif]]
> L'anxiété est orientée vers l'**avenir** : elle anticipe une menace réelle ou imaginée. Contrairement à la [[Peur]] (réponse à un danger présent), l'anxiété est une réponse à une **possibilité** — quelque chose qui pourrait arriver, qui pourrait être vrai, que quelqu'un pourrait penser.
>
> Elle se distingue du stress (réponse à une surcharge) et de l'inquiétude (pensée répétitive sur un problème spécifique) par son objet : l'évaluation anticipée, l'image projetée, le contrôle sur quelque chose d'incertain.

**Signature BIS/BAS générique :** → [[Fondements théoriques/05 — BIS & BAS]]
- **BIS :** ↑ variable — menace anticipée → BIS actif en prévention
- **BAS :** neutre à bas — l'anticipation inhibe le drive d'approche

---

## II. Formes documentées dans ce vault

| Forme | Objet | BIS/BAS | Fiche |
|---|---|---|---|
| **Anxiété d'évaluation** | Être jugé par un pair compétent | BIS↑ BAS neutre | [[Anxiété d'évaluation]] |

*D'autres formes seront ajoutées à mesure qu'elles émergent de l'expérience — pas avant.*

---

## III. Vue d'ensemble — toutes les anxiétés documentées

> [!note]- Sessions liées à une forme d'anxiété
> ```dataviewjs
> let sessions=dv.pages('"Journal/Session/Feedback/2026"').where(page=>{const emotions=page.file.lists.emotion;return dv.array(emotions).some(e=>typeof e==='string'&&e.toLowerCase().includes('anxi'));});
> if(sessions.length>0){dv.list(sessions.sort(s=>s.file.name,'desc').file.link);}else{dv.paragraph("*Aucune session identifiée.*");}
> ```

---

## Notes liées
- [[Anxiété d'évaluation]] — forme principale documentée
- [[Peur]] — distinction anxiété (menace future) vs peur (menace présente)
- [[01 — Mentalisation -- Dissociation]] — véhicule cognitif de l'anxiété d'évaluation
- [[00 — Protocole In-Game]]
