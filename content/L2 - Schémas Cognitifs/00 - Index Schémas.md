---
type: index_schemas
tags:
  - index
  - schémas
  - cognition
  - inner-mapping
date: 2026-06-06
---

# 🔍 Index — Schémas

> Ce fichier est un répertoire de navigation. La profondeur est dans les fiches liées.
> Pour les fondements théoriques du modèle : [[Fondements théoriques — Inner Mapping]]
> Pour le cheminement de construction : [[Genèse — Inner Mapping]]

---

## Architecture du modèle

| Niveau | Nom | Définition | Fenêtre | Type de fiche |
|---|---|---|---|---|
| **L1** | Prémisse opératoire | Proposition traitée comme vraie sans travail délibéré · pré-situationnelle · globale · stable | Semaines — mois | `schema_base` |
| **L2** | Opération cognitive | Mécanisme semi-automatique · situationnel · reproductible · output perçu comme observation | Avant session → timebank | `pattern_cognitif` |
| **L3** | État émotionnel | Réponse psycho-physiologique · temporaire · valenced · action tendency · nommable | Timebank · immédiat | `fiche_emotion` |
| **L4** | Comportement | Action observable · post-hoc · mesurable contre les prix à payer | Post-hoc | *dans fiche_emotion* |

> [!info] Bidirectionnalité
> Les 4 niveaux opèrent dans les deux boucles. L'appui L1 (Peur / Confiance) détermine la direction. Voir [[01 — Fondements théoriques]] — Section III.

---

## 🪨 L1 — Prémisses opératoires

*Croyances stables sur soi. Nécessitent du travail de fond (dépolarisation). Génèrent les L2.*

| Schéma | Description | Source | Statut |
|---|---|---|---|
| **Perfectionnisme protecteur** | Maîtrise technique comme rempart identitaire. *"Stratégie de survie identitaire."* | Alexis [documenté] 04-20-2026 | 🔷 À créer |
| **Résultats-dépendance** | Confiance liée aux résultats. En good run : suranticipation. En bad run : doute du niveau. | Alexis [documenté] 05-08-2026 | 🔷 À créer |
| **Intransigeance envers soi** | Ne pas s'accorder le droit à l'erreur sur ce qu'on "devrait" maîtriser. | Alexis [documenté] 04-07-2026 | 🔷 À créer |

---

## ⚙️ L2 — Opérations cognitives

*Le tableau liste les opérations neutres avec leurs deux pôles. Ce qui est documenté dans les fiches actuelles = pôles mal-être.*

| Opération L2 neutre             | Pôle mal-être                                                | Statut           | Pôle bien-être            | Statut             |
| ------------------------------- | ------------------------------------------------------------ | ---------------- | ------------------------- | ------------------ |
| **Mentalisation**               | [[01 — Mentalisation -- Dissociation]]                       | ✅ Fiche complète | Empathie · connexion      | ⚠️ À conscientiser |
| **Évaluation causale**          | [[02 — Évaluation causale -- Confabulation]]                 | ✅ Fiche créée    | Analyse fondée            | ⚠️ À conscientiser |
| **Reconstruction mémorielle**   | [[03 — Reconstruction mémorielle -- Sélectivité mémorielle]] | ✅ Fiche créée    | Reconstruction équilibrée | ⚠️ À conscientiser |
| **Calibration temporelle**      | Vision zoomée                                                | 🔷 À créer       | Perspective long terme    | ⚠️ À conscientiser |
| **Évaluation du soi**           | Pensée binaire                                               | 🔷 À créer       | Gradient d'identité       | ⚠️ À conscientiser |
| **Évaluation de l'enjeu**       | Piédestal                                                    | 🔷 À créer       | ?                         | ⚠️ À conscientiser |
| **Projection temporelle**       | Suranticipation                                              | 🔷 À créer       | ?                         | ⚠️ À conscientiser |
| **Allocation attentionnelle**   | Étoilement                                                   | 🔷 À créer       | ?                         | ⚠️ À conscientiser |
| **Validation de la créativité** | Intellectualiser la créativité                               | 🔷 À créer       | ?                         | ⚠️ À conscientiser |

> [!note] Pôles bien-être L2
> Non documentés intentionnellement — à conscientiser par l'expérience, pas par théorisation.

---

## L3 — Émotions

*Référence vers `🧠 Inner Mapping/L3 — Émotions/`. La profondeur est dans les fiches.*

```dataviewjs
let fiches = dv.pages('"🧠 Inner Mapping/L3 — Émotions"')
    .where(p => p.type === "fiche_emotion");
if (fiches.length > 0) {
    dv.table(
        ["Fiche", "Émotion véhiculée par"],
        fiches.sort(f => f.file.name, 'asc')
              .map(f => [f.file.link, f.émotion_véhiculée || "—"])
    );
} else {
    dv.paragraph("*⚠️ Chemin à corriger — remplacer l'emoji Émotions si besoin*");
}
```

---

## 📎 Manifestations — dans les fiches émotions

*Comportements ou états secondaires déjà couverts. Pas de fiche séparée.*

| Manifestation | Appartient à | Note |
|---|---|---|
| Show-off | [[Dissociation]] | Variante comportementale |
| Rumination | [[La Honte]] | Carburant entre les sessions |
| Catastrophisation | [[Anxiété d'évaluation]] | À documenter quand la fiche se complète |
| Résignation | [[Frustration]] | Stade terminal d'une frustration non nommée |

---

## 🔗 Cascades

*Séquences L1→L2→L3→L4 documentées. Un fichier par cascade dans `🧠 Inner Mapping/L2 — Schémas Cognitifs/Cascades/`.*

```dataviewjs
let cascades = dv.pages('"🧠 Inner Mapping/L2 — Schémas Cognitifs/Cascades"')
    .where(p => p.type === "fiche_cascade");
if (cascades.length > 0) {
    dv.table(
        ["Cascade", "Trigger", "Circuit", "Quadrant", "L3"],
        cascades.map(c => [
            c.file.link,
            c.trigger || "—",
            c.circuit || "—",
            c.quadrant || "—",
            c.L3_émotion || "—"
        ])
    );
} else {
    dv.paragraph("*Aucune cascade détectée dans `🧠 Inner Mapping/L2 — Schémas Cognitifs/Cascades/`*");
}
```

---

## 📎 Sources

Les schémas sourcés *Alexis [documenté]* proviennent des call transcripts `Mindset/Alexis/Call/` — source privée.
Les bases théoriques du modèle : [[Fondements théoriques — Inner Mapping]].

---

## Notes liées

- [[Fondements théoriques — Inner Mapping]]
- [[Genèse — Inner Mapping]]
- [[🧭 Boussole émotionnelle]]
- [[00 Convoquer le Stratège- Protocole_In-Game]]
- [[PROMPT — Rigueur d'attribution Moukheiber × Alexis]]
