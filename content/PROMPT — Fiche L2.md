---
type: prompt_template
tags:
  - prompt
  - L2
  - template
  - inner-mapping
date: 2026-06-21
version: 3.0
---

# 📐 Template — Fiche L2 · Schéma Cognitif

---

## Philosophie de la fiche

> [!abstract] Principe directeur — Le puzzle : expérience comme ancrage, théorie comme grille
> Construire une fiche L2, c'est redessiner un puzzle à partir de quelques pièces connues (l'expérience personnelle documentée), en utilisant la théorie pour **géolocaliser** ces pièces dans un espace plus large et **compléter** les patterns adjacents qui doivent exister.
>
> **L'expérience est le point de départ** — les instances personnelles datées ancrent la fiche dans quelque chose de réel et de vérifiable.
>
> **La théorie est la grille de complétion** — elle explique *pourquoi* ces pièces apparaissent là, et permet de déduire les patterns adjacents qui n'ont pas encore été vécus mais qui sont mécaniquement prédits par les mêmes fondements.
>
> **Ce qu'on évite :** documenter uniquement ce qui a été observé (puzzle incomplet) ou partir d'une cartographie théorique abstraite déconnectée du vécu (puzzle sans ancrage).

**Convention de sourcing :**
- `[documenté]` — issu d'une source théorique identifiée
- `[inféré depuis X]` — déduit des fondements à partir d'une pièce connue
- `[observation personnelle — date]` — instance personnelle qui ancre la fiche
- `[adjacent — non encore observé]` — pattern prédit par la théorie depuis les pièces connues

---

## FRONTMATTER

```yaml
---
type: schema_L2
tags: [L2, schema, inner-mapping]
L2_neutre: "[nom de l'opération cognitive neutre]"
pôle_défensif: "[nom du pôle dysfonctionnel]"
pôle_générateur: "[nom du pôle fonctionnel]"
L1_déclencheurs: ["[L1 défensif principalement impliqué]"]
émotions_produites: ["[[L3 typiquement générée]]"]
stratégies_Gross: ["[numéro et nom de la stratégie applicable]"]
entity_mastery: "défensif|générateur|les deux"
date: YYYY-MM-DD
statut: documenté | en cours | angle mort
---
```

---

## STRUCTURE DE LA FICHE

---

### I. L'opération neutre — [Nom]

**Ce bloc répond à :** qu'est-ce que ce mécanisme fait, structurellement, indépendamment de tout appui ?

- **Définition fonctionnelle :** l'opération en termes de traitement de l'information. Input → processus → output. Pas de jugement de valeur.
- **Ancrage théorique :** référence(s) documentée(s). Priorité : Barrett (cerveau prédictif, body budget), Gross, Dweck (entity/mastery), Kahneman, Moukheiber.
- **Modulation par L0 :** comment le niveau de budget corporel module l'activation et l'intensité de cette opération.
- **Universalité :** pourquoi ce mécanisme existe — quelle fonction adaptative il remplit dans un contexte neutre.

> [!abstract] ✅ Fondement — [Auteur(s) · Année]
> [Citation reformulée ou référence précise]

---

### II. Cartographie des pôles — Toutes expressions possibles

> **Méthode :** partir des instances personnelles documentées pour les géolocaliser dans l'espace théorique (L1 × entity/mastery × L0), puis compléter les expressions adjacentes qui doivent exister selon les mêmes mécanismes — même si non encore observées. Chaque expression est taguée selon sa source.

#### A. Pôle défensif — [Nom]

*Expression(s) sous appui L1 défensif et/ou entity thinking*

> **Rappel architectural :** un L2 défensif est une opération cognitive mobilisée *au service* d'un L1 défensif menacé. Le L1 actif détermine la *direction* de la distorsion — l'opération cherche à protéger le besoin entravé. Identifier le L1 précis, c'est identifier *pourquoi* l'opération déraille dans ce sens et pas un autre. Sans ce lien, on décrit le symptôme sans en comprendre la racine.

