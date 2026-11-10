# Rapport voix v2 — narration tuto Athena parents

## Prise et génération
- Texte : voice/narration-propre.txt (approuvé, wording inchangé). Entrée TTS = voice/narration-avec-tags.txt (mêmes mots + balises d'émotion validées).
- Modèle : google/gemini-3.8-flash-tts, voix Kore, UN SEUL appel pour toute la narration.
- Prompt de style : verbatim, tel que fourni (énergie joyeuse, souriante, dynamique ; pause courte entre deux idées ; vouvoiement ; pas de ton publicitaire).
- Tentatives (même requête) : take 1 = 80,36 s / silence max 0,88 s ; take 2 = 79,32 s / 0,86 s ; take 3 = 85,12 s / 0,82 s. Take 3 retenu : seule prise dans la bande de durée.

## Mesures
- Durée totale : 85,12 s (cible 85-92 s : atteinte)
- Silence le plus long : 0,82 s à 64,18 s (cible ≤ 0,40 s : non atteinte — phrase signalée ci-dessous)
- Loudness : -16,05 LUFS intégrés (cible -16 : atteinte), true peak -1,00 dBTP (cible -1 : atteinte), format 48 kHz / 16 bits / mono, pas de clipping
- Aucun traitement de tempo ou de hauteur : la durée vient de la livraison TTS.

## Phrase signalée (pause > 0,40 s)
« Côté finance, toutes les factures sont là, à payer ou déjà réglées. Sélectionnez une facture, choisissez Max It ou Wave, et l'école est payée sans file d'attente ni déplacement. Et voilà, c'est RÉGLÉ ! »
La pause de 0,82 s tombe juste après « Et voilà, c'est RÉGLÉ ! » : c'est la respiration du tag <sigh> (soupir de « mission accomplie ») avant l'idée suivante. Elle est structurelle : présente dans les 3 générations (0,83-0,88 s) à la même jonction. Le texte approuvé ne peut pas être prononcé sans cette respiration tant que le soupir est joué ; les cures possibles sont un autre essai (re-tirage identique) ou la suppression du tag <sigh> dans le script, décision qui revient au fondateur.

## Transcription et WER
- Méthode : faster-whisper (small, int8), timestamps de mots, transcription comparée à narration-propre.txt après normalisation (minuscules, sans accents ni ponctuation, nombres « six/quatre/sept/douze » mis en chiffres, élisions et traits d'union refusionnés).
- WER : 11,07 % (28 erreurs / 253 mots : 20 substitutions, 7 délétions, 1 insertion).
- Les écarts sont dominés par des rendus ASR, pas par des mots absents :
  - ponctuation supprimée par l'ASR (les « : » et « ! ») ;
  - singulier/pluriel : absences → absence, retards → retard, sanctions → sanction, réglées → réglé ;
  - formats numériques : « 7 heures 12 » transcrit « 7h12, 2 », « deux » en chiffre ;
  - marques : « Max It » entendu « Max Heat », « par SEPRO » transcrit « paraît ses pros » ;
  - vocalisation « Ouh ! » performée sur le tag <phew> (scène 5) et « FINI les carnets perdus » rapide mal transcrit (« Finis l'écarnée perdue »).
- Une écoute humaine reste nécessaire pour distinguer ce qui vient du TTS de ce qui vient de l'ASR.

## Liste des écarts (28)
1. attendu « : » — entendu « — »
2. attendu « de » — entendu « — »
3. attendu « ! » — entendu « — »
4. attendu « : » — entendu « Finis »
5. attendu « FINI » — entendu « l'écarnée »
6. attendu « les » — entendu « perdue, »
7. attendu « carnets » — entendu « — »
8. attendu « perdus, » — entendu « — »
9. attendu « — » — entendu « Ouh »
10. attendu « absences, » — entendu « absence, »
11. attendu « retards » — entendu « retard »
12. attendu « sanctions, » — entendu « sanction, »
13. attendu « de » — entendu « — »
14. attendu « : » — entendu « — »
15. attendu « réglées, » — entendu « réglé, »
16. attendu « It » — entendu « Heat »
17. attendu « file » — entendu « fil »
18. attendu « ! » — entendu « — »
19. attendu « : » — entendu « — »
20. attendu « : » — entendu « Montez »
21. attendu « monté » — entendu « — »
22. attendu « 7 » — entendu « 7h12, »
23. attendu « heures » — entendu « 2 »
24. attendu « 12, » — entendu « — »
25. attendu « deux » — entendu « — »
26. attendu « par » — entendu « paraît »
27. attendu « SEPRO. » — entendu « ses »
28. attendu « — » — entendu « pros. »

## Fichiers
- voice/v2/narration_v2.wav — take final, loudnorm deux passes, 48 kHz 16 bits mono
- voice/v2/words.json — 253 mots du texte approuvé avec start/end (s, depuis le début de la narration)
- voice/v2/silences.txt — les 42 silences ≥ 0,2 s (début, fin, durée)
- voice/v2/REPORT.md — ce rapport
