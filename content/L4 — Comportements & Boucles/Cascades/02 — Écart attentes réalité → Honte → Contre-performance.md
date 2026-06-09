---
type: fiche_cascade
tags:
  - cascade
  - inner-mapping
  - attentes
  - honte
trigger: "Écart entre les attentes élevées et la réalité de la performance perçue"
quadrant: "HE+BM — Friction"
circuit: high_road
L1_activé:
  - Perfectionnisme protecteur
L2_processus:
  - Piédestal
  - Pensée binaire
L3_émotion: "[[La Honte]]"
L4_comportement: "Contre-performance · contraction · sur-vigilance · jeu forcé"
date: 2026-06-06
statut: documentée
---

# 🔗 Cascade : Écart attentes/réalité → Honte → Contre-performance

> *Ce n'est pas la haute énergie qui déclenche la cascade — c'est l'écart entre les attentes qu'elle génère et la réalité perçue.*
> *"Vouloir ne pas gâcher crée les conditions du plantage."* [documenté — Alexis 05-29-2026]

---

## 1. Déclencheur

L'énergie haute génère des attentes élevées sur la performance. Dès qu'un écart apparaît entre ces attentes et la réalité perçue (un mauvais coup, une session en dessous), le Perfectionnisme protecteur s'active. La Honte est déclenchée par la **déviation d'intention** — pas par le résultat financier.

> [!warning] Distinction Honte / Peur
> **Honte** = écart entre l'intention de performance (qualité) et la réalité perçue
> **Peur** = résultat financier négatif · bad run · variance
> Voir [[01 — Résultat négatif → Peur → Retrait]]

---

## 2. Séquence

```
Haute énergie → attentes élevées sur la performance
        ↓
L1 — Perfectionnisme protecteur activé
"Si je joue parfaitement aujourd'hui, ma valeur est confirmée"
        ↓
L2 — Piédestal
"Plus je suis proche de mon potentiel idéal, plus j'ai à perdre"
Enjeu perçu disproportionné — potentiel immense ET risque de le rater
        ↓
Écart attentes/réalité
Premier mauvais coup · décision en dessous des attentes · session qui ne décolle pas
        ↓
L2 — Pensée binaire
"J'aurais dû jouer ça parfaitement → je suis en dessous de ce que je croyais"
        ↓
L3 — Honte
"Je SUIS défaillant" · déviation d'intention · sentiment d'avoir raté ce que j'aurais dû réussir
        ↓
L4 — Contre-performance · contraction · sur-vigilance · jeu forcé
```

---

## 3. Points d'interruption

> [!tip] Au Piédestal — signal d'entrée
> *"Est-ce que je joue CE coup, ou est-ce que je gère l'image de ma forme ?"*
> → Revenir à la main devant soi — pas à la session globale

> [!tip] À l'écart attentes/réalité
> *"Est-ce que ce coup définit la session, ou est-ce un coup parmi d'autres ?"*
> → Désactiver la signification globale d'un événement local

> [!tip] À la Honte
> Nommer : *"Je suis en Honte — c'est l'écart d'intention qui parle, pas mon niveau."*
> Distinguer : *"J'ai mal joué CE coup"* ≠ *"Je suis défaillant"*
> → [[00 — Protocole In-Game]]

---

## 4. Retournement vers le bien-être

**Circuit high road → désamorcer l'enjeu perçu avant que la Honte s'installe.**

1. Détecter le Piédestal tôt — avant le premier écart
2. Baisser l'enjeu perçu : *"Je joue depuis moi, pas pour l'image de cette forme"*
3. À la Honte : nommer sans s'y identifier
4. Reconvoquer le Stratège sur le coup présent uniquement
5. Si contraction déjà là : ancrage corporel → revenir à la main

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
>     dv.paragraph("*Aucune session identifiée — tagger avec `[cascade:: Écart attentes/réalité → Honte → Contre-performance]`*");
> }
> ```

---

## Notes liées

- [[00 — Index]]
- [[La Honte]]
- [[Anxiété d'évaluation]]
- [[00 — Protocole In-Game]]
