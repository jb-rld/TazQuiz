---
title: TazQuiz — Brief produit
status: final
created: 2026-10-08
updated: 2026-10-08
---

# Brief produit : TazQuiz

## En bref

TazQuiz est l'application de quiz et de vote en direct de Tasmane, dans l'esprit de Kahoot. Un animateur projette la partie sur grand écran (et la partage dans Teams). Les joueurs, sur place ou à distance, répondent depuis leur téléphone avec un simple pseudo. TazQuiz remplace Kahoot pour tous les moments collectifs de Tasmane : formations, SummerSchool, onboarding et séminaires en interne ; ateliers, formations, CODIR et restitutions chez les clients.

Plus qu'une économie de licence, c'est un outil souverain qui appartient à Tasmane, une vitrine de son savoir-faire sur mesure et un premier projet de montée en compétence sur le développement assisté par l'IA. Sa valeur se joue sur l'expérience : un classement animé qui fait vivre la compétition, et une partie qui ne plante jamais, même devant un client.

Première utilisation réelle : un quiz interne avec ~40 collègues le **lundi 2 novembre 2026**.

## Pourquoi TazQuiz

Tasmane anime aujourd'hui ses quiz collectifs avec Kahoot. Ça fonctionne, mais l'outil ne nous appartient pas. Le projet répond à quatre motivations :

- **Un outil à nous.** TazQuiz est possédé par Tasmane et personnalisable à volonté (charte, habillage, formats de questions). L'économie de la licence Kahoot (~1 000 €/an) est un plus, pas la justification.
- **Une vitrine du savoir-faire Tasmane.** Une partie de TazQuiz devant un client doit lui donner envie de dire « c'est vous qui avez fait ça ? ». Si un client veut l'outil pour lui, TazQuiz reste interne : on lui propose de lui construire le sien.
- **Une montée en compétence.** Le projet forme au moins deux personnes au développement assisté par l'IA, dont un profil non technique qui veut apprendre à créer ce type d'outil par lui-même. En cas de conflit, l'outil qui fonctionne passe avant l'apprentissage : déléguer est acceptable si le résultat est là.
- **La souveraineté et la confidentialité.** On doit pouvoir mettre des données chiffrées d'un client dans une question sans les confier à un tiers. TazQuiz est hébergé chez OVHcloud, en France, et aucun service hors UE ne reçoit le contenu des quiz ni les données des joueurs. Seule exception assumée : Entra ID (Microsoft), qui authentifie les animateurs sans rien voir des quiz. Côté joueurs, on ne demande que le pseudo, avec une mention RGPD à l'accueil. Le statut RGPD de Tasmane (sous-traitant du client) reste à valider, et la cohérence avec le Plan d'Assurance Sécurité Tasmane est prévue avant le premier usage client.

## Pour qui

**Les créateurs et animateurs : tout collaborateur Tasmane.**
- Ils se connectent avec leur compte Microsoft Tasmane. Le compte suffit pour accéder à l'application, et un départ de l'entreprise coupe l'accès automatiquement.
- Chacun retrouve ses quiz dans une bibliothèque personnelle et peut les dupliquer. Un quiz est privé par défaut (son créateur et les collègues avec qui il le partage) ou public : tout collaborateur peut alors le voir, l'animer et le dupliquer, mais seuls ses auteurs le modifient. Les quiz publics forment la bibliothèque commune de Tasmane.
- Ils peuvent travailler à plusieurs sur un même quiz, chacun son tour (pas de coédition en direct).
- L'un des contributeurs lance la partie, en général seul, depuis l'ordinateur branché au projecteur. Il donne le rythme : entre deux questions, la partie attend son clic.

