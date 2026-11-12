# Rapport voix v4 - DIRECTION (administrateur) (tuto Athena)

## Prise
- Texte direction : base voice/roles-v1/admin (tags <short pause> et <cheer>), avec les trois remplacements de la consigne v4. (282 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel TTS par prise (narration entiere), prompt de style identique a la prise approuvee (verbatim voice/v2/style.txt). Cle : OPENROUTER_GEN_API_KEY.
- Generations (8 essais sur 8 autorises) :
- take 1 = 97.36 s — gap max > 0,8 s
- take 2 = 97.92 s — gap max > 0,8 s
- take 3 = 102.8 s — gap max > 0,8 s
- take 4 = 96.8 s — gap max > 0,8 s
- take 5 = 101.28 s — gap max > 0,8 s
- take 6 = 92.8 s — gap max > 0,8 s
- take 7 = 101.88 s — gap max > 0,8 s
- take 8 = 93.84 s — gap max > 0,8 s
- Prise retenue : take 8 (best-effort (dans la bande, gap max > 0,8 s)). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 93.84 s (bande 90.0-106.0 s : ATTEINTE)
- Plus long gap entre mots consecutifs (words.json) : 0.86 s (cible <= 0,80 s : NON ATTEINTE (best-effort))
- Plus long silence (silencedetect -35 dB) : 0.73 s a 16.82 s
- Loudness : -16.11 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.
- Lecture des mesures : le plus long silence (silencedetect -35 dB) est de 0,73 s ; l'écart de 0,86 s calculé sur words.json tombe sur une jonction de tag (<short pause> avant « Le suivi des professeurs »), avec la marge d'incertitude des timestamps ASR.

## Gaps > 0,5 s entre mots consecutifs
- 5.72 s : gap de 0.66 s entre « SEPRO. » et « Voici »
- 7.6 s : gap de 0.78 s entre « vous. » et « Vous »
- 13.98 s : gap de 0.64 s entre « profil. » et « Dès »
- 19.4 s : gap de 0.56 s entre « mois, » et « les »
- 21.62 s : gap de 0.64 s entre « sanctions. » et « Plus »
- 24.08 s : gap de 0.54 s entre « là. » et « Mon »
- 26.64 s : gap de 0.84 s entre « ici. » et « Et »
- 36.9 s : gap de 0.72 s entre « espèces. » et « Les »
- 43.44 s : gap de 0.72 s entre « premier. » et « Une »
- 45.8 s : gap de 0.84 s entre « s’affichent. » et « Même »
- 51.84 s : gap de 0.8 s entre « motif. » et « Les »
- 56.62 s : gap de 0.56 s entre « enseigne. » et « Et »
- 60.9 s : gap de 0.54 s entre « sanctions. » et « Une »
- 68.86 s : gap de 0.86 s entre « voient. » et « Le »
- 73.04 s : gap de 0.64 s entre « retard. » et « Et »
- 78.22 s : gap de 0.62 s entre « vérifier. » et « Enfin, »
- 83.0 s : gap de 0.54 s entre « transport, » et « les »
- 86.06 s : gap de 0.53 s entre « pointés. » et « Vous »
- 89.5 s : gap de 0.56 s entre « sécurité. » et « L’Application »

## WER
- 13.48 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (38) :
1. attendu « Piloter » — entendu « Pilotez »
2. attendu « baï » — entendu « by »
3. attendu « SEPRO. » — entendu « Cepro. »
4. attendu « tap » — entendu « tape »
5. attendu « : » — entendu « — »
6. attendu « et » — entendu « est »
7. attendu « de » — entendu « des »
8. attendu « les » — entendu « demandées, »
9. attendu « demander » — entendu « — »
10. attendu « : » — entendu « — »
11. attendu « : » — entendu « — »
12. attendu « : » — entendu « — »
13. attendu « facturé » — entendu « facturer »
14. attendu « : » — entendu « — »
15. attendu « Money, » — entendu « monnaie, »
16. attendu « espèces. » — entendu « espèce. »
17. attendu « ? » — entendu « élèvent »
18. attendu « Élève » — entendu « — »
19. attendu « ses » — entendu « c'est »
20. attendu « reçus » — entendu « reçu »
21. attendu « s’affichent. » — entendu « sa »
22. attendu « — » — entendu « fiche. »
23. attendu « : » — entendu « — »
24. attendu « : » — entendu « — »
25. attendu « : » — entendu « absence, »
26. attendu « absences, » — entendu « retard, »
27. attendu « retards, » — entendu « sanction. »
28. attendu « sanctions. » — entendu « — »
29. attendu « vous » — entendu « aux »
30. attendu « intrigue » — entendu « intrigues, »
31. attendu « ? » — entendu « — »
32. attendu « : » — entendu « — »
33. attendu « : » — entendu « — »
34. attendu « : » — entendu « — »
35. attendu « : » — entendu « — »
36. attendu « baï » — entendu « by »
37. attendu « SEPRO » — entendu « Cepro, »
38. attendu « : » — entendu « — »

## Phrases signalées
- « Piloter toute votre école depuis votre poche » : l'ASR entend « Pilotez ». Vérifier que l'infinitif s'entend (la phrase est un infinitif de présentation, pas un impératif).
- « Wave, Orange Money, espèces » : l'ASR entend « monnaie, espèce ». Vérifier la prononciation de « Orange Money » et le pluriel « espèces ».
- « Une facture, et ses reçus s'affichent » : l'ASR rend « sa fiche ». Vérifier « ses reçus s'affichent ».
- « Une classe vous intrigue ? » : l'ASR entend « intrigues ». Écart de liaison mineur, à vérifier.
- « baï SEPRO » transcrit « by Cepro » : rendu attendu et artefact ASR, aucun défaut.
- Aucune phrase n'a été coupée ni reformulée ; les écarts de ponctuation et d'accord sont des artefacts ASR.

## Texte envoyé au TTS
```text
Piloter toute votre école depuis votre poche, c’est possible avec L’Application Athena, baï SEPRO. Voici ce que cela change pour vous. <short pause> Vous vous connectez comme tout le monde, et si vous avez aussi un espace professeur ou parent, un tap suffit pour changer de profil. <short pause> Dès l’ouverture, l’essentiel vous attend : ce qui a été encaissé aujourd’hui et ce mois, les absents de la semaine, les sanctions. Plus besoin de les demander : ils sont là. Mon conseil : commencez votre journée par ici. <cheer> Et la finance, regardez comme c’est CLAIR : le facturé contre l’encaissé, mois par mois ou sur l’année, et les encaissements par mode : Wave, Orange Money, espèces. Les restants à recouvrer ? Élève par élève, et vous filtrez par cycle ou par mois pour savoir qui relancer en premier. Une facture, et ses reçus s’affichent. Même un document annulé reste visible : jamais supprimé, avec la date, la personne et le motif. <short pause> Les effectifs, ensuite : qui est inscrit, classe par classe, et qui enseigne. Et la vie scolaire, cycle par cycle : absences, retards, sanctions. Une classe vous intrigue ? Ouvrez-la : les élèves, la vie scolaire, et le cahier de texte publié par les professeurs, exactement comme les familles le voient. <short pause> Le suivi des professeurs, maintenant : qui a pointé, qui est en retard. Et rassurez-vous : un professeur non pointé n’est jamais compté absent, sa séance est simplement à vérifier. Enfin, les notifications vous alertent sur ce qui compte : les absences déclarées au transport, les restants à recouvrer, les professeurs non pointés. <cheer> Vous voyez TOUT, en un coup d’œil, et en toute sécurité. L’Application Athena, baï SEPRO : l’école, plus près de vous.
```
