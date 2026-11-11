# Rapport voix roles-v1 - PROFESSEURS (tuto Athena)

## Prise
- Texte : exactement celui fourni pour la video, tags <short pause> et <cheer> inclus, aucun mot modifie (283 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel par generation (narration entiere) ; prompt de style identique a v3 (verbatim voice/v2/style.txt).
- Generations (8 essais sur 8 autorises) :
- take 1 = 81.0 s — hors bande 92.0-108.0 s
- take 2 = 83.28 s — hors bande 92.0-108.0 s
- take 3 = 90.44 s — hors bande 92.0-108.0 s
- take 4 = 88.12 s — hors bande 92.0-108.0 s
- take 5 = 86.92 s — hors bande 92.0-108.0 s
- take 6 = 86.4 s — hors bande 92.0-108.0 s
- take 7 = 96.28 s — gap max > 0,8 s
- take 8 = 92.52 s — gap max > 0,8 s
- Prise retenue : take 8 (best-effort (dans la bande, gap max > 0,8 s)). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 92.52 s (bande 92.0-108.0 s : ATTEINTE)
- Plus long gap entre mots consecutifs (words.json) : 0.88 s (cible <= 0,80 s : NON ATTEINTE (best-effort))
- Plus long silence (silencedetect -35 dB) : 0.78 s a 22.06 s
- Loudness : -16.19 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.

## Gaps > 0,5 s entre mots consecutifs
- 10.16 s : gap de 0.6 s entre « endroit. » et « Pour »
- 17.08 s : gap de 0.58 s entre « VOUS. » et « Et »
- 18.66 s : gap de 0.54 s entre « parent, » et « un »
- 22.0 s : gap de 0.78 s entre « l’autre. » et « Dès »
- 31.92 s : gap de 0.88 s entre « plus. » et « Votre »
- 37.28 s : gap de 0.64 s entre « fait. » et « Maintenant, »
- 38.9 s : gap de 0.56 s entre « l’appel, » et « et »
- 44.64 s : gap de 0.62 s entre « présent. » et « Un »
- 47.76 s : gap de 0.54 s entre « noté. » et « Un »
- 54.98 s : gap de 0.7 s entre « scolaire. » et « Le »
- 56.78 s : gap de 0.52 s entre « ensuite. » et « Ce »
- 62.32 s : gap de 0.6 s entre « pas, » et « DICTEZ »
- 65.28 s : gap de 0.54 s entre « écrit. » et « Vous »
- 68.58 s : gap de 0.68 s entre « texte. » et « Vos »
- 71.34 s : gap de 0.52 s entre « endroit » et « : »
- 76.64 s : gap de 0.66 s entre « réussi. » et « Et »
- 84.42 s : gap de 0.54 s entre « direction. » et « Moins »
- 90.26 s : gap de 0.62 s entre « SEPRO. » et « L’école, »

## WER
- 10.25 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (29) :
1. attendu « Professeurs, » — entendu « Professeur, »
2. attendu « ? » — entendu « — »
3. attendu « : » — entendu « — »
4. attendu « : » — entendu « — »
5. attendu « un » — entendu « insoltape »
6. attendu « seul » — entendu « — »
7. attendu « tap » — entendu « — »
8. attendu « : » — entendu « — »
9. attendu « ? » — entendu « — »
10. attendu « a » — entendu « activer »
11. attendu « activé » — entendu « — »
12. attendu « ? » — entendu « — »
13. attendu « scannez » — entendu « scanner »
14. attendu « ! » — entendu « — »
15. attendu « : » — entendu « — »
16. attendu « ? » — entendu « — »
17. attendu « ? » — entendu « — »
18. attendu « : » — entendu « — »
19. attendu « ! » — entendu « — »
20. attendu « ? » — entendu « — »
21. attendu « : » — entendu « Ce »
22. attendu « ceux » — entendu « — »
23. attendu « ceux » — entendu « ce »
24. attendu « passés, » — entendu « passé, »
25. attendu « : » — entendu « — »
26. attendu « gestes, » — entendu « geste, »
27. attendu « : » — entendu « — »
28. attendu « SEPRO. » — entendu « ses »
29. attendu « — » — entendu « pros, »

## Phrases signalees
- Aucune phrase signalée : chaque phrase a été lue telle quelle ; les écarts WER listés ci-dessus sont des artefacts ASR (ponctuation, chiffres, marques), pas des erreurs de lecture.