**Les joueurs : clients ou collègues, jusqu'à 200 par partie à terme.**
- Ils rejoignent la partie avec un code PIN ou un QR code et un simple pseudo, sans compte ni inscription.
- Leur téléphone recopie intégralement la question et les réponses, sans rien tronquer : on peut jouer sans voir le grand écran. Chaque réponse garde la même couleur, la même forme et la même lettre (A à F) sur les deux écrans.
- Après chaque question, le téléphone leur dit s'ils ont répondu juste, quelle était la bonne réponse, combien de points ils ont gagné, leur score et leur rang.
- **Sur place**, ils regardent le grand écran 16:9.
- **À distance**, ils suivent le même écran partagé dans Teams. Le décalage de quelques secondes est accepté, sans compensation au classement.
- **En hybride**, les deux groupes jouent dans la même partie.
- Ils jouent souvent depuis un réseau qu'on ne maîtrise pas (wifi invité, réseau d'entreprise filtré, 4G). TazQuiz doit passer partout, et une page de test permet au client de vérifier son réseau avant la séance.

## Ce qui doit faire « waouh » : l'esprit de compétition

Ce qui fait le succès de Kahoot, c'est la compétition. TazQuiz doit soigner en priorité les moments qui la font vivre :

- **La salle d'attente** : les pseudos des joueurs apparaissent en direct sur le grand écran au fur et à mesure qu'ils rejoignent. La partie commence avant même la première question.
- **Le classement après chaque question** : c'est le moment fort. On doit *voir* les joueurs se dépasser, avec une animation, et pas seulement lire un nouveau tableau.
- **Les séries** : un joueur qui enchaîne les bonnes réponses est mis en avant (« en boost ») sur le grand écran et sur son téléphone.
- **Les bruitages** : ils rythment le compte à rebours, les réponses et le podium. En hybride, le son doit passer aussi dans le partage Teams.

TazQuiz ne revendique aucune fonctionnalité que Kahoot n'aurait pas : sa différence tient à ce qu'il appartient à Tasmane et s'adapte à chaque contexte.

## Périmètre

### V1 : l'inauguration du 2 novembre 2026

Objectif : jouer en interne une partie complète et réussie avec ~40 collègues, sur place et à distance, avec un outil déjà prêt pour un usage client. Tout ce qui suit est livré pour le 2 novembre.

- **Formats de questions :** choix simple (2 à 4 réponses, Vrai/Faux préconfiguré), choix multiple (2 à 6 réponses, nombre de bonnes réponses affichable) et **classement** (3 à 6 éléments à ordonner). Chaque question peut avoir une image et son propre temps limite.
- **Quiz ou vote :** chaque question est scorée ou non. Une question non scorée affiche la répartition des réponses, ou le rang moyen de chaque élément pour un classement (priorisation collective).
- **Éditeur :** bibliothèque personnelle, duplication, aperçu « écran projeté » et « vue téléphone ».
- **Accès et partage :** connexion avec le compte Microsoft Tasmane ; quiz privés par défaut, partageables avec des collègues ou rendus publics ; accès des animateurs journalisés.
- **Rejoindre une partie :** code PIN ou QR code, avec un simple pseudo et une mention RGPD ; les pseudos apparaissent en direct dans la salle d'attente du grand écran.
- **Partie en direct :** 50 joueurs simultanés, sur place, à distance et en hybride ; l'animateur lance chaque question d'un clic ; affichage complet sur le téléphone et retour immédiat après chaque question.
- **Robustesse :** fonctionne sur les réseaux filtrés (HTTPS sur le port 443, repli si le WebSocket est bloqué) ; page de test de connectivité ; un joueur déconnecté revient sans perdre son score ni sa série ; l'animateur reprend la partie s'il ferme sa page.
- **Scores :** barème Kahoot, soit de 500 à 1 000 points selon la vitesse, plus un bonus de série. Pour un classement, les points dépendent du nombre d'éléments bien placés.
- **Classement :** affiché après chaque question, puis podium final.
- **Après la partie :** export Excel détaillé des résultats.
- **Habillage :** charte Tasmane et un choix basique de fond d'écran.

