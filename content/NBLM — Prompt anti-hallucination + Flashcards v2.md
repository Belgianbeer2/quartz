---
type: référence_nblm
tags: [inner-mapping, notebooklm, phase-2]
date: 2026-06-26
---

# 🧠 NotebookLM — Prompts Phase 2

---

## Prompt d'initialisation — À coller au début de chaque NBLM

> Coller ce prompt dans la première conversation de chaque nouveau notebook.

```
Tu es un assistant d'étude spécialisé dans le système Inner Mapping de Pierre.

RÈGLE ABSOLUE : tu ne réponds qu'à partir des documents que je t'ai fournis. Si une notion ne figure pas dans mes documents, dis-le explicitement plutôt que d'inférer depuis tes données d'entraînement.

Contexte :
- Inner Mapping est un système de cartographie psychologique personnel en 5 niveaux : L0 (physiologie), L1 (besoins profonds), L2 (schémas cognitifs), L3 (émotions), L4 (comportements).
- Le vocabulaire est précis et non-standard : "Fenêtre d'activation", "BIS/BAS", "Starbursting vs Scattering", "Reappraisal", etc. Utilise exactement ces termes — ne les traduis pas ou ne les reformule pas en termes génériques.
- Quand tu n'es pas certain qu'une information vient des documents fournis, signale-le avec [inféré] ou [non documenté].

Format de réponse par défaut :
1. Mécanisme (complet — sans limite de longueur)
2. Ce que ça change concrètement (1-2 exemples concrets du contexte poker/IRL)
```

---

## Prompt — Session d'étude profonde (fiches théoriques J5-J9)

> Pour les 5 fiches théoriques. Remplacer [NOM DE LA FICHE] par le nom exact.

```
Fiche étudiée : [NOM DE LA FICHE]

Étape 1 — Explication du mécanisme
Explique-moi le mécanisme de cette fiche en utilisant uniquement les documents fournis. Couvre tous les points importants — ne compresse pas. Pour chaque point traité, illustre avec 1 exemple concret (IRL à Siem Reap OU session poker) — l'exemple s'intègre dans l'explication, pas en annexe.

Étape 2 — Test
Pose-moi 3 questions pour vérifier que j'ai compris le mécanisme. Les questions doivent porter sur le mécanisme, pas sur des détails de vocabulaire.
```

---

## Prompt — Génération de flashcards (NBLM centralisé J10-J11)

> Pour le notebook centralisé avec le document de définitions L0-L3.

```
À partir du document de définitions que je t'ai fourni, génère des flashcards au format suivant :

FACE AVANT : [Terme]
FACE ARRIÈRE : [Définition en 1-2 phrases — mécanisme + ce que ça change]

Contraintes :
- Utilise exactement les termes du document, sans reformulation
- La face arrière doit permettre de reconnaître le terme dans une situation réelle, pas juste de le définir abstraitement
- Commence par les L0, puis L1, puis L2, puis L3
- Génère d'abord les 10 premières — je te demanderai la suite
```

---

## Document de définitions — À importer dans le NBLM centralisé

> Ce document est la source unique pour le NBLM de flashcards (J10-J11).
> Ne pas utiliser pour les NBLM thématiques profonds — trop condensé.

---

### L0 — Physiologie & Budget Corporel

**Fenêtre d'activation**
Zone de tolérance physiologique optimale entre hypo et hyperactivation. En dehors de cette zone, les capacités cognitives (PFC) sont réduites — le recadrage devient moins accessible, les décisions moins fiables.

**Intéroception**
Capacité à percevoir les signaux corporels internes (rythme cardiaque, tension musculaire, respiration). C'est le premier point de détection des émotions — avant le nommage cognitif.

**Co-régulation sociale**
Restauration du budget L0 via la présence d'une autre personne. Contact social même passif (présence de Sassa) réduit l'activation du système de stress. Signal : l'isolement prolongé dégrade L0.

---

### L1 — Structures Profondes (Besoins)

**Besoin de Compétence**
Besoin d'efficacité et de maîtrise perçue. Mode générateur : curiosité, plaisir du défi. Mode défensif (Intransigeance) : l'erreur devient une menace identitaire plutôt qu'une information.

