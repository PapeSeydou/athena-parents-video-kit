# flow.md — Track A (design viewer), captures-2026-11-09

## 1. HEADER
- Source: athena_mobile / design / forks/actuel/athena/screens/
- athena_mobile commit: e2bd742
- Capture date: 2026-11-09
- Viewport: 412 x 917 CSS px, device scale factor 2, PNG 824 x 1834
- Serving method: file://
- Browser: Chromium 156.0.8078.4 (HeadlessChrome), Playwright 1.64.1 (Python)
- Recording: trackA-flow-recording.mp4, 824 x 1834, 30/1 fps, 113.133333 s, H.264 yuv420p
- UI language: French

## 2. REAL SCREEN ORDER
1. screen-accueil.png | reached by: (départ de la marche) | status: existing
2. 01_accueil_sheet-reinscription.png | reached by: « Réinscription 2026-2027 » sur accueil | status: new
3. 02_drawer_ouvert.png | reached by: burger « Menu » | status: new
4. screen-mes-enfants.png | reached by: drawer Enfants → « Amadou Sarr · CM1 B » | status: existing
5. 03_mes-enfants_sheet-photo.png | reached by: zone photo de l’enfant | status: new
6. screen-notes.png | reached by: drawer Scolarité → Notes | status: existing
7. 04_notes_t2.png | reached by: « Trimestre 2 » | status: new
8. 04_notes_t3.png | reached by: « Trimestre 3 » | status: new
9. screen-bulletins.png | reached by: drawer Scolarité → Bulletins | status: existing
10. screen-vie-scolaire.png | reached by: drawer Scolarité → Vie scolaire | status: existing
11. 04_vie-scolaire_absences.png | reached by: onglet « Absences » | status: new
12. 04_vie-scolaire_retards.png | reached by: onglet « Retards » | status: new
13. 04_vie-scolaire_sanctions.png | reached by: onglet « Sanctions » | status: new
14. screen-cahier-texte.png | reached by: drawer Scolarité → Cahier de texte | status: existing
15. 04_cahier-texte_jour-avec-entrees.png | reached by: « Jour précédent » (jusqu’à un jour rempli) | status: new
16. 04_cahier-texte_a-faire.png | reached by: filtre « À faire » | status: new
17. 04_cahier-texte_calendrier.png | reached by: « Choisir une date » | status: new
18. screen-factures.png | reached by: drawer Finance → Factures | status: existing
19. 05_factures_filtre-enfant.png | reached by: filtre enfant | status: new
20. 05_factures_filtre-statut.png | reached by: filtre « Statut » | status: new
21. 10_factures_invoice-selected.png | reached by: sélection d’une facture | status: new
22. 10_factures_payment-sheet.png | reached by: « Payer 1 facture… » puis « Max It » — STOP avant le bouton final de paiement | status: new
23. screen-notifications.png | reached by: drawer → « Tout voir » | status: existing
24. 11_notifications_non-lues.png | reached by: filtre « Non lues » | status: new
25. 11_notifications_apres-markall.png | reached by: « Tout marquer comme lu » | status: new
26. screen-bus.png | reached by: drawer Transport → Suivi du bus | status: existing
27. 07_bus_apres-midi.png | reached by: toggle « Après-midi » | status: new
28. screen-bus-etats.png | reached by: état « bus passé » | status: existing
29. screen-reinscription.png | reached by: réinscription | status: existing
30. 13_reinscription_services-checked.png | reached by: 4 services cochés, total mis à jour | status: new
31. screen-reinscription-confirm.png | reached by: « Confirmer la réinscription » | status: existing
32. screen-parametres.png | reached by: paramètres | status: existing
33. screen-parametres-personnes-autorisees.png | reached by: → Personnes autorisées | status: existing
34. screen-parametres-mes-infos.png | reached by: → Mes informations | status: existing
35. screen-parametres-etablissement.png | reached by: → Informations de l’établissement | status: existing
36. screen-parametres-cgu.png | reached by: → CGU | status: existing
37. screen-etats.png | reached by: états | status: existing
38. screen-factures-vide.png | reached by: factures vides | status: existing
39. screen-notes-enfant-unique.png | reached by: notes enfant unique | status: existing
40. screen-accueil.png | reached by: fin de la marche sur accueil | status: existing

