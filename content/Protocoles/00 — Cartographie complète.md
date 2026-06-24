---
type: référence
tags:
  - inner-mapping
  - protocoles
  - cartographie
  - logistique
date: 2026-06-21
---

# 🗺️ Cartographie complète des protocoles

> Référence logistique — organisée par moment d'utilisation.
> Légende : 📍 Emplacement · ⏰ Timing · 💾 Données collectées · 📊 Données affichées

---

## ☀️ Matin

### Observation et ressentis *(première étape MR)*
📍 `Modèles/(modèle) - Observation et ressentis.md` → fichier unique en append
⏰ Matin · avant tout le reste · première étape de la Morning Routine
💾 Entrées dans `Journal/1 — observation et ressentis.md`
📊 Log Morning Routine · Dashboard Mindset

---

### Morning Routine
📍 `Modèles/(modèle) Morning routine.md` → instancié dans `Journal/Morning/`
⏰ Chaque matin — après le scan O&R
💾 Frontmatter : toggles signaux binaires · timeline sélectionnée
📊 Dashboard Mindset

**Toggles signaux** *(binaires — oui/non)* :
`Insomnie · DemiInsomnie · NuitSaccadée · Collapse · Déprime · DayOff · Malade · Blessé · Créatine · Courbatures`
→ Ces toggles ne capturent PAS la largeur de fenêtre — ils signalent qu'une évaluation est nécessaire.

**Comportement conditionnel :**
Si Insomnie · NuitSaccadée · Collapse ou Déprime activé → bloc Drill 02 apparaît avec lien vers le log.
⚠️ L'évaluation réelle de la fenêtre (Large / Réduite / Très réduite) se fait **dans le Drill 02 log**, pas dans la MR.

**Sélecteur Timeline** *(intégré dans la MR — pas des protocoles séparés)* :
`originale⏳ · stratège♟️ · performance🏔️ · friction💢 · préservation🛡️`
→ Quand `friction💢` est sélectionné → bloc "prix à payer de la journée" s'affiche automatiquement.
→ Les 5 fichiers TIMELINE sont les **contenus injectés selon le mode** — pas des protocoles indépendants.

---

### Drill 02 — Rétrospective accumulation *(si signal MR)*
📍 `Protocoles/Transversaux/02 — Drill · L0 Fenêtre d'activation`
📍 Log : `Protocoles/Transversaux/log — Drill 02 — Rétrospective accumulation.md`
📍 Item : `Modèles/(item) Drill 02.md` → inséré dans la MR via Templater
⏰ Matin uniquement · si signal présent dans la MR
💾 Entrée YAML dans le log Drill 02 `{d, frictions, signal, fenetre, action, resultat, emotion}`
→ C'est ici que la largeur de fenêtre est évaluée et stockée : `Large · Réduite · Très réduite`
📊 Log Drill 02 (4 vues) · fiches L3 correspondantes (filtrées par `emotion`)

---

## 🎯 Avant session

### Boussole émotionnelle *(scan pré-session)*
📍 `Journal/00 - Dashboard/🧭 Boussole émotionnelle.md`
⏰ Avant chaque session — point d'entrée systématique
💾 Pas de stockage dédié — outil de lecture
📊 Affiche : état L0 · BIS/BAS · L1 actif · cascades · capital générative

**Oriente vers le bon protocole :**
- L0 rouge/jaune + pas de Drill 02 ce matin → Drill 02
- BIS/BAS → Piédestal → vigilance Drill 03 in-game
- BIS/BAS → Retrait → Drill 01 avant de commencer
- BIS/BAS → Fatigue → envisager de reporter

---

### Protocol Avant session
📍 `Protocoles/Performance/01 — Avant session.md`
⏰ Avant de lancer les tables
💾 Non collecté formellement — checklist de préparation
📊 Non affiché

---

### Warmup
📍 `Modèles/(modèle) - Warmup.md` → instancié avant session
⏰ Avant de lancer les tables
💾 Note individuelle dans `Journal/Session/Warmup/`
📊 Non agrégé

