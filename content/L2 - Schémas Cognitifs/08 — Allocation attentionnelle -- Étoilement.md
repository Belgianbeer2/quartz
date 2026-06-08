---
type: pattern_cognitif
tags:
  - pattern
  - allocation-attentionnelle
  - étoilement
  - cognition
L2_neutre: "Allocation attentionnelle"
pôle_mal_être: "Étoilement"
pôle_bien_être: "Focus priorisé"
émotion_véhiculée: "[[Frustration]] · [[Anxiété d'évaluation]]"
date: 2026-06-06
statut: documenté
---

# ⚙️ Allocation attentionnelle -- Étoilement

> *"Se disperser, perdre le fil, s'éparpiller sur plusieurs sujets simultanément sous charge mentale ou fatigue."* [documenté — Alexis 03-23-2026]

---

## I. L'opération neutre — Allocation attentionnelle

**Définition :** Mécanisme par lequel le cerveau distribue son attention entre plusieurs objets, tâches ou préoccupations. En état de budget corporel plein, cette distribution est priorisée et ciblée. En état épuisé, elle devient diffuse.

**[documenté — Barrett 2017]** L'attention est une ressource métabolique. Quand le budget corporel est appauvri, la capacité à maintenir un focus concentré diminue — le cerveau revient à un mode de traitement distribué et peu hiérarchisé (état de Default Mode Network).

---

## II. Pôle mal-être — Étoilement

**Mécanisme biaisé :** Dispersion de l'attention sur plusieurs sujets simultanément, sans hiérarchie, sous charge mentale ou fatigue. Aucun sujet n'est traité à fond. Sentiment de tourner en rond sans avancer.

**[documenté — Alexis 03-23-2026]** *"Se disperser, perdre le fil, s'éparpiller sur plusieurs sujets simultanément sous charge mentale ou fatigue."*

**Conditions d'activation :**
- Fatigue physique ou mentale (budget corporel épuisé)
- Charge mentale élevée (multiples préoccupations simultanées)
- Stress prolongé ou mauvaise période de résultats

**Manifestations potentielles :**
- Travailler sur plusieurs aspects du jeu en même temps sans progression sur aucun
- Passer d'un sujet à l'autre dans les sessions d'étude sans terminer
- In-game : essayer de gérer simultanément plusieurs dynamiques de table sans focus

---

## III. Pôle bien-être — Focus priorisé

**Mécanisme génératif :** Identification claire de la priorité du moment. Une seule chose à la fois. Capacité à terminer avant de passer à la suite.

**Lié au budget corporel :** Ce pôle est plus accessible quand le sommeil, l'alimentation et la récupération physique sont satisfaisants.

> [!note] Documentation à compléter
> Manifestations en session à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Étoilement est actif quand...
> - Plusieurs onglets ouverts, plusieurs sujets commencés, aucun terminé
> - Sentiment de travailler sans avancer
> - In-game : attention qui passe d'une table à l'autre sans focus sur la décision présente
>
> **Question de détection :** *"Quelle est la seule chose la plus utile à faire maintenant ?"*

---

## V. Protocole d'interruption

> [!tip] Avant session / étude
> Identifier une seule priorité. L'écrire. Fermer tout le reste.

> [!tip] Si étoilement détecté en cours de session
> Stop. Nommer : *"Je suis en étoilement."*
> Choisir une seule chose. Y revenir.

> [!tip] Budget corporel
> L'étoilement est souvent un signal de budget épuisé. Vérifier : sommeil, alimentation, récupération.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[pattern:: Étoilement]`*");
> ```

---

## Notes liées
- [[00 — Index]] · [[Fondements théoriques — Inner Mapping]]
- [[Frustration]] · [[Anxiété d'évaluation]]
- [[Surchauffe cognitive → Colère → Impulsivité]]
