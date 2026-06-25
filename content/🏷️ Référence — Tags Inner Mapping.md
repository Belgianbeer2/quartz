---
type: référence
tags:
  - inner-mapping
  - tags
  - référence
date: 2026-06-21
statut: référence stable
---

# 🏷️ Référence — Tags Inner Mapping

> Référence rapide à consulter lors du Feedback, de l'O&R, ou de tout autre document de collecte.
> **Règle générale :** un tag par ligne, format `[tag:: Valeur]`

---

## Format des tags — Résumé rapide

| Tag | Format | Document de collecte | Lu par |
|---|---|---|---|
| `[emotion:: X]` | Nom exact de la fiche L3 | Feedback · O&R | Fiches L3 (§VI DataviewJS sessions) |
| `[pattern:: X]` | Nom du pôle défensif L2 | Feedback · O&R | Fiches L2 (§VIII DataviewJS sessions) |
| `[cascade:: X]` | Nom de la cascade L4 | Feedback | Fiches L4 (§DataviewJS) |
| `[comportement:: X]` | Description courte du L4 observé | Feedback · O&R | Index L4 |
| `[protocoles_utilisés:: X]` | Noms des protocoles activés | Feedback · MR · O&R | Dashboard Mindset |
| `[declencheur:: X]` | Déclencheur précis (sous `[emotion:: X]`) | Feedback | Fiches L3 §VI.1 |
| `[pensee:: X]` | Pensée automatique (sous `[emotion:: X]`) | Feedback | Fiches L3 §VI.2 |
| `[reaction:: X]` | Réaction comportementale (sous `[emotion:: X]`) | Feedback | Fiches L3 §VI.3 |

---

## Émotions L3 disponibles — `[emotion:: X]`

### Pôle défensif
```
[emotion:: Colère]
[emotion:: Colère IRL]
[emotion:: Frustration]
[emotion:: La Réactance]
[emotion:: La Honte]
[emotion:: Anxiété]
[emotion:: Anxiété d'évaluation]
[emotion:: Peur]
[emotion:: Impuissance]
[emotion:: Délaissement]
[emotion:: Accablement]
[emotion:: Culpabilité]
[emotion:: Déception]
[emotion:: Doute]
[emotion:: Solitude]
[emotion:: Tristesse]
```

### Pôle générateur
```
[emotion:: Plénitude]
[emotion:: Plénitude IRL]
[emotion:: Certitude]
[emotion:: Détermination]
[emotion:: Curiosité]
[emotion:: Enthousiasme]
[emotion:: Satisfaction]
[emotion:: Sérénité]
```

---

## Schémas cognitifs L2 — `[pattern:: X]`

*Utiliser le **nom du pôle défensif** (colonne `pôle_défensif` du frontmatter de la fiche L2)*

```
[pattern:: Dissociation]
[pattern:: Confabulation]
[pattern:: Sélectivité mémorielle]
[pattern:: Vision zoomée]
[pattern:: Pensée binaire]
[pattern:: Piédestal]
[pattern:: Suranticipation]
[pattern:: Scattering]
[pattern:: Auto-flagellation]
[pattern:: Rumination]
[pattern:: Suramplification]
```

---

## Cascades L4 — `[cascade:: X]`

*Utiliser le nom exact de la cascade documentée dans `L4 — Comportements & Boucles/`*

```
[cascade:: Erreur → Colère → Impulsivité]
[cascade:: Résultat négatif → Peur → Retrait]
[cascade:: Haute énergie → Piédestal → Contraction]
[cascade:: Accumulation → Scattering → Accablement]
```

---

## Structure type dans un Feedback

```markdown
**Émotions L3 détectées :**
- [emotion:: Frustration]
  - [declencheur:: Bad beat répété]
  - [pensee:: je dois laisser paraître des tells]
  - [reaction:: augmentation du volume]
- [emotion:: Certitude]

**Schémas L2 actifs :**
- [pattern:: Confabulation]
- [pattern:: Sélectivité mémorielle]

**Cascades / Comportements L4 :**
- [cascade:: Erreur → Colère → Impulsivité]
- [comportement:: Fold trop tôt sur riverbet]

**Protocoles utilisés :**
[protocoles_utilisés:: Switch Actif · Drill 01]
```

---

## Notes liées
- [[L2 - Schémas Cognitifs/00 - Index Schémas]]
- [[L3 - Émotions/]]
- [[L4 — Comportements & Boucles/00 — Index]]
- [[Protocoles/00 — Vue d'ensemble]]
