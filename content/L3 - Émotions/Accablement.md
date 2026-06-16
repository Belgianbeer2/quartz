---
type: emotion
tags:
  - L3
  - hypoactivation
  - accablement
  - inner-mapping
date: 2026-06-15
statut: documenté
BIS_BAS: "BAS- / BIS-"
émotions_composantes: "[[Impuissance]] · [[Culpabilité]]"
---
```dataviewjs
const log = dv.page("log — Drill 02 — Rétrospective accumulation");
const nomFiche = dv.current().file.name;

if (!log || !log.entries) {
    dv.paragraph("*Aucune donnée Drill 02.*");
} else {
    const relevant = log.entries.filter(e => e.emotion === nomFiche);
    if (relevant.length === 0) {
        dv.paragraph("*Aucune activation Drill 02 liée à cette émotion pour l'instant.*");
    } else {
        const fenetreColor = (f) => {
            if (!f) return "#555";
            if (String(f).includes("Très")) return "#e74c3c";
            if (String(f).includes("Réduite")) return "#FF9500";
            return "#2ecc71";
        };
        let html = "";
        relevant.sort((a, b) =>
            moment(b.d, "MM-DD-YYYY").valueOf() - moment(a.d, "MM-DD-YYYY").valueOf()
        ).forEach(e => {
            const f = String(e.fenetre || "").trim();
            const signaux = e.signal ? String(e.signal).split("·").map(s => s.trim()).filter(s => s) : [];
            html += `<div style="border-left:3px solid ${fenetreColor(f)};padding:8px 12px;margin-bottom:8px;background:rgba(255,255,255,0.02);border-radius:0 4px 4px 0;">
                <div style="display:flex;justify-content:space-between;margin-bottom:6px;">
                    <span style="color:#6edff6;font-size:12px;font-weight:bold;">${e.d || "—"}</span>
                    <span style="color:${fenetreColor(f)};font-size:11px;">Fenêtre ${f || "—"}</span>
                </div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Frictions : <span style="color:#ccc;">${e.frictions || "—"}</span></div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Signaux : <span style="color:#BB86FC;">${signaux.join(" · ") || "—"}</span></div>
                <div style="font-size:11px;color:#888;margin-bottom:3px;">Action : <span style="color:#ccc;">${e.action || "—"}</span></div>
                <div style="font-size:11px;color:#888;">Résultat : <span style="color:#aaa;">${e.resultat || "—"}</span></div>
            </div>`;
        });
        dv.paragraph(`*${relevant.length} activation(s) Drill 02 liée(s)*`);
        dv.container.createEl("div").innerHTML = html;
    }
}
```

# 😞 Accablement

> [!info] Une phase, pas un instant
> Les fiches L3 existantes documentent des émotions ponctuelles — des réactions à un événement identifiable. L'Accablement est différent : c'est la **texture affective d'une phase d'hypoactivation prolongée** ([[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]). Pas une réaction à un événement précis — un état qui envahit L1 à L4 pendant que le système récupère.

---

## I. Signature motivationnelle — BAS-/BIS-

> [!abstract] ✅ Voir [[05 — BIS & BAS]] §II
> L'Accablement partage la signature motivationnelle de l'**Apathie** : faible réactivité aux signaux de récompense ET de menace simultanément. Ni les opportunités ni les risques ne mobilisent — pas par choix, mais parce que le système (L0) est en mode récupération active (*sickness behavior*, [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]] §III.2).

Ce qui distingue l'Accablement de l'Apathie générique : l'Apathie peut être un état de fond stable. L'Accablement est **consécutif** à une sortie de fenêtre récente (hyperactivation → bascule) — il a une histoire immédiate, même si, dans l'instant, il n'y a pas de déclencheur identifiable.

---

## II. Signature affective — Impuissance ET Culpabilité, pas l'une ou l'autre

> [!abstract] ✅ Voir [[06 — Contrôle perçu & régulation émotionnelle]] §I, §VI
> Deux émotions au profil d'évaluation distinct (fiche 06) **coexistent ou alternent** plutôt que de se substituer :
>
> - **Impuissance** — contrôle situationnel absent ("rien à faire")
> - **Culpabilité** — contrôle self/autre tourné vers soi, orientation passée ("je devrais pourtant pouvoir")

