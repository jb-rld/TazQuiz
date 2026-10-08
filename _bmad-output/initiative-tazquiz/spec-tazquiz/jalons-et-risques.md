# Jalons et risques

## Jalons

| Date | Jalon | Ce qu'il valide |
|---|---|---|
| au plus tôt | Une page vide déployée sur OVH, sur le sous-domaine Tasmane | La chaîne d'hébergement et de déploiement |
| avant le 2026-10-16 | Prototype temps réel et test de charge : 50 joueurs simulés, avant de construire le reste | Le risque principal, au plus tôt |
| lun. 2026-10-26, midi | Mini-partie, 3 à 4 personnes | Le parcours complet, de CAP-4 à CAP-8, les trois formats et la reconnexion (CAP-11, CAP-16) |
| avant le 2026-10-30 | Nouveau test de charge, 50 joueurs simulés, sur la V1 complète | CAP-6 en charge, sans perte de réponse |
| ven. 2026-10-30 | Répétition générale, 5 à 10 collègues, dont au moins un téléphone en 4G | Le parcours, le réseau mobile, la page de test (CAP-17), le son dans Teams (CAP-9) |
| lun. 2026-11-02 | Inauguration : quiz interne, ~40 participants sur place et à distance | Le signal de succès |

## Ordre de sacrifice en cas de retard

Toute la V1 est engagée pour le 2 novembre. Seulement en cas de retard avéré, on retire dans cet ordre :

1. Les aperçus de l'éditeur (CAP-19).
2. L'export Excel (CAP-20).
3. La duplication de quiz (CAP-18 ; la bibliothèque personnelle reste).
4. La page de test de connectivité (CAP-17).
5. La journalisation des accès (CAP-21).
6. Les images dans les questions (CAP-2).
7. Le partage entre collègues (CAP-3 ; un quiz reste privé ou public).
8. Le QR code (CAP-4 ; on garde le PIN seul).
9. Le bonus de série (CAP-7 ; on garde le score selon la vitesse).

Le format classement (CAP-12) et la date sont intouchables.

## Risques

| Risque | Parade |
|---|---|
| Le temps réel ne tient pas à 40-50 joueurs (risque principal) | Prototyper et tester la charge en premier, avant le 2026-10-16. Une répétition à 10 personnes ne suffit pas à valider la charge. |
| Le wifi invité ou le pare-feu d'un client bloque le temps réel | HTTPS sur 443, repli long-polling, page de test (CAP-17, résultat vert, orange ou rouge) à envoyer avant la séance, test en 4G à chaque répétition. |
| La mise en place de l'infrastructure OVH (base managée, stockage, déploiement, CI) prend du temps à une équipe débutante | Déployer une page vide sur le sous-domaine au plus tôt. |
| La V1 élargie en 25 jours pour une équipe qui apprend | Risque accepté. Appliquer l'ordre de sacrifice. Plan B : garder Kahoot prêt le 2026-11-02 pour assurer la séance. |
