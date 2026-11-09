# Voix off — identité et leçons

## Identité (VALIDÉE à l'écoute)

- Voix : **Kore** (femme, tutoriel posé) via `google/gemini-3.8-flash-tts` (OpenRouter).
- Prompt de style, à passer dans `instructions`, JAMAIS dans `input`, à l'octet près :

> Narratrice chaleureuse et sincèrement enthousiaste, accent sénégalais naturel, qui partage une excellente nouvelle avec une amie en français conversationnel, en gardant le vouvoiement. Intonation haute, joyeuse et pétillante, comme si chaque écran apportait une bonne surprise ; elle est contente de guider ses auditeurs pas à pas. Débit détendu : elle prend le temps de poser chaque idée, sans jamais se presser ni précipiter. Le sourire s'entend du début à la fin, et jamais la voix ne baisse, même sur les explications. Chaque fonctionnalité est présentée comme une évidence heureuse : c'est simple, ça marche, et c'est tant mieux. Petites respirations naturelles avant chaque nouvelle idée, satisfaction chaleureuse sur les formules de conclusion. Voix, accent et hauteur constants, sans ton publicitaire ni surjeu : l'enthousiasme vient du rythme, des mots et des petits élans de voix, pas du volume.

- Prononciation : « Athena School » tel quel, SEPRO = sé-pro, Max It = max it, Wave = ouaïve.

## Leçons (apprises à l'écoute, ne pas réapprendre)

1. « énergie haute / rythme vivant » dans le prompt => le modèle PARLE TROP VITE. L'énergie vient
   de « intonation haute, joyeuse et pétillante » combiné à « débit détendu ».
2. « plus lent et plus posé sur les points importants » => le modèle MURMURE les explications
   (-19 dBFS mesurés sur la scolarité). Interdit.
3. `<long pause>` est TROP long à l'écoute. Utiliser `<short pause>`.
4. `<chuckle>` est hors ton ici. `<cheer>` après « Bienvenue chez vous ! » est VALIDÉ.
5. `<sigh>` = « c'est fait, sorti de votre vie » (après « c'est réglé ! »). `<phew>` = « c'était
   pénible, c'est fini » (après « fini les carnets perdus »). `<gasp>` = « regardez ça » (bus en direct).
6. MAJUSCULES = accent vocal documenté. Utilisées : POCHE, AUSSITÔT, CHEZ VOUS, VRAIMENT, FINI,
   LIMPIDE, RÉGLÉ, EN DIRECT.
7. Un SEUL appel pour tout le texte, puis découpe (voir TIMING.md). Un prompt de style qui change
   entre scènes fait sonner deux narratrices.
8. Tags de la doc Gemini 3.8 : en anglais, même pour un transcript français. Angle brackets.
9. Run-to-run non déterministe : deux appels identiques ne rendent pas le même audio.
