# Barème (CAP-7)

Ce barème reprend la mécanique de Kahoot. Il n'a pas été confirmé au point près : voir les hypothèses de la spec. Il ne s'applique qu'aux questions scorées.

| Élément | Règle |
|---|---|
| Mauvaise réponse ou absence de réponse (hors classement partiel) | 0 point. La série retombe à 0. |
| Bonne réponse (« score de vitesse ») | `arrondi(1000 × (1 − (t / T) / 2))`, où `t` est le temps de réponse mesuré depuis le lancement de la question par l'animateur, et `T` le temps limite de la question. Une bonne réponse rapporte donc entre 500 et 1 000 points. |
| Choix multiple | Il faut cocher exactement les bonnes réponses. Une réponse partielle compte comme fausse. *(hypothèse ; question ouverte)* |
| Classement (CAP-12) | Trois états. **Juste** (ordre exact) : points pleins selon la vitesse, la série continue. **Partiel** (au moins un élément bien placé) : `arrondi(score de vitesse × éléments bien placés / nombre d'éléments)`, la série retombe à 0. **Faux** (aucun élément bien placé) : 0 point, la série retombe à 0. |
| Question non scorée (CAP-13) | Aucun point. La série n'est ni cassée ni prolongée. *(hypothèse)* |
| Bonus de série | À partir de la 2ᵉ bonne réponse consécutive : +100 par réponse de la série au-delà de la première, plafonné à +500. |
| Mise en avant « boost » | Elle s'active dès que la série atteint 2. |