C'est cette coexistence qui distingue l'Accablement d'une Impuissance "simple" (L3 isolé, réaction à un événement précis). Dans l'Accablement, les deux alternent souvent dans la même heure — *"rien à faire"* puis *"je devrais y arriver"* puis retour à *"rien à faire"* — sans qu'aucune des deux ne se stabilise.

---

## III. Pourquoi le recadrage a une portée réduite ici

> [!warning] Ce n'est pas un manque d'effort
> [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]] §III.1 (Arnsten) : le PFC est moins disponible pendant l'hypoactivation, pas seulement pendant l'hyperactivation. Or les deux recadrages documentés en [[06 — Contrôle perçu & régulation émotionnelle]] §VI — changement de portée (Impuissance) et changement de temporalité (Culpabilité) — sont des opérations de *changement cognitif* (Gross #4), qui demandent précisément les ressources PFC les plus réduites à ce moment.
>
> Ce n'est donc pas "je n'arrive pas à recadrer parce que je ne fais pas assez d'effort". C'est : le mécanisme de recadrage lui-même est temporairement moins accessible. Vouloir l'appliquer quand même peut ajouter une couche de Culpabilité supplémentaire ("même ça je n'y arrive pas") — auto-entretenant l'Accablement.

**Implication pratique directe :** pendant l'Accablement, les protocoles pertinents ne sont pas les drills de recadrage (Protocole Lucidité, Contrôle secondaire en mode actif) — ce sont les protocoles L0 : repos sans culpabilité, behavioral activation minimal, lumière, micro-contact social à faible coût. Le recadrage redevient accessible **après**, quand le budget L0 est partiellement restauré — pas pendant.

---

## IV. Cas documenté

> [!example] 🔍 11-13/06/2026
> Trois jours suivant un collapse (colère noire déclenchée par un concept entraîné par répétition, cf. [[04 — Voie rapide & voie lente — au-delà de Pensée → Corps → Émotions]]). Signature complète : *"envie de rien, juste dormir"* (Apathie/BAS bas) · *"tout m'énerve, quart de tour"* (BIS encore réactif par moments, pas un pur BAS-/BIS- stable) · *"je ne suis pas encore sorti de mes schémas défensifs"* · idéations tournées vers le pire (rupture, isolement — Impuissance projetée) · tentative de SPA sans capacité d'engagement, *"les bains m'énervent, je n'ai pas la patience"* (Culpabilité implicite face à sa propre incapacité à se détendre).
>
> Aucun drill de recadrage n'a été tenté pendant cette phase — le repos (sommeil répété, arrêt caféine) a précédé tout travail cognitif, qui n'a commencé que le 14/06, après le premier signe de bascule.
>
> → [[Synthèse — Collapse du 10-06 et direction Inner Mapping]]

---

## V. Distinction avec les fiches voisines

| Fiche | Portée | Déclencheur |
|---|---|---|
| [[Impuissance]] | Ponctuelle, L3 isolé | Un événement identifiable |
| [[Culpabilité]] | Ponctuelle, L3 isolé | Un événement identifiable |
| **Accablement** | Phase, L1-L4 envahis | Sortie de fenêtre récente — pas un événement, une bascule |
| Apathie (fiche 05 §II) | Signature motivationnelle | Description BAS/BIS, sans la couleur affective |

---

## VI. Ce qui reste à approfondir

- [ ] Proxy observable pour détecter la transition Impuissance ponctuelle → Accablement (durée ? nombre de domaines touchés ?)
- [ ] Le Drill 02 (rétrospective accumulation) est conçu pour détecter *avant* la bascule — est-ce qu'une version adaptée pourrait aussi aider à détecter la *sortie* de l'Accablement (signal de "recadrage redevient possible") ?
- [ ] État "acceptation/sérénité" (fiche 06 §VI.1) comme possible signal de sortie — à observer

---

## Notes liées
- [[L0 — Physiologie & Budget Corporel/04 — Fenêtre d'activation]]
- [[05 — BIS & BAS]] §II
- [[06 — Contrôle perçu & régulation émotionnelle]] §I, §VI
- [[04 — Voie rapide & voie lente — au-delà de Pensée → Corps → Émotions]]
- [[Synthèse — Collapse du 10-06 et direction Inner Mapping]]
- [[Protocoles/Transversaux/02 — Drill · L0 Fenêtre d'activation — Rétrospective accumulation]]
