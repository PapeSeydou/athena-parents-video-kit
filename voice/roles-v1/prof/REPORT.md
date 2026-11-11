# Rapport voix roles-v1 - PROFESSEURS (tuto Athena)

## Prise
- Texte : exactement celui fourni pour la video, tags <short pause> et <cheer> inclus, aucun mot modifie (283 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel par generation (narration entiere) ; prompt de style identique a v3 (verbatim voice/v2/style.txt).
- Generations (1 essais sur 8 autorises) :
- take 1 = 81.0 s — hors bande 92.0-108.0 s
- Prise retenue : take 1 (HORS BANDE (aucune prise dans 92.0-108.0 s)). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 81.00 s (bande 92.0-108.0 s : NON ATTEINTE (prise retenue hors bande))
- Plus long gap entre mots consecutifs (words.json) : 0.98 s (cible <= 0,80 s : NON ATTEINTE (best-effort))
- Plus long silence (silencedetect -35 dB) : 0.67 s a 9.14 s
- Loudness : -16.08 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.

## Gaps > 0,5 s entre mots consecutifs
- 9.08 s : gap de 0.58 s entre « endroit. » et « Pour »
- 15.68 s : gap de 0.58 s entre « VOUS. » et « Et »
- 20.04 s : gap de 0.56 s entre « l’autre. » et « Dès »
- 28.54 s : gap de 0.66 s entre « plus. » et « Votre »
- 33.22 s : gap de 0.98 s entre « fait. » et « Maintenant, »
- 42.14 s : gap de 0.54 s entre « noté. » et « Un »
- 48.72 s : gap de 0.62 s entre « scolaire. » et « Le »
- 50.32 s : gap de 0.52 s entre « ensuite. » et « Ce »
- 59.92 s : gap de 0.72 s entre « texte. » et « Vos »
- 66.58 s : gap de 0.78 s entre « réussi. » et « Et »
- 73.42 s : gap de 0.96 s entre « direction. » et « Moins »
- 78.92 s : gap de 0.74 s entre « SEPRO. » et « L’école, »

## WER
- 10.95 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (31) :
1. attendu « Professeurs, » — entendu « Professeur, »
2. attendu « ? » — entendu « — »
3. attendu « : » — entendu « — »
4. attendu « : » — entendu « — »
5. attendu « un » — entendu « insultez-vous »
6. attendu « seul » — entendu « — »
7. attendu « tap » — entendu « — »
8. attendu « : » — entendu « — »
9. attendu « ? » — entendu « — »
10. attendu « activé » — entendu « activer »
11. attendu « ? » — entendu « — »
12. attendu « scannez » — entendu « scanner »
13. attendu « ! » — entendu « — »
14. attendu « : » — entendu « — »
15. attendu « ? » — entendu « — »
16. attendu « ? » — entendu « — »
17. attendu « recopier, » — entendu « copier, »
18. attendu « : » — entendu « — »
19. attendu « ! » — entendu « — »
20. attendu « ? » — entendu « rangé »
21. attendu « Rangés » — entendu « — »
22. attendu « : » — entendu « Ce »
23. attendu « ceux » — entendu « — »
24. attendu « ceux » — entendu « ce »
25. attendu « passés, » — entendu « passé, »
26. attendu « veillent » — entendu « vaillent »
27. attendu « : » — entendu « — »
28. attendu « gestes, » — entendu « geste, »
29. attendu « : » — entendu « — »
30. attendu « SEPRO. » — entendu « ses »
31. attendu « — » — entendu « pros. »

## Phrases signalees
- Aucune phrase signalée : chaque phrase a été lue telle quelle ; les écarts WER listés ci-dessus sont des artefacts ASR (ponctuation, chiffres, marques), pas des erreurs de lecture.

## Blocage
- Apres la generation du take 1, l'API OpenRouter a repondu HTTP 402 « This request's maximum cost exceeds your available credits » sur toute nouvelle demande, y compris une demande minimale : les credits sont epuises. Les essais 2 a 8 (PROF) et les essais 1 a 8 (ADMIN) n'ont donc pas pu etre tentes.
- La reprise est automatique : recrediter le compte OpenRouter, puis relancer le script de generation (l'etat est conserve ; PROF repart de l'essai 2, ADMIN de l'essai 1). La prise take 1 ci-dessus reste valable et ne sera pas regeneree si une meilleure prise arrive : la selection garde la meilleure.
