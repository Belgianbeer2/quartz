---
type: pattern_cognitif
tags:
  - pattern
  - projection-temporelle
  - suranticipation
  - cognition
L2_neutre: "Projection temporelle"
pôle_mal_être: "Suranticipation"
pôle_bien_être: "Projection ancrée"
émotion_véhiculée: "[[Peur]] · [[Anxiété d'évaluation]]"
date: 2026-06-06
statut: documenté
---

# ⚙️ Projection temporelle -- Suranticipation

> *"Je gagne trop pour le moment → anticipation anxieuse du retournement."* [documenté — Alexis 03-02-2026]

---

## I. L'opération neutre — Projection temporelle

**Définition :** Mécanisme par lequel le cerveau projette un état présent vers le futur pour anticiper ce qui va arriver. Cette projection est nécessaire — le cerveau prédit en permanence. Elle devient dysfonctionnelle quand elle extrapole un état temporaire (bon run, bonne forme) comme s'il était permanent, puis anticipe anxieusement son inévitable fin.

**[documenté — Barrett 2017]** Le cerveau prédit toujours à partir du présent. En bon run, la prédiction du futur inclut mécaniquement le retour à la baseline — c'est du traitement bayésien normal. La suranticipation, c'est quand ce traitement devient anxiogène plutôt que neutre.

---

## II. Pôle mal-être — Suranticipation

**Mécanisme biaisé :** Prendre un état présent positif (bon run, bonne session, bonne forme) et l'extrapoler anxieusement : *"ça va forcément casser"* → anticipation du retournement avant qu'il ne se produise → budget corporel dépensé en anticipation d'une menace non encore réelle.

**[documenté — Alexis 03-02-2026]** *"Je gagne trop pour le moment"* → anticipation du retournement.

**Conditions d'activation :**
- Bon run prolongé → peur de le voir s'arrêter
- Haute énergie perçue (lié au Piédestal)
- Perfectionnisme actif : *"ça va forcément casser parce que je ne suis pas encore vraiment ce joueur"*

**Manifestation documentée :**
Bon run → *"je gagne trop"* → *"ça va casser"* → anticipation anxieuse → [[Peur]] latente → réduction du volume ou jeu contracté.

---

## III. Pôle bien-être — Projection ancrée

**Mécanisme génératif :** Projection temporelle qui reconnaît la variance sans l'anticiper anxieusement. L'état présent est apprécié pour ce qu'il est. Le futur est incertain — et c'est acceptable.

**Lié à :** La dépolarisation sur les résultats ([[Mini dépos frustré de run bad en live]]) construit ce pôle — être présent dans les bons moments sans en faire une source d'anxiété.

> [!note] Documentation à compléter
> Manifestations en session à documenter.

---

## IV. Signaux de détection

> [!warning] Le pattern Suranticipation est actif quand...
> - Un état positif présent génère une pensée sur son inévitable fin
> - *"Je gagne trop"* / *"ça va casser"* / *"je ne mérite pas ce run"*
> - La haute énergie ou le bon run génère de l'anxiété plutôt que de la satisfaction
>
> **Question de détection :** *"Est-ce que je suis dans cette session, ou est-ce que je suis dans la prochaine ?"*

---

## V. Protocole d'interruption

> [!tip] In-game
> *"Je joue ce coup — pas le run que j'imagine être en train de perdre."*
> Revenir au moment présent : la décision devant soi.

> [!tip] Hors session
> Nommer la suranticipation explicitement : *"Je suis en suranticipation."*
> La variance est symétrique — elle peut continuer dans les deux sens.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[pattern:: Suranticipation]`*");
> ```

---

## Notes liées
- [[Index]] · [[Fondements théoriques — Inner Mapping]]
- [[05 — Évaluation du soi -- Pensée binaire]]
- [[Peur]] · [[Anxiété d'évaluation]]
- [[Résultat négatif → Peur → Retrait]]
