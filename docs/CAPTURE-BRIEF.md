# Capture brief — Athena School, espace Parents (video: "Athena, l'école dans votre poche")

Vertical 9:16 tutorial, target length under 2 minutes (the edit has room: current timing plan is 98,8 s).
You are capturing the screens a parent sees, for a motion tutorial built from real captures.
The film has two kinds of visuals, so the capture has **two tracks**. Both are required.

## TRACK A — App UI screens (design viewer)

The current parent UI lives as HTML mockups in the athena_mobile repo: `design/forks/actuel/athena/screens/`
(fork `actuel` = shipped design; fork `boutique` = future, DO NOT CAPTURE IT). The viewer opens from
`file://` or `npm run serve` (live-server, port 8080) inside `design/`.

- **Viewport 412x917, device scale factor 2 → 824x1834 PNG. 2x only.**
- Deliberate deviation from the 390x844 instruction: the Athena design canvas is FIXED at 412x917.
  A 390 viewport clips 22 px off the right edge of every screen. 412x917 is the phone size this
  product was drawn at; use it for every Track A capture so all screens match.
- No browser chrome, no cursor, no hover states. Wait for fonts and images before each capture.
- The painted status bar (9:30) is part of the mockups: KEEP it, it is consistent across screens.
- Capture from `file://` paths or the local server; same method for the whole track.

## TRACK B — Real authentication flow (Flutter app, real phone)

The login/OTP/PIN screens do not exist in the design viewer; they must come from the real app on the
founder's Android phone (proven method; an Android emulator is acceptable only if the staging build
already runs there — do not set one up from scratch).

- Capture at the phone's native resolution (reference set: 1264x2780). Do not downscale.
- **Crop the status bar off every capture** (uniform band) — no status-bar clutter.
- Use ONLY the test account and dummy values. Never type a real PIN, never use a real OTP code
  (screenshot the OTP screen with the boxes EMPTY or with a dummy code that is then invalidated).
- If any screen echoes the phone number, pixelate the number before delivery (the existing
  `assets/auth/04_otp_*.jpg` show the expected blur treatment: band y 964-1060, x >= 682 at
  1264x2780 — recompute proportionally for your resolution).

## PAYMENT SCREENS — DECISION (applies to both tracks)

Capturing the **provider list is allowed and required**: the payment sheet that lists **Max It** and
**Wave** (names + logos + radio rows + the total) contains no entry fields and no personal data.
**STOP BEFORE any entry field or handoff**: do NOT tap « Payer par Max It / Wave », do NOT capture
the provider's own app/page, any phone-number or card entry, OTP entry of the provider, or a
confirmation that reveals personal data. The sheet itself, once selected-state included, is the last
payment capture. The film ends that scene on a rebuilt "Payée" stamp, so no payment-success capture
is needed.

## PROCESS — capture in this order; if the real flow differs, keep the real order and say so in flow.md

Track B (real app), auth:
01 Login screen: empty; filled (dummy number format + test school code); CGU checkbox unchecked, then checked; the validation error for a wrong combination (dummy values only)
02 OTP screen: boxes empty; boxes with a dummy code; the expired/wrong-code error text
03 PIN creation: « Définir un code PIN » empty; 4 digits entered; « Confirmer » screen; the mismatch error
04 PIN entry: empty; filled (dummy PIN); the « code PIN oublié » sheet open
05 Log-out state (if reachable from settings)

Track A (design viewer), parents space:
06 accueil: default state; the réinscription sheet open; the children sheet open
07 drawer: open state (already captured; re-capture only if it changed)
08 mes-enfants: default; bus status row; photo sheet open
09 scolarité: notes (T1/T2/T3 if distinct), bulletins, vie-scolaire (each tab: Emploi du temps, Absences, Retards, Sanctions), cahier-texte (a day with entries; the « à faire » filter; calendar sheet)
10 factures: list; filter sheets (par enfant, statut); one invoice selected; **the payment sheet with Max It / Wave visible — STOP RULE ABOVE**
11 notifications:Tout and Non lues states
12 bus: en-route state, passed state, après-midi toggle
13 réinscription: form with services checked, total updated; reinscription-confirm
14 parametres: main, personnes-autorisees, mes-infos, etablissement, CGU
15 etats (edge states) and factures-vide, notes-enfant-unique

