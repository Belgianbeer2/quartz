---
type: fiche_emotion
---
# 🧠 Fiche  : La Colère


## 🔬 0. Comprendre l'émotion

> [!abstract] Ce que Moukheiber éclaire
> La fiche IRL illustre un mécanisme précis : le discours interne explosif (*"je vais les défoncer"*, *"je vais tout faire péter"*) et la réaction réelle (stratégie de l'autruche) sont **opposés**. Ce n'est pas une contradiction — c'est le fonctionnement normal du cerveau sous impuissance.
>
> Quand on n'a aucun pouvoir sur une situation, le cerveau génère une **histoire d'agentivité** pour compenser. *"Je vais tout faire péter"* n'est pas un plan — c'est une illusion de contrôle produite pour rendre la situation supportable. La stratégie de l'autruche est la réaction *réelle* ; le discours explosif est la réaction *narrative*. L'écart entre les deux, c'est exactement ce que Moukheiber montre : le *soi narratif* et le *soi comportemental* ne coïncident pas sous pression.

> [!abstract] Ce que Alexis pointe — Les 3 niveaux de traitement
> La colère n'est pas irrationnelle quand le trigger touche aux valeurs fondamentales (liberté, autodétermination). Elle est **cohérente** avec qui tu es. Le travail n'est pas de l'effacer — c'est de la traverser :
>
> 1. **Je la subis** — le trigger crée l'impuissance, l'émotion déborde.
> 2. **Je la gère** — stratégie de l'autruche, faire des choses à conséquences limitées le temps de s'apaiser.
> 3. **Je la transforme** — la valeur (liberté, autodétermination) devient **levier de détermination** : *"je joue pour construire l'indépendance qui me permettra d'aider les gens qui m'importent."*
>
> *→ Voir aussi :* [[Être et Faire — Réconciliation Moukheiber × Alexis]] *— Cas pratique Colère*

---

## 📊 1. Patterns de l'émotion

> [!danger] **1. Déclencheurs (Trigger)**
> *Fréquence des faits bruts identifiés (In-game) :*
> - Le beau père de Sassa, qui est enfermé en prison injustement est sur le point de mourir. Il est mal nourrit, incapable de bouger et mal traité par les officiers (injustices)

> [!danger] **2. Pensées automatiques**
>*Fréquence des histoires mentales récurrentes :*
> - "j'aurais préféré ne pas être au courant"
> - "je vais les défoncer"
> - "Je vais tout faire pêter"
> 

> [!danger] **3. Schémas comportementaux (Réactions)**
>*Fréquence des réactions identifiées :*
>- Stratégie de l'autruche
>	- faire des choses qui ont des conséquences limités (le temps que je m'appaise)
>

> [!danger] **4. Prix à payer de rester dans l'illusion de la Colère**
> - [ ] [Prix à payer:: me faire guider par mes émotion (ne plus être le conducteur de mon corps)]
> - [ ] [Prix à payer:: ]
## 🔍 2. Travail de fond (Vrai problème)

> [!danger] **Analyse à froid (Hors session)**
> ### 1. A quoi le trigger fait-il écho ?
> - injustice + impuissance
> 	Pourquoi ça importe pour moi ?
> 	- je veux que les gens puissent vivre librement
> 	- Je veux que les gens puissent s'auto-déterminé
> ### 2. Qu'est-ce que j'en fais ?
> *1. je la subis. 2. Je la gère (stratégie) 3. Je la transforme (je crée un levier de détermination)*
> 	- Comment je transforme toutes ces valeur humaine pour en faire qqch d'utile et non qqch qui me bouffe ?
> >**Dépolarisation sur l'injustice**
## 🛡️ 3. Protocole de Recentrage : Plan d'action adaptés

> [!danger] **Recentrage Stratégique**
> - [ ] [Plan d'action:: Rubber ducké]
>
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

>