**Si on est en retard**, on retire dans cet ordre :
1. les aperçus de l'éditeur ;
2. l'export Excel ;
3. la duplication de quiz ;
4. la page de test de connectivité ;
5. la journalisation des accès ;
6. les images dans les questions ;
7. le partage entre collègues ;
8. le QR code (on garde le PIN seul) ;
9. le bonus de série.

Le format classement et la date sont intouchables.

### V2 : engagement et prêt client

- sondage mis à jour en temps réel ;
- nuage de mots ;
- image dévoilée progressivement ;
- logo Tasmane masquable et habillage aux couleurs d'un client ;
- restitution client agrégée et anonymisée ;
- purge des résultats nominatifs après une durée à fixer, avec conservation des agrégats ;
- cohérence avec le Plan d'Assurance Sécurité et réponse aux questionnaires sécurité des clients ;
- génération de questions par IA ;
- tenue de charge jusqu'à 200 joueurs.

### V3 : les formats avancés

- placer un point sur une image ;
- analyse des résultats par joueur.

### Hors périmètre

- un service en libre-service pour les clients, ou une vente de l'outil (un client intéressé se voit proposer un outil construit pour lui) ;
- la coédition en direct d'un quiz ;
- une compensation du décalage pour les joueurs à distance ;
- les espaces par mission ou par client ;
- le mode asynchrone, le jeu en équipes et l'import de quiz Kahoot.

## Critères de succès

**Pour l'inauguration du 2 novembre**
- La partie va au bout sans qu'on ait besoin de Kahoot.
- Aucun joueur ne reste bloqué ou déconnecté sans pouvoir revenir.
- Rejoindre la partie prend moins de 30 secondes entre le scan du QR code et l'arrivée dans la salle d'attente.
- Les collègues réagissent spontanément (« c'est super, vous êtes trop forts »).

**Pour la vitrine client** (à partir des premières utilisations en séminaire)
- Les clients réagissent spontanément (« c'est fluide », « c'était un super moment », « c'est vous qui avez fait ça ? »).
- Des clients demandent à réutiliser l'outil.
- Aucune partie n'est interrompue par un bug devant un client.

**Pour la montée en compétence**
- Paul est capable de créer seul, avec l'IA, un outil interne de A à Z. TazQuiz est le premier, pas le dernier.

## Jalons et risques

| Date | Jalon |
|---|---|
| au plus tôt | Une page vide déployée chez OVH, sur le sous-domaine Tasmane |
| avant le 16 oct. 2026 | Prototype temps réel et test de charge simulant 50 joueurs, avant de construire le reste |
| lun. 26 oct. 2026 | Mini-partie test à midi, 3 à 4 personnes |
| avant le 30 oct. 2026 | Nouveau test de charge de 50 joueurs, sur la V1 complète |
| ven. 30 oct. 2026 | Répétition générale avec 5 à 10 collègues, dont au moins un téléphone en 4G |
| lun. 2 nov. 2026 | Inauguration : quiz interne, ~40 participants |

- **Le temps réel avec 40 à 50 joueurs** est le principal risque technique. Une répétition à 10 personnes ne le valide pas : il faut un test de charge dès le 16 octobre, avant de construire le reste, puis un second sur la V1 complète avant le 30 octobre.
- **Le réseau chez les clients** (wifi invité, pare-feu) n'est plus un risque qu'on accepte : le repli réseau et la page de test le couvrent, avec un test en 4G à chaque répétition.
- **L'infrastructure OVH** est un premier chantier pour une équipe qui débute : on la met en place dès le départ.
- **Le délai** : 25 jours pour une V1 élargie, avec une équipe qui apprend. Le risque est accepté. On applique l'ordre de sacrifice si besoin, et Kahoot reste prêt le 2 novembre pour que la séance ait lieu quoi qu'il arrive.

## Questions ouvertes

- Choix multiple : tout ou rien, ou des points partiels ?
- Offre OVH standard ou SecNumCloud ?
- Statut RGPD de Tasmane et durée de conservation des résultats nominatifs.
- Nom exact du sous-domaine Tasmane.
