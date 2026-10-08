---
id: SPEC-tazquiz
companions:
  - bareme.md
  - jalons-et-risques.md
  - feuille-de-route.md
sources:
  - ../brief-tazquiz/brief-tazquiz.md
---

> **Contrat de référence.** Cette spec et les fichiers listés dans `companions:` forment le contrat complet de ce qu'il faut construire, tester et valider. Les sources listées dans `sources:` ne servent qu'à la traçabilité.

# TazQuiz : V1 (inauguration du 2 novembre 2026)

## Why

C'est une vision et une échéance. Tasmane anime des moments collectifs, en interne (formations, SummerSchool, onboarding, séminaires) comme chez ses clients (ateliers, formations, CODIR, restitutions), avec Kahoot, un outil qu'elle ne possède pas. TazQuiz le remplace par un outil maison et souverain, qui permet de lancer en quelques minutes un quiz ou un vote en direct, auquel les participants répondent depuis leur téléphone. Il doit être assez robuste pour être utilisé devant un client, y compris en hybride. C'est aussi une vitrine du savoir-faire sur mesure de Tasmane et le premier projet d'une montée en compétence sur le développement assisté par l'IA. La valeur se joue sur l'expérience : l'esprit de compétition doit se sentir et une partie ne doit jamais planter. Pour arbitrer, retenir trois règles. Un outil qui fonctionne passe avant l'apprentissage. Ce qui fait vivre la compétition passe avant le reste de l'interface. La date du 2 novembre 2026 est ferme.

## Capabilities

- **CAP-1**
  - **intent :** un collaborateur Tasmane accède à l'application avec son compte Microsoft Tasmane.
  - **success :** un compte du tenant Tasmane se connecte. Un compte hors tenant, ou désactivé, est refusé.
- **CAP-2**
  - **intent :** un collaborateur crée et modifie un quiz de questions à choix simple (2 à 4 réponses, Vrai/Faux préconfiguré), à choix multiple (2 à 6 réponses, nombre de bonnes réponses attendues affichable) et de classement (CAP-12). Chaque question a un énoncé, une image facultative, un temps limite propre et peut être scorée ou non (CAP-13).
  - **success :** un quiz mêlant les trois formats, avec et sans image, des temps limites différents et des questions scorées et non scorées, s'enregistre, se rouvre à l'identique et se joue.
- **CAP-3**
  - **intent :** un quiz est privé par défaut (son créateur et les collègues avec qui il le partage) ou public. Les collègues avec qui il est partagé peuvent le modifier à tour de rôle et l'animer. Un quiz public peut être vu, animé et dupliqué par tout collaborateur Tasmane, mais seuls son créateur et ses collègues de partage le modifient.
  - **success :** un collègue avec qui le quiz est partagé le voit, le modifie et lance une partie. Un collaborateur sans partage ne voit pas un quiz privé. Il voit un quiz public, l'anime et le duplique, mais ne peut pas le modifier.
- **CAP-4**
  - **intent :** l'animateur lance une partie, qui affiche sur le grand écran un code PIN et un QR code pour la rejoindre.
  - **success :** le QR code scanné ouvre directement la saisie du pseudo, et le PIN saisi mène au même endroit.
- **CAP-5**
  - **intent :** un joueur rejoint la partie avec un simple pseudo, sans compte, sur un écran qui porte la mention RGPD. Le grand écran affiche en direct les pseudos qui arrivent dans la salle d'attente.
  - **success :** il faut moins de 30 s entre le scan du QR code et l'arrivée dans la salle d'attente. Chaque pseudo apparaît sur le grand écran dès que le joueur a rejoint. Seul le pseudo est demandé.
- **CAP-6**
  - **intent :** l'animateur déroule la partie depuis l'ordinateur branché au projecteur. Entre deux questions, la partie attend : un clic de l'animateur affiche la question suivante et lance son compte à rebours. Le téléphone de chaque joueur recopie intégralement l'énoncé et les réponses, empilées verticalement, avec le compte à rebours, pour qu'il puisse répondre sans voir le grand écran.
  - **success :** une partie de bout en bout avec 50 joueurs simultanés (simulés ou réels) affiche chaque question en même temps sur le grand écran et sur les téléphones, et enregistre toutes les réponses. Une question à 6 réponses longues s'affiche sans troncature sur un petit téléphone.
