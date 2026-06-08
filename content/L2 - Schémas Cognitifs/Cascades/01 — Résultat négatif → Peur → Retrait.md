---
type: fiche_cascade
tags:
  - cascade
  - inner-mapping
  - résultats
  - peur
trigger: "Session perdante · bad run · résultat financier sous les attentes"
quadrant: "BE+BM — Préservation"
circuit: high_road
L1_activé:
  - Résultats-dépendance
L2_processus:
  - Vision zoomée
  - Sélectivité mémorielle
  - Pensée binaire
L3_émotion: "[[Peur]]"
L4_comportement: "Retrait · évitement session suivante · rumination financière · off-day non choisi"
date: 2026-06-06
statut: documentée
---

# 🔗 Cascade : Résultat négatif → Peur → Retrait

> *La peur n'est pas déclenchée par la perte elle-même — elle est construite par la signification que les L2 lui attribuent.*

---

## 1. Déclencheur

Session perdante, mauvais run, résultat financier en dessous des attentes. Le déclencheur est **financier et résultat-dépendant** — distinct de la [[La Honte|Honte]], qui est déclenchée par une déviation d'intention du warmup (qualité de jeu perçue, pas résultat).

---

## 2. Séquence

```
Résultat négatif (financier)
        ↓
L1 — Résultats-dépendance activée
"La confiance est liée aux résultats"
        ↓
L2 — Vision zoomée
"Depuis 3 sessions ça ne marche pas → le système est cassé"
        ↓
L2 — Sélectivité mémorielle
Le remembering self reconstruit la session depuis l'état émotionnel présent
"J'ai mal joué toute la session" — efface les bons coups
        ↓
L2 — Pensée binaire
"Je perds → je suis mauvais joueur → je ne suis pas encore ce joueur"
        ↓
L3 — Peur
Peur de ne pas être ce joueur · peur de la perte financière · peur du run bad prolongé
        ↓
L4 — Retrait · évitement · rumination financière
```

---

## 3. Points d'interruption

> [!tip] Après Vision zoomée
> *"Sur quelle fenêtre est-ce que j'évalue ? Une semaine difficile est un bruit statistique sur 4-6 mois."*
> → Ramener la perspective long terme (L2 bien-être : calibration temporelle)

> [!tip] Après Pensée binaire
> *"Est-ce que je perds parce que je joue mal, ou parce que la variance est là ?"*
> → Gradient d'identité — distinguer le jeu du résultat

> [!tip] À la Peur
> Nommer : *"Je suis en Peur — c'est le résultat financier qui parle, pas mon niveau."*
> → [[00 — Protocole In-Game]]

---

## 4. Retournement vers le bien-être

**Circuit high road → intervention cognitive d'abord.**

1. Nommer la Peur — ne pas la laisser opérer silencieusement
2. Identifier le L2 actif (Vision zoomée ou Pensée binaire en premier ?)
3. Rétablir la fenêtre temporelle correcte (4-6 mois)
4. Si L1 accessible : dépolarisation Résultats-dépendance
5. Ne pas lancer la session suivante depuis cet état

> [!warning] Ne pas confondre avec [[La Honte]]
> Peur = résultat financier · bad run · variance
> Honte = déviation d'intention warmup · qualité de jeu perçue

---

## 5. Suivi en session

> [!note]- 📜 Sessions où cette cascade a été identifiée
> ```dataviewjs
> let p = dv.current();
> let targetCascade = p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const cascades = page.file.lists.cascade;
>         return dv.array(cascades).includes(targetCascade);
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée — tagger avec `[cascade:: Résultat négatif → Peur → Retrait]`*");
> }
> ```

---

## Notes liées

- [[00 — Index]]
- [[01 — Fondements théoriques]]
- [[00 — Protocole In-Game]]
