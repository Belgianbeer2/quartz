---
type: fiche_cascade
tags:
  - cascade
  - inner-mapping
  - fatigue
  - chaleur
  - colère
trigger: "Fatigue + fortes chaleurs simultanées"
quadrant: "BE+BM → HE+BM (bascule)"
circuit: low_road
L1_activé:
  - Perfectionnisme protecteur
L2_processus:
  - Confabulation
L3_émotion: "[[Frustration]] → [[Colère_IRL]]"
L4_comportement: "Colère comme tentative de reprise de pouvoir sur l'impuissance"
date: 2026-06-06
statut: documentée
---

# 🔗 Cascade : Surchauffe cognitive → Colère → Impulsivité

> *Fatigue + chaleur épuisent le préfrontal. Le cerveau confabule pour donner du sens à l'inconfort. La colère tente de récupérer un pouvoir sur ce qui lui échappe.*

---

## 1. Déclencheur

**Physiologique et contextuel** — la fatigue combinée aux fortes chaleurs dépasse le seuil de régulation préfrontale. Ce n'est pas un déclencheur situationnel (une main, un résultat) — c'est un état de fond qui rend tous les L2 plus actifs et moins interruptibles.

> [!warning] Cascade Low Road
> L'épuisement préfrontal signifie que les protocoles cognitifs habituels sont moins accessibles. L'intervention physiologique doit précéder toute tentative de raisonnement.

---

## 2. Séquence

```
Fatigue + fortes chaleurs
        ↓
Déplétion préfrontale
(cortex préfrontal sous-disponible — régulation affaiblie)
        ↓
L1 — Perfectionnisme protecteur activé
Besoin de contrôle amplifié par l'épuisement
        ↓
L2 — Confabulation (réécriture des corrélations)
Obsession par les corrélations ayant généré le mal-être
Oubli des prix à payer des actions précédentes
(ex : avoir accepté un chien dans la maison → troubles du sommeil → situations compliquées)
        ↓
L2 — Réécriture des corrélations
Justifier les frustrations actuelles par des causalités réécrites
"C'est à cause de X que je suis mal" (X = corrélation post-rationalisée)
        ↓
L3 — Frustration → Colère
La colère comme tentative de récupérer une forme de pouvoir
sur l'impuissance face aux derniers événements
        ↓
L4 — Comportement de reprise de pouvoir
Décisions impulsives · changements de situation · confrontations
```

---

## 3. Points d'interruption

> [!tip] Avant session — détection préventive
> Checklist : fatigue élevée + chaleur importante = risque surchauffe cognitive
> → Réduire le volume de session ou reporter
> → Ne pas prendre de décisions de vie importantes dans cet état

> [!tip] Sur la réécriture des corrélations
> *"Est-ce que c'est la fatigue qui réécrit, ou est-ce une analyse fondée ?"*
> *"Quels étaient les prix à payer que j'avais acceptés ?"*
> → Revenir aux engagements documentés avant l'état de surchauffe

> [!tip] À la Frustration
> Nommer + stop loss immédiat
> L'intervention physiologique d'abord (ancrage, sortie de l'environnement si possible)
> Raisonnement après récupération — pas pendant

---

## 4. Retournement vers le bien-être

**Circuit low road dominant → physiologique avant tout.**

1. Reconnaître l'état : *"Je suis en surchauffe cognitive"*
2. Stop loss physiologique : sortir de la session, changer d'environnement si possible
3. Récupération active : hydratation, air frais, repos
4. **Ne pas raisonner avec les corrélations réécrites** — elles ne sont pas valides dans cet état
5. Reporter toute décision de vie ou d'ajustement de système
6. Reprendre l'analyse à froid, après récupération complète

> [!danger] Prix à payer documenté
> Toute décision prise en état de surchauffe cognitive est potentiellement une décision confabulée. Les corrélations réécrites semblent vraies — c'est leur caractéristique principale.

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
>     dv.paragraph("*Aucune session identifiée — tagger avec `[cascade:: Surchauffe cognitive → Colère → Impulsivité]`*");
> }
> ```

---

## Notes liées

- [[Index]]
- [[Frustration]]
- [[Colère IRL]]
- [[01 — Fondements théoriques]]
