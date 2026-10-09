# Étapes de validation et risques

## Étapes de validation

Les dates sont indicatives. Chaque étape doit être passée avant la suivante ; si l'une échoue, on corrige et on la rejoue, et l'inauguration glisse d'autant. C'est la qualité qui déclenche l'inauguration, pas le calendrier.

| # | Étape | Date indicative | Ce qu'elle valide |
|---|---|---|---|
| 1 | Une page vide déployée sur OVH, sur le sous-domaine Tasmane | dès que possible | La chaîne d'hébergement et de déploiement |
| 2 | Prototype temps réel et premier test de charge (protocole ci-dessous), avant de construire le reste | 2026-10-16 | Le risque principal : le temps réel en charge (CAP-6, CAP-23), y compris en long-polling |
| 3 | Mini-partie, 3 à 4 personnes | 2026-10-26 | Le parcours complet sur toutes les capacités : CAP-1 à CAP-24, y compris les trois formats, le vote, la reconnexion (CAP-11, CAP-16), l'export (CAP-20) et le journal (CAP-21) |
| 4 | Second test de charge, sur la V1 complète (même protocole) | avant la répétition | CAP-6 et CAP-11 en charge |
| 5 | Gel du code | la veille de la répétition | Seuls les correctifs bloquants passent ensuite |
| 6 | Répétition générale, 5 à 10 collègues, dont au moins un téléphone en 4G ; quiz Kahoot de secours prêt | 2026-10-30 | Le parcours, le réseau mobile, la page de test sur trois réseaux (CAP-17), le son dans Teams (CAP-9), le plan B |
| 7 | Inauguration : quiz interne, environ 40 participants sur place et à distance | 2026-11-02 | Le signal de succès |

## Protocole des tests de charge

- 50 joueurs simulés, depuis plusieurs machines, dont 20 % forcés en long-polling et quelques coupures suivies de reconnexions.
- Une partie complète avec les trois formats et un vote.
- Réussite : toutes les réponses émises et acquittées sont stockées, les scores recalculés sont identiques, et l'écart d'affichage entre grand écran et téléphones reste d'au plus 1 s au 95ᵉ centile.
- Un tir exploratoire à 200 joueurs est souhaitable, sans condition de réussite.

## Risques

| Risque | Parade |
|---|---|
| Le temps réel ne tient pas à 40-50 joueurs (risque principal) | Prototyper et tester la charge en premier (étape 2), selon le protocole. Une répétition à 10 personnes ne suffit pas à valider la charge. |
| Le wifi invité ou le pare-feu d'un client bloque le temps réel | HTTPS sur 443, repli long-polling testé en charge, page de test (CAP-17) à envoyer avant la séance, test en 4G à chaque répétition. |
| La mise en place de l'infrastructure OVH (base managée, stockage, déploiement, CI) prend du temps | Déployer une page vide sur le sous-domaine dès que possible (étape 1). |
| L'outil plante pendant l'inauguration malgré la validation | Plan B : quiz Kahoot de secours prêt dès la répétition générale. |
| La mascotte en diable de Tasmanie et le nom TazQuiz rappellent le Taz des Looney Tunes (Warner Bros.) : risque de propriété intellectuelle devant des clients | Retenir une mascotte nettement distincte du Taz et vérifier que le nom ne pose pas de conflit avant le premier usage client. |
| Un pseudo offensant échappe au filtre et s'affiche devant un client, sans exclusion possible | Filtre de gros mots à la saisie ; l'exclusion par l'animateur reste hors V1 (choix assumé). |
