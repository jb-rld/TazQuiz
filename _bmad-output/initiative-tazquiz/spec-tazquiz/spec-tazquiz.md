---
id: SPEC-tazquiz
companions:
  - bareme.md
  - jalons-et-risques.md
  - feuille-de-route.md
sources:
  - ../brief-tazquiz/brief-tazquiz.md
---

> **Contrat de référence.** Cette spec et les fichiers listés dans `companions:` forment le contrat complet de ce qu'il faut construire, tester et valider. Le brief listé dans `sources:` ne sert qu'à la traçabilité.

# TazQuiz : V1 (inauguration du 2 novembre 2026)

## Why

C'est une vision et une échéance. Tasmane anime ses quiz collectifs (séminaires clients, formations, moments internes) avec Kahoot, un outil qu'elle ne possède pas. TazQuiz le remplace pour quatre raisons. C'est un outil possédé et personnalisable. C'est une vitrine qui montre aux clients ce que Tasmane sait construire sur mesure. C'est le premier projet d'une montée en compétence sur le développement assisté par l'IA. Et il permet de mettre des chiffres clients dans une question sans les confier à un tiers. La valeur se joue sur l'expérience : l'esprit de compétition doit se sentir et une partie ne doit jamais planter. Pour arbitrer, retenir trois règles. Un outil qui fonctionne passe avant l'apprentissage. Ce qui fait vivre la compétition passe avant le reste de l'interface. La date du 2 novembre 2026 est ferme.

## Capabilities

- **CAP-1**
  - **intent :** un collaborateur Tasmane accède à l'application avec son compte Microsoft Tasmane.
  - **success :** un compte du tenant Tasmane se connecte. Un compte hors tenant, ou désactivé, est refusé.
- **CAP-2**
  - **intent :** un collaborateur crée et modifie un quiz de questions QCM (4 choix, une ou plusieurs bonnes réponses) et Vrai/Faux.
  - **success :** un quiz mêlant QCM à réponse unique, QCM à réponses multiples et Vrai/Faux s'enregistre, se rouvre à l'identique et se joue.
- **CAP-3**
  - **intent :** un collaborateur partage un quiz avec des collègues, qui peuvent le modifier à tour de rôle et l'animer.
  - **success :** le collègue avec qui le quiz est partagé le voit, le modifie et lance une partie avec. Un collaborateur sans partage n'y a pas accès (voir les questions ouvertes).
- **CAP-4**
  - **intent :** l'animateur lance une partie, qui affiche sur le grand écran un code PIN et un QR code pour la rejoindre.
  - **success :** le QR code scanné ouvre directement la saisie du pseudo, et le PIN saisi mène au même endroit.
- **CAP-5**
  - **intent :** un joueur rejoint la partie avec un simple pseudo, sans compte. Le grand écran affiche en direct les pseudos qui arrivent dans la salle d'attente.
  - **success :** il faut moins de 30 s entre le scan du QR code et l'arrivée dans la salle d'attente. Chaque pseudo apparaît sur le grand écran dès que le joueur a rejoint.
- **CAP-6**
  - **intent :** l'animateur déroule la partie question par question depuis l'ordinateur branché au projecteur. Chaque joueur voit la question et les choix sur son téléphone et y répond.
  - **success :** une partie de bout en bout avec 50 joueurs simultanés (simulés ou réels) affiche chaque question en même temps sur le grand écran et sur les téléphones, et enregistre toutes les réponses.
- **CAP-7**
  - **intent :** chaque bonne réponse rapporte des points selon la vitesse de réponse, plus un bonus de série. Un joueur en série est mis en avant (« en boost ») sur le grand écran et sur son téléphone.
  - **success :** les scores calculés correspondent au barème de `bareme.md` sur un jeu de réponses de test, et la mise en avant apparaît dès la 2ᵉ bonne réponse consécutive.
- **CAP-8**
  - **intent :** après chaque question, le grand écran montre le classement mis à jour avec une animation des dépassements. La partie se termine sur un podium.
  - **success :** quand un joueur en dépasse un autre, on voit l'animation correspondante. Le podium final présente les 3 premiers.
- **CAP-9**
  - **intent :** des bruitages rythment le compte à rebours, la révélation des réponses et le podium, et sortent du grand écran.
  - **success :** les sons sont audibles dans la salle et dans un partage d'écran Teams (avec l'option de partage du son activée).
- **CAP-10**
  - **intent :** la partie s'affiche à la charte Tasmane, et l'animateur choisit un fond d'écran parmi quelques options.
  - **success :** le fond choisi s'applique au grand écran pendant toute la partie.
- **CAP-11**
  - **intent :** un joueur déconnecté (veille du téléphone, réseau coupé) revient dans la partie en cours.
  - **success :** après avoir coupé le réseau puis l'avoir rétabli, ou rouvert la page, le joueur reprend la question en cours sans repasser par la salle d'attente.

## Constraints

- **Charge :** 50 joueurs simultanés en V1. La cible produit est de 100 : aucun choix ne doit empêcher d'y monter.
- **Hébergement :** il est maîtrisé par Tasmane, et aucun tiers ne reçoit le contenu des quiz. On ne conserve pas de données au-delà du besoin.
- **Authentification :** Microsoft 365 pour les collaborateurs uniquement. Les joueurs n'ont ni compte ni inscription.
- **Hybride :** les joueurs à distance suivent le grand écran via le partage d'écran Teams. Tout ce qui doit être vu ou entendu passe par l'écran de l'animateur. Le décalage est toléré, sans compensation.
- **Formats d'écran :** le grand écran est en 16:9 ; les joueurs utilisent un téléphone (navigateur mobile).
- **Réseau des joueurs :** wifi invité du client ou 4G. Le temps réel doit fonctionner sur ces réseaux.
- **Échéance :** l'inauguration du 2026-11-02 est ferme. En cas de retard, on sacrifie dans l'ordre CAP-3, puis le QR code de CAP-4, puis le bonus de série de CAP-7 (voir `jalons-et-risques.md`).
- **Équipe :** 2 personnes, dont un profil non technique, en développement assisté par l'IA. La solution doit rester compréhensible et maintenable par cette équipe.

## Non-goals

- Un service en libre-service pour les clients, ou la vente de l'outil.
- La coédition d'un quiz en direct.
- La compensation du décalage pour les joueurs à distance.
- Les formats et options des V2 et V3 (`feuille-de-route.md`), dont l'habillage client et le logo masquable.
- L'analyse des résultats par joueur.

## Success signal

- Le 2026-11-02, une partie interne avec ~40 collègues sur place et à distance va au bout sans recourir à Kahoot, et aucun joueur ne reste bloqué.
- Avant le 2026-10-30, un test de charge simulant 50 joueurs déroule une partie complète sans perte de réponse.

## Assumptions

- L'ordre de sacrifice (CAP-3, puis le QR de CAP-4, puis le bonus de CAP-7) s'applique sans nouvelle consultation.
- Le détail chiffré du barème (`bareme.md`) reprend la mécanique connue de Kahoot et n'a pas été confirmé au point près.

## Open Questions

- Où héberger : sur l'Azure du tenant Tasmane ou ailleurs ?
- Quelles données conserve-t-on après une partie (pseudos, réponses, scores), et combien de temps ?
- Qui voit les quiz : tous les collaborateurs voient-ils tous les quiz, ou seulement ceux qu'on leur a partagés ?
- La durée de réponse est-elle fixe, ou réglable question par question ?
- Les questions peuvent-elles contenir des images dès la V1 ?
- Un joueur qui revient après une déconnexion (CAP-11) conserve-t-il son score et sa série ?
