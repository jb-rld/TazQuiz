# BMad sur TazQuiz — aide-mémoire

BMad est installé dans ce repo (modules `core-tools`, `method`, `toolsmith`). Ce sont des *skills* pour Claude Code : on les appelle en tapant `/nom-du-skill` dans Claude Code, ou simplement en le demandant en langage naturel (« fais un brief produit », « review ce code »…).

Tout ce que BMad produit atterrit dans `_bmad-output/`, rangé par *initiative* (un dossier par chantier).

## Première fois sur le repo

1. Prérequis : [`uv`](https://docs.astral.sh/uv/) installé (`brew install uv`).
2. Ouvrir Claude Code dans le repo et lancer `/bmad setup`.
3. En cas de doute à tout moment : `/bmad` → il regarde l'état du projet et dit quoi faire ensuite.

## Par où commencer ?

| Ma situation | Commande |
|---|---|
| Petite modif évidente (typo, config) | Rien, on la fait directement |
| Un changement faisable en une session (feature, bug) | `/bmad-build` |
| Pas encore d'idée, besoin d'en générer | `/bmad-brainstorming` |
| Une idée floue, je ne sais pas si elle tient | `/bmad-forge-idea` |
| Je suis sûr de l'idée mais rien n'est écrit | `/bmad-product-brief` |
| Je veux tester si le concept vaut le coup | `/bmad-prfaq` |
| J'ai assez de matière (notes, brief, PRD, ticket) | `/bmad-spec` puis `/bmad-ticket` |

Le chemin typique pour un gros sujet : **idée → brief / PRD / UX / archi (au besoin) → `bmad-spec` → `bmad-ticket` → un `bmad-build` par story → review**. On ne fait que les étapes utiles, pas toutes.

## Les commandes

### Comprendre et cadrer (analyse)

| Commande | Ce que ça fait |
|---|---|
| `/bmad-brainstorming` | Session de brainstorming guidée pour sortir des idées évidentes. |
| `/bmad-forge-idea` | Challenge une idée par des questions jusqu'à pouvoir la lancer… ou l'abandonner. |
| `/bmad-deep-recon` | Recherche sourcée (marché, techno, concurrents, avis utilisateurs) pour éclairer une décision. |
| `/bmad-product-brief` | Brief produit de 1–2 pages. Plus léger qu'un PRD. |
| `/bmad-prfaq` | Méthode Amazon « Working Backwards » : communiqué de presse + FAQ difficile + verdict. |

### Planifier

| Commande | Ce que ça fait |
|---|---|
| `/bmad-spec` | **Le pivot.** Condense n'importe quelle entrée (idée, brief, PRD, notes) en une spec courte que les builds lisent. |
| `/bmad-prd` | PRD détaillé, quand les exigences, les parties prenantes ou la conformité le justifient. |
| `/bmad-ux` | Look & comportement du produit (`DESIGN.md` + `EXPERIENCE.md`), maquettes possibles. |
| `/bmad-architecture` | Décisions techniques qui gardent les parties cohérentes (stack, hébergement…). Pas besoin d'être expert. |
| `/bmad-ticket` | Découpe en initiatives / epics / stories et sert de board (prêt, suivant, bloqué, fini). « Où en est-on ? » → ici. |

### Construire

| Commande | Ce que ça fait |
|---|---|
| `/bmad-build` | Une session de dev complète : clarifie, planifie, code, se relit, commit. À utiliser pour tout vrai changement ; accepte un texte libre ou un ticket. |
| `/bmad-build-auto` | Build d'un ticket sans humain, lancé par une boucle/script. Pour des stories bien spécifiées uniquement. |
| `/bmad-correct-course` | Gros changement de cap en cours de route : évalue l'impact sur PRD/spec/epics. |

### Vérifier

| Commande | Ce que ça fait |
|---|---|
| `/bmad-code-review` | Review par plusieurs agents d'un diff, d'une branche ou d'une PR. |
| `/bmad-review` | Review d'un diff ou d'un document selon des angles choisis (adversarial, cas limites, structure, rédaction). |
| `/bmad-walkthrough` | Visite guidée d'un changement pour qu'un humain le relise ou découvre le code. |
| `/bmad-qa-generate-e2e-tests` | Génère des tests API / end-to-end pour des features existantes. |
| `/bmad-retrospective` | Bilan d'une epic terminée, avec actions à mener. |

### Outils transverses

| Commande | Ce que ça fait |
|---|---|
| `/bmad` | L'aide : installation, état, mise à jour, initiative active, « quoi faire maintenant ? ». |
| `/bmad-advanced-elicitation` | Pousse Claude à retravailler son dernier résultat (premiers principes, pre-mortem, red team…). |
| `/bmad-party-mode` | Discussion à plusieurs agents/personas sur un sujet. |
| `/bmad-customize` | Change le comportement d'un skill sans le modifier (équipe : commité ; perso : `*.user.toml`, non commité). |
| `/bmad-project-context` | Tient à jour `AGENTS.md` avec les règles que les agents doivent suivre dans ce repo. |
| `/bmad-toolsmith` | Smithy : crée ou modifie nos propres skills/agents. |
| `/bmad-eval` | Mesure si un skill fonctionne vraiment. |

## Les agents (si vous préférez discuter avec un expert)

Plutôt que lancer un skill, on peut parler à un agent qui guide toute une phase et propose les bons skills :

| Agent | Rôle |
|---|---|
| `/bmad-agent-analyst` — Mary | Analyse, recherche, brief |
| `/bmad-agent-pm` — John | PRD, epics, stories |
| `/bmad-agent-ux-designer` — Sally | UX / UI |
| `/bmad-agent-architect` — Winston | Architecture |
| `/bmad-agent-dev` — Amelia | Dev, tests, review, board |

## Bon à savoir

- **Initiative active** : chacun choisit la sienne (`/bmad` pour l'afficher ou en changer) ; c'est stocké dans un fichier perso non commité.
- **Mise à jour de BMad** : demander `/bmad update`, puis committer.
- Doc complète : https://docs.bmad-method.org/
