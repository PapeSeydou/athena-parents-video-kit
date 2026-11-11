# flow.md — Espace Manager / administrateur (design viewer), captures-roles-2026-11-11

## 1. HEADER
- Source : athena_mobile / design / forks/actuel/admins/screens/ (fork « actuel » ; fork « boutique » non utilisé)
- athena_mobile commit : 8ca716d (branche design/import_new_design)
- Date de capture : 2026-11-11
- Viewport : 412 x 917 CSS px, device scale factor 2, PNG 824 x 1834 (captures hautes : 824 x [1840 à 11814] selon le contenu)
- Serving : live-server du design system (design/, node live-server.js --port=8080 --ignore=node_modules --no-browser), http://localhost:8080, même serveur pour toute la session
- Navigateur : Chromium 156.0.8078.4 (HeadlessChrome), Playwright 1.64.1 (Python), profil propre, souris à 0,0, gel des animations avant chaque PNG
- Compte de démonstration : Omar Ndiaye (affiché « M. Ndiaye », « Manager · changer de profil », rôle détaillé « Directeur ») ; écrans de connexion hors périmètre
- Sécurité données : aucune donnée réelle (voir §7)

## 2. REAL SCREEN ORDER
1. admin_01_accueil_default | reached by : (départ) | status : new
2. admin_02_drawer_ouvert | reached by : « Menu » (burger) | status : new
3. admin_03_profil_changer-sheet | reached by : « Changer de profil » (bloc identité du drawer) | status : new
4. admin_04_finance_default | reached by : navigation directe (drawer « Pilotage » → « Finance ») | status : new
5. admin_05_finance_annee | reached by : « Année » dans la carte « Facturé vs Encaissé » | status : new
6. admin_06_finance_encaissements | reached by : « Année » dans la carte « Encaissements » (onglet par défaut « Mois ») | status : new
7. admin_07_restants_default | reached by : navigation directe (Finance → « Voir le détail › ») | status : new
8. admin_08_restants_filtres | reached by : « Filtrer » | status : new
9. admin_09_restants_facture-recus | reached by : rangée « Fatou Bah CP B · FA2526-000498 · Janvier » | status : new
10. admin_09_restants_facture-sans-recu | reached by : rangée « Fatou Bah CP B · FA2526-000117 · Octobre » | status : new
11. admin_10_annulations_default | reached by : navigation directe (pastille « 2 annulations » du tableau de bord) | status : new
12. admin_11_annulations_detail | reached by : rangée « Facture FA2526-000117 Fatou Bah · CP B » | status : new
13. admin_12_effectifs_default | reached by : navigation directe (drawer « Pilotage » → « Effectifs ») | status : new
14. admin_13_effectifs_cycle | reached by : rangée « Moyen 7 classes · 142 apprenants › » | status : new
15. admin_14_vie-scolaire_ce-mois | reached by : navigation directe (drawer « Vie scolaire » → « Vie scolaire école ») | status : new
16. admin_15_vie-scolaire_trimestre | reached by : « Trimestre » | status : new
17. admin_16_vie-scolaire_filtre | reached by : « Filtrer » (« Type d'événement ») | status : new
18. admin_17_classe_default | reached by : navigation directe (drawer « Fiche classe ») | status : new
19. admin_18_classe_eleves | reached by : navigation directe (« Tout voir › » du module « Apprenants ») | status : new
20. admin_19_classe_vie-scolaire | reached by : navigation directe (« Tout voir › » des modules Absences/Retards/Sanctions) | status : new
21. admin_20_classe_cahier | reached by : navigation directe (« Tout voir › » du module « Cahier de texte ») | status : new
22. admin_21_profs_semaine | reached by : navigation directe (drawer « Professeurs » → « Suivi des profs ») | status : new
23. admin_22_profs_trimestre | reached by : « Trimestre » | status : new
24. admin_23_profs_filtres | reached by : « Filtrer » (Cycle / Statut) | status : new
25. admin_24_profs_detail-prof | reached by : « Semaine » (retour) puis rangée « SO Mme Sow CE2 B · 3 non pointés › » | status : new
26. admin_25_profs_detail-classe | reached by : rangée « SO CE2 B Mme Sow · Lun 26 · Mar 27 · Mer 28 · 3 cours › » (« Classes à vérifier ») | status : new
27. admin_26_notifications_tout | reached by : navigation directe (drawer, « Tout voir › ») | status : new
28. admin_27_notifications_non-lues | reached by : « Non lues » (4) | status : new
29. admin_28_mes-infos | reached by : navigation directe (drawer Réglages → Paramètres → « Mes informations ») | status : new
Captures hautes (contenu > 917 px, barre d'état + en-tête une fois en haut, drawer fermé) : admin_01__full (1840), admin_04__full (2692), admin_05__full (2722), admin_06__full (2692), admin_07__full (2774), admin_17__full (2500), admin_18__full (3672), admin_19__full (3052), admin_20__full (11814), admin_21__full (3230), admin_22__full (2030). Les états avec feuille ouverte (filtres, facture, détail) ne sont pas déroulés.

## 3. EXACT ON-SCREEN TEXT
- Tableau de bord : « ATHENA », « Espace Manager », « Bonjour, M. Ndiaye », « Mercredi 28 janvier » ; tuiles « ENCAISSÉ — CE JOUR » 600 000, « ABSENTS — SEMAINE » 29, « ENCAISSÉ — CE MOIS » 9 697 000, « SANCTIONS — SEMAINE » 3 ; sections « FINANCE » (pastille « 2 annulations »), « EFFECTIFS PAR CYCLE », « VIE SCOLAIRE — CE MOIS », « SUIVI DES PROFS », note « +7 autres absences aujourd'hui — détail dans Vie scolaire. »
- Drawer : « Notifications » + « Tout voir › », groupes « Pilotage » (« Tableau de bord », « Finance », « Effectifs »), « Professeurs » (« Suivi des profs »), « Vie scolaire » (« Vie scolaire école », « Fiche classe »), « Réglages » (« Paramètres », « Déconnexion ») ; identité « M. Ndiaye », « Manager · changer de profil » ; feuille « Changer de profil » : « Espace Manager » (Actif) / « Espace Professeur »
- Finance : « Restant — toutes périodes », « 8 350 000 », « 15 classes concernées · tous les mois, toutes les années », « Facturé vs Encaissé » (onglets « Mois » / « Année »), « Encaissements » (onglets « Jour » / « Mois » / « Année »), « Encaissements par mode — janvier » : « Wave » 4 697 000, « Orange Money » 3 350 000, « Espèces » 1 650 000, « Total » 9 697 000 ; « Restants par cycle » ; « Dépenses — Janvier 2026 » : « Salaires & charges » 5 420 000, « Cantine & fournitures » 850 000, « Entretien & factures » 470 000, « Total » 6 740 000
- Restants : « Factures impayées », groupes « Élémentaire » (« CP → CE1 → CE2 »), « Moyen » (« CM1 → CM2 »), « Secondaire » (« 6e ») ; « Aucune facture impayée pour ces filtres. » ; « Échantillon de factures impayées par apprenant — la liste complète sera alimentée par le back-office. Tap sur une facture pour voir ses reçus. » ; filtres « Filtres — Restants » (« Cycle » : « Tous les cycles / Élémentaire / Moyen / Secondaire », « Mois » : « Tous les mois / Septembre ... Janvier », « Réinitialiser », « Appliquer »)
- Feuille facture : « Facture — FA2526-000498 », « Fatou Bah », « CP B · Janvier », « Facturé » 26 000, « Encaissé » 20 000, « Restant » 6 000, « Reçus 1 », « Reçu RC-2526-0341 », « 20/01/2026 », « Wave », « 20 000 » ; variante « Facture — FA2526-000117 » : « Reçus 0 », « Aucun reçu — rien n'a été encaissé sur cette facture. »
- Annulations : « Annulé — semaine », « 86 000 », « 2 documents · 26 → 28 janvier 2026 », sections « Factures annulées », « Reçus annulés », « Paiements annulés » ; règle « Un document annulé n'est jamais supprimé de l'historique : il est marqué, gardé, et visible ici. » ; feuille détail : « Montant facturé », « Émise le », « Annulée le », « Annulée par » : « M. Ndiaye », « Motif déclaré » : « double saisie » ; limite « Consultation seule. Cette page ne permet ni de rétablir ni de modifier un document. »
- Effectifs : « Inscrits 2025-2026 » 439, « Classes » 18, « Nouveaux » +39, « Professeurs » 20 ; « PAR CYCLE » ; feuille cycle « Moyen — 142 apprenants · 7 classes », niveaux « Niveau CM1 » etc., classes avec professeur et « Ouvrir »
- Vie scolaire : onglets « Ce mois » / « Trimestre » ; cycles « Élémentaire », « Moyen », « Secondaire » avec « absences », « retards », « sanctions » ; trimestre : « 214 absences · 87 retards · 18 sanctions », note « Sanctions — dont 16 avertissements · 2 exclusions d'1 jour » ; « Données transmises par l'appel des classes. » ; filtre « Type d'événement » (« Tous / Absence / Retard / Sanction », « Appliquer »)
- Fiche classe : « CM1 B — Mathématiques », « M. Diallo · Salle 4 · 30 apprenants », tuiles « Effectif » 30, « Absences — mois » 11, « Retards — mois » 7, « Sanctions — mois » 2 ; module « Cahier de texte » (« Entrées cette semaine », « Entrées ce mois », « Devoirs donnés — mois », « Jours de classe renseignés », « Dernière publication : Mercredi 28 janvier · 3 entrées aujourd'hui. ») ; « Dossier de classe en lecture seule. »
- Apprenants : « Apprenants — CM1 B », « 30 apprenants · 16 F / 14 M », « 11 absences · 7 retards · 2 sanction — janvier », « Roster transmis par la scolarité — lecture seule. »
- Vie scolaire de classe : « Vie scolaire — CM1 B », onglets « Absences » / « Retards » / « Sanctions » et « Semaine » / « Mois » / « Année », filtres « Justification » / « Motif », « Un bloc par apprenant concerné... Lecture seule. »
- Cahier de classe : « Cahier de texte — CM1 B », filtres matières (« Toutes / Mathématiques / Français / Anglais / Histo-Géo / Sciences / EPS / Arts Plastiques »), « Journal publié par les professeurs — mêmes entrées que celles vues par les familles, en lecture seule. »
- Suivi des profs : onglets « Semaine » / « Trimestre » ; « Présents » 18, « En retard » 4, « Profs non pointés » 7, « Cours à vérifier » 12 ; « RÉPARTITION — SEMAINE » (« À l'heure » 39, « En retard » 9, « Non pointés » 12, « 20 profs × 3 jours · 60 pointages · référence 08h00 + 10 min ») ; « RETARDS PAR JOUR » ; « Classes à vérifier » ; « Profs à suivre » ; règle « Un prof non pointé un jour de cours = séance à vérifier (oubli de scan possible) — jamais compté absent. » ; filtres « Cycle » (« Tous / Élémentaire / Moyen / Secondaire ») et « Statut » (« Tous / Retards / Non pointés »), « Appliquer » ; feuille professeur : « Mme Sow », « Semaine : 3 non pointés », « Trimestre : 71 pointages · 4 retards · 8 non pointés », jours « Non pointé » / « à vérifier » / « À venir »
- Notifications : « Tout » (6), « Non lues » (4), « Tout marquer comme lu » ; items « Absences déclarées au transport », « 11 absents aujourd'hui », « Restants à recouvrer », « Professeurs non pointés », « Sanction enregistrée », « Réinscriptions 2026-2027 »
- Paramètres et Mes informations : identiques au professeur avec « Rôle » : « Directeur », nom « Omar NDIAYE »

## 4. DIFFERENCES
- Aucun écart bloquant avec docs/roles/ROLES-MAP.md. La carte indiquait : « Remarque : annulations.html n'est déclarée dans aucun groupe du manifest (groupes "Pilotage" : finance, restants, effectifs). Elle est atteinte par la pastille rouge "2 annulations" du tableau de bord. » — confirmé (admin_10 atteint par la pastille, navigation directe utilisée pour la capture).
- La carte ROLES-MAP.md indiquait pour effectifs « "Ouvrir" par classe » — vu : les puces « Ouvrir » sont des liens vers classe.html à l'intérieur de la feuille de cycle (admin_13) ; non capturé en navigation (hors états demandés), le lien existe.
- admin_24 et admin_25 mènent à la MÊME feuille (détail de Mme Sow) : la rangée « Classes à vérifier » ouvre la fiche du professeur concerné, pas une fiche de classe distincte. La carte le laissait ambigu (« détail prof et détail classe ») — précisé ici.
- Les listes « Profs à suivre » / « Classes à vérifier » n'existent que dans l'onglet « Semaine » : retour à « Semaine » effectué après admin_22/23 avant admin_24/25.
- Onglet par défaut des « Encaissements » : « Mois » ; « Jour » reste disponible (admin_06 montre « Année », puis retour à « Mois »).
- Feuilles sans contrôles interactifs (admin_09, admin_11, admin_24, admin_25) : JSON vides car les feuilles n'ont ni bouton ni lien et la zone sombre couvre tout le reste — conforme à la consigne « éléments visibles et non couverts ».
- Restauration d'état : retour « Mois » après admin_05/admin_06 pour laisser chaque état dans son contexte d'origine.

## 5. CLAIMS TO SUPPORTING SCREENS
- le tableau de bord montre quatre indicateurs (encaissé jour, absents semaine, encaissé mois, sanctions semaine) : OUI — admin_01
- la finance montre facturé vs encaissé et les encaissements par mode (Wave, Orange Money, Espèces) : OUI — admin_04 (modes) + admin_05 (« Facturé vs Encaissé » sur « Année ») + admin_06 (« Encaissements » sur « Année »)
- restants liste les impayés par élève et une facture montre ses reçus : OUI — admin_07 + admin_09_restants_facture-recus (Reçu RC-2526-0341, Wave, 20 000) et admin_09_restants_facture-sans-recu (« Aucun reçu — rien n'a été encaissé sur cette facture. »)
- un document annulé n'est jamais supprimé et la page est en consultation seule : OUI — admin_10 + admin_11 (« Un document annulé n'est jamais supprimé de l'historique... » / « Consultation seule. Cette page ne permet ni de rétablir ni de modifier un document. »)
- effectifs montre apprenants, classes, nouveaux, professeurs : OUI — admin_12 (439 / 18 / +39 / 20)
- la vie scolaire montre absences, retards, sanctions par cycle : OUI — admin_14 (ce mois) + admin_15 (trimestre : 214 absences · 87 retards · 18 sanctions)
- le dossier de classe (apprenants, vie scolaire, cahier) est en lecture seule : OUI — admin_17/18/19/20 (« Dossier de classe en lecture seule. », « Roster transmis par la scolarité — lecture seule. », « ...en lecture seule. »)
- un professeur non scanné compte comme « séance à vérifier », jamais comme absent : OUI — admin_21 + admin_24 (« Un prof non pointé un jour de cours = séance à vérifier (oubli de scan possible) — jamais compté absent. », jours « à vérifier » / « Non pointé »)
- l'espace manager n'a aucune action de création, modification ou approbation : OUI — sur les 16 écrans capturés, aucune interface de saisie ; les seuls contrôles sont des onglets, filtres et forages de consultation (libellés « lecture seule » / « Consultation seule »)

## 6. TEST DATA
- Manager fictif : Omar Ndiaye (« M. Ndiaye »), rôle affiché « Directeur »
- École : 439 apprenants, 18 classes, 20 professeurs, +39 nouveaux ; cycles « Élémentaire » (8 classes, 197), « Moyen » (7 classes, 142), « Secondaire » (3 classes, 100)
- Finance : encaissé ce jour 600 000 ; ce mois 9 697 000 ; facturé mensuel 11 400 000 ; restants 8 350 000 (15 classes) ; modes « Wave » 4 697 000, « Orange Money » 3 350 000, « Espèces » 1 650 000 ; dépenses janvier 6 740 000 (dont salaires 5 420 000)
- Factures de démo : « Fatou Bah CP B » FA2526-000117 (Octobre, 26 000, aucun reçu) et FA2526-000498 (Janvier, restant 6 000, reçu RC-2526-0341 du 20/01/2026 par Wave 20 000) ; autres élèves : Moussa Diop, Ousmane Fall, Amadou Sarr, Awa Sow, Bineta Touré, Moussa Konaté, Pape Ndiaye, Awa Ba, Ibrahima Ndiaye, Samba Diop
- Annulation démo : FA2526-000117, « Annulée le » 28/01/2026, « Annulée par » M. Ndiaye, « Motif déclaré » « double saisie » ; semaine = 86 000 (2 documents)
- Professeurs suivis : Mme Sow (CE2 B, 3 non pointés), M. Sagna, M. Ba, M. Diagne (3 retards), M. Sène, Mme Sy, M. Kane ; référence de retard « 08h00 + 10 min »
- Vie scolaire : 11 absents le jour (Awa Sow CM1 B, Djibril Diagne 6e A, Anta Pouye CP B, Ibou Thiam 6e B...), trimestre 214/87/18
- Numéro de téléphone affiché : « +221 77 123 45 67 » (fictif, provenant de design/system/data.js) ; établissement « +221 33 800 00 00 » (fictif)

## 7. PROBLEMS
- Aucun crash, aucune erreur console ; chaque état charge en moins de 2 s sur live-server.
- admin_20 (cahier de classe) est très long (contenu 5907 px -> PNG 824 x 11814) : la capture haute reste lisible mais lourde.
- admin_01 (accueil) dépasse à peine le viewport (contenu 920 px) : capture haute de 1840 px produite pour homogénéité.
- Les listes manager sont des échantillons (« la liste complète sera alimentée par le back-office ») : les filtres « Trimestre / Année » des annulations montrent plus de documents que la pastille semaine (comportement attendu du design).
- Version maquette « Version: 3.0.3, Build:281 » > build lue « 3.0.2+270 ».
- Recherche de données sensibles sur texts/ et screens/ : aucun numéro réel (ni la valeur recherchée à l'étape 0, ni ses variantes), aucun PIN/OTP/mot de passe/jeton ; seuls les numéros fictifs du §6 apparaissent. Un faux positif d'octets sur un PNG binaire a été ignoré.

## 8. DO NOT INCLUDE
- Respecté : aucun nom réel, aucun numéro réel, aucun chiffre de PIN, code OTP, mot de passe ou jeton dans les PNG, JSON, TXT ou le présent fichier.
