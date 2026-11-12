# Rapport voix v4 - PARENTS (tuto Athena)

## Prise
- Texte parent : version approuvee au tournage v3 (voice/v3) avec les deux phrases remplacees de la consigne v4. Le texte de docs/SCRIPT.md contient encore le tag <sigh> retire au v3 apres « c’est RÉGLÉ ! » ; il n’a pas ete reintroduit (prise v3 approuvee sans soupir, et ce soupir depassait la cible de gap). Tous les autres tags sont inchanges. (273 mots hors tags ; les tags ne sont pas lus).
- Modele : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel TTS par prise (narration entiere), prompt de style identique a la prise approuvee (verbatim voice/v2/style.txt). Cle : OPENROUTER_GEN_API_KEY.
- Generations (6 essais sur 6 autorises) :
- take 1 = 86.64 s — hors bande 90.0-105.0 s
- take 2 = 86.8 s — hors bande 90.0-105.0 s
- take 3 = 91.32 s — gap max > 0,8 s
- take 4 = 90.16 s — gap max > 0,8 s
- take 5 = 90.08 s — gap max > 0,8 s
- take 6 = 90.76 s — gap max > 0,8 s
- Prise retenue : take 4 (best-effort (dans la bande, gap max > 0,8 s)). Aucune edition audio, aucun traitement de tempo, de hauteur ou de vitesse.

## Mesures
- Duree totale : 90.16 s (bande 90.0-105.0 s : ATTEINTE)
- Plus long gap entre mots consecutifs (words.json) : 1.18 s (cible <= 0,80 s : NON ATTEINTE (best-effort))
- Plus long silence (silencedetect -35 dB) : 0.78 s a 8.68 s
- Loudness : -16.10 LUFS integres ; true peak -1.00 dBTP ; 48 kHz / 16 bits / mono ; pas de clipping.
- Lecture des mesures : le plus long silence (silencedetect -35 dB) est de 0,78 s ; l'écart de 1,18 s calculé sur words.json tombe sur la jonction <phew> (« enfant. » puis « Les »), où le son de performance occupe le temps sans être transcrit par l'ASR.

## Gaps > 0,5 s entre mots consecutifs
- 8.66 s : gap de 0.74 s entre « d’œil. » et « Et »
- 16.14 s : gap de 0.64 s entre « AUSSITÔT. » et « Un »
- 25.44 s : gap de 0.7 s entre « VOUS. » et « Bienvenue »
- 34.22 s : gap de 0.54 s entre « affiché. » et « Et »
- 37.3 s : gap de 0.56 s entre « quotidien » et « : »
- 42.42 s : gap de 1.18 s entre « enfant. » et « Les »
- 48.66 s : gap de 0.64 s entre « sanctions, » et « le »
- 56.08 s : gap de 0.62 s entre « d’œil. » et « Les »
- 73.64 s : gap de 0.88 s entre « ici. » et « Et »
- 77.64 s : gap de 0.74 s entre « DIRECT » et « : »
- 80.7 s : gap de 0.68 s entre « restants. » et « La »

## WER
- 11.72 % (faster-whisper small, alignement normalise ; ecarts attendus : ponctuation, chiffres, noms de marque).
- Ecarts (32) :
1. attendu « les » — entendu « l'écarnée, »
2. attendu « carnets, » — entendu « — »
3. attendu « baï » — entendu « by »
4. attendu « SEPRO. » — entendu « Cepro. »
5. attendu « : » — entendu « — »
6. attendu « ! » — entendu « — »
7. attendu « : » — entendu « Finis »
8. attendu « FINI » — entendu « l'écarnée »
9. attendu « les » — entendu « perdue, »
10. attendu « carnets » — entendu « — »
11. attendu « perdus, » — entendu « — »
12. attendu « — » — entendu « Ouf »
13. attendu « absences, » — entendu « absence, »
14. attendu « retards » — entendu « retard »
15. attendu « sanctions, » — entendu « sanction, »
16. attendu « : » — entendu « — »
17. attendu « réglées, » — entendu « réglé, »
18. attendu « It » — entendu « Heat »
19. attendu « file » — entendu « fil »
20. attendu « ! » — entendu « — »
21. attendu « : » — entendu « — »
22. attendu « : » — entendu « Montez »
23. attendu « monté » — entendu « — »
24. attendu « 7 » — entendu « 7h12, »
25. attendu « heures » — entendu « dosar »
26. attendu « 12, » — entendu « est »
27. attendu « deux » — entendu « restant. »
28. attendu « arrêts » — entendu « — »
29. attendu « restants. » — entendu « — »
30. attendu « baï » — entendu « by »
31. attendu « SEPRO » — entendu « Cepro. »
32. attendu « : » — entendu « — »

