---
type: fiche_emotion_index
tags:
  - anxiété
  - émotions
  - index
---

# 🧠 Anxiété — Index

> [!abstract] Qu'est-ce que l'anxiété
>
> L'anxiété est une émotion orientée vers l'**avenir** : elle anticipe une menace, réelle ou imaginée. Contrairement à la peur (réponse à un danger présent), l'anxiété est une réponse à une **possibilité** — quelque chose qui pourrait arriver, qui pourrait être vrai, que quelqu'un pourrait penser.
>
> Elle se distingue du stress (réponse à une surcharge) et de l'inquiétude (pensée répétitive sur un problème spécifique) par son objet : l'évaluation anticipée, l'image projetée, le contrôle sur quelque chose d'incertain.

> [!abstract] Formes documentées dans ce vault
>
> | Forme | Objet | Fiche |
> |---|---|---|
> | **Anxiété d'évaluation** | Être jugé/évalué par un observateur compétent | [[Anxiété d'évaluation]] |
>
> *D'autres formes seront ajoutées à mesure qu'elles émergent de l'expérience — pas avant.*

---

## 📊 Vue d'ensemble — toutes les anxiétés documentées

> [!note]- Sessions liées à une forme d'anxiété (auto)
> ```dataviewjs
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const emotions = page.file.lists.emotion;
>         return dv.array(emotions).some(e => 
>             typeof e === 'string' && e.toLowerCase().includes('anxi')
>         );
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```

---

## 🔗 Notes liées

- [[Dissociation]] — pattern cognitif qui véhicule souvent l'anxiété d'évaluation
- [[Être et Faire — Réconciliation Moukheiber × Alexis]]
- [[00 — Protocole In-Game]]
