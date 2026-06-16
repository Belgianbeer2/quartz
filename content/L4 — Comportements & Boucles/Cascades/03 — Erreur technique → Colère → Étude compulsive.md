---
type: fiche_cascade
tags:
  - cascade
  - inner-mapping
  - erreur
  - colère
trigger: Erreur technique identifiée · leak reconnu · décision perçue en dessous du niveau maîtrisé
quadrant: HE+BM — Friction
circuit: high_road
L1_activé:
  - Intransigeance envers soi
  - Perfectionnisme protecteur
L2_processus:
  - Pensée binaire
L3_émotion: "[[Colère IRL]]"
L4_comportement: Évaluation constante en bien/mal · perte de nuance stratégique · étude acharnée compulsive
date: 2026-06-06
statut: documentée
---

# 🔗 Cascade : Erreur technique → Colère → Étude compulsive

> *"L'élément déclencheur principal de l'instabilité émotionnelle : la colère liée aux erreurs techniques qu'il pense devoir maîtriser."* [documenté — Alexis 04-07-2026]

---

## 1. Déclencheur

Erreur technique identifiée en session — bluff mal exécuté, leak reconnu, décision perçue en dessous du niveau déjà maîtrisé. Le déclencheur est la **reconnaissance de l'erreur**, pas l'erreur elle-même.

---

## 2. Séquence

```
Erreur technique identifiée
        ↓
L1 — Intransigeance envers soi
"Je connais ce spot — j'aurais dû le jouer correctement"
"Ce type d'erreur est impardonnable à mon niveau"
        ↓
L1 — Perfectionnisme protecteur
"Si la théorie est appliquée à 100%, l'estime de soi est protégée"
"Si je perds en jouant parfaitement, seule la variance est responsable"
        ↓
L2 — Pensée binaire
"Mauvaise décision = je joue mal = je suis mauvais joueur"
Pas de gradient — pas de "j'ai mal joué CE coup"
        ↓
L3 — Colère
Injustice perçue envers soi-même · pression de contrôle total
        ↓
L4 — Évaluation constante · perte de nuance · étude acharnée comme réponse compulsive
```

---

## 3. Points d'interruption

> [!tip] À l'Intransigeance — signal d'entrée
> *"Est-ce que j'aurais DÛ maîtriser ce spot, ou est-ce que je pense que j'aurais dû ?"*
> → Distinguer l'erreur réelle de l'intransigeance envers l'erreur

> [!tip] À la Pensée binaire
> *"J'ai mal joué CE coup. Pas : je suis un mauvais joueur."*
> → Gradient d'identité — l'erreur ne définit pas le niveau

> [!tip] À la Colère
> Nommer : *"Je suis en Colère — l'intransigeance parle, pas l'analyse."*
> Identifier le prix à payer : [[Colère IRL]] — section prix à payer
> → [[00 — Protocole In-Game]]

---

## 4. Retournement vers le bien-être

**Circuit high road → déconstruire la signification de l'erreur.**

1. Nommer la Colère sans agir dessus
2. *"Cette erreur est de l'information, pas un jugement de valeur"*
3. Identifier si l'étude compulsive est déjà déclenchée → stop, c'est du L4
4. Reporter l'analyse de l'erreur après la session, hors état émotionnel
5. Si L1 accessible : dépolarisation Intransigeance envers soi

> [!warning] L4 à surveiller
> L'étude acharnée post-erreur est une réponse compulsive au L1 Perfectionnisme — elle se déguise en rigueur. Elle renforce le cycle au lieu de le couper.

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
>     dv.paragraph("*Aucune session identifiée — tagger avec `[cascade:: Erreur technique → Colère → Étude compulsive]`*");
> }
> ```

---

## Notes liées

- [[Index]]
- [[Colère IRL]]
- [[00 — Protocole In-Game]]
