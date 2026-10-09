---
id: SPEC-tazquiz
companions:
  - bareme.md
  - jalons-et-risques.md
  - feuille-de-route.md
  - ../ux-tazquiz/ux-tazquiz.md
sources:
  - ../brief-tazquiz/brief-tazquiz.md
---

> **Contrat de référence.** Cette spec et les fichiers listés dans `companions:` forment le contrat complet de ce qu'il faut construire, tester et valider. Les sources listées dans `sources:` ne servent qu'à la traçabilité.

# TazQuiz : V1 (inauguration du 2 novembre 2026)

## Why

TazQuiz porte une vision et une échéance. Tasmane anime des moments collectifs, en interne (formations, SummerSchool, onboarding, séminaires) comme chez ses clients (ateliers, formations, CODIR, restitutions), avec Kahoot, un outil qu'elle ne possède pas. TazQuiz le remplace par un outil maison et souverain, qui permet de lancer en quelques minutes un quiz ou un vote en direct, auquel les participants répondent depuis leur téléphone.

Il doit être assez robuste pour être utilisé devant un client, y compris en hybride. C'est aussi une vitrine du savoir-faire sur mesure de Tasmane et le premier projet d'une montée en compétence sur le développement assisté par l'IA. La valeur se joue sur l'expérience : l'esprit de compétition doit se sentir et une partie ne doit jamais planter.

Pour arbitrer, appliquer ces trois règles, dans cet ordre :

1. La date du 2 novembre 2026 est ferme.
2. Un outil qui fonctionne passe avant l'apprentissage.
3. Ce qui fait vivre la compétition passe avant le reste de l'interface.

## Lexique

- **Animateur** : collaborateur Tasmane qui lance et pilote une partie depuis l'ordinateur branché au projecteur.
- **Joueur** : participant à une partie, interne ou client, identifié par son seul pseudo.
- **Grand écran** : l'écran projeté de l'animateur, également partagé dans Teams.
- **Question de classement** : format où le joueur ordonne des éléments (CAP-12). À ne pas confondre avec le **classement des joueurs**, le tableau des scores (CAP-8).
- **Vote** : question non scorée (CAP-13).
- **Série** : suite de bonnes réponses consécutives d'un joueur ; **boost** : sa mise en avant à l'écran.
- **Compte Tasmane** : compte Microsoft 365 du tenant Tasmane, authentifié par Entra ID.

## Capabilities

### Accès et droits

- **CAP-1**
  - **intent :** un collaborateur Tasmane accède à l'application avec son compte Tasmane.
  - **success :** un compte membre du tenant Tasmane se connecte. Un compte hors tenant, un compte invité ou un compte désactivé est refusé.
- **CAP-3**
  - **intent :** un quiz est privé par défaut, c'est-à-dire visible par son créateur et par les collègues avec qui celui-ci le partage, ou public. Les collègues avec qui il est partagé peuvent le modifier à tour de rôle et l'animer. Un quiz public peut être vu, animé et dupliqué par tout collaborateur, mais seuls son créateur et les collègues avec qui il est partagé le modifient.
  - **success :** un collègue avec qui le quiz est partagé le voit, le modifie et lance une partie. Un collaborateur sans partage ne voit pas un quiz privé. Il voit un quiz public, l'anime et le duplique, mais ne peut pas le modifier.
- **CAP-21**
  - **intent :** les accès des animateurs sont journalisés : connexion, ouverture, modification et lancement d'un quiz. Seuls les administrateurs (JBR et Paul) lisent le journal.
  - **success :** chacune de ces actions laisse une entrée datée qui nomme son auteur, consultable par un administrateur et par personne d'autre.

### Édition et bibliothèque

- **CAP-2**
  - **intent :** un collaborateur crée et modifie un quiz de questions à choix simple (2 à 4 réponses, Vrai/Faux préconfiguré), à choix multiple (2 à 6 réponses, nombre de bonnes réponses attendues affichable) et de classement (CAP-12). Chaque question a un énoncé, une image facultative, un temps limite propre et peut être scorée ou non (CAP-13). Une question scorée à choix simple a exactement une bonne réponse ; à choix multiple, au moins une.
  - **success :** un quiz mêlant les trois formats, avec et sans image, des temps limites différents et des questions scorées et non scorées, s'enregistre, se rouvre à l'identique et se joue. L'éditeur refuse un nombre de réponses hors bornes, une question scorée sans bonne réponse et un temps limite absent.
- **CAP-12**
  - **intent :** une question de classement demande d'ordonner 3 à 6 éléments, par glisser-déposer ou par tap séquentiel. L'ordre initial présenté est mélangé et jamais égal au bon ordre.
  - **success :** sur téléphone, un joueur ordonne 6 éléments par l'une ou l'autre méthode, valide, et son ordre est enregistré tel quel. Scorée, la question est notée selon `bareme.md`.