**Besoin d'Autonomie**
Besoin de contrôle sur ses propres décisions et actions. Déclenche la Réactance quand une liberté d'action est perçue comme menacée. Mode générateur : jouer depuis ses propres convictions.

**Besoin d'Appartenance**
Besoin de connexion et de place dans un groupe. Déclenche le Délaissement quand des bids for connection répétés sont refusés ou ignorés. Particulièrement actif à distance (Cambodge/Europe).

**Besoin de Contrôle**
Besoin de levier sur les événements. Déclenche l'Impuissance quand le levier est absent (variance, tiers). Distinct de l'Autonomie : contrôle sur les résultats vs contrôle sur les décisions.

**Prémisses éthiques**
Standards moraux préchargés (liberté, justice, autodétermination). Déclenchent la Colère IRL via BIS éthique quand une valeur est violée — indépendamment du BAS.

---

### L2 — Schémas Cognitifs (pôle défensif)

**Dissociation**
Projection dans la tête d'un observateur — construire ce qu'il pense plutôt que traiter la situation réelle. Véhicule cognitif de l'Anxiété d'évaluation. Signal : décisions orientées vers une image projetée.

**Confabulation**
Justification a posteriori d'une décision déjà prise émotionnellement. 3 marqueurs : sélectivité des arguments, causalité inversée (décision → raisonnement), certitude rapide. Véhicule de la Réactance.

**Sélectivité mémorielle**
Reconstruction biaisée des événements passés selon l'état émotionnel présent. Sous Peur : ne retient que les pertes. Sous Honte : efface les moments du Stratège.

**Vision zoomée**
Fenêtre temporelle trop courte appliquée à l'évaluation. 3-5 sessions = "tendance". Produit la Peur des résultats et des conclusions non fondées sur le niveau.

**Pensée binaire**
Évaluation en tout-ou-rien — bon/mauvais, compétent/incompétent. Produit le verdict identitaire dans la Honte. Absence de graduations entre les pôles.

**Piédestal**
Surévaluation de l'enjeu d'un événement ou d'un état. "Cette session est unique, je ne peux pas la rater." Transforme la Plénitude en pression et la Certitude en fragilité.

**Suranticipation**
Projection excessive dans le futur — imaginer les conséquences en cascade avant qu'elles existent. Produit l'Anxiété et amplifie l'Impuissance.

**Scattering**
Dispersion attentionnelle défensive — activation simultanée de trop de fronts pour éviter de s'engager sur l'un d'eux. Signal : procrastination productive, sur-ingénierie.

**Auto-flagellation**
Application d'un jugement sévère sur soi après une erreur plutôt qu'un encodage neutre. Renforce la Honte en boucle. Opposé fonctionnel : Self-compassion (Neff).

**Rumination**
Répétition mentale d'un événement passé sans résolution. Distingue de l'analyse : la rumination tourne en boucle sans nouvelle information produite.

**Suramplification**
Mobilisation compensatoire excessive — engagement maximal défensif pour compenser un manque perçu. Épuise L0 rapidement.

---

### L3 — Émotions (mécanisme + BIS/BAS + action tendency)

**Agacement**
BIS léger sur un irritant externe répété, BAS neutre. Action tendency : éviter/retirer l'irritant. Double lecture : standalone (irritant réel) ou signal L0 (seuil de tolérance effondré = "quart de tour").

**Frustration**
BAS actif bloqué par un obstacle externe, BIS neutre. Action tendency : chercher un autre passage. "Le bol qui se remplit" — signal précoce avant la Colère. Clé : nommer avant que le bol déborde.

**Colère**
BAS frustré intensifié + BIS réactif. Action tendency : reprendre le contrôle, agir contre l'obstacle. Transformable (niveau 3 Alexis) : redirection du contrôle perçu → Détermination.

**Réactance**
BAS très actif + obstacle perçu comme menace sur la liberté d'action. Action tendency : agir dans la direction bloquée avec intensité supérieure. Distingué de la stratégie par 3 marqueurs de confabulation.

**Peur**
BIS très élevé, BAS bas. Action tendency : retrait, évitement. Double circuit LeDoux : low road (viscéral, 12ms) et high road (construit par L2). Objet financier/identitaire : distinct de la Honte.

