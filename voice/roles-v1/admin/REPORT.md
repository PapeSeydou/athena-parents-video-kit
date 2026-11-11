# Rapport voix roles-v1 - DIRECTION (administrateur) (tuto Athena)

## Blocage : aucune generation possible
- Aucun essai n'a pu etre lance : des la premiere generation (PROF take 1), l'API OpenRouter a repondu HTTP 402 « This request's maximum cost exceeds your available credits » (raison : weight_exceeds_budget ; source : openrouter_credits), y compris sur une demande minimale de test. Les credits du compte sont epuises.
- Les deux cles alternatives du coffre ont ete testees sans succes : OPENROUTER_RESPONSE_API_KEY (404, endpoint audio non accessible pour cette cle) et OPENCODE_GO_API_KEY (cle Google invalide pour l'API TTS directe).
- Aucun audio ADMIN n'existe donc a ce jour ; narration.wav, words.json et silences.txt manquent a l'appel volontairement : rien n'a ete simule ni fabrique.

## Etat pret pour la reprise
- Texte ADMIN verbatim conserve (script admin-tags.txt dans le repertoire de travail), prompt de style identique a v3, modele google/gemini-3.8-flash-tts, voix Kore, un seul appel par generation.
- Cible : duree 90-106 s, gap max entre mots consecutifs <= 0,80 s, -16 LUFS / -1 dBTP, 48 kHz / 16 bits / mono. Huit essais autorises, meilleure prise retenue, aucune edition audio.
- Reprise : recrediter le compte OpenRouter (https://openrouter.ai/settings/credits) puis relancer le script de generation pour la role admin ; il demarre a l'essai 1 et produit les quatre fichiers de ce dossier, avec le meme rapport.
