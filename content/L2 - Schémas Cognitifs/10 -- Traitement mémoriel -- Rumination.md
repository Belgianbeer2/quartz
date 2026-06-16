---
type: pattern_cognitif
tags:
  - pattern
  - traitement-mémoriel
  - rumination
  - cognition
L2_neutre: "Traitement mémoriel"
pôle_mal_être: "Rumination"
pôle_bien_être: "Analyse fondée"
émotion_véhiculée: "[[La Honte]] · [[Impuissance]]"
date: 2026-06-06
statut: documenté
---

# ⚙️ Traitement mémoriel -- Rumination

> *"Le lendemain matin d'une session difficile, ce que tu ressens n'est pas un accès direct à la session — c'est le remembering self sous rumination."* [inféré depuis Kahneman 2011 · Nolen-Hoeksema 2008]

---

## I. L'opération neutre — Traitement mémoriel

**Définition :** Mécanisme par lequel le cerveau traite les événements passés en mémoire de travail. Ce traitement peut être orienté vers la résolution (analyse), passif et répétitif (rumination), ou sélectif (sélectivité mémorielle). Les trois utilisent le même mécanisme de base mais produisent des outputs radicalement différents.

**Distinction des trois pôles :**

| Mode | Orientation | Résolution | Émotion typique |
|---|---|---|---|
| **Analyse** | Passé → solution future | Oui | Curiosité · détermination |
| **Rumination** | Passé → boucle sans issue | Non | Honte · impuissance |
| **Sélectivité mémorielle** | Passé → confirmation de l'affect présent | Partielle | Peur · honte (amplifié) |

---

## II. Pôle mal-être — Rumination

> [!abstract] ✅ Fondement solide — Nolen-Hoeksema (1991, 2008)
> La rumination est un style de réponse aux émotions négatives caractérisé par la focalisation répétitive et passive sur les causes, significations et conséquences des symptômes de détresse — sans orientation vers la résolution ou l'action. Elle prolonge et amplifie les états négatifs, dégrade la qualité de la prise de décision, et est associée à la dépression et à l'anxiété.[^1]

**Ce qui la distingue de l'analyse :**
- L'analyse est orientée vers une action future : *"qu'est-ce que j'aurais pu faire différemment → voilà ce que je ferai la prochaine fois"*
- La rumination tourne sur le passé sans issue : *"pourquoi j'ai fait ça — je suis vraiment nul — j'aurais dû — pourquoi j'ai fait ça"*

**Ce qui la distingue de la sélectivité mémorielle :**
- La sélectivité filtre les souvenirs (L2 documenté)
- La rumination rejoue les mêmes souvenirs en boucle

**Conditions d'activation :**
- Session difficile + budget corporel épuisé (le lendemain matin)
- Erreur technique sur spot connu (avec Intransigeance active)
- Isolement social (pas de co-régulation disponible)

**[documenté — Barrett 2017]** La rumination est métaboliquement coûteuse : le cerveau tourne en boucle sans résoudre l'erreur de prédiction à l'origine de l'état négatif. Le budget continue à se dépenser.

---

## III. Pôle bien-être — Analyse fondée

**Mécanisme génératif :** Même matériau mémoriel, orientation vers la résolution. La question pivot : *"qu'est-ce que ça m'apprend sur la prochaine fois ?"*

**Conditions d'activation :** Budget corporel satisfait · état émotionnel régulé · feedback structuré (pas de jugement de valeur sur le soi).

> [!note] Distinction pratique
> Si tu te retrouves à penser au même spot pour la 4ème fois sans avoir formulé une action concrète → c'est de la rumination. Arrêter. Écrire une seule chose à faire différemment. Fermer.

---

## IV. Signaux de détection

> [!warning] Le pattern Rumination est actif quand...
> - Le même événement est rejoué mentalement plus de 2 fois sans résolution
> - La question est *"pourquoi j'ai fait ça"* plutôt que *"qu'est-ce que ça m'apprend"*
> - Le lendemain matin d'une session difficile génère un état pire que la veille
> - L'étude ou la réflexion augmente l'état négatif plutôt que de le réduire
>
> **Question de détection :** *"Est-ce que je pense à ça pour apprendre quelque chose, ou est-ce que je tourne en boucle ?"*

---

## V. Protocole d'interruption

> [!tip] Interruption active
> 1. Nommer : *"Je suis en rumination."*
> 2. Écrire UNE chose concrète à faire différemment → fermer le fichier
> 3. Engagement corporel immédiat (marcher, sport, changement d'environnement physique)

> [!tip] Prévention post-session
> Feedback structuré immédiatement après la session — quand l'état est encore frais mais pas encore en boucle. Un feedback fait à chaud résout l'erreur de prédiction avant que la rumination ne commence.

> [!tip] Budget corporel
> La rumination est amplifiée par le budget épuisé. La combattre sans s'occuper du budget (sommeil, co-régulation) est moins efficace.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
> if (sessions.length > 0) dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> else dv.paragraph("*Aucune session — tagger avec `[pattern:: Rumination]`*");
> ```

---

## Sources
[^1]: Nolen-Hoeksema, S. (2008). *Women Who Think Too Much.* Henry Holt. · Nolen-Hoeksema, S. (1991). *Responses to depression and their effects on the duration of depressive episodes.* Journal of Abnormal Psychology.

## Notes liées
- [[Index]] · [[Reconstruction mémorielle -- Sélectivité mémorielle]]
- [[La Honte]] · [[Impuissance]]
- [[L4 — Comportements & Boucles/02 — Boucles L4 → L1]]
- [[L0 — Physiologie & Budget Corporel/02 — Allostase]]