**Honte**
BIS très élevé, BAS bas. Action tendency : se cacher, paralysie. Objet : "je SUIS défaillant" (identité). Distinct de la Culpabilité ("j'AI fait quelque chose de mal"). Carburant : entity thinking.

**Culpabilité**
BIS actif, BAS orienté vers la réparation. Action tendency : corriger le comportement, fermer la boucle. Résolvable contrairement à la Honte — l'action répare.

**Impuissance**
BAS bas (absence de levier), BIS neutre-bas. Action tendency : discours compensatoire (narratif) ou retrait. Souvent sous-jacente à la Réactance et à la Colère IRL.

**Accablement**
BAS très bas, BIS très bas (récupération active). Texture affective d'une phase post-épuisement. Le recadrage n'est pas accessible — protocoles L0 uniquement. Signal de sortie : Sérénité ou Curiosité légère.

**Délaissement**
BIS actif (connexion refusée = menace sociale), BAS bas. Action tendency : retrait, questionnement relationnel. Déclencheur type : le "vu" sans réponse. Non-intentionnel dans la majorité des cas.

**Anxiété d'évaluation**
BIS actif, BAS neutre. Action tendency : jeu d'image, décisions EV-dégradées. Objet : être jugé par un pair compétent. Véhicule cognitif : Dissociation. Régulation : question de réalité.

**Plénitude**
BAS actif, BIS bas. Action tendency : jouer depuis soi, fold facile, lâcher prise. État à documenter (comportements, pas l'état lui-même) — base des reconvocations futures du Stratège.

**Sérénité**
BAS légèrement bas, BIS bas. Arousal très basse positive. Signal de sortie de l'Accablement. Distinct de la Plénitude : moins active, plus contemplative.

---

## Notes d'utilisation

**1 NBLM par fiche théorique (J5-J9)**
Import : la fiche étudiée + les fiches fondements qu'elle cite + les fiches L1/L2/L3 liées.
Ne pas importer l'intégralité du vault — ça dilue la précision.

**1 NBLM centralisé pour les flashcards (J10-J11)**
Import : ce document uniquement.
Prompt : générer des flashcards par groupe de 10, commencer par L0 puis descendre.

---

## Prompt — Génération de synthèse de référence

> Coller ce prompt dans le NBLM thématique de la fiche concernée.
> La synthèse générée devient la **référence d'évaluation** — Pierre l'étudie, puis la restitue de mémoire avec ses propres mots.

```
Génère une synthèse complète de la fiche [NOM DE LA FICHE].

Règles :
- Reprends tous les titres et sous-titres importants de la fiche — aucune omission sur les sections significatives
- Pour chaque section, développe le contenu fidèlement au document fourni, sans le compresser artificiellement
- Pour chaque section, ajoute 1 exemple concret (IRL à Siem Reap OU session poker) illustrant le point traité — l'exemple fait partie de la section, pas en annexe
- Utilise exactement le vocabulaire Inner Mapping (BIS/BAS, L0/L1/L2/L3, noms des schémas, noms des stratégies Gross)
- Aucune information en dehors des documents fournis — si tu inféres, signale-le avec [inféré]

Cette synthèse est une référence d'évaluation. Pierre devra la restituer de mémoire avec ses propres mots. La complétude prime sur la concision.
```

---

## Protocole d'évaluation — J12

> Pierre envoie ses 5 restitutions à Claude.
> Claude évalue chaque restitution par rapport à la synthèse de référence NBLM.

### Grille par fiche

| Critère | Points | Détail |
|---|---|---|
| **Titres présents** | 1 pt / titre | Chaque titre de section de la synthèse est présent ou clairement évoqué |
| **Contenu complet** | 2 pts / section | 2 = complet · 1 = partiel (idée présente mais incomplète) · 0 = absent |
| **Exemple par section** | 1 pt / section | 1 exemple concret (IRL OU poker) intégré dans chaque section · 0 si absent |

**Score max** = (N titres × 1) + (N sections × 2) + (N sections × 1) = 4N points
**Seuil de réussite** = 75% du score max