Pour chaque expression distincte — même non encore observée personnellement :

**Expression [N] — [Nom descriptif]**
- **L1 actif :** [Besoin fondamental menacé — Compétence · Autonomie · Appartenance · Contrôle · Éthique] en mode défensif
  *Ce qui est menacé :* [une phrase précise sur ce que ce besoin spécifique perd ou craint de perdre dans ce contexte]
- **Mécanisme L1→L2 :** [Comment la menace sur ce L1 précis produit cette distorsion — le lien causal entre le besoin entravé et l'opération biaisée. Ce champ est le cœur de la fiche : il explique pourquoi ce L2 s'active et pas un autre.]
- **Condition déclenchante :** [état L0 + contexte + ce qui expose le L1 à la menace]
- **Lien entity thinking :** [comment ET amplifie ou est nécessaire à cette expression]
- **Output typique :** [ce que ça produit concrètement]
- **L3 générée :** [[Émotion liée]]
- **Statut :** [documenté | inféré depuis X | observation personnelle - date | adjacent non encore observé]

#### B. Pôle générateur — [Nom]

*Expression(s) sous appui L1 générateur et/ou mastery thinking*

Pour chaque expression distincte :

**Expression [N] — [Nom descriptif]**
- **Condition :** [L1 générateur + état L0 + contexte]
- **Mécanisme :** [ce qui se passe dans le traitement]
- **Lien mastery thinking :** [comment MT soutient ou est nécessaire à cette expression]
- **Output typique :** [ce que ça produit concrètement]
- **L3 générée :** [[Émotion liée]]
- **Statut :** [documenté | inféré depuis X | observation personnelle - date | angle mort théorique]

---

### III. Instances personnelles documentées

*Section qui s'enrichit avec l'expérience — ne conditionne pas l'exhaustivité théorique de la fiche*

| Date | Contexte | Expression activée | Émotion produite | Source |
|---|---|---|---|---|
| | | | | |

---

### IV. Connexions dans l'écosystème L0→L4

