# Rapport voix v4 - PROFESSEURS (tuto Athena)

## Prise
- Texte professeur : base voice/roles-v1/prof (tags <short pause> et <cheer>), avec les trois remplacements de la consigne v4. La consigne dit « Athena School by SEPRO » ; le texte approuve porte « Athena School, par SEPRO » : la phrase visee est remplacee dans les deux cas, le resultat est identique. (280 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel TTS par prise (narration entiere), prompt de style identique a la prise approuvee (verbatim voice/v2/style.txt). Cle : OPENROUTER_GEN_API_KEY.
- Generations (8 essais sur 8 autorises) :
- take 1 = 85.32 s — hors bande 92.0-108.0 s
- take 2 = 92.48 s — gap max > 0,8 s
- take 3 = 80.96 s — hors bande 92.0-108.0 s
- take 4 = 86.16 s — hors bande 92.0-108.0 s
- take 5 = 92.48 s — gap max > 0,8 s
- take 6 = 79.68 s — hors bande 92.0-108.0 s
- take 7 = 81.72 s — hors bande 92.0-108.0 s
- take 8 = 81.84 s — hors bande 92.0-108.0 s
- Prise retenue : take 5 (best-effort (dans la bande, gap max > 0,8 s)). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 92.48 s (bande 92.0-108.0 s : ATTEINTE)
- Plus long gap entre mots consecutifs (words.json) : 0.88 s (cible <= 0,80 s : NON ATTEINTE (best-effort))
- Plus long silence (silencedetect -35 dB) : 0.86 s a 34.94 s
- Loudness : -16.11 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.
- Lecture des mesures : le plus long silence (silencedetect -35 dB) est de 0,86 s à 34,94 s, au même endroit que l'écart de 0,88 s de words.json (jonction après « et c'est fait. » et le tag <cheer>). La cible de 0,8 s est dépassée de 0,06 s à cette seule jonction.

## Gaps > 0,5 s entre mots consecutifs
- 7.92 s : gap de 0.66 s entre « poche. » et « Pour »
- 14.14 s : gap de 0.52 s entre « PIN, » et « et »
- 15.74 s : gap de 0.64 s entre « VOUS. » et « Et »
- 20.68 s : gap de 0.8 s entre « l’autre. » et « Dès »
- 34.9 s : gap de 0.88 s entre « fait. » et « Maintenant, »
- 42.42 s : gap de 0.68 s entre « présent. » et « Un »
- 44.82 s : gap de 0.52 s entre « touchez. » et « C’est »
- 45.84 s : gap de 0.72 s entre « noté. » et « Un »
- 51.18 s : gap de 0.54 s entre « recopier, » et « tout »
- 53.84 s : gap de 0.64 s entre « scolaire. » et « Le »
- 55.86 s : gap de 0.58 s entre « ensuite. » et « Ce »
- 63.74 s : gap de 0.64 s entre « écrit. » et « Vous »
- 67.36 s : gap de 0.62 s entre « texte. » et « Vos »
- 75.04 s : gap de 0.56 s entre « réussi. » et « Et »
- 83.12 s : gap de 0.64 s entre « direction. » et « Moins »
- 90.12 s : gap de 0.7 s entre « : » et « l’école, »

## WER
- 12.86 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (36) :
1. attendu « ? » — entendu « Chez »
2. attendu « C’est » — entendu « — »
3. attendu « baï » — entendu « by »
4. attendu « SEPRO, » — entendu « CEPRO »
5. attendu « : » — entendu « — »
6. attendu « un » — entendu « installe »
7. attendu « seul » — entendu « tape »
8. attendu « tap » — entendu « — »
9. attendu « : » — entendu « — »
10. attendu « ? » — entendu « — »
11. attendu « tap. » — entendu « tape. »
12. attendu « activé » — entendu « activer »
13. attendu « ? » — entendu « — »
14. attendu « scannez » — entendu « scanner »
15. attendu « ! » — entendu « — »
16. attendu « : » — entendu « — »
17. attendu « ? » — entendu « — »
18. attendu « ? » — entendu « — »
19. attendu « petit » — entendu « petits »
20. attendu « conseil » — entendu « conseils »
21. attendu « : » — entendu « — »
22. attendu « DICTEZ » — entendu « dictés. »
23. attendu « ! » — entendu « — »
24. attendu « ? » — entendu « — »
25. attendu « : » — entendu « Ce »
26. attendu « ceux » — entendu « avenir, »
27. attendu « à » — entendu « ce »
28. attendu « venir, » — entendu « — »
29. attendu « ceux » — entendu « — »
30. attendu « passés, » — entendu « passé. »
31. attendu « : » — entendu « — »
32. attendu « gestes, » — entendu « geste, »
33. attendu « : » — entendu « — »
34. attendu « baï » — entendu « by »
35. attendu « SEPRO » — entendu « Cepro. »
36. attendu « : » — entendu « — »

## Phrases signalées
- « Et si vous êtes aussi parent, un seul tap sur votre profil » : l'ASR entend « un installe tape » (le groupe « un seul tap » est mal segmenté). Cette phrase avait déjà été signalée sur la prise roles-v1 ; elle est à écouter en priorité.
- « ceux à venir, ceux déjà passés » : l'ASR rend « à venir, ce ... passé » et perd un « ceux ». Vérifier que les deux « ceux » s'entendent.
- « n'écrivez pas, DICTEZ ! » : l'ASR entend « dictés » ; l'accent d'insistance sur DICTEZ peut être moins net que voulu. À vérifier.
- « vos devoirs ? Rangés au même endroit : ceux à venir... » : voir ci-dessus, même passage.
- « baï SEPRO » transcrit « by Cepro » : rendu attendu et artefact ASR, aucun défaut.
- Aucune phrase n'a été coupée ni reformulée ; les écarts de ponctuation et d'accord sont des artefacts ASR.

## Texte envoyé au TTS
```text
Et si votre journée devenait plus LÉGÈRE ? C’est ce que vous offre L’Application Athena, baï SEPRO, pour votre classe dans votre poche. <short pause> Pour commencer, rien de plus simple : votre numéro, le code de l’établissement, votre code PIN, et vous voilà CHEZ VOUS. Et si vous êtes aussi parent, un seul tap sur votre profil, et vous passez d’un espace à l’autre. <short pause> Dès l’ouverture, voici votre journée : vos cours, classe par classe. Un autre jour ? Un tap. Et vous ne voyez que VOS classes, pas une de plus. Votre établissement a activé le pointage ? Alors vous scannez le QR à l’entrée, et c’est fait. <cheer> Maintenant, l’appel, et là, vous allez gagner du temps ! Vous ouvrez le cours : la liste est prête, tout le monde est présent. Un élève est absent ? Vous le touchez. C’est noté. Un retard, une sanction avec son motif ? Même geste. Et sans rien recopier, tout part automatiquement à la vie scolaire. <short pause> Le cahier de texte, ensuite. Ce que vous avez fait en classe, ce que vous donnez à faire... et petit conseil : n’écrivez pas, DICTEZ ! Vous parlez, c’est écrit. Vous publiez, et les parents le retrouvent dans leur cahier de texte. <short pause> Vos devoirs ? Rangés au même endroit : ceux à venir, ceux déjà passés, avec la moyenne de la classe et le nombre d’élèves qui ont réussi. Et pour ne rien oublier, les notifications veillent pour vous : un cahier à remplir, des devoirs à valider, un message de la direction. <cheer> Moins de gestes, plus de temps pour ce qui compte : vos ÉLÈVES. Avec L’Application Athena, baï SEPRO : l’école, plus près de vous.
```
