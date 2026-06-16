---
type: pattern_cognitif
tags:
  - pattern
  - calibration-temporelle
  - vision-zoomée
  - cognition
L2_neutre: "Calibration temporelle"
pôle_mal_être: "Vision zoomée"
pôle_bien_être: "Perspective long terme"
émotion_véhiculée: "[[Peur]] · [[La Honte]]"
date: 2026-06-06
statut: documenté
---

# ⚙️ Calibration temporelle -- Vision zoomée

> *"Une semaine difficile n'est qu'un bruit statistique sur 4 à 6 mois."* [documenté — Alexis 04-20-2026]

---

## I. L'opération neutre — Calibration temporelle

**Définition :** Mécanisme par lequel le cerveau choisit la **fenêtre temporelle** sur laquelle il évalue une situation. Il peut évaluer sur quelques jours, quelques semaines, ou plusieurs mois. Ce choix conditionne tout ce qui suit — les conclusions sur le système, sur le niveau, sur la validité d'une direction.

**[inféré depuis Barrett 2017]** La fenêtre temporelle du cerveau est une prédiction : il pondère les données récentes plus lourdement que les données anciennes par défaut (recency bias). Quand le budget corporel est épuisé, ce biais s'accentue — les données récentes (mauvaise série) écrasent les données historiques (évolution sur plusieurs mois).

---

## II. Pôle mal-être — Vision zoomée

**Mécanisme biaisé :** Évaluation du système sur quelques sessions plutôt que sur la fenêtre correcte (4–6 mois). Les données récentes semblent représentatives de la réalité globale alors qu'elles sont du bruit statistique.

**[documenté — Alexis 04-20-2026]** *"Une semaine difficile n'est qu'un bruit statistique."*

**Conditions d'activation :**
- Mauvais run prolongé + budget corporel épuisé (mauvais sommeil, stress)
- Pas de données long terme visibles (pas de suivi graphique)
- Isolation sociale (Siem Reap) qui amplifie l'interprétation des résultats

**Manifestation documentée :**
Séquence : 3 sessions perdantes → *"depuis 3 sessions ça ne marche pas"* → *"le système est cassé"* → doute sur le niveau → activation de [[Peur]] et [[Reconstruction mémorielle -- Sélectivité mémorielle]].

---

## III. Pôle bien-être — Perspective long terme

**Mécanisme générative :** Évaluation sur la bonne fenêtre (4–6 mois minimum). Les fluctuations récentes sont lues comme du bruit statistique dans une trajectoire plus large.

**Conditions d'activation :** Budget corporel satisfait · données long terme accessibles · résultats ancrés dans une vision de processus.

> [!note] Documentation à compléter
> Les manifestations de ce pôle en session sont à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Vision zoomée est actif quand...
> - Une évaluation globale ("le système est cassé") suit directement quelques sessions
> - La confiance varie fortement selon les 3–5 dernières sessions
> - Le mot "depuis" introduit une conclusion sur un horizon très court
>
> **Question de détection :** *"Sur quelle fenêtre temporelle est-ce que j'évalue ça ? Combien de sessions ? Combien de mois ?"*

---

## V. Protocole d'interruption

> [!tip] In-game / Sur la timebank
> *"Est-ce que cette session est représentative du système, ou est-ce du bruit statistique ?"*
> Ramener la fenêtre : 4–6 mois minimum pour évaluer un système.

> [!tip] Hors session
> Consulter les données long terme avant de tirer une conclusion sur le niveau ou le système.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[pattern:: Vision zoomée]`*");
> ```

---

## Notes liées
- [[Index]] · [[Fondements théoriques — Inner Mapping]]
- [[Reconstruction mémorielle -- Sélectivité mémorielle]] · [[Évaluation du soi -- Pensée binaire]]
- [[Peur]] · [[Résultat négatif → Peur → Retrait]]
- [[L1 — Structures profondes/01 — Besoin de Compétence]]