| Niveau | Sens | Connexion |
|---|---|---|
| **Opération neutre → L0** | intrinsèque | [Coût de base de l'opération indépendamment du pôle — certaines opérations (ex : Mentalisation, Traitement mémoriel) ont un coût métabolique plancher même quand elles fonctionnent correctement] |
| **L0 → L2** | descendant | [Comment le budget corporel module ce L2 — seuil d'activation, intensité selon l'état] |
| **L2(défensif) → L0** | ascendant ⚠️ | [Coût métabolique du pôle défensif — consomme-t-il du budget L0 ? Sous quelle forme ? À quelle vitesse ? (ex : Rumination = activation prolongée DMN = coût élevé)] |
| **L2(générateur) → L0** | ascendant ✅ | [Effet net du pôle générateur sur le budget L0 — coûteux mais compensé par la résolution d'erreurs de prédiction ? Ou réellement restaurateur ? (ex : Analyse fondée = ferme la boucle = réduit le coût de l'incertitude non résolue)] |
| **L1 → L2** | descendant | [Quels L1 défensifs déclenchent ce schéma · quels L1 générateurs le soutiennent] |
| **L2(défensif) → L1** | ascendant ⚠️ | [Quelle prédiction L1 défensive s'entraîne à chaque activation répétée — quel L1 défensif est renforcé par la répétition de ce pôle ?] |
| **L2(générateur) → L1** | ascendant ✅ | [Quels L1 générateurs sont consolidés par la répétition du pôle générateur — quelle prédiction profonde positive s'entraîne ?] |
| **L2 associés** | latéral | [Autres schémas qui co-activent, précèdent ou suivent] |
| **L3 produites** | descendant | [Émotions générées par chaque pôle] |
| **L4 comportements** | descendant | [Comportements typiquement déclenchés] |

**Distinction des schémas proches :**
[Si risque de confusion avec un autre L2 — clarifier la différence précise de mécanisme]

---

### V. Régulation — Stratégies Gross disponibles

> Rappel — les 5 stratégies de Gross (1998), de l'amont vers l'aval :
> 1. Sélection de situation · 2. Modification de situation · 3. Déploiement attentionnel · 4. Reappraisal (changement cognitif) · 5. Modulation de la réponse

| Stratégie | Moment d'intervention | Application concrète |
|---|---|---|
| 1 · Sélection | Avant la situation | |
| 2 · Modification | Pendant — amont | |
| 3 · Attentionnel | Pendant — amont | |
| 4 · Reappraisal | Pendant — aval | |
| 5 · Modulation | Pendant / après | |

**Stratégie prioritaire pour ce schéma :** [laquelle est la plus accessible et la plus stable]

**Note L0 :** sous budget épuisé, les stratégies 1-3 deviennent moins accessibles. Documenter ici quelle stratégie reste disponible en condition dégradée.

---

### VI. Signaux de détection

> [!warning] Le pattern [Pôle défensif] est actif quand...
> - [Signal observable 1]
> - [Signal observable 2]
> - [Signal observable 3]
>
> **Question de détection :** *"[Question courte utilisable in-game ou hors session]"*

---

### VII. Protocoles d'interruption

> [!tip] In-game · Timebank
> [Action immédiate — max 2 phrases. Préférer stratégies Gross 3-4]

> [!tip] Avant session
> [Action de prévention. Préférer stratégies Gross 1-2]

> [!tip] Post-session · Review
> [Action d'analyse — contribue à la Section III]

> [!tip] Si L0 épuisé
> [Adaptation — protocole minimum quand le budget est bas]

---

### VIII. Suivi en session

```dataviewjs
let p = dv.current();
let targetPattern = p["pôle_défensif"] || p.file.name;
let sessions = dv.pages('"Journal/Session/Feedback/2026"')
    .where(page => dv.array(page.file.lists.pattern).includes(targetPattern));
if (sessions.length > 0) {
    dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
} else {
    dv.paragraph(`*Aucune session — tagger avec \`[pattern:: ${targetPattern}]\`*`);
}
```

---

### Sources

[^1]: [Référence principale]

### Notes liées
- [[00 - Index Schémas]] · [[01 — Architecture du modèle]]
- [L1 déclencheurs] · [L3 émotions] · [Cascades L4] · [Protocoles associés]

---

## CHECKLIST DE COHÉRENCE

- [ ] Chaque expression défensive nomme explicitement le L1 actif et ce qui est menacé
- [ ] Le mécanisme L1→L2 est formulé (pourquoi ce L1 menacé produit cette distorsion précise)
- [ ] Les instances personnelles sont présentes et géolocalisées dans l'espace théorique
- [ ] Les expressions adjacentes prédites par la théorie depuis ces ancres sont documentées
- [ ] Chaque expression est distinguée par son mécanisme précis, pas seulement son nom
- [ ] Le lien entity thinking est explicite dans chaque expression défensive
- [ ] Le lien mastery thinking est explicite dans chaque expression générative
- [ ] Les stratégies Gross sont identifiées et la stratégie prioritaire est nommée
- [ ] La modulation par L0 est documentée (activation normale ET condition dégradée)
- [ ] Le coût de base de l'opération neutre (→L0 intrinsèque) est documenté
- [ ] Le coût métabolique du pôle défensif (L2défensif→L0) est documenté
- [ ] L'effet net du pôle générateur sur L0 (restaurateur ou simplement moins coûteux) est documenté
- [ ] Le renforcement de L1 défensif par répétition (L2défensif→L1) est documenté
- [ ] Le renforcement de L1 générateur par répétition (L2générateur→L1) est documenté
- [ ] La distinction avec les L2 proches est clarifiée
- [ ] Les connexions L0/L1/L3/L4 sont toutes renseignées dans les deux sens
- [ ] Pas de contradiction interne avec les fondements (Barrett, Gross, Dweck, SDT)
