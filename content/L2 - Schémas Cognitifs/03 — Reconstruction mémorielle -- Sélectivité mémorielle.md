---
type: pattern_cognitif
tags:
  - pattern
  - mémoire
  - reconstruction-mémorielle
  - cognition
L2_neutre: "Reconstruction mémorielle"
pôle_mal_être: "Sélectivité mémorielle"
pôle_bien_être: "Reconstruction équilibrée"
émotion_véhiculée: "[[La Honte]] · [[Frustration]]"
date: 2026-06-06
statut: extrait de [[La Honte]] + [[Frustration]]
---

# ⚙️ Reconstruction mémorielle -- Sélectivité mémorielle

> *"Je n'ai pas accès à la session — j'ai accès à la version que mon état émotionnel présent a reconstruite."*

---

## I. L'opération neutre — Reconstruction mémorielle

**Définition :** Mécanisme par lequel le cerveau reconstruit le souvenir d'un événement passé. Ce n'est pas un accès direct à ce qui s'est passé — c'est une reconstruction active influencée par l'état présent.

**[documenté]** Kahneman (2011) distingue l'*experiencing self* (ce qui se passe en temps réel) et le *remembering self* (la version reconstruite après coup). Le remembering self ne stocke pas des faits — il stocke des évaluations émotionnelles.[^1]

**[documenté — Moukheiber]** Sur une session en run bad, le cerveau réécrit chaque main à travers le prisme de l'échec — même celles qui étaient bien jouées. *"Je dois laisser paraître des tells"* n'est pas une observation — c'est une reconstruction narrative depuis l'état émotionnel présent.[^2]

---

## II. Pôle mal-être — Sélectivité mémorielle

> *La reconstruction filtrée par l'état émotionnel négatif — seules les preuves de l'échec survivent.*

### Mécanisme biaisé

Sous appui Peur ou état émotionnel négatif, la reconstruction mémorielle ne sélectionne que les événements congruents avec l'état présent. Les moments positifs sont effacés — non par choix, mais par mécanique du remembering self.

### Conditions d'activation

- État émotionnel négatif au moment du rappel
- Fin de session perdante ou difficile
- Feedback réalisé dans un état non régulé
- Fatigue — le remembering self est plus actif quand le préfrontal est épuisé

### Manifestations documentées

**Manifestation 1 — Review post-session en run bad**
Session perdante → état négatif au feedback → relecture avec prisme de l'échec → *"j'ai mal joué toute la session"* — en effaçant les bons folds, les moments de focus, les décisions correctes.

**Manifestation 2 — Session 28-05 (Honte post-session)**
Le retrait du 29/05 n'était pas causé par la perte financière (-$1432) — il était causé par la reconstruction biaisée comme *"échec d'identité total"*. Les moments du Stratège présents dans la session (relecture des documents in-game, focus maintenu après les bad beats) ont été effacés. Le souvenir ne correspondait pas aux données objectives du feedback.

---

## III. Pôle bien-être — Reconstruction équilibrée

> *La même opération avec un rappel actif des deux côtés — les moments difficiles ET les moments du Stratège.*

**Mécanisme :** Sous appui Confiance, la reconstruction mémorielle peut être orientée délibérément pour inclure les moments positifs que la sélectivité aurait effacés. Ce n'est pas de l'optimisme — c'est forcer le remembering self à reconstruire depuis les données réelles.

**[documenté — La Honte, session 28-05]** *"Le paradoxe : reconnaître l'écart, c'est le Stratège qui regarde. Si tu vois que tu n'étais pas le Stratège — c'est lui qui a vu."* La reconstruction équilibrée active cette même capacité.

**Outil :** Question de reconvocation mémorielle — *"Quels moments du Stratège étaient présents dans cette session ?"* Force le rappel des preuves positives pour contrebalancer la sélectivité.

> [!note] Documentation à compléter
> Les conditions d'activation spontanée du pôle bien-être sont à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Sélectivité mémorielle est actif quand...
>
> - Le souvenir de la session est uniformément négatif sans nuance
> - On identifie des "tells" ou "fuites" sans données objectives pour les supporter
> - La reconstruction est plus sévère que les feedbacks documentés à chaud
> - On se souvient de l'émotion de la session, pas des décisions spécifiques
>
> **Question de détection :** *"Est-ce que ce souvenir correspond à ce que j'ai documenté dans mon feedback — ou est-ce que c'est mon état émotionnel présent qui parle ?"*

---

## V. Protocole d'interruption

> [!tip] Pendant le feedback
> Faire le feedback immédiatement après la session. Plus le temps passe sous état négatif, plus la reconstruction est biaisée.

> [!tip] Si feedback en état émotionnel activé
> Commencer par les données objectives (mains documentées, prix à payer respectés) avant l'évaluation qualitative.

> [!tip] Le lendemain d'une session difficile
> *"Ce que je ressens ce matin, c'est le remembering self — pas un accès direct à la session."*
> Revenir au feedback documenté à chaud comme référence.

> [!tip] Sur la cascade Honte
> *"Quels moments du Stratège étaient présents dans cette session ?"* — forcer le rappel des moments positifs contrebalance la sélectivité.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const patterns = page.file.lists.pattern;
>         return dv.array(patterns).includes(targetPattern);
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session — tagger avec `[pattern:: Sélectivité mémorielle]`*");
> }
> ```

---

## Sources

[^1]: Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux.
[^2]: Albert Moukheiber — Interview × Les Lueurs (2026). Voir [[01 — Albert Moukheiber × Les Lueurs]].

## Notes liées

- [[00 — Index]] · [[La Honte]] · [[Frustration]] · [[00 — Protocole In-Game]]
