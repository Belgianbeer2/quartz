----
type: fiche_emotion 
---
# 🧠 Fiche d'exploration : Plénitude IRL

> [!note]- 📜 Voir les sessions liées à cette émotion
> *Cliquez sur une session pour ouvrir le feedback correspondant.*
> ```dataviewjs
> let p = dv.current();
> let targetEmotion = p.file.name;
> 
> let sessions = dv.pages('"Journal/Session/2. Feedback/2026"')
>     .where(page => {
>         const emotionsDansSession = page.file.lists.emotion;
>         return dv.array(emotionsDansSession).includes(targetEmotion);
>     });
> 
> if (sessions.length > 0) {
>     dv.list(sessions.sort(s => s.file.name, 'desc').file.link);
> } else {
>     dv.paragraph("*Aucune session identifiée pour le moment.*");
> }
> ```


## 🔬 0. Comprendre l'émotion

> [!abstract] Ce que Moukheiber éclaire
> La plénitude IRL (se sentir utile pour quelqu'un d'important, connexion empathique sur les vulnérabilités) et la plénitude in-game ont des sources différentes — mais un signal commun : **présence totale + absence de résistance**. Le cerveau n'est pas en train de prouver quelque chose ni de combattre quelque chose.
>
> Le prix à payer documenté (*"sortir de cette bulle vient souvent avec une frustration"*) est normal et prévisible : retour mécanique à la baseline. Ce n'est pas un signe que la plénitude était fausse — c'est de la biologie.

> [!abstract] Ce que Alexis pointe
> La plénitude IRL nourrit la plénitude in-game. La connexion empathique, le sentiment d'utilité — ces états construisent **l'être** en dehors de la table. Ce que le Stratège est dans la vie se transfère à la table : un homme qui se sent utile et connecté joue depuis une identité pleine, pas depuis un vide à combler par la performance.
>
> L'entretenir demande une discipline sur l'exposition au stress — comme documenté dans les prix à payer. Ce n'est pas de la fragilité : c'est reconnaître que cet état a des conditions d'existence.
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Plénitude*

---

## 📊 1. Patterns de l'émotion

> [!example] 1. Déclencheurs (Trigger)
> *Fréquence des faits bruts identifiés (In-game) :*
> - sentiment de m'être rendu utile pour quelque chose d'important pour une personne qui m'est cher 
> - lorsque j'arrive à me connecter en empathie avec une personne qui partage ses faiblesses, ses vulnérabilité, ce questionnement sur la vie.


> [!example] 2. Pensées automatiques
> *Fréquence des histoires mentales récurrentes :*
> - verbalisation de mes ressentis en discours interne 


> [!example] 3. Schémas comportementaux (Réactions)
> *Fréquence des réactions identifiées :*
> - contemplation 
> - ralentissement de mon rythme de vie 
> - introspection avec discours interne

> [!example] 4. Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Prix à payer"] && !c.completed);
> let local = p.file.lists.where(l => l["Prix à payer"] && !l.completed);
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun prix à payer actif.*");
> ```
> > [!note]- ➕ Ajouter un prix à payer à froid
> > - [ ] [Prix à payer::  j'accepte que ce que je pense avoir été utile s'il ne l'est peut-être pas pour la personne en face de moi]
> > - [ ] [Prix à payer::  j'accepte de sortir de cette bulle de sérénité vient souvent avec une frustration]
> >- [ ] [Prix à payer::  j'accepte que entretenir cette bulle de sérénité demande une forme de discipline sur l'exposition au stress]

## 🔍 2. Travail de fond (Vrai problème)

> [!example] *Analyse à froid (Hors session)*
> ### 1. Identification de l'origine de l'émotion
> - 
> ### 2. Identification de l'Objet de l'émotion
> - 

## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!example] Recentrage Stratégique
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let ingame = dv.array(descendants).where(c => c["Plan d'action"] && !c.completed);
> let local = p.file.lists.where(l => l["Plan d'action"] && !l.completed);
> 
> if (ingame.length > 0 || local.length > 0) dv.taskList([...ingame, ...local], false);
> else dv.paragraph("*Aucun plan d'action actif.*");
> ```
> > [!note]- ➕ Ajouter un plan d'action à froid
> > - [ ] [Plan d'action:: ]

## 🗄️ ARCHIVES INTERACTIVES

> [!quote]- 💸 Archives : Prix à payer
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Prix à payer"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucun prix archivé.*");
> ```

> [!quote]- 🎯 Archives : Plans d'action
> ```dataviewjs
> let p = dv.current();
> let items = dv.pages('"Journal/Session/2. Feedback/2026"').file.lists.where(l => l.emotion == p.file.name);
> 
> let getDescendants = (item) => {
>     let results = [];
>     if (item.children) {
>         item.children.forEach(child => {
>             results.push(child);
>             results.push(...getDescendants(child));
>         });
>     }
>     return results;
> };
> 
> let descendants = items.flatMap(getDescendants);
> let archives = dv.array([...descendants, ...p.file.lists]).where(c => c.completed && c["Plan d'action"]);
> if (archives.length > 0) dv.taskList(archives, false);
> else dv.paragraph("*Aucune action archivée.*");
> ```

## 📝 Notes de suivi & Coaching
-