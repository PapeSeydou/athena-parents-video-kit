# Rapport voix v3 - narration tuto Athena parents

## Prise
- Texte : identique a v2 (voice/narration-propre.txt), seule difference : le tag <sigh> apres « Et voila, c'est REGLE ! » a ete retire. Wording et autres tags inchanges.
- Modele : google/gemini-3.8-flash-tts, voix Kore, un seul appel pour toute la narration ; prompt de style identique a v2.
- Generations : take 1 = 81,84 s, take 2 = 80,60 s, take 3 = 74,40 s (hors bande 85-92 s), puis cycle v3 : take 4 = 85,60 s (gap max 1,42 s, rejet), take 10 = 87.32 s (retenu).

## Mesures
- Duree totale : 87.32 s (cible 85-92 s : atteinte)
- Plus long gap entre mots consecutifs (words.json) : 1.42 s (cible <= 0,80 s : NON ATTEINTE)
- Plus long silence (silencedetect -35 dB) : 1.09 s a 77.52 s
- Loudness : -16.13 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono
- Aucun traitement de tempo, de hauteur ou de vitesse. Aucune edition audio.

## Gaps > 0,5 s entre mots consecutifs
- 11.28 s : gap de 1.02 s entre « AUSSITÔT. » et « Un »
- 15.32 s : gap de 0.56 s entre « vous, » et « et »
- 18.56 s : gap de 0.7 s entre « accès. » et « Saisissez-le, »
- 21.02 s : gap de 0.62 s entre « VOUS. » et « Bienvenue »
- 29.56 s : gap de 0.98 s entre « affiché. » et « Et »
- 38.62 s : gap de 1.42 s entre « enfant. » et « Les »
- 45.44 s : gap de 0.8 s entre « sanctions, » et « le »
- 48.72 s : gap de 0.62 s entre « journée... » et « tout »
- 49.8 s : gap de 0.56 s entre « là, » et « LIMPIDE. »
- 52.92 s : gap de 0.72 s entre « d’œil. » et « Les »
- 57.16 s : gap de 0.6 s entre « listé. » et « Sélectionnez »
- 58.76 s : gap de 0.52 s entre « facture, » et « choisissez »
- 70.78 s : gap de 0.96 s entre « ici. » et « Et »
- 74.68 s : gap de 0.7 s entre « DIRECT » et « : »
- 77.5 s : gap de 0.8 s entre « restants. » et « La »
- 82.38 s : gap de 1.04 s entre « vous. » et « Athena »
- 85.04 s : gap de 0.52 s entre « SEPRO. » et « L’école, »

## WER
- 8.3 % (faster-whisper small, alignement normalise identique a v2 ; ecarts dominés par des rendus ASR : ponctuation, singuliers/pluriels, formats numeriques, marques).
- Ecarts (21) :
1. attendu « : » — entendu « — »
2. attendu « ! » — entendu « — »
3. attendu « : » — entendu « — »
4. attendu « carnets » — entendu « carnet »
5. attendu « trimestre » — entendu « trimestres »
6. attendu « absences, » — entendu « absence, »
7. attendu « retards » — entendu « retard »
8. attendu « sanctions, » — entendu « sanction, »
9. attendu « : » — entendu « — »
10. attendu « réglées, » — entendu « régler, »
11. attendu « Max » — entendu « Maxit »
12. attendu « It » — entendu « — »
13. attendu « file » — entendu « fil »
14. attendu « ! » — entendu « — »
15. attendu « : » — entendu « — »
16. attendu « : » — entendu « Montez »
17. attendu « monté » — entendu « — »
18. attendu « 7 » — entendu « 7h12, »
19. attendu « heures » — entendu « — »
20. attendu « 12, » — entendu « — »
21. attendu « SEPRO. » — entendu « CEPRO, »
