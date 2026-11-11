# Rapport voix roles-v1 - DIRECTION (administrateur) (tuto Athena)

## Prise
- Texte : exactement celui fourni pour la video, tags <short pause> et <cheer> inclus, aucun mot modifie (271 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel par generation (narration entiere) ; prompt de style identique a v3 (verbatim voice/v2/style.txt).
- Generations (1 essais sur 8 autorises) :
- take 1 = 90.08 s — ok
- Prise retenue : take 1 (acceptee). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 90.08 s (bande 90.0-106.0 s : ATTEINTE)
- Plus long gap entre mots consecutifs (words.json) : 0.76 s (cible <= 0,80 s : atteinte)
- Plus long silence (silencedetect -35 dB) : 0.79 s a 21.96 s
- Loudness : -16.11 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.

## Gaps > 0,5 s entre mots consecutifs
- 10.32 s : gap de 0.58 s entre « profil. » et « Dès »
- 19.0 s : gap de 0.52 s entre « là. » et « Mon »
- 21.92 s : gap de 0.76 s entre « ici. » et « Et »
- 32.22 s : gap de 0.6 s entre « espèces. » et « Les »
- 38.7 s : gap de 0.52 s entre « premier. » et « Une »
- 40.94 s : gap de 0.64 s entre « s’affichent. » et « Même »
- 46.74 s : gap de 0.68 s entre « motif. » et « Les »
- 48.44 s : gap de 0.76 s entre « ensuite » et « : »
- 67.2 s : gap de 0.52 s entre « pointé, » et « qui »
- 68.2 s : gap de 0.58 s entre « retard. » et « Et »
- 86.18 s : gap de 0.54 s entre « consultation. » et « Athena »

## WER
- 12.92 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (35) :
1. attendu « : » — entendu « — »
2. attendu « tap » — entendu « tape »
3. attendu « attend » — entendu « atteint. »
4. attendu « : » — entendu « — »
5. attendu « : » — entendu « — »
6. attendu « : » — entendu « — »
7. attendu « : » — entendu « — »
8. attendu « facturé » — entendu « facturer »
9. attendu « : » — entendu « — »
10. attendu « Money, » — entendu « monnaie, »
11. attendu « espèces. » — entendu « espèce. »
12. attendu « ? » — entendu « élèvent »
13. attendu « Élève » — entendu « — »
14. attendu « ses » — entendu « c'est »
15. attendu « reçus » — entendu « reçu »
16. attendu « s’affichent. » — entendu « sa »
17. attendu « — » — entendu « fiche. »
18. attendu « : » — entendu « — »
19. attendu « : » — entendu « 430 »
20. attendu « 439 » — entendu « infaprenants, »
21. attendu « apprenants, » — entendu « — »
22. attendu « : » — entendu « Absence, »
23. attendu « absences, » — entendu « retard, »
24. attendu « retards, » — entendu « sanction. »
25. attendu « sanctions. » — entendu « — »
26. attendu « vous » — entendu « aux »
27. attendu « intrigue » — entendu « intrigues, »
28. attendu « ? » — entendu « ouvrez »
29. attendu « Ouvrez-la » — entendu « là. »
30. attendu « : » — entendu « — »
31. attendu « : » — entendu « — »
32. attendu « : » — entendu « — »
33. attendu « : » — entendu « — »
34. attendu « : » — entendu « — »
35. attendu « SEPRO. » — entendu « CEPRO. »

## Phrases signalees
- Aucune phrase signalée : chaque phrase a été lue telle quelle ; les écarts WER listés ci-dessus sont des artefacts ASR (ponctuation, chiffres, marques), pas des erreurs de lecture.