## 3. EXACT ON-SCREEN TEXT
Voir texts/*.txt (un fichier par écran et par état). Points clés :
- accueil : bandeau « Réinscription 2026-2027 », sélecteur enfant avec flèches (Enfant précédent / Enfant suivant)
- scolarité : Notes (Trimestre 1/2/3), Bulletins, Vie scolaire (Emploi du temps, Absences, Retards, Sanctions), Cahier de texte (Tout / À faire, calendrier)
- factures : chips de filtre (enfant, Statut, Tout effacer), statuts « Payé / Restant / Payée / À payer », bouton « Payer N facture(s) · total », fournisseurs « Max It » et « Wave »
- notifications : « Tout / Non lues », « Tout marquer comme lu »
- bus : statut « En route · il y a 1 min », puce « Monté · 07:12 », toggles Matin / Après-midi
- réinscription : « Réinscription 2026-2027 », services (Cantine scolaire 15 000 F/mois, Tenue de sport 10 000 F/an, Uniforme 15 000 F/an, Cahiers & fournitures 20 000 F/an), total

## 4. DIFFERENCES FROM THE BRIEF
- accueil : clic sur le sélecteur enfant sans effet (feuille non ouverte)
- mes-enfants : la rangée bus des enfants de démo n’est pas un lien (aucune navigation) — le lien bus n’existe que pour le fallback hors liste
- factures : le bouton « Payer … » n’a pas répondu au clic réel (clic scripté utilisé) — barre non cliquable dans la maquette
- STOP RULE appliquée rétroactivement :
  - JSON : 1 entrée retirée de 10_factures_invoice-selected.json (libellé du bouton final de
    paiement : verbe de paiement + fournisseur sélectionné + montant en FCFA).
  - TXT : le bloc de lignes du bouton final de paiement (5 lignes : verbe, fournisseur, séparateur,
    montant, devise) a été retiré de 10_factures_invoice-selected.txt et
    10_factures_payment-sheet.txt. Les rangées fournisseurs « Max It » et « Wave » ainsi que les
    totaux sont conservées.
  - Crops : le crop du bouton retiré a été supprimé ; aucun élément éligible n'est resté sans crop.
- Le sélecteur d'extraction a été étendu (payopt, facture-card, service-check, vs-chip, filter-chip,
  ct-icobtn, ct-calchip, trimestre, reinsc-banner, tile, mini-act, kid-section, sens__seg) : les
  éléments cliquables Alpine (@click) n'ont pas d'attribut onclick et étaient invisibles au
  sélecteur de base du brief.

## 5. CLAIMS TO SUPPORTING SCREENS
- "une flèche suffit pour passer de l’un à l’autre" → screen-accueil.png (flèches présentes) ; l'état "enfant suivant" n'a pas été capturé (voir §7)
- "tout ce que vous voyez concerne l’enfant affiché" → screen-accueil.png + screen-notes.png (bloc enfant courant sur chaque écran)
- "notes et bulletins trimestre par trimestre" → screen-notes.png + 04_notes_t2.png + 04_notes_t3.png + screen-bulletins.png
- "vie scolaire avec absences, retards et sanctions" → 04_vie-scolaire_absences.png + 04_vie-scolaire_retards.png + 04_vie-scolaire_sanctions.png
- "cahier de texte ... au fil de la journée" → 04_cahier-texte_jour-avec-entrees.png
- "à payer ou déjà réglées" → screen-factures.png (statuts Payée / À payer)
- "Max It ou Wave" → 10_factures_payment-sheet.png
- "sans file d’attente ni déplacement" → 10_factures_payment-sheet.png (paiement dans l’app)
- "les annonces ... dans vos notifications" → screen-notifications.png + screen-activites.png
- "monté à 7 heures 12, deux arrêts restants" → screen-bus.png (« Monté · 07:12 »)
- "La réinscription ... depuis l’application" → screen-reinscription.png + 13_reinscription_services-checked.png
- "se fait en quelques minutes" → narration only
- "FINI les carnets perdus, les appels et les allers-retours" → narration only (vignette vidéo)

## 6. TEST DATA
- Enfants fictifs : Amadou Sarr (CM1 B, E220092), Khadi Sarr (CM2 A, E220106), Fatou Sarr (CP A, E220121)
- Parent de démo : « Papa Seydou BA »
- Factures de démo avec périodes et montants FCFA (voir texts/factures.txt)
- Avatars : dicebear (api.dicebear.com, seeds des prénoms)

## 7. PROBLEMS
- Aucun crash. Chargements < 2 s sur file://.
- États non capturés : feuille « Mes Enfants » et bascule d’enfant depuis le sélecteur de l’accueil
  (le clic sur le sélecteur n’ouvre pas la feuille dans la maquette — voir §4).
- Recherche de données sensibles (numéro réel, PIN, OTP, tokens) : effectuée sur texts/ et screens/,
  rien trouvé (données de démonstration uniquement).

## 8. DO NOT INCLUDE
- Respecté : aucun nom réel, numéro réel, PIN, OTP, mot de passe ou donnée de paiement.
  Le bouton final de paiement (fournisseur sélectionné + montant) n’apparaît dans aucun JSON, aucun TXT ni aucun crop ; les rangées fournisseurs « Max It » / « Wave » et les totaux sont conservés..