RECORDING: one full walk of each track at the capture size (Track A browser 412x917; Track B phone
screen recording). Any frame rate ≥ 30 fps; the recording is motion reference for the editor, not
final footage. Name them `trackA-flow-recording.mp4`, `trackB-flow-recording.mp4`.

NAMING: `NN_screen_state.png` (+ `NN_screen_state.json` positions file per screenshot:
`{ "label", "type": "input|button|checkbox|card|link", "x", "y", "width", "height", "tap" }`
in pixels of the PNG, `tap: true` on everything pressed in the flow). Text exports (.txt) of every
list or legal screen: invoice rows, services and prices, CGU.

DELIVERY: folders `/screens /elements /assets` + the two recordings + `flow.md`, added to this
repository under `captures-<date>/`, or uploaded to chat (~30 MB max per file).

## flow.md — reporting contract (copy verbatim into your instructions to the agent)

```
flow.md must contain these sections, in this order.

1. HEADER
- App name, build version (for example 3.0.2+270 or the actual one), git commit hash, capture date.
- Environment used (staging, test, emulator, or browser), device size 390x844, scale 2x, UI language.
- Method: how the screens were captured (emulator, browser, or other).

2. REAL SCREEN ORDER
A numbered list of every screen in the order a parent reaches it. For each one:
- File name (NN_screen_state.png)
- The tap or action that leads there
- Whether the screen is new, unchanged, or missing compared to the brief

3. EXACT ON-SCREEN TEXT
Copy the exact text as shown, including accents, capitalization, and punctuation, for:
- Login screen: field labels, placeholders, button, and the CGU/terms checkbox wording
- OTP screen: title, instructions, resend option, and any timer text
- PIN screens: the title of the creation screen, the title of the confirmation screen, and the entry screen
- Home screen: banners, child card labels, and how switching between children works (arrows, swipe, or dropdown)
- Scolarité: tab or section names for grades, bulletin, school life, and the homework diary
- Invoices: list labels, filter names, status words (payée, à payer, or other), and the payment button
- Notifications: filter names and the mark-all-as-read label
- School feed: section title and item format

4. DIFFERENCES FROM THE BRIEF
Each difference as a separate line:
- Renamed buttons or labels, with old and new text
- Extra steps (permission prompts, onboarding screens, welcome carousels)
- Missing screens or features, with the search or menu path you used to confirm they are absent
- Fields that do not exist or differ from the brief

5. VALIDATION AND ERROR MESSAGES
Every error message you saw, with its exact text and the field or action that triggered it.

6. CLAIMS TO CHECK
Answer each one yes or no, with the screen that supports the answer:
- Does the home screen show only the selected child's information?
- Does the homework diary show entries for every class, and how often does it update?
- After a successful payment, does the invoice show as paid, and what confirmation message appears?
- Does the bus tracking exist in this build? If yes, give the status text and stop count format. If no, say so and do not describe it.
- Does the réinscription banner exist in this build? If yes, give its exact year text.

7. TEST DATA USED
- The test account, referred to only as "the test account" (never the password or username).
- The dummy phone number format used, without the full number.
- Fictional children names, classes, and any dummy documents uploaded.
- Any values you changed to make the form accept input, and why.

8. PROBLEMS
- Crashes, timeouts, slow screens, and loading states longer than 2 seconds.
- Screens that could not be captured, and why.
- Anything the agent was unsure about.

9. DO NOT INCLUDE
- Passwords, tokens, OTP codes, the real PIN, or any credential.
- Real names, real phone numbers, or real student data.
- Any payment-method or card information.
```

## Already delivered (do not redo unless changed)

22 Track A screens and 6 Track B auth captures are in `assets/screens/` and `assets/auth/`
(inventory in `docs/CAPTURES.md`). What is still MISSING and expected from this brief:
PIN confirmation (Track B), OTP filled + expired error (Track B), PIN mismatch error,
forgot-PIN sheet, CGU checked/unchecked, login error states, factures payment sheet open with
providers visible (Track A), invoice selected state, notifications unread state, réinscription
services-checked state.