- **CAP-7**
  - **intent :** chaque réponse juste, ou partiellement juste pour un classement, à une question scorée rapporte des points selon la justesse et la vitesse, plus un bonus de série. Un joueur en série est mis en avant (« en boost ») sur le grand écran et sur son téléphone.
  - **success :** les scores calculés correspondent au barème de `bareme.md` sur un jeu de réponses de test couvrant les trois formats, et la mise en avant apparaît dès la 2ᵉ bonne réponse consécutive.
- **CAP-8**
  - **intent :** après chaque question scorée, le grand écran montre le classement mis à jour avec une animation des dépassements. La partie se termine sur un podium.
  - **success :** quand un joueur en dépasse un autre, on voit l'animation correspondante. Le podium final présente les 3 premiers.
- **CAP-9**
  - **intent :** des bruitages rythment le compte à rebours, la révélation des réponses et le podium, et sortent du grand écran.
  - **success :** les sons sont audibles dans la salle et dans un partage d'écran Teams (avec l'option de partage du son activée).
- **CAP-10**
  - **intent :** la partie s'affiche à la charte Tasmane, et l'animateur choisit un fond d'écran parmi quelques options.
  - **success :** le fond choisi s'applique au grand écran pendant toute la partie.
- **CAP-11**
  - **intent :** un joueur déconnecté (veille du téléphone, réseau coupé) revient automatiquement dans la partie en cours, sans perdre son score ni sa série.
  - **success :** après avoir coupé le réseau puis l'avoir rétabli, ou rouvert la page, le joueur reprend la question en cours sans repasser par la salle d'attente, avec le même score et la même série.
- **CAP-12**
  - **intent :** une question de classement demande d'ordonner 3 à 6 éléments, par glisser-déposer ou par tap séquentiel.
  - **success :** sur téléphone, un joueur ordonne 6 éléments par l'une ou l'autre méthode et son ordre est enregistré tel quel. Scorée, la question est notée selon `bareme.md`.
- **CAP-13**
  - **intent :** une question non scorée sert de vote : elle ne rapporte aucun point et le grand écran montre seulement la répartition des réponses, ou le rang moyen de chaque élément pour un classement (priorisation collective), sans le classement des joueurs.
  - **success :** après une question non scorée, les scores sont inchangés et le grand écran affiche la répartition, ou le rang moyen, conforme aux réponses reçues, puis passe à la suite sans montrer le classement.
- **CAP-14**
  - **intent :** chaque réponse est identifiée par une couleur, une forme et une lettre (A à F), identiques sur le grand écran et sur le téléphone.
  - **success :** pour chaque question, la réponse C a la même couleur, la même forme et la même lettre sur les deux écrans.
- **CAP-15**
  - **intent :** après chaque question, le téléphone du joueur affiche son résultat, ses points gagnés, son score et son rang. Le résultat dépend du format : juste ou faux et la bonne réponse pour un choix simple ou multiple ; son ordre à côté du bon ordre, éléments bien placés mis en évidence, pour un classement ; son choix (ou son ordre), sans juste ni faux, pour un vote.
  - **success :** pour chacun des trois cas, le téléphone affiche les informations prévues, et le score et le rang correspondent au classement des joueurs.
- **CAP-16**
  - **intent :** si le navigateur ou l'ordinateur de l'animateur se ferme, il se reconnecte, depuis le même poste ou un autre, et reprend la partie là où elle était.
  - **success :** l'animateur ferme son onglet en pleine partie, se reconnecte depuis un autre ordinateur, et la partie reprend au même point, joueurs et scores intacts.
- **CAP-17**
  - **intent :** une page de test de connectivité, transmissible avant la séance, vérifie que le réseau d'un participant laisse passer TazQuiz.
  - **success :** la page donne l'un de trois résultats : vert quand tout passe, orange quand la partie est jouable en mode dégradé grâce au repli long-polling, rouge quand rien ne passe.
- **CAP-18**
  - **intent :** un collaborateur retrouve ses quiz dans une bibliothèque personnelle et peut dupliquer un quiz.
  - **success :** la copie d'un quiz est indépendante de l'original : modifier l'une ne change pas l'autre.
