# Jalons et risques

## Jalons

| Date | Jalon | Ce qu'il valide |
|---|---|---|
| dès que possible | Une page vide déployée sur OVH, sur le sous-domaine Tasmane | La chaîne d'hébergement et de déploiement |
| avant le 2026-10-16 | Prototype temps réel et premier test de charge (protocole ci-dessous), avant de construire le reste | Le risque principal : le temps réel en charge (CAP-6), y compris en long-polling |
| ven. 2026-10-16 | **Revue de décision 1** | Prototype validé ? Sinon, revoir l'architecture et appliquer l'ordre de sacrifice |
| ven. 2026-10-23 | **Revue de décision 2** | CAP-1 à CAP-8, CAP-12 et CAP-22 fonctionnent ? Sinon, retirer les éléments suivants de l'ordre de sacrifice |
| lundi 2026-10-26, midi | Mini-partie, 3 à 4 personnes | Le parcours complet sur toutes les capacités : CAP-1 à CAP-22, y compris les trois formats, le vote, la reconnexion (CAP-11, CAP-16), l'export (CAP-20) et le journal (CAP-21) |
| avant le 2026-10-30 | Second test de charge, sur la V1 complète (même protocole) | CAP-6 et CAP-11 en charge |
| jeu. 2026-10-29, soir | Gel du code | Seuls les correctifs bloquants passent ensuite |
| ven. 2026-10-30 | Répétition générale, 5 à 10 collègues, dont au moins un téléphone en 4G ; quiz Kahoot de secours prêt | Le parcours, le réseau mobile, la page de test sur trois réseaux (CAP-17), le son dans Teams (CAP-9), le plan B |
| lundi 2026-11-02 | Inauguration : quiz interne, environ 40 participants sur place et à distance | Le signal de succès |

## Protocole des tests de charge

- 50 joueurs simulés, depuis plusieurs machines, dont 20 % forcés en long-polling et quelques coupures suivies de reconnexions.
- Une partie complète avec les trois formats et un vote.
- Réussite : toutes les réponses émises et acquittées sont stockées, les scores recalculés sont identiques, et l'écart d'affichage entre grand écran et téléphones reste d'au plus 1 s au 95ᵉ centile.
- Un tir exploratoire à 200 joueurs est souhaitable, sans condition de réussite.

## Ordre de sacrifice en cas de retard

Décidé par JBR et Paul à une revue de décision. Il s'applique sans nouvelle consultation, dans cet ordre :

1. Les aperçus de l'éditeur (CAP-19).
2. L'export Excel (CAP-20).
3. La duplication de quiz (CAP-18 ; la bibliothèque personnelle reste).
4. La page de test de connectivité (CAP-17).
5. La journalisation des accès (CAP-21).
6. Les images dans les questions (CAP-2).
7. Le partage entre collègues (CAP-3 ; un quiz reste privé, à son créateur seul, ou public).
8. Le QR code (CAP-4 ; on garde le PIN seul, et le critère de CAP-5 se mesure de la saisie du PIN à la salle d'attente).
9. Le bonus de série (CAP-7 ; on garde le score de vitesse, la série et le boost).

La question de classement (CAP-12), la mascotte (CAP-22) et la date ne peuvent pas être sacrifiées.

## Risques

| Risque | Parade |
|---|---|
| Le temps réel ne tient pas à 40-50 joueurs (risque principal) | Prototyper et tester la charge en premier, avant le 2026-10-16, selon le protocole. Une répétition à 10 personnes ne suffit pas à valider la charge. |
| Le wifi invité ou le pare-feu d'un client bloque le temps réel | HTTPS sur 443, repli long-polling testé en charge, page de test (CAP-17) à envoyer avant la séance, test en 4G à chaque répétition. |
| La mise en place de l'infrastructure OVH (base managée, stockage, déploiement, CI) prend du temps à une équipe débutante | Déployer une page vide sur le sous-domaine dès que possible. |
| Livrer la V1 élargie (22 capacités contre 11 au cadrage initial, dont trois intouchables avec la date) en 25 jours est ambitieux pour une équipe qui apprend | Risque accepté. Revues de décision datées, ordre de sacrifice, gel du code. Plan B : quiz Kahoot de secours prêt le 2026-10-30. |
| La mascotte en diable de Tasmanie et le nom TazQuiz rappellent le Taz des Looney Tunes (Warner Bros.) : risque de propriété intellectuelle devant des clients | Retenir une mascotte nettement distincte du Taz et vérifier que le nom ne pose pas de conflit avant le premier usage client. |
| Un pseudo offensant échappe au filtre et s'affiche devant un client, sans exclusion possible | Filtre de gros mots à la saisie ; l'exclusion par l'animateur reste hors V1 (choix assumé). |
