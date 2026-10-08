# TazQuiz — Notes de cadrage (session avec Mary, analyste)

> Date : 2026-10-08 · Participants : Paul Collard, Mary (BMad Business Analyst)
> Statut : notes de découverte, **à transformer en brief produit** (`/bmad-product-brief`).

## Vision

Un outil interne de quiz en direct, très gamifié, inspiré de Kahoot, permettant à un animateur Tasmane de faire jouer jusqu'à ~100 participants simultanément.

**Insight clé :** TazQuiz n'est pas seulement un outil interne, c'est aussi une **vitrine du savoir-faire Tasmane** auprès des clients. L'effet « waouh » (fluidité, rendu, ambiance) fait partie de la valeur, pas du bonus.

## Pourquoi construire plutôt qu'utiliser Kahoot

1. **Indépendance et coût** : supprimer la licence Kahoot.
2. **Confidentialité** : pouvoir intégrer des informations sensibles dans les quiz, ce qui impose de maîtriser l'hébergement et les données.
3. **Image** : montrer aux clients que Tasmane sait concevoir ce type d'outil, et qu'il fonctionne bien.

## Contextes et modes d'usage

- **Usages :** séminaires clients, formations internes, tout moment collectif.
- **Modes de jeu :** présentiel (grand écran principal au format 16:9), à distance, **et hybride** : joueurs sur place et à distance dans la même partie.
- **Modèle d'exploitation :** Tasmane garde la main. Les animateurs sont Tasmane, les clients ne sont que joueurs. Pas de SaaS en libre-service, pas d'inscription publique ni de facturation.

## Fonctionnalités exprimées

### Formats de questions

| Format | Rôle | Complexité estimée | Points ? |
|---|---|---|---|
| QCM 4 choix, 1 ou plusieurs bonnes réponses | Cœur du jeu | Faible | Oui |
| Vrai / Faux | Variante QCM | Très faible | Oui |
| Sondage actualisé en temps réel | Engagement | Faible | Non |
| Nuage de mots | Engagement / brise-glace | Moyenne (saisie libre, regroupement, modération) | Non |
| Image dévoilée progressivement (pixels) | Suspense, effet waouh | Moyenne | Oui (plus on répond tôt, plus on gagne) |
| Placer un point sur une image (carte du monde ou autre) | Effet waouh fort | Élevée (distance, affichage des réponses) | Oui (selon la proximité) |

### Rejoindre une partie

- Code PIN **et** QR code.
- **Pseudo uniquement** : pas de compte ni d'identification, pour aucune friction chez le client.

### Gamification et scores

- Classement mis à jour après chaque question.
- Bonus pour les séries de bonnes réponses.
- Podium final façon remise des prix.

### Identité visuelle et UX

- UX soignée : belle et simple à utiliser.
- Charte Tasmane par défaut.
- Fonds d'écran interchangeables selon le contexte ou le thème du quiz.
- Habillage aux couleurs d'un client possible, logo Tasmane désactivable par une option.

### Après la partie

- Podium final.
- Analyse détaillée par joueur (mesurer les acquis d'une formation, par exemple) **pas nécessaire pour l'instant**, envisagée plus tard.

## Contraintes et rythme

- ~100 joueurs simultanés : le temps réel fiable est **le principal risque technique**, à valider tôt.
- Pas de date butoir. Approche itérative : une première version rapide, la tester, l'améliorer.

## Découpage proposé (à valider)

- **V1, une partie de bout en bout :** création de quiz QCM + Vrai/Faux ; PIN/QR + pseudo ; partie en direct ~100 joueurs (présentiel, distance, hybride) ; score avec bonus de vitesse et de série ; classement par question ; podium ; charte Tasmane et choix du fond d'écran.
- **V2, formats d'engagement :** sondage temps réel, nuage de mots, image dévoilée, logo masquable et habillage client.
- **V3, formats avancés :** placement d'un point sur une image, analyse des résultats par joueur.

## Questions ouvertes

1. Le découpage V1/V2/V3 convient-il ? (Faut-il remonter le sondage en V1 ?)
2. Barème : reprendre celui de Kahoot (jusqu'à 1 000 pts selon la vitesse, plus un bonus de série) ou autre chose ?
3. Hébergement et confidentialité : où héberger, qui accède aux quiz, quelles données joueurs conserver ?
4. Accès animateurs : quel mode d'authentification pour les animateurs Tasmane ?

## Prochaine étape

Lancer `/bmad-product-brief` (ou le menu CB de Mary) en s'appuyant sur ces notes.
