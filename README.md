# Athena — Kit vidéo tuto « Espace Parents » (transfert)

Kit complet pour produire la vidéo tutorielle verticale (9:16, 1080x1920) qui présente
l'**espace Parents** de l'application mobile **Athena School** (par SEPRO) aux parents.

## État à la prise en main

- **Voix off : VALIDÉE.** Take final de 94,3 s, généré en un seul appel TTS, découpé en 9 scènes,
  loudness équilibrée. Ne pas la regénérer sans raison : elle a été adoptée à l'écoute.
- **Script : VALIDÉ** (texte + émotions inline). Voir `docs/SCRIPT.md`.
- **Storyboard : MAPPÉ** scène par scène avec deux dispositifs visuels validés en intention.
  Voir `docs/STORYBOARD.md`.
- **Maquette de style : NON VALIDÉE.** Une maquette de 45,7 s a été construite
  (`preview/maquette-NON-VALIDEE.mp4`) ; le client ne l'a pas retenue. Le LOOK est donc à
  (re)faire — c'est le travail à accomplir. La maquette reste utile comme référence de timing
  et de mécanique (checklist, éventail de scènes, vignette SVG).

## Contenu

| Dossier | Contenu |
|---|---|
| `assets/screens/` | Les 22 écrans de l'espace Parents (maquettes HTML capturées en PNG @2x, 824x1834) |
| `assets/auth/` | 6 captures RÉELLES de l'écran de connexion/PIN (téléphone du fondateur, numéro flouté) |
| `assets/brand/` | Logos Athena (fond clair et fond sombre) |
| `design-system/` | `tokens.css` (LA loi palette) et `ui.css` du design system officiel |
| `voice/` | Take final WAV + MP3, les 9 découpes par scène, le script (propre et avec tags), le prompt de style |
| `preview/` | La maquette de style NON VALIDÉE (référence, pas un modèle à suivre) |
| `docs/` | Script, voix, timing, storyboard, captures, design kit, workflow de rendu |

## Par où commencer

1. Lire `docs/STORYBOARD.md` (le plan visuel) et `docs/DESIGN-KIT.md` (la marque).
2. Écouter `voice/narration_complet.mp3` une fois en lisant `docs/TIMING.md`.
3. Regarder `preview/maquette-NON-VALIDEE.mp4` pour savoir ce qui a été REFUSÉ.
4. Construire les scènes à 60 fps avec le pipeline de `docs/WORKFLOW.md`.

## Règles non négociables

- Écrans montrés ENTIERS (jamais de zoom agressif), les autres éléments s'atténuent quand un point est traité.
- Ouverture et fin sur fond navy (`--navy: #1C2B4B`), alternance clair/sombre entre les scènes.
- Typo Poppins, palette du design system (`design-system/tokens.css`), texte français avec typographie FR
  (apostrophes typographiques, espace insécable avant ! ? : ;), vouvoiement.
- Données de démo fictives uniquement (les maquettes en contiennent déjà).
- Une barre de progression fine en bas de l'écran, numéros d'étape « ÉTAPE n ».
