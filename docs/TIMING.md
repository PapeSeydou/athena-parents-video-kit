# Timing — coupes et assemblage

## Coupes du take final (94,32 s)

Détection : RMS par fenêtres de 20 ms, seuil = max(150, P95 x 0,06), silences de >= 160 ms,
coupe placée à début du silence + 50 ms (aucune phrase coupée), choisie par proximité (< 2,6 s)
avec la position proportionnelle du nombre de caractères parlés.

| Frontière | Temps (s) |
|---|---|
| Scène 1 -> 2 | 3,89 |
| 2 -> 3 | 12,49 |
| 3 -> 4 | 23,57 |
| 4 -> 5 | 32,77 |
| 5 -> 6 | 59,25 |
| 6 -> 7 | 70,85 |
| 7 -> 8 | 77,35 |
| 8 -> 9 | 89,59 |
| Fin | 94,32 |

## Montage du film (règle des queues)

Chaque scène dure voix + 0,4 à 0,6 s de queue (les jonctions sonnent coupées sans ça) :

| Scène | Début (s) | Durée (s) |
|---|---|---|
| 1 ouverture | 0 | 4,39 |
| 2 connexion | 4,39 | 9,10 |
| 3 code + PIN | 13,49 | 11,58 |
| 4 accueil | 25,07 | 9,70 |
| 5 scolarité | 34,77 | 26,98 |
| 6 factures | 61,75 | 12,10 |
| 7 notifications | 73,85 | 7,00 |
| 8 bus + réinscription | 80,85 | 12,74 |
| 9 fin | 93,59 | 5,23 |
| **TOTAL** | | **98,8** |

## Fichiers

`voice/scene_01.wav` à `scene_09.wav` = découpes prêtes (loudness équilibrée à ±2 dB,
clampée, la prise maîtresse n'est pas retouchée). `voice/narration_complet.wav` = take maître.

## Livraison audio — format retenu (un seul WAV + bornes)

Le take maître est `voice/narration_complet.wav` (94,32 s). Bornes de chaque scène DANS ce fichier
(début inclut, fin exclut) :

| Scène | Début (s) | Fin (s) |
|---|---|---|
| 1 ouverture | 0,00 | 3,89 |
| 2 connexion | 3,89 | 12,49 |
| 3 code + PIN | 12,49 | 23,57 |
| 4 accueil | 23,57 | 32,77 |
| 5 scolarité | 32,77 | 59,25 |
| 6 factures | 59,25 | 70,85 |
| 7 notifications | 70,85 | 77,35 |
| 8 bus + réinscription | 77,35 | 89,59 |
| 9 fin | 89,59 | 94,32 |

Pour le montage, ajouter 0,4 à 0,6 s de queue après chaque fin (voir le tableau de démarrages du film
plus haut). Les `voice/scene_XX.wav` sont fournies par commodité (mêmes bornes, loudness équilibrée),
mais la référence est le take maître + ce tableau.
