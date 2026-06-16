---
type: pattern_cognitif
tags:
  - pattern
  - mentalisation
  - dissociation
  - cognition
L2_neutre: "Mentalisation"
pôle_mal_être: "Dissociation"
pôle_bien_être: "Empathie · connexion réelle"
émotion_véhiculée: "[[Anxiété d'évaluation]]"
date: 2026-06-06
statut: en cours
---

# ⚙️ Mentalisation -- Dissociation

> *L'opération est neutre. L'appui L1 détermine si elle produit de la connexion ou de la surveillance.*

---

## I. L'opération neutre — Mentalisation

**Définition :** Capacité à modéliser les états mentaux d'autrui — ses intentions, émotions, pensées, perspectives. Mécanisme cognitif fondamental de la vie sociale, actif en continu dans les interactions et même en l'absence d'interlocuteur réel.

**[documenté]** Fonagy désigne ce processus comme la *theory of mind* — la capacité à traiter autrui comme un agent avec des états internes distincts des siens.[^1]

**[documenté]** Moukheiber affirme que l'identité se construit par l'action sociale répétée. *"On n'est pas des êtres personnels — on est des êtres sociaux."* La mentalisation est le moteur de cette construction.[^2]

**Pourquoi c'est l'état par défaut :** Quand le cortex préfrontal est épuisé, le cerveau bascule dans le Default Mode Network — le terreau naturel de la pensée autoréférentielle et de la modélisation d'autrui.[^2]

---

## II. Pôle mal-être — Dissociation

> *"Je me projette dans la tête des autres en continu, et j'y projette mon propre jugement sur moi-même."*

### Mécanisme biaisé

La dissociation est la mentalisation sous appui Peur : sans interlocuteur réel, le cerveau invente un autrui et lui prête son propre jugement négatif sur soi. On se juge soi-même déguisé en observateur extérieur.

**[inféré]** La dissociation est structurellement incompatible avec le principe *"être avant d'agir"* — on ne peut pas construire son identité depuis un regard imaginé. Les deux directions sont opposées : l'une de l'intérieur vers l'extérieur, l'autre de l'extérieur imaginé vers l'intérieur.

**[observation personnelle — 04-06-2026]** *"J'ai presque envie de dire que c'est un état d'être par défaut inné en moi."* Le Stratège n'est pas l'état naturel — c'est un état construit. La dissociation est ce qui précède ou suit cet effort.

### Conditions d'activation

- Fatigue physique ou mentale
- Baisse des gardes cognitives
- Faible engagement dans une tâche précise
- **Présence d'un observateur perçu comme compétent** — le déclencheur spécifique : pas n'importe quel regard, un regard qualifié pour évaluer

### Manifestations documentées

**L'observateur fantasmé — structure commune**
Dans toutes les manifestations, l'observateur qui déclenche le pattern **n'est probablement pas en train d'observer**. C'est la signature centrale.

**Manifestation 1 — Le reg identifié comme "source de danger"** *(in-game)*
Reg compétent identifié → étiquette "source de danger" → projection dans sa tête *avant* toute main jouée. Online, le reg joue plusieurs tables en parallèle — la probabilité qu'il ait traité une main spécifique est quasi nulle. On s'ajuste contre sa propre auto-critique déguisée en regard adverse.

**Manifestation 2 — Le reg spectateur d'un pot** *(in-game)*
Play créatif contre un autre joueur — projection que le reg, depuis sa position de spectateur, a vu et en a tiré des conclusions. Observateur fantasmé à 100% — aucun déclencheur relationnel réel.

**Manifestation 3 — Le scooter à Siem Reap** *(IRL)*
Touristes perçus comme observateurs → conduire plus vite pour montrer ce dont on est capable. Structure identique aux cas in-game.

---

## III. Pôle bien-être — Empathie · connexion réelle

> *La même opération, sous appui Confiance : modéliser l'autre pour se connecter, pas pour se juger.*

**Mécanisme :** La mentalisation sous appui Confiance oriente le traitement vers l'autre réel — ses besoins, sa perspective, ce qu'il ressent. Elle produit de l'empathie et de la connexion authentique, pas de la surveillance imaginée.

**In-game :** Modéliser le range adverse depuis des données objectives (actions, timing, sizing) pour prendre une décision fondée — pas depuis un jugement imaginé sur ce qu'il pense de toi.

**IRL :** Connexion documentée dans [[Plénitude IRL]] — *"se connecter en empathie avec une personne qui partage ses vulnérabilités"* — c'est la mentalisation bien-être en action.

> [!note] Documentation à compléter
> Les conditions d'activation et les manifestations du pôle bien-être sont à documenter par l'expérience.

---

## IV. Signaux de détection

> [!warning] Le pattern Dissociation est actif quand...
>
> - Tu modélises ce qu'un adversaire pense de toi *pendant* une main plutôt qu'après
> - Tu ajustes ta stratégie *avant* d'avoir joué contre quelqu'un
> - Tu imagines être observé dans un pot où l'adversaire que tu surveilles n'est pas impliqué
> - Tu agis pour une image projetée plutôt que depuis ton propre jeu
>
> **Question de détection :** *"Est-ce que je joue ce coup depuis moi — ou pour l'image que je projette ?"*

---

## V. Protocole d'interruption

> [!tip] In-game
> - **Question de réalité :** est-il dans ce pot ? Si non → observateur fantasmé à 100%. Si oui → combien de tables joue-t-il ? Si plus de 4 → il n'a probablement pas traité cette main.
> - **Nommer** : *"dissociation"* — puis revenir à la main devant soi.

> [!tip] Avant session — warmup
> - Ancrage corporel avant de poser les intentions : sensation physique concrète (pieds au sol, respiration abdominale).
> - Si dissociation détectée pendant le warmup : différer le lancement des tables.

> [!tip] Hors session
> - Engagement dans une tâche à concentration requise (sport, lecture, conversation réelle) pour sortir du DMN.

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
>     dv.paragraph("*Aucune session — tagger avec `[pattern:: Dissociation]`*");
> }
> ```

---

## Sources

[^1]: Fonagy, P. & Bateman, A. (2006). *Mentalization-based Treatment*. Oxford University Press.
[^2]: Albert Moukheiber — Interview × Les Lueurs (2026). Voir [[01 — Albert Moukheiber × Les Lueurs]].

## Notes liées

- [[Index]] · [[Anxiété d'évaluation]] · [[Plénitude IRL]] · [[00 — Protocole In-Game]]
