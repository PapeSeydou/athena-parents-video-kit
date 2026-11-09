# Script voix off (VALIDÉ)

Durée lue : 94,3 s. 1 477 caractères parlés. Voix : Kore (voir `VOICE.md`).

## Version avec émotions inline (CE qui a été envoyé au TTS)

Les tags restent en ANGLAIS même avec un texte français (comportement documenté de Gemini 3.8 TTS).
Les MAJUSCULES sont une technique documentée d'accent vocal.

```text
Athena, c’est l’école de vos enfants, dans votre POCHE. <short pause> Et pour y entrer, rien de plus simple : vous entrez votre numéro de téléphone et le code de l’établissement, et l’application vous reconnaît AUSSITÔT. <exhales> Un code à six chiffres arrive par SMS pour confirmer que c’est bien vous, et un code PIN à quatre chiffres protège votre accès. Saisissez-le, et vous êtes CHEZ VOUS. Bienvenue chez vous ! <cheer> Vos enfants sont réunis sur l’accueil, une flèche suffit pour passer de l’un à l’autre, et tout ce que vous voyez concerne l’enfant affiché. <short pause> <exhales> Et c’est là qu’Athena change VRAIMENT votre quotidien : FINI les carnets perdus, les appels et les allers-retours pour savoir où en est votre enfant. <phew> Les notes et les bulletins trimestre par trimestre, la vie scolaire avec absences, retards et sanctions, le cahier de texte que les professeurs remplissent au fil de la journée... tout est là, LIMPIDE. Vous voyez tout, en un coup d’œil. <short pause> Les factures, c’est pareil : à payer ou déjà réglées, tout est listé. Sélectionnez une facture, choisissez Max It ou Wave, et l’école est payée sans file d’attente ni déplacement. Et voilà, c’est RÉGLÉ ! <sigh> <exhales> Chaque annonce de l’école arrive directement dans vos notifications : rien à chercher, tout est ici. <short pause> Et si votre enfant prend le bus, vous suivez son trajet EN DIRECT : <gasp> monté à 7 heures 12, deux arrêts restants. La réinscription, elle aussi, se fait en quelques minutes, sans bouger de chez vous. <breath> Athena School, par SEPRO. L’école, plus près de vous.
```

## Durées par scène

| # | Scène | Caractères | Audio réel |
|---|-------|-----------|------------|
| 1 | Ouverture | 55 | 3,89 s |
| 2 | Connexion | 101 | 8,60 s |
| 3 | Code SMS + PIN | 177 | 11,08 s |
| 4 | Accueil | 161 | 9,20 s |
| 5 | Scolarité | 274 | 26,48 s |
| 6 | Factures | 185 | 11,60 s |
| 7 | Notifications | 99 | 6,50 s |
| 8 | Bus + réinscription | 170 | 12,24 s |
| 9 | Fin | 53 | 4,73 s |

## Regénération (un seul appel pour TOUT le texte)

POST `https://openrouter.ai/api/v1/audio/speech` — body :
`{ model: "google/gemini-3.8-flash-tts", input: <script avec tags>, instructions: <prompt de style, voir VOICE.md>, voice: "Kore", response_format: "pcm" }`
La réponse est du PCM brut 24 kHz mono 16 bits : ajouter un en-tête WAV (44 octets) pour l'écouter.