---

## ♟️ In-game

### Protocol In-Game
📍 `L3 - Émotions/00 — Protocole In-Game.md`
⏰ En cours de session · référence rapide
💾 Non collecté — document de référence
📊 Non affiché

---

### Switch Actif *(précipitation naissante)*
📍 `Modèles/(item) Switch Actif.md` → inséré dans le Feedback via Templater
⏰ In-game · dès qu'une précipitation ou reconvocation est nécessaire
💾 Stocké dans le Feedback de la session (item Templater)
📊 Feedback de la session

---

### Protocole Lucidité
📍 `Modèles/(1). Item - Protocole Lucidité.md` → inséré dans le Feedback via Templater
⏰ In-game · activation manuelle si nécessaire
💾 Stocké dans le Feedback de la session
📊 Feedback de la session

---

### Drill 03 — Interrupt escalade *(in-game ou IRL)*
📍 `Protocoles/Transversaux/03 — Drill · L3 Colère froide — Interrupt escalade`
📍 Log : `Protocoles/Transversaux/log — Drill 03 — Interrupt escalade.md`
⏰ Dès détection du signal d'escalade (stade 1 = respiration · stade 2 = colère · stade 3 = dissociation)
💾 Entrée YAML dans le log Drill 03 `{d, contexte, stade, signal_somatique, ancre, action_contextuelle, resultat}`
📊 Log Drill 03 · fiche `Colère IRL.md` · fiche `La Réactance.md`

---

## 📋 Post-session

