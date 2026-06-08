---
type: pattern_cognitif
tags:
  - pattern
  - confabulation
  - évaluation-causale
  - cognition
L2_neutre: "Évaluation causale"
pôle_mal_être: "Confabulation"
pôle_bien_être: "Analyse fondée"
émotion_véhiculée: "[[La Réactance]]"
date: 2026-06-06
statut: extrait de [[La Réactance]]
---

# ⚙️ Évaluation causale -- Confabulation

> *L'opération est neutre : évaluer les causes avant d'agir. L'appui détermine si l'évaluation précède la décision ou la justifie.*

---

## I. L'opération neutre — Évaluation causale

**Définition :** Mécanisme par lequel le cerveau attribue des causes à une situation pour orienter une décision. Il peut opérer dans l'ordre logique (évaluation → décision) ou dans l'ordre inversé (décision → justification).

**[documenté]** Moukheiber nomme le mécanisme inversé *confabuler* — d'abord utilisé en neurologie pour les patients qui inventent des souvenirs pour combler des lacunes, étendu à la production de justifications rationnelles post-hoc.[^1]

---

## II. Pôle mal-être — Confabulation

> *"Le raisonnement est venu justifier après coup — la décision était déjà prise."*

### Mécanisme biaisé

Le cerveau construit une explication rationnelle *a posteriori* d'une décision déjà activée émotionnellement. L'output est perçu comme une analyse — c'est son invisibilité.

**[documenté]** In-game, la confabulation *"utilise le vocabulaire du jeu"* pour habiller une impulsion émotionnelle. *"Les propriétés de cette main sont pas mal pour reprendre l'initiative"* ressemble à de l'analyse GTO. Mais la décision de jouer a été prise avant le raisonnement. La main n'est pas nécessairement mauvaise — c'est sa *source* qui l'est.

### Les 3 marqueurs — justification vs analyse

**[documenté — Moukheiber × contexte Alexis]**

**Marqueur 1 — La sélectivité**
Une analyse considère toutes les propriétés — pour ET contre. Une justification ne convoque que les propriétés favorables.

**Marqueur 2 — Le sens de la causalité**
Analyse : j'évalue → je décide.
Confabulation : je décide → je trouve des raisons.

**Marqueur 3 — La vitesse et la certitude**
Une vraie analyse génère de l'incertitude. Une justification est rapide et certaine — la conclusion était déjà là avant que le raisonnement commence.

### Manifestation documentée

Bluff-catch → impulsion de reprendre le contrôle → *"les propriétés de cette main sont pas mal pour reprendre l'initiative"* → play depuis la réactance habillé en analyse stratégique.

---

## III. Pôle bien-être — Analyse fondée

> *La même opération dans l'ordre logique : évaluation complète → décision avec incertitude.*

**Mécanisme :** L'évaluation causale bien-être est l'inversion exacte des 3 marqueurs — toutes les propriétés pesées (pour et contre), évaluation qui précède la décision, conclusion arrivant avec de l'incertitude résiduelle.

**Signal :** *"J'ai examiné les propriétés défavorables avec le même poids que les favorables. Je ne suis pas certain. J'ai décidé quand même."*

**[documenté — Alexis]** Question de test : *"Est-ce que je joue ce coup pour optimiser mon EV, ou pour reprendre le contrôle ?"* Si EV → analyse fondée. Si reprendre le contrôle → confabulation.

> [!note] Documentation à compléter
> Les manifestations de l'analyse fondée en session sont à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Confabulation est actif quand...
>
> - Le raisonnement est arrivé vite et avec certitude juste après une sensation
> - On ne convoque que les arguments favorables
> - L'analyse génère peu ou pas d'incertitude
> - On peut répondre "oui" à : *"Si l'adversaire n'avait pas été agressif juste avant, est-ce que cette main m'aurait semblé jouable ?"*
>
> **Question de détection :** *"Est-ce que j'évalue → je décide, ou je décide → je justifie ?"*

---

## V. Protocole d'interruption

> [!tip] In-game — sur la timebank
> 1. Identifier le sens de la causalité : évalue → décide, ou décide → justifie ?
> 2. Appliquer le marqueur de sélectivité : ai-je pesé les propriétés défavorables ?
> 3. Si confabulation détectée : fold par défaut.

> [!tip] Après session
> Repérer les mains où le raisonnement semblait évident et rapide — les examiner en premier dans le feedback.

---

## VI. Suivi en session

> [!note]- 📜 Sessions où ce pattern a été identifié
> ```dataviewjs
> let p = dv.current();
> let targetPattern = p["pôle_mal_être"] || p.file.name;
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const patterns = page.file.lists.pattern;
>         return dv.array(patterns).includes(targetPattern);
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session — tagger avec `[pattern:: Confabulation]`*");
> }
> ```

---

## Sources

[^1]: Albert Moukheiber — Interview × Les Lueurs (2026). Voir [[01 — Albert Moukheiber × Les Lueurs]].

## Notes liées

- [[00 — Index]] · [[La Réactance]] · [[00 — Protocole In-Game]]
