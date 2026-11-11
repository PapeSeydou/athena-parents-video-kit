# flow.md — Espace Professeur (design viewer), captures-roles-2026-11-11

## 1. HEADER
- Source : athena_mobile / design / forks/actuel/profs/screens/ (fork « actuel » ; fork « boutique » non utilisé)
- athena_mobile commit : 8ca716d (branche design/import_new_design)
- Date de capture : 2026-11-11
- Viewport : 412 x 917 CSS px, device scale factor 2, PNG 824 x 1834 (captures hautes : 824 x 4426)
- Serving : live-server du design system (design/, npm run serve en direct : node live-server.js --port=8080 --ignore=node_modules --no-browser), http://localhost:8080, même serveur pour toute la session
- Navigateur : Chromium 156.0.8078.4 (HeadlessChrome), Playwright 1.64.1 (Python), profil propre, pas de chrome, pas de curseur, pas d'état hover (souris à 0,0 avant chaque capture), gel des animations (style tag) avant chaque PNG
- Compte de démonstration : Mamadou Diallo (affiché « M. Diallo », « Professeur · changer de profil ») ; écrans de connexion hors périmètre
- Sécurité données : aucune donnée réelle ; les seuls numéros affichés par la maquette sont fictifs (voir §7)

## 2. REAL SCREEN ORDER
1. prof_01_tableau_default | reached by : (départ) | status : new
2. prof_02_tableau_pointage-actif | reached by : navigation directe (variante avec pointage activé) | status : new
3. prof_03_tableau_pointage-scan | reached by : « Pointer » sur la carte « Pointer votre arrivée », puis « Pointer » dans la feuille « Pointer — Salle 4 » (le bouton « Scanner pour pointer » fait partie de cet état de viseur) | status : new
4. prof_04_tableau_autre-jour | reached by : « Jeu 29 » sur prof_01 | status : new
5. prof_05_drawer_ouvert | reached by : « Menu » (burger) sur prof_01 | status : new
6. prof_06_profil_changer-sheet | reached by : « Changer de profil » (bloc identité du drawer) | status : new
7. prof_07_fiche-classe_default | reached by : navigation directe (CM1 B — Mathématiques, liste d'appel) | status : new
8. prof_08_fiche-classe_absent | reached by : rangée « Amadou Sarr » puis « Marquer absent » dans la feuille de l'apprenant | status : new
9. prof_09_cahier_vide | reached by : « Cahier de texte » sur fiche-classe | status : new
10. prof_10_cahier_dictee | reached by : micro « Dicter Séance du jour par la voix » dans la feuille « Cahier — CM1 B » | status : new
11. prof_11_cahier_rempli | reached by : « J'ai terminé » (séance), micro « Dicter Travail donné par la voix », « J'ai terminé » (travail) | status : new
12. prof_12_cahier_publie | reached by : « Publier » | status : new
13. prof_13_retard_sheet | reached by : rangée « Mariama Diallo » puis « Retard » dans la feuille de l'apprenant (la feuille se referme d'elle-même, voir §4) | status : new
14. prof_14_sanction_sheet | reached by : rangée « Ibrahima Ndiaye », « Sanction », motif « Bavardage » | status : new
15. prof_15_emploi-du-temps | reached by : navigation directe (drawer « Emploi du temps ») | status : new
16. prof_16_devoirs_a-venir | reached by : navigation directe (haut de page, section « À venir ») | status : new
17. prof_17_devoirs_passes | reached by : défilement jusqu'à la section « Passés » | status : new
18. prof_18_devoirs_saisie | reached by : — | status : UNREACHABLE (voir §4)
19. prof_19_devoirs_detail-note | reached by : rangée « Devoir — Mathématiques CM1 B · Lun 26/01 » | status : new
20. prof_20_notifications_tout | reached by : navigation directe (drawer, « Tout voir › ») | status : new
21. prof_21_notifications_non-lues | reached by : « Non lues » (2) | status : new
22. prof_22_mes-infos | reached by : navigation directe (drawer Réglages → Paramètres → « Mes informations ») | status : new
Captures hautes (contenu > 917 px) : prof_07__full et prof_08__full (824 x 4426, contenu 2213 px, barre d'état et en-tête peints une fois en haut, drawer fermé). devoirs et emploi-du-temps tiennent dans le viewport (contenu mesuré <= 917 px), pas de __full nécessaire.

## 3. EXACT ON-SCREEN TEXT
- En-tête accueil : « ATHENA », « Espace Professeur », « Bonjour, M. Diallo »
- Pointage inactif : « Le pointage existe dans Athena, mais il n'est pas actif dans votre établissement. », puce « Non activé » ; variante active : « Pointer votre arrivée », « Scannez le QR à l'entrée pour signaler votre présence à l'école. », « Pointer », « Scannée 7h58 · Porte A »
- Feuille « Pointer — Salle 4 » : « Mercredi 28/01/2026 · Mathématiques · séance 08h00 », « Vous êtes bien en Salle 4 ? Pointez pour confirmer votre présence à la séance. », « Pointer », « Viseur caméra — visez le QR de la salle », « Scanner pour pointer », preuve « Scannée 8h02 · Salle 4 »
- Jours : « Lun 26 », « Mar 27 », « Mer 28 », « Jeu 29 », « Ven 30 » ; section « MES COURS », lien « EMPLOI DU TEMPS › » (rendu en capitales)
- Drawer : « Notifications », « Tout voir › », groupes « Accueil » (lien « Ma journée »), « Emploi du temps », « Devoirs », « Réglages » (« Paramètres », « Déconnexion ») ; bloc identité « M. Diallo », « Professeur · changer de profil »
- Feuille « Changer de profil » : « Espace Professeur » (détail « Vos classes · l'appel · le cahier », marqueur « Actif »), « Espace Parents » (détail « Suivre la scolarité de vos enfants »), « Fermer ✕ »
- Fiche-classe : « CM1 B — Mathématiques », « Mercredi 28/01/2026 · 08h00 · Salle 4 », « Scanner pour pointer (Salle 4) », compteur « 30/30 présents » (puis « 29/30 présents »), puces « Présent » / « Absent » / « Retard », « Modifications transmises automatiquement à la vie scolaire. », feuille apprenant : « Marquer absent » / « Marquer présent », « Retard », « Sanction » ; indices « Présent — compté dans l'appel », « Absent — signalé à la vie scolaire », « En retard — compté présent »
- Feuille « Cahier — CM1 B » : sections « En classe (on a fait) » (champ « Séance du jour ») et « À faire (prochaine séance) » (champ « Travail donné »), micro « Dicter Séance du jour par la voix » / « Dicter Travail donné par la voix », « Enregistrement… », « J'ai terminé », « Annuler l'enregistrement », « Publier », « Visible par les parents dans le cahier de texte. », état publié « Publié — visible par les parents » + « Modifier »
- Feuille sanction : « Sanction — Ibrahima Ndiaye », « Motif : », motifs « Bavardage », « Retard », « Devoir non fait », « Tenue », « Insolence », « Autre », « Note (optionnel) », « Ajouter la sanction »
- Emploi du temps : grille « Lun » à « Ven », heures 08h à 14h, ligne « Pause », cours « Mathématiques / Salle 4 » et « Français / Salle 7 »
- Devoirs : sections « À venir » et « Passés », rangées « Devoir — Mathématiques », moyennes « 11,4 » / « 12,0 », « 25/29 ont réussi », « 5/6 ont réussi », puce « À saisir », feuille détail : « Moyenne de la classe », mention « abs. »
- Notifications : « Tout » (5), « Non lues » (2), « Tout marquer comme lu » ; items « Cahier de texte à remplir », « Devoirs à valider », « Message de la direction », « Appel enregistré », « Sanction enregistrée »
- Paramètres : « Informations de l'établissement » (« École · contacts »), « Mes informations » (« Compte et profil »), « Modifier mon code PIN » (« Code secret à 4 chiffres »), « Me déconnecter » (« Quitter l'application »), « Version: 3.0.3, Build:281 », lien « Conditions générales d'utilisation », feuille « Modification de code PIN » (« Annuler » / « Confirmer » — jamais confirmée)
- Mes informations : « Profil », « Prénoms & Nom » : « Mamadou DIALLO », « Numéro de téléphone » : fictif, « Rôle » : « Professeur »

## 4. DIFFERENCES
- fiche-classe ouvre TOUTE SEULE la feuille « Pointer — Salle 4 » 4 s après le chargement si la salle n'est pas pointée (x-init setTimeout 4000). Nudge automatique du design : attendu (4,6 s), fermé par tap sur la zone sombre, puis prof_07 et les états suivants capturés sans la feuille.
- Aucune feuille « Retard » dédiée n'existe : l'option « Retard » de la feuille apprenant applique la puce « Retard » et referme la feuille (setPresence fait eleve.open = false). prof_13 montre donc la liste d'appel avec la puce « Retard » (compteur « 29/30 présents »).
- prof_18_devoirs_saisie UNREACHABLE : la rangée « À saisir » (CM1 B · Mer 28/01) est un div.row sans handler (@click absent) et la maquette n'a aucune interface de saisie de notes. Écart avec docs/roles/ROLES-MAP.md qui indiquait : « Saisir les notes d'un devoir : devoirs, ouvrir un devoir à l'état "À saisir", saisir une note par élève (absent : "abs."), la moyenne se calcule et s'affiche "Moyenne de la classe". » — vu : pas de saisie possible, la maquette n'affiche que des devoirs déjà notés (prof_19).
- Écart ROLES-MAP.md sur le retard : la carte indiquait « Déclarer un retard ou une sanction : fiche-classe, bouton "Retard" ou "Sanction", sheet avec "Motif :" ... "Ajouter la sanction" ». Vu : la feuille avec « Motif : » et « Ajouter la sanction » n'existe que pour la SANCTION ; le retard s'applique sans motif ni feuille.
- « À venir » et « Passés » ne sont pas des onglets mais deux sections empilées de la même page ; prof_16 = haut de page, prof_17 = page défilée sur « Passés ».
- prof_19 : le JSON ne contient aucun élément (la feuille de détail du devoir n'a aucun contrôle interactif et la zone sombre couvre tout le reste) — conforme à la consigne « éléments visibles et non couverts ».
- Restauration d'état entre captures : retour « Mois » après admin non applicable ici ; côté profs, aucune restauration nécessaire (chaque écran revient par navigation directe).

## 5. CLAIMS TO SUPPORTING SCREENS
- l'appel marque un élève absent d'un seul tap et la page dit que les changements vont automatiquement à la vie scolaire : OUI — prof_08 (« Marquer absent » en un tap sur la feuille, puce « Absent », compteur « 29/30 présents », ligne « Modifications transmises automatiquement à la vie scolaire. »)
- le cahier de texte peut être dicté à la voix : OUI — prof_10 (« Enregistrement… » en cours après le micro « Dicter Séance du jour par la voix ») et prof_11 (texte démo du design ajouté aux deux champs après « J'ai terminé »)
- un cahier publié est « visible par les parents » : OUI — prof_12 (« Publié — visible par les parents » + bouton « Modifier »)
- les notes se saisissent par élève, « abs. » existe et la moyenne de classe se met à jour : PARTIEL — l'affichage par élève avec « abs. » et « Moyenne de la classe » : OUI (prof_19, moyenne 11,4, « Ndeye Awa Youm abs. ») ; la SAISIE : NON, aucune interface (prof_18 non capturable, voir §4)
- le professeur ne voit que ses classes : OUI — prof_01/prof_04 (« Mes cours » limité à CM1 B, CM1 A, CM2 A, 6e A, 6e B), prof_15 (emploi du temps des mêmes classes), prof_07 (appel CM1 B) ; aucun accès finance/effectifs dans le drawer
- le pointage QR existe et peut être « Non activé » : OUI — prof_01 (bande « Non activé ») et prof_02/prof_03 (pointage actif, viseur caméra)

## 6. TEST DATA
- Professeur fictif : Mamadou Diallo (« M. Diallo »), matières Mathématiques (Salle 4) et Français (Salle 7)
- Classes : CM1 B (30 élèves, classe vitrine), CM1 A, CM2 A (Mathématiques), 6e A, 6e B (Français)
- Élèves CM1 B récurrents : Amadou Sarr (marqué absent dans prof_08), Mariama Diallo (Retard dans prof_13), Ibrahima Ndiaye (sanction « Bavardage » dans prof_14), Awa Sow, Modou Gueye, Bineta Touré, Mame Diarra Dème, Ndeye Awa Youm (« abs. » au devoir noté)
- Devoirs : « Devoir — Mathématiques CM1 B · Lun 26/01 » moyenne 11,4 (25/29 ont réussi), « Devoir — Français 6e B · Mar 27/01 » moyenne 12,0 (5/6), « À saisir » CM1 B · Mer 28/01
- Cahier démo (inséré par la dictée) : « Les apprenants ont fait des exercices d'application au tableau. » / « Apprendre la table de 3 pour la prochaine séance. » ; champs préremplis « La multiplication posée à deux chiffres. » / « Exercices 8-10 p.48 »
- Motifs de sanction : « Bavardage », « Retard », « Devoir non fait », « Tenue », « Insolence », « Autre »
- Numéro de téléphone affiché : « +221 77 654 32 10 » (fictif, provenant de design/system/data.js) ; établissement « +221 33 800 00 00 » (fictif)

## 7. PROBLEMS
- Aucun crash, aucune erreur console ; chaque état charge en moins de 2 s sur live-server.
- Nudge automatique du scan à 4 s (voir §4) : à connaître pour toute future capture de fiche-classe.
- Feuilles sans contrôles (prof_19) : JSON vide car rien d'interactif n'est visible — voulu.
- La puce d'arrivée « Scannée 7h58 · Porte A » est une décoration statique de la variante pointage (la carte « Pointer votre arrivée » reste affichée).
- Version maquette « 3.0.3, Build:281 » > build lue « 3.0.2+270 ».
- Recherche de données sensibles sur texts/ et screens/ : aucun numéro réel (ni la valeur recherchée à l'étape 0, ni ses variantes), aucun PIN/OTP/mot de passe/jeton ; seuls les numéros fictifs du §6 apparaissent. Un faux positif d'octets sur un PNG binaire a été ignoré.

## 8. DO NOT INCLUDE
- Respecté : aucun nom réel, aucun numéro réel, aucun chiffre de PIN, code OTP, mot de passe ou jeton dans les PNG, JSON, TXT ou le présent fichier.