- **CAP-13**
  - **intent :** une question non scorée sert de vote : elle ne rapporte aucun point. Le grand écran montre la répartition des réponses, ou le rang moyen de chaque élément pour une question de classement (priorisation collective), sans le classement des joueurs.
  - **success :** après un vote, les scores sont inchangés et le grand écran affiche la répartition, ou le rang moyen calculé sur les seuls ordres validés, avec le nombre de votants, puis passe à la suite sans montrer le classement des joueurs. Sans aucune réponse, il affiche « aucune réponse ».
- **CAP-18**
  - **intent :** un collaborateur retrouve dans une bibliothèque personnelle les quiz qu'il a créés et ceux partagés avec lui, et peut dupliquer un quiz.
  - **success :** la copie est privée, appartient à celui qui duplique, et n'hérite d'aucun partage. Modifier la copie ne change pas l'original, et inversement.
- **CAP-19**
  - **intent :** l'éditeur montre un aperçu de chaque question telle qu'elle sera projetée et telle qu'elle apparaîtra sur le téléphone.
  - **success :** sur un quiz étalon, l'aperçu et l'affichage réel en partie sont identiques sur les deux écrans, dans les deux thèmes.

### Lancement et jeu

- **CAP-4**
  - **intent :** l'animateur lance une partie, qui affiche sur le grand écran un code PIN et un QR code pour la rejoindre.
  - **success :** le QR code scanné ouvre directement la saisie du pseudo, et le PIN saisi mène au même endroit. Un PIN erroné ou celui d'une partie terminée donne un message clair.
- **CAP-5**
  - **intent :** un joueur rejoint la partie avec un simple pseudo, sans compte, sur un écran qui porte la mention RGPD. Le grand écran affiche en direct les pseudos qui arrivent dans la salle d'attente. Un pseudo est unique dans la partie (suffixe automatique), limité en longueur et filtré contre les gros mots. Un joueur peut rejoindre une partie commencée : il entre avec 0 point et joue à partir de la question suivante. Au-delà de 200 joueurs, la partie affiche « partie complète ».
  - **success :** sur un téléphone en 4G, il faut moins de 30 s, en médiane, entre le scan du QR code et l'arrivée dans la salle d'attente. Chaque pseudo apparaît sur le grand écran dès que le joueur a rejoint. Deux « Paul » deviennent « Paul » et « Paul 2 ». Un pseudo grossier est refusé. Un retardataire joue dès la question suivante.
- **CAP-6**
  - **intent :** l'animateur déroule la partie depuis le grand écran, sans écran de pilotage séparé, avec des commandes discrètes et des raccourcis clavier, et voit combien de joueurs ont répondu. Entre deux questions, la partie attend : un clic de l'animateur affiche la question suivante et lance son compte à rebours. La bonne réponse est révélée à la fin du compte à rebours, ou dès que tous les joueurs connectés au lancement de la question ont répondu. Le téléphone de chaque joueur recopie intégralement l'énoncé et les réponses, empilées verticalement, avec le compte à rebours, pour qu'il puisse répondre sans voir le grand écran. Une réponse à choix simple est définitive au premier tap ; une réponse à choix multiple ou de classement exige de valider.
  - **success :** une partie de bout en bout avec 50 joueurs simultanés affiche chaque question sur le grand écran et sur les téléphones avec un écart d'au plus 1 s (95ᵉ centile), et enregistre toutes les réponses. Aucune question ne démarre sans action de l'animateur. Quand tous ont répondu, la révélation est immédiate ; un joueur déconnecté ne la bloque pas. Une question à 6 réponses longues s'affiche sans troncature sur un téléphone de 360 px de large.
- **CAP-14**
  - **intent :** chaque réponse est identifiée par une couleur, une forme et une lettre (A à F), identiques sur le grand écran et sur le téléphone.
  - **success :** sur des questions à 2, 4 et 6 réponses, chaque lettre de A à F a la même couleur et la même forme sur les deux écrans, dans les deux thèmes.
- **CAP-15**
  - **intent :** après chaque question, le téléphone du joueur affiche son résultat, ses points gagnés, son score, son rang, ainsi que le pseudo du joueur juste devant lui et l'écart de points qui les sépare. Le résultat dépend du format :
    - choix simple ou multiple : juste ou faux, et la bonne réponse ;
    - question de classement : son ordre à côté du bon ordre, éléments bien placés mis en évidence ;
    - vote : son choix (ou son ordre), sans juste ni faux ;
    - pas de réponse : « pas de réponse », la bonne réponse et 0 point.
  - **success :** dans chacun des quatre cas, le téléphone affiche les informations prévues ; le score et le rang correspondent au classement des joueurs. Le premier voit un message de tête à la place de l'écart.
