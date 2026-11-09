# Design kit — Athena School

## La palette (design-system/tokens.css = LA LOI)

| Token | Valeur | Usage |
|---|---|---|
| `--mint` | #ECF2E3 | zone d'en-tête claire |
| `--sheet` / `--card` | #FFFFFF | corps, cartes |
| `--olive` | **#6B8C21** | accents, icônes, statut « ok » — LA couleur de marque |
| `--sage` | #EBF0DB | pastilles d'icônes |
| `--navy` | **#1C2B4B** | actions primaires, emphase, fonds sombres de la vidéo |
| `--ink` / `--ink-soft` / `--ink-faint` | #1C2B4B / #5A6577 / #97A0AE | texte |
| statuts | ok #6B8C21 (bg #EBF0DB) · due #E8A13D (bg #FBF1DE) · late #D9534F (bg #FBE4E3) | chips d'état |
| voies de bus | bus A #35C759 · bus B #0A84FF | plein = passé, pointillé = à venir |

## L'application Flutter (écrans d'authentification réels)

Les vrais écrans de login utilisent leur propre palette, plus claire :
mainColor **#B0CF67** (lime), mainTextColor #374A0B, navy #1C274C, fond sélection #F6FAED,
fond principal #E1F0C0. Ne pas « corriger » ces captures vers la palette du design system :
les scènes 2-3 montrent l'application telle qu'elle est, le habillage (titres, fond, checklist)
utilise lui la palette du design system.

## Typographie

**Poppins** (400, 500, 600, 700 — Google Fonts, `@fontsource/poppins`). Display 600/800,
texte 400/600. Titres de scène 84-112 px en 1080x1920.

## Logos

`assets/brand/athena.png` (fond clair) et `athena-white.png` (à inverser `brightness(0) invert(1)`
déjà appliqué dans les exemples, sur fond navy). Signature : « Athena School, par SEPRO ».

## Ton et langue

Français, vouvoiement, chaleureux et direct. Typographie FR : apostrophes typographiques (’),
« guillemets », espace insécable avant ! ? : ;. Aucun ton publicitaire.

## Composants récurrents (voir design-system/ui.css)

Cartes blanches rayon ~22-30 px, ombres douces très diffuses (rgba(28,43,75,.18-.22)),
chips arrondies 999 px, listes de rangées avec icône en pastille sage.
