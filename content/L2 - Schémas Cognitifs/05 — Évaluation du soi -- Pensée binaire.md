---
type: pattern_cognitif
tags:
  - pattern
  - évaluation-enjeu
  - piédestal
  - cognition
L2_neutre: "Évaluation de l'enjeu"
pôle_mal_être: "Piédestal"
pôle_bien_être: "Enjeu calibré"
émotion_véhiculée: "[[Anxiété d'évaluation]] · [[La Honte]]"
date: 2026-06-06
statut: documenté
---

# ⚙️ Évaluation de l'enjeu -- Piédestal

> *"Plus je suis proche de mon potentiel idéal, plus j'ai à perdre."* [documenté — Alexis 05-29-2026]
> *"Vouloir ne pas gâcher crée les conditions du plantage."* [documenté — Alexis 05-29-2026]

---

## I. L'opération neutre — Évaluation de l'enjeu

**Définition :** Mécanisme par lequel le cerveau évalue l'importance d'une situation — ce qu'il y a à gagner ou à perdre. Cette évaluation calibre la mobilisation de ressources : plus l'enjeu perçu est élevé, plus le cerveau alloue de ressources (et de tension).

**[inféré depuis Barrett 2017]** Un enjeu perçu élevé = une prédiction de coût métabolique important = mobilisation accrue = tension physique = contraction. Le cerveau optimise pour éviter la perte perçue.

---

## II. Pôle mal-être — Piédestal

**Mécanisme biaisé :** En haute énergie ou en contexte d'attentes élevées, l'enjeu perçu explose dans les deux sens simultanément — potentiel immense ET risque de le rater immense. La situation est mise sur un piédestal qui rend la performance impossible par contraction.

**[documenté — Alexis 05-29-2026]** *"Vouloir ne pas gâcher crée les conditions du plantage."*

**Lien avec L1 :** Le Piédestal est activé par le Perfectionnisme protecteur (L1 défensif) — si la maîtrise est un rempart identitaire, les moments de haute performance potentielle deviennent des tests de la valeur du rempart.

**Conditions d'activation :**
- Haute énergie perçue → *"aujourd'hui je peux jouer au sommet"*
- Bonne dynamique de session en cours
- Anticipation d'un résultat important

**Manifestations documentées :**
- *"Aujourd'hui je suis en super forme → je ne peux pas gâcher ça"* → contraction → contre-performance
- Session qui démarre bien → enjeu qui monte → anxiété d'évaluation → dégradation

---

## III. Pôle bien-être — Enjeu calibré

**Mécanisme génératif :** L'enjeu perçu reste proportionné à la réalité. La haute énergie est utilisée comme ressource, pas comme pression. *"Je joue depuis moi, pas pour l'image de cette forme."*

> [!note] Documentation à compléter
> Manifestations de ce pôle à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Piédestal est actif quand...
> - Une pensée sur la forme ou l'énergie du jour est suivie d'une pensée sur "ne pas gâcher"
> - La session semble trop importante pour être jouée normalement
> - La haute énergie génère de la tension plutôt que de la fluidité
>
> **Question de détection :** *"Est-ce que je joue cette session, ou est-ce que je gère l'image de ma forme ?"*

---

## V. Protocole d'interruption

> [!tip] In-game / Sur la timebank
> *"Je joue ce coup depuis moi — pas pour l'image de cette forme."*
> Abaisser l'enjeu perçu : cette session ne définit pas ce joueur.

> [!tip] Avant session — warmup
> Si haute énergie détectée : nommer le risque Piédestal explicitement dans le warmup.
> Intention d'ancrage : *"Je joue depuis mon identité, indépendamment du résultat de cette session."*

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[pattern:: Piédestal]`*");
> ```

---

## Notes liées
- [[Index]] · [[Fondements théoriques — Inner Mapping]]
- [[Évaluation du soi -- Pensée binaire]]
- [[Anxiété d'évaluation]] · [[La Honte]]
- [[Écart attentes réalité → Honte → Contre-performance]]
- [[L1 — Structures profondes/01 — Besoin de Compétence]]