## Phrases signalées
- « Suivre la scolarité de vos enfants, sans courir après les carnets » : l'ASR entend « après l'écarnée » (les deux mots « les carnets » sont fusionnés). Même artefact qu'au v2 sur « FINI les carnets perdus ». À vérifier à l'écoute : si le mot « carnets » s'entend nettement, rien à corriger.
- « FINI les carnets perdus, les appels et les allers-retours » : l'ASR perd « les » et rend « Finis l'écarnée perdue ». Même famille d'artefact ; vérifier que « carnets » et « perdus » s'entendent.
- « monté à 7 heures 12, deux arrêts restants » : l'ASR rend « 7h12, dosar est restant ». Vérifier les nombres et « deux arrêts » à l'écoute.
- « c'est RÉGLÉ ! » suivi de <exhales> : l'ASR note une vocalisation « Ouf ». C'est le son du tag, pas un mot ajouté.
- « baï SEPRO » est transcrit « by Cepro » : c'est le rendu attendu (« baï » se prononce comme l'anglais « by »), et « Cepro » est un artefact ASR sur SEPRO. Aucun défaut.
- Aucune phrase n'a été coupée, reformulée ni réenregistrée phrase par phrase.

## Texte envoyé au TTS
```text
Suivre la scolarité de vos enfants, sans courir après les carnets, c’est possible avec L’Application Athena, baï SEPRO. Voici comment, en un coup d’œil. <short pause> Et pour y entrer, rien de plus simple : vous entrez votre numéro de téléphone et le code de l’établissement, et l’application vous reconnaît AUSSITÔT. <exhales> Un code à six chiffres arrive par SMS pour confirmer que c’est bien vous, et un code PIN à quatre chiffres protège votre accès. Saisissez-le, et vous êtes CHEZ VOUS. Bienvenue chez vous ! <cheer> Vos enfants sont réunis sur l’accueil, une flèche suffit pour passer de l’un à l’autre, et tout ce que vous voyez concerne l’enfant affiché. <short pause> <exhales> Et c’est là qu’Athena change VRAIMENT votre quotidien : FINI les carnets perdus, les appels et les allers-retours pour savoir où en est votre enfant. <phew> Les notes et les bulletins trimestre par trimestre, la vie scolaire avec absences, retards et sanctions, le cahier de texte que les professeurs remplissent au fil de la journée... tout est là, LIMPIDE. Vous voyez tout, en un coup d’œil. <short pause> Les factures, c’est pareil : à payer ou déjà réglées, tout est listé. Sélectionnez une facture, choisissez Max It ou Wave, et l’école est payée sans file d’attente ni déplacement. Et voilà, c’est RÉGLÉ ! <exhales> Chaque annonce de l’école arrive directement dans vos notifications : rien à chercher, tout est ici. <short pause> Et si votre enfant prend le bus, vous suivez son trajet EN DIRECT : <gasp> monté à 7 heures 12, deux arrêts restants. La réinscription, elle aussi, se fait en quelques minutes, sans bouger de chez vous. <breath> Vous venez de voir L’Application Athena, baï SEPRO : l’école, plus près de vous.
```
