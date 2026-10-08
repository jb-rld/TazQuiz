# Barème (CAP-7)

Ce barème reprend la mécanique de Kahoot. Il n'a pas été confirmé au point près : voir les hypothèses de la spec.

| Élément | Règle |
|---|---|
| Mauvaise réponse ou absence de réponse | 0 point. La série retombe à 0. |
| Bonne réponse | `arrondi(1000 × (1 − (t / T) / 2))`, où `t` est le temps de réponse et `T` la durée de la question. Une bonne réponse rapporte donc entre 500 et 1 000 points. |
| QCM à plusieurs bonnes réponses | Il faut cocher exactement les bonnes réponses. Une réponse partielle compte comme fausse. *(hypothèse)* |
| Bonus de série | À partir de la 2ᵉ bonne réponse consécutive : +100 par réponse de la série au-delà de la première, plafonné à +500. |
| Mise en avant « boost » | Elle s'active dès que la série atteint 2. |
