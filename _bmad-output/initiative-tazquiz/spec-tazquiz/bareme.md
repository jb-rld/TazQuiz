# Barème (CAP-7)

Ce barème reprend la mécanique de Kahoot. Il n'a pas été confirmé au point près : voir les hypothèses de la spec. Il ne s'applique qu'aux questions scorées.

## Règles

| Élément | Règle |
|---|---|
| Score de vitesse | `arrondi(1000 × (1 − (t / T) / 2))`, où `t` est le temps entre le lancement de la question par l'animateur et la validation de la réponse, et `T` le temps limite de la question. Il va de 500 à 1 000 points, hors bonus. |
| Choix simple ou multiple juste | Score de vitesse. Pour un choix multiple, il faut cocher exactement les bonnes réponses ; une réponse partielle compte comme fausse. *(hypothèse ; question ouverte)* |
| Question de classement (CAP-12) | On compte les paires d'éléments dans le bon ordre relatif. **Juste** (toutes les paires) : score de vitesse, la série continue. **Partiel** (au moins une paire, pas toutes) : `arrondi(score de vitesse × paires bien ordonnées / nombre de paires)`, sans bonus, la série retombe à 0. **Faux** (aucune paire, ordre exactement inversé) : 0 point, la série retombe à 0. |
| Réponse fausse, ou pas de réponse | 0 point. La série retombe à 0. |
| Question entièrement manquée par déconnexion (CAP-11) | 0 point. La série est gelée : ni cassée ni prolongée. |
| Vote (CAP-13) | Aucun point. La série n'est ni cassée ni prolongée. *(hypothèse)* |
| Bonus de série | Ajouté au score de vitesse d'une réponse juste : 2ᵉ bonne réponse consécutive +100, 3ᵉ +200, 4ᵉ +300, 5ᵉ +400, 6ᵉ et suivantes +500. Une question rapporte donc au plus 1 500 points. |
| Boost | Il s'active dès que la série atteint 2 et disparaît quand elle retombe à 0. |
| Égalité de score | Les ex æquo partagent le même rang. |
| Arrondi | À l'entier le plus proche, 0,5 arrondi au-dessus. *(hypothèse)* |

## Exemples chiffrés

| Cas | Calcul | Points |
|---|---|---|
| Choix simple juste, `t` = 0 s, `T` = 20 s | 1000 × (1 − 0) | 1 000 |
| Choix simple juste, `t` = 10 s, `T` = 20 s | 1000 × (1 − 0,25) | 750 |
| Choix simple juste, `t` = `T` = 20 s | 1000 × (1 − 0,5) | 500 |
| Même réponse à 10 s, 3ᵉ bonne réponse consécutive | 750 + 200 | 950 |
| 7ᵉ bonne réponse consécutive, `t` = 0 s | 1 000 + 500 | 1 500 |
| Classement de 4 éléments (6 paires), 5 paires bien ordonnées, `t` = 10 s, `T` = 20 s | arrondi(750 × 5/6) = arrondi(625) | 625, série à 0 |
| Classement de 3 éléments (3 paires), 1 paire bien ordonnée, `t` = 0 s | arrondi(1000 × 1/3) = arrondi(333,3) | 333, série à 0 |
| Classement de 4 éléments exactement inversé | aucune paire | 0, série à 0 |
