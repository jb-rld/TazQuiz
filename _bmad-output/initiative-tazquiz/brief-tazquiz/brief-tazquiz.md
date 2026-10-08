---
title: TazQuiz — Brief produit
status: final
created: 2026-10-08
updated: 2026-10-08
---

# Brief produit : TazQuiz

## En bref

TazQuiz est l'application de quiz en direct de Tasmane, dans l'esprit de Kahoot. Un animateur projette la partie sur grand écran (et la partage dans Teams), et les joueurs, sur place ou à distance, répondent depuis leur téléphone avec un simple pseudo. Elle remplace Kahoot pour les séminaires clients, les formations et les moments collectifs.

Plus qu'une économie de licence, c'est un outil à Tasmane, une vitrine de son savoir-faire sur mesure et un premier projet de montée en compétence sur le développement assisté par l'IA. Sa valeur se joue sur l'expérience : un classement animé qui fait vivre la compétition, et une partie qui ne plante jamais.

Première utilisation réelle : un quiz interne avec ~40 collègues le **lundi 2 novembre 2026**.

## Pourquoi TazQuiz

Tasmane anime aujourd'hui ses quiz collectifs (séminaires clients, formations internes) avec Kahoot. Ça fonctionne, mais l'outil ne nous appartient pas. Le projet répond à quatre motivations :

- **Un outil à nous.** TazQuiz est possédé par Tasmane et personnalisable à volonté (charte, habillage, formats de questions). L'économie de la licence Kahoot (~1 000 €/an) est un plus, pas la justification.
- **Une vitrine du savoir-faire Tasmane.** Une partie de TazQuiz devant un client doit lui donner envie de dire « c'est vous qui avez fait ça ? ». Si un client veut l'outil pour lui, TazQuiz reste interne : on lui propose de lui construire le sien.
- **Une montée en compétence.** Le projet forme au moins deux personnes au développement assisté par l'IA, dont un profil non technique qui veut apprendre à créer ce type d'outil par lui-même. En cas de conflit, l'outil qui fonctionne passe avant l'apprentissage : déléguer est acceptable si le résultat est là.
- **Maîtriser la confidentialité.** Le besoin est anticipé plutôt que vécu : pouvoir mettre des données chiffrées d'un client dans une question sans les confier à un tiers. Aucune exigence réglementaire n'a été identifiée. Le niveau attendu est un hébergement maîtrisé par Tasmane, sans conservation inutile des données.

## Pour qui

**Les créateurs et animateurs : tout collaborateur Tasmane.**
- Ils se connectent avec leur compte Microsoft Tasmane. Le compte suffit pour accéder à l'application, et un départ de l'entreprise coupe l'accès automatiquement.
- Ils peuvent travailler à plusieurs sur un même quiz, chacun son tour (pas de coédition en direct).
- L'un des contributeurs lance la partie, en général seul, depuis l'ordinateur branché au projecteur.

**Les joueurs : clients ou collègues, jusqu'à ~100 par partie.**
- Ils rejoignent la partie avec un code PIN ou un QR code et un simple pseudo, sans compte ni inscription.
- Ils répondent sur leur téléphone, qui affiche aussi la question et les choix en petit, pour qu'ils puissent suivre sans regarder le grand écran.
- **Sur place**, ils regardent le grand écran 16:9.
- **À distance**, ils suivent le même écran partagé dans Teams. Le décalage de quelques secondes est accepté, sans compensation au classement.
- **En hybride**, les deux groupes jouent dans la même partie.

## Ce qui doit faire « waouh » : l'esprit de compétition

Ce qui fait le succès de Kahoot, c'est la compétition. TazQuiz doit soigner en priorité les moments qui la font vivre :

- **La salle d'attente** : les pseudos des joueurs apparaissent en direct sur le grand écran au fur et à mesure qu'ils rejoignent. La partie commence avant même la première question.
- **Le classement après chaque question** : c'est le moment fort. On doit *voir* les joueurs se dépasser, avec une animation, et pas seulement lire un nouveau tableau.
- **Les séries** : un joueur qui enchaîne les bonnes réponses est mis en avant (« en boost ») sur le grand écran et sur son téléphone.
- **Les bruitages** : ils rythment le compte à rebours, les réponses et le podium. En hybride, le son doit passer aussi dans le partage Teams.

Le reste peut rester sobre en V1. TazQuiz ne revendique aucune fonctionnalité que Kahoot n'aurait pas : sa différence tient à ce qu'il appartient à Tasmane et s'adapte à chaque contexte.

## Périmètre

### V1 : l'inauguration du 2 novembre 2026

Objectif : jouer en interne une partie complète et réussie avec ~40 collègues, sur place et à distance.

- **Créer un quiz :** questions QCM (4 choix, une ou plusieurs bonnes réponses) et Vrai/Faux.
- **Accès :** connexion avec le compte Microsoft Tasmane, et partage d'un quiz entre collègues.
- **Rejoindre une partie :** code PIN ou QR code, avec un simple pseudo ; les pseudos apparaissent en direct dans la salle d'attente du grand écran.
- **Partie en direct :** 50 joueurs simultanés (la cible produit reste 100), sur place, à distance et en hybride, avec la question affichée sur le téléphone.
- **Scores :** barème Kahoot, soit jusqu'à 1 000 points selon la vitesse, plus un bonus de série.
- **Classement :** affiché après chaque question, puis podium final.
- **Habillage :** charte Tasmane et un choix basique de fond d'écran.

**Si on est en retard**, on retire dans cet ordre :
1. le partage entre collègues ;
2. le QR code (on garde le PIN seul) ;
3. le bonus de série.

### V2 : les formats d'engagement
- sondage en temps réel ;
- nuage de mots ;
- image dévoilée progressivement ;
- logo Tasmane masquable et habillage aux couleurs d'un client ;
- tenue de charge jusqu'à 100 joueurs.

### V3 : les formats avancés
- placer un point sur une image ;
- analyse des résultats par joueur.

### Hors périmètre
- un service en libre-service pour les clients, ou une vente de l'outil (un client intéressé se voit proposer un outil construit pour lui) ;
- la coédition en direct d'un quiz ;
- une compensation du décalage pour les joueurs à distance.

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
| lun. 26 oct. 2026 | Mini-partie test à midi, 3 à 4 personnes |
| ven. 30 oct. 2026 | Répétition générale avec 5 à 10 collègues, dont au moins un téléphone en 4G |
| lun. 2 nov. 2026 | Inauguration : quiz interne, ~40 participants |

- **Le temps réel avec 40 à 50 joueurs** est le principal risque technique. Une répétition à 10 personnes ne le valide pas : il faut un test de charge qui simule 50 joueurs avant le 30 octobre.
- **Le réseau chez les clients** (wifi invité, pare-feu) : aucun incident vécu jusqu'ici. Le risque est accepté, avec un test en 4G à chaque répétition.
- **Le délai** est de 25 jours pour une équipe qui apprend. Plan B : garder Kahoot prêt le 2 novembre pour que la séance ait lieu quoi qu'il arrive.