### Feedback
📍 `Modèles/(modèle) - Feedback.md` → instancié dans `Journal/Session/Feedback/2026/`
⏰ Immédiatement après la session
💾 Tags `[emotion:: X]` · `[protocoles_utilisés:: X]` · items Switch Actif · items Lucidité
📊 Fiches L3 (déclencheurs · pensées · réactions · plans d'action) · Boussole §5 Capital générative

**Champs clés :**
- `protocoles_utilisés` → trace quels protocoles ont été activés pendant la session
- `[emotion:: X]` → alimente automatiquement les DataviewJS des fiches L3
- Items Templater (Switch Actif · Lucidité) → détail de l'exécution in-game

---

### Checkup Métriques
📍 `Modèles/(2). Item - Checkup Métriques.md` → inséré dans le Feedback
⏰ Post-session · optionnel selon le contexte
💾 Dans le Feedback de la session
📊 Non agrégé séparément

---

### Protocol Post-session
📍 `Protocoles/Performance/03 — Post-session.md`
⏰ Après le Feedback · clôture formelle
💾 Non collecté — checklist de clôture
📊 Non affiché

---

## 🌍 IRL — Transversaux (hors session)

### Drill 01 — Contrôle secondaire
📍 `Protocoles/Transversaux/01 — Drill · L1 Besoin de contrôle — Contrôle secondaire`
📍 Log : `Protocoles/Transversaux/log — Drill 01 — Contrôle secondaire.md`
⏰ IRL · 3 modes : baseline quotidien · anticipatoire · post-situationnel
💾 Entrée YAML dans le log Drill 01 `{d, mode, situation, controle, l1_touche, acceptation, levier, resultat}`
📊 Log Drill 01 (bibliothèque des acceptations) · fiche `Impuissance.md`

---

### Drill 04 — Bid for connection rejetée
📍 `Protocoles/Transversaux/04 — Drill · L1 Appartenance — Bid for connection rejetée`
📍 Log : `Protocoles/Transversaux/log — Drill 04 — Bid for connection rejetée.md`
⏰ IRL · dès qu'une bid for connection est refusée ou ignorée
💾 Entrée YAML dans le log Drill 04 `{d, relation, forme, phase_atteinte, escalade, resultat}`
📊 Log Drill 04 (phases atteintes) · fiche `Délaissement.md`

---

---

### Prix à payer *(anticipatoire)*
📍 `Modèles/(modèle) - Prix à payer.md`
⏰ Anticipatoire · avant une journée chargée ou après identification d'un domaine hors contrôle
💾 Dans le fichier du jour ou dans le Drill 01 (mode anticipatoire)
📊 Drill 01 log si formalisé en YAML · sinon non agrégé

---

## 📅 Hebdomadaire

### Débriefing performance
📍 `Modèles/(modèle) Débriefing performance (Semaine N).md`
⏰ Fin de semaine
💾 Note hebdomadaire dans `Journal/Semaine/`
📊 Non agrégé

---

## 🧠 Coaching Alexis

### Dépolarisation
📍 `Modèles/(modèle) Dépolarisation - Sujet.md`
⏰ En session avec Alexis
💾 Note dans `Mindset/Alexis/dépolarisation/`
📊 Boussole §6 (historique des dépolarisations)

### Mini-Dépolarisation
📍 `Modèles/(modèle) Mini-Dépolarisation.md`
⏰ Entre sessions · exercice autonome
💾 Note dans `Mindset/Alexis/dépolarisation/`
📊 Boussole §6

---

## ⚠️ Redondances & Éléments à clarifier

### ✅ Clarification — Les 5 TIMELINES ne sont pas redondantes

`PRÉSERVATION · PERFORMANCE · STRATÈGE · FRICTION · ORIGINALE`
Ce sont des **contenus injectés dans la MR** selon le mode sélectionné via le sélecteur intégré — pas des protocoles indépendants. Le sélecteur est dans la MR (`INPUT[inlineSelect...]`), et chaque timeline est un template de contenu pour la journée. Toutes les 5 sont utiles selon le contexte.

**`Prix à payer`** vs **`Drill 01 mode anticipatoire`**
Les deux formalisent l'acceptation de ce qui est hors contrôle avant que ça arrive. Prix à payer = format Alexis (liste narrative). Drill 01 mode 2 = format structuré avec champs YAML. Si le log Drill 01 est bien en place, le modèle Prix à payer perd de son utilité comme point de collecte.

### 🟡 Éléments à clarifier

**`(Date) Process Rebuild ma confiance et injecter de la clarté.md`**
Semble être un document ponctuel spécifique, pas un protocole récurrent. À archiver ou supprimer si obsolète.

**`(modèle) - émotion.md`**
Unclear — est-ce que ce modèle sert encore à créer de nouvelles fiches L3 ? Si oui, il est utile. Si les fiches L3 sont considérées comme terminées, il est obsolète.

**`(4) Item-AjouterSession.md`**
Item Templater inséré dans le Feedback quand plusieurs sessions sont jouées dans la même journée. Ajoute un bloc supplémentaire : durée · sens · auto-évaluation. Pas une redondance — un complément au Feedback pour les journées multi-sessions.

**`⏳ TIMELINE ORIGINALE.md`**
Si c'est la version de référence dont toutes les autres dérivent, à conserver. Sinon à archiver.

---

## 🔗 Vue d'ensemble — flux par moment

```
MATIN
  O&R (Observation et ressentis) → Log MR + Dashboard Mindset
  Morning Routine
  └── si signal → Drill 02 (log Drill 02)

AVANT SESSION
  Boussole émotionnelle → oriente vers le protocole adapté
  └── Retrait → Drill 01 (log Drill 01)
  └── Piédestal → vigilance Drill 03
  └── Stratège → Warmup → Protocol Avant session

IN-GAME
  Switch Actif (Feedback) · Protocole Lucidité (Feedback)
  └── Escalade → Drill 03 (log Drill 03)

POST-SESSION
  Feedback (emotion + protocoles_utilisés + items)
  └── Checkup Métriques (optionnel)
  Protocol Post-session

IRL
  Drill 01 (log Drill 01)
  Drill 04 (log Drill 04)
  O&R

HEBDO
  Débriefing performance

ALEXIS
  Dépolarisation · Mini-Dépolarisation
```

---

## Notes liées
- [[🧠 Inner Mapping/Protocoles/00 — Vue d'ensemble]]
- [[Journal/00 - Dashboard/🧭 Boussole émotionnelle]]
- [[🔧 Carte des protocoles]]
