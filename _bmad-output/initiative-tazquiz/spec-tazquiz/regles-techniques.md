# Règles techniques

Exigences de comportement issues de la revue du 2026-10-09. Elles font partie du contrat ; le mécanisme qui les satisfait est laissé à l'architecture, qui peut en proposer une autre formulation argumentée.

## Temps et réponses

- Le temps de réponse `t` est mesuré par le serveur, du lancement de la question par l'animateur à la réception de la réponse confirmée, et borné à [0, T].
- Une réponse reçue après `T` plus une tolérance courte est refusée.
- Une réponse est comptée une seule fois par joueur et par question, même si elle est renvoyée après une reconnexion ; la première reçue fait foi pour `t`.
- Une question se clôt une seule fois, à la fin du chrono ou à la révélation anticipée (CAP-23), même si les deux arrivent en même temps. Après la clôture, aucune réponse n'est acceptée.

## État de la partie

- L'état de la partie (question en cours, chronos, scores, séries, thème, fond, niveau de la mascotte) vit côté serveur. Il est renvoyé à chaque connexion et reconnexion d'un joueur ou de l'animateur (CAP-10, CAP-11, CAP-16).
- Un joueur sans compte est reconnu à son retour par un identifiant conservé sur son téléphone.
- Une seule session pilote une partie à la fois ; la reprise ferme la précédente. Une même commande envoyée deux fois (par exemple « question suivante ») n'a d'effet qu'une fois.
- Si l'animateur est absent pendant une question, le serveur la clôt à la fin du chrono et attend son retour.
- Une partie abandonnée expire après une période d'inactivité ; les téléphones affichent alors un écran de fin.
- Le PIN est unique parmi les parties en cours et n'est plus valide après la fin de la partie.

## Quiz

- Une partie joue une copie du quiz figée au lancement : une modification ou une suppression pendant la partie ne la change pas.
- Une seule personne modifie un quiz à la fois. Le verrou expire si elle quitte sans le libérer. Une seconde ouverture se fait en lecture seule, sans écrasement silencieux.

## Son et confidentialité

- Le son est activé par une action de l'animateur, car les navigateurs bloquent la lecture automatique (CAP-9).
- Aucune ressource tierce hors UE n'est chargée par le grand écran ni par les téléphones : polices, CDN, génération de QR code, mesure d'audience. Cela vaut aussi pour les outils de test de charge qui reçoivent des données.
