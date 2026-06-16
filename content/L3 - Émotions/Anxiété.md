---
type: fiche_emotion_index
tags:
  - anxiété
  - émotions
  - index
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

# 🧠 Anxiété — Index

> [!abstract] Qu'est-ce que l'anxiété
>
> L'anxiété est une émotion orientée vers l'**avenir** : elle anticipe une menace, réelle ou imaginée. Contrairement à la peur (réponse à un danger présent), l'anxiété est une réponse à une **possibilité** — quelque chose qui pourrait arriver, qui pourrait être vrai, que quelqu'un pourrait penser.
>
> Elle se distingue du stress (réponse à une surcharge) et de l'inquiétude (pensée répétitive sur un problème spécifique) par son objet : l'évaluation anticipée, l'image projetée, le contrôle sur quelque chose d'incertain.

> [!abstract] Formes documentées dans ce vault
>
> | Forme | Objet | Fiche |
> |---|---|---|
> | **Anxiété d'évaluation** | Être jugé/évalué par un observateur compétent | [[Anxiété d'évaluation]] |
>
> *D'autres formes seront ajoutées à mesure qu'elles émergent de l'expérience — pas avant.*

---

## 📊 Vue d'ensemble — toutes les anxiétés documentées

> [!note]- Sessions liées à une forme d'anxiété (auto)
> ```dataviewjs
> let sessions = dv.pages('"Journal/Session/Feedback/2026"')
>     .where(page => {
>         const emotions = page.file.lists.emotion;
>         return dv.array(emotions).some(e => 
>             typeof e === 'string' && e.toLowerCase().includes('anxi')
>         );
>     });
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```

---

## 🔗 Notes liées

- [[Dissociation]] — pattern cognitif qui véhicule souvent l'anxiété d'évaluation
- [[Être et Faire — Réconciliation Moukheiber × Alexis]]
- [[00 — Protocole In-Game]]