- **CAP-9**
  - **intent :** une musique d'attente accompagne la salle d'attente, et des bruitages rythment le compte à rebours, la révélation des réponses et le podium. Ils sortent du grand écran, après une action de l'animateur qui active le son.
  - **success :** chacun de ces sons est audible dans la salle et dans un partage d'écran Teams (avec l'option de partage du son activée). Un indicateur signale à l'animateur si le son est actif.
- **CAP-10**
  - **intent :** la partie s'affiche à la charte Tasmane, dans un thème clair ou foncé, avec un fond d'écran choisi parmi quelques options. L'animateur choisit thème et fond dans la salle d'attente ; ils sont verrouillés au lancement et les téléphones suivent le thème.
  - **success :** le thème et le fond choisis s'appliquent au grand écran pendant toute la partie, le thème aux téléphones aussi, y compris après une reconnexion, et ne changent plus après le lancement.
- **CAP-22**
  - **intent :** une mascotte présentatrice commente la partie sur le grand écran, en bulles de texte, à tous ses moments (salle d'attente, lancement, compte à rebours, révélation, répartition, classement, podium). Ses répliques viennent d'une banque écrite à l'avance et rattachée à des situations. L'animateur choisit son niveau dans la salle d'attente (1 sans blague, 2 quelques blagues, 3 piquante) ; il est verrouillé au lancement. Elle chambre un groupe, jamais une personne ni un pseudo, et ne cache jamais l'énoncé, les réponses ou le chrono.
  - **success :** pour chaque situation de la banque, la mascotte affiche une réplique du niveau choisi. Au niveau 1, aucune blague. Aucune bulle ne recouvre l'énoncé, les réponses ou le chrono.

### Score et classement

- **CAP-7**
  - **intent :** à une question scorée, chaque réponse juste (ou partiellement juste, pour une question de classement) rapporte des points selon la justesse et la vitesse, plus un bonus de série. Un joueur en série est mis en avant (« en boost ») sur le grand écran et sur son téléphone.
  - **success :** les scores calculés correspondent aux exemples chiffrés de `bareme.md`. Le boost apparaît sur les deux écrans dès la 2ᵉ bonne réponse consécutive, disparaît après une erreur ou un classement partiel, et ne change pas après un vote.
- **CAP-8**
  - **intent :** après chaque question, le grand écran montre la répartition des réponses. Après une question scorée, il montre ensuite le top 5 du classement des joueurs, avec une animation des entrées, sorties et dépassements. Les ex æquo partagent le même rang. La partie se termine sur un podium révélé progressivement, puis chaque téléphone affiche le rang final et la partie se ferme.
  - **success :** après chaque question scorée, on voit la répartition puis le top 5 ; quand un joueur entre dans le top 5 ou en dépasse un autre, l'animation le montre. Le podium présente les trois premiers rangs, avec tous les ex æquo, et seulement les places occupées s'il y a moins de trois joueurs. Après la fin, le PIN n'est plus valide.

### Résilience et réseau

- **CAP-11**
  - **intent :** un joueur déconnecté (veille du téléphone, réseau coupé) revient automatiquement dans la partie en cours, sans perdre son score ni sa série. Pendant une question entièrement manquée à cause d'une déconnexion, sa série est gelée.
  - **success :** après avoir coupé le réseau puis l'avoir rétabli, ou rouvert la page, le joueur reprend l'écran en cours sans repasser par la salle d'attente, avec le même score et la même série, sans créer de doublon. Une réponse envoyée juste avant la coupure compte une fois. Après la révélation, il ne peut plus répondre à la question.
- **CAP-16**
  - **intent :** si le navigateur ou l'ordinateur de l'animateur se ferme, l'animateur, ou un collègue avec qui le quiz est partagé, se reconnecte depuis le même poste ou un autre et reprend la partie là où elle était. Une seule session pilote la partie à la fois.
  - **success :** l'animateur ferme son onglet en plein compte à rebours, se reconnecte depuis un autre ordinateur, et la partie reprend au même point, joueurs, scores, thème et niveau de la mascotte intacts. Un collaborateur sans partage ne peut pas reprendre la partie.
- **CAP-17**
  - **intent :** une page de test de connectivité, publique et transmissible avant la séance, vérifie que le réseau d'un participant laisse passer TazQuiz.
  - **success :** sur trois réseaux contrôlés, la page donne le bon résultat : vert quand tout passe, orange quand seul le repli long-polling fonctionne (partie jouable en mode dégradé), rouge quand rien ne passe.

### Export

- **CAP-20**
  - **intent :** l'animateur de la partie et les auteurs du quiz exportent en Excel le détail des résultats.
  - **success :** sur une partie étalon (trois formats, un vote, un joueur sans réponse, un joueur reconnecté), le fichier contient une ligne par joueur et par question, avec la réponse, la justesse (juste, partiel, faux, ou sans objet pour un vote), le temps et les points.

## Constraints

- **Charge :** 50 joueurs simultanés garantis en V1. La cible produit est de 200, qui est aussi le plafond d'une partie : aucun choix ne doit empêcher d'y monter.
- **Hébergement :** OVHcloud, datacenters en France, services managés privilégiés. Aucun tiers hors UE ne reçoit de contenu de quiz ou de donnée joueur, polices, CDN et outils compris. Entra ID est une exception assumée : il n'authentifie que les animateurs.
- **Données :** aucune donnée n'est conservée au-delà du besoin. La mention RGPD de la V1 n'annonce pas de durée de conservation : cet écart est assumé jusqu'à la purge prévue en V2.
- **Domaine :** l'application est servie depuis un sous-domaine Tasmane.
- **Authentification :** compte Tasmane pour les collaborateurs uniquement. Les joueurs n'ont ni compte ni inscription, et ne fournissent que leur pseudo.
- **Réseau des joueurs :** wifi invité de client, réseau d'entreprise filtré ou 4G. Tout passe par HTTPS sur le port 443, avec un repli en long-polling quand le WebSocket est bloqué.
- **Hybride :** les joueurs à distance suivent le grand écran via le partage d'écran Teams. Tout ce qui doit être vu ou entendu passe par le grand écran. Le décalage du partage Teams est toléré, sans compensation.
- **Formats d'écran :** le grand écran est en 16:9 ; les joueurs utilisent un téléphone (navigateur mobile).
- **Échéance :** l'inauguration du 2026-11-02 est ferme et toute la V1 y est livrée. En cas de retard constaté à une revue datée, on applique l'ordre de sacrifice de `jalons-et-risques.md`. La question de classement (CAP-12) et la mascotte (CAP-22) ne peuvent pas être sacrifiées.
- **Équipe :** 2 personnes, dont un profil non technique, en développement assisté par l'IA. La stack, que l'architecture choisira sans préférence imposée, doit rester compréhensible et maintenable par cette équipe et s'héberger sur OVH.

## Non-goals

- Un service en libre-service pour les clients, ou la vente de l'outil.
- La coédition d'un quiz en direct.
- La compensation du décalage pour les joueurs à distance.
- L'exclusion d'un joueur par l'animateur.
- Les espaces par mission ou par client.
- Le mode asynchrone, le jeu en équipes et l'import de quiz Kahoot.
- Les éléments des V2 et V3 (`feuille-de-route.md`), dont l'habillage client, la restitution client anonymisée, la purge des résultats, la génération de questions par IA, les répliques de la mascotte générées par IA et ses vannes sur les téléphones.

## Success signal

- Le 2026-11-02, une partie interne avec environ 40 collègues sur place et à distance va au bout sans recourir à Kahoot. Le journal serveur ne montre aucun joueur resté déconnecté sans retour, et un vote de fin de partie (« ça a marché pour vous ? ») le confirme.
- Les deux tests de charge à 50 joueurs passent selon le protocole de `jalons-et-risques.md`.

## Assumptions

- Le détail chiffré du barème (`bareme.md`) reprend la mécanique de Kahoot et n'a pas été confirmé au point près.
- Une question à choix multiple ne rapporte des points que si toutes les bonnes réponses sont cochées, et elles seules.
- Il n'y a ni pause en cours de question, ni fin anticipée de la partie en V1.
- Un vote ne casse ni ne prolonge la série.
- Le temps de réponse se mesure à partir du clic de l'animateur qui lance la question, jusqu'à la validation de la réponse.
- Seuls les membres du tenant Tasmane accèdent, pas les comptes invités.
- Un quiz sans question scorée se termine sans podium, sur la synthèse des votes.
- Pour un vote à choix multiple, la répartition est exprimée en pourcentage des votants, et son total peut dépasser 100 %.
- Les seuils de vérification (écart d'affichage d'au plus 1 s, téléphone de 360 px, 20 % de joueurs simulés en long-polling) viennent de la revue et restent à confirmer.

## Open Questions

- Choix multiple : tout ou rien (hypothèse retenue, voir Assumptions), ou des points partiels ?
- Offre OVH standard ou SecNumCloud ?
- Tasmane est-elle sous-traitante du client au sens du RGPD ? Combien de temps garde-t-on les résultats nominatifs (pseudos, réponses, scores) ? À trancher avant la purge de la V2.
- Quel est le nom exact du sous-domaine ? À trancher avant le jalon du 2026-10-16.