- **CAP-19**
  - **intent :** l'éditeur montre un aperçu de chaque question telle qu'elle sera projetée et telle qu'elle apparaîtra sur le téléphone.
  - **success :** l'aperçu correspond à l'affichage réel en partie, sur les deux écrans.
- **CAP-20**
  - **intent :** l'animateur exporte en Excel le détail des résultats d'une partie.
  - **success :** le fichier contient une ligne par joueur et par question, avec la réponse, la justesse, le temps et les points.
- **CAP-21**
  - **intent :** les accès des animateurs sont journalisés : connexion, ouverture, modification et lancement d'un quiz.
  - **success :** chacune de ces actions laisse une entrée datée qui nomme son auteur.

## Constraints

- **Charge :** 50 joueurs simultanés en V1. La cible produit est de 200 : aucun choix ne doit empêcher d'y monter.
- **Hébergement :** OVHcloud, datacenters en France, services managés privilégiés. Aucun tiers hors UE ne reçoit de contenu de quiz ou de donnée joueur. Entra ID est une exception assumée : il n'authentifie que les animateurs. Aucune donnée n'est conservée au-delà du besoin ; la mention RGPD de la V1 n'annonce pas de durée de conservation, un écart assumé jusqu'à la purge prévue en V2.
- **Domaine :** l'application est servie depuis un sous-domaine Tasmane.
- **Authentification :** Microsoft 365 pour les collaborateurs uniquement. Les joueurs n'ont ni compte ni inscription, et ne fournissent que leur pseudo.
- **Réseau des joueurs :** wifi invité de client, réseau d'entreprise filtré ou 4G. Tout passe par HTTPS sur le port 443, avec un repli en long-polling quand le WebSocket est bloqué.
- **Hybride :** les joueurs à distance suivent le grand écran via le partage d'écran Teams. Tout ce qui doit être vu ou entendu passe par l'écran de l'animateur. Le décalage est toléré, sans compensation.
- **Formats d'écran :** le grand écran est en 16:9 ; les joueurs utilisent un téléphone (navigateur mobile).
- **Échéance :** l'inauguration du 2026-11-02 est ferme et toute la V1 y est livrée. En cas de retard avéré seulement, on applique l'ordre de sacrifice de `jalons-et-risques.md`. Le classement (CAP-12) n'en fait pas partie.
- **Équipe :** 2 personnes, dont un profil non technique, en développement assisté par l'IA. La stack, que l'architecture choisira sans préférence imposée, doit rester compréhensible et maintenable par cette équipe et s'héberger sur OVH.

## Non-goals

- Un service en libre-service pour les clients, ou la vente de l'outil.
- La coédition d'un quiz en direct.
- La compensation du décalage pour les joueurs à distance.
- Les espaces par mission ou par client.
- Le mode asynchrone, le jeu en équipes et l'import de quiz Kahoot.
- Les éléments des V2 et V3 (`feuille-de-route.md`), dont l'habillage client, la restitution client anonymisée, la purge des résultats et la génération de questions par IA.

## Success signal

- Le 2026-11-02, une partie interne avec ~40 collègues sur place et à distance va au bout sans recourir à Kahoot, et aucun joueur ne reste bloqué.
- Avant le 2026-10-16, un test de charge simulant 50 joueurs déroule une partie complète sans perte de réponse ; il est rejoué sur la V1 complète avant le 2026-10-30.

## Assumptions

- Le détail chiffré du barème (`bareme.md`) reprend la mécanique connue de Kahoot et n'a pas été confirmé au point près.
- Un QCM à plusieurs bonnes réponses ne rapporte des points que si toutes les bonnes réponses sont cochées, et elles seules.
- Il n'y a ni pause en cours de question, ni fin anticipée de la partie en V1.
- Une question non scorée ne casse ni ne prolonge la série.
- Le temps de réponse se mesure à partir du clic de l'animateur qui lance la question.
- L'ordre de sacrifice s'applique sans nouvelle consultation. Si le partage entre collègues est retiré, un quiz reste privé (son créateur seul) ou public.

## Open Questions

- QCM multiple : tout ou rien, ou des points partiels ?
- Offre OVH standard ou SecNumCloud ?
- Quel est le statut RGPD de Tasmane (sous-traitant du client) ? Combien de temps garde-t-on les résultats nominatifs (pseudos, réponses, scores) ? À trancher avant la purge de la V2.
- Quel est le nom exact du sous-domaine ?
