# Carte des rôles — professeur et administrateur (Athena School)

Analyse statique du rôle professeur et du rôle administrateur (« Manager ») dans Athena School, plus les autres rôles trouvés. Document de travail pour le kit vidéo « Espace Parents » ; il complète docs/CAPTURES.md, qui couvre le flux parents.

- Sources : dépôt athena_mobile (code Flutter) et son dossier design/ (forks « actuel » et « boutique »). Aucune exécution contre des données réelles, aucune capture d'écran, aucune donnée personnelle réelle.
- Build lue : application « athena », version 3.0.2+270 (pubspec.yaml), branche design/import_new_design, commit 8ca716d (2026-11-09).
- Maquettes lues : design/system/ (data.js, components.js, manifest.js) et design/forks/actuel/ (écrans HTML générés par design/scripts/gen_*.js). Les maquettes affichent « Version: 3.0.3, Build:281 » : elles décrivent un état légèrement postérieur à la build lue.
- Méthode : chaque libellé français ci-dessous est copié tel quel du code ou des maquettes. Ce qui n'a pas été trouvé est marqué « non trouvé » avec l'endroit où la recherche a eu lieu.

## 1. Rôles qui existent

| Rôle | Nom dans le code | Libellé à l'écran | Présence |
|---|---|---|---|
| Parent | clé « parent » (data.js, window.ATHENA.account) ; côté build, valeur du champ role renvoyée par le backend | « Espace Parents », « Parent » | build + maquettes |
| Professeur | window.PROFS (data.js), dossiers design/forks/*/profs/ | « Espace Professeur », « Professeur » | maquettes seulement |
| Manager (l'administrateur) | window.ADMIN (data.js), dossiers design/forks/*/admins/, slot de drawer « admins » ; ancien nom « Espace Admins » renommé « Manager » | « Espace Manager » ; rôle détaillé affiché : « Directeur » | maquettes seulement |
| Surveillant de sortie | dossier design/forks/*/surveillant-sortie/, slot de drawer « surveillant-sortie » | « Poste de sortie » (pas de libellé de rôle à l'écran) | maquette seulement |
| Accompagnateur (bus) | dossier design/forks/*/accompagnateur/ ; nom du manifest : « Espace Bus scolaire » | « Bus scolaire » (pas de libellé de rôle à l'écran) | maquettes seulement |

Non trouvé : comptable, intendant, censeur, proviseur, surveillant général ou tout autre rôle. Recherches menées dans lib/ (149 fichiers Dart) pour « professeur, administrateur, surveillant, comptable, directeur, enseignant, teacher, admin, manager, staff, role » et dans design/ (fichiers HTML, data.js, manifest.js) : aucun autre rôle que les cinq ci-dessus.

### 1.1 Connexion et détermination du rôle

Dans la build, la connexion est unique et identique pour tous les rôles :

- Un seul écran d'authentification (lib/screens/auth_screen.dart, route /auth) : champs « Numéro de téléphone » et « Code d'établissement », bouton « Envoyer », lien « Conditions Générales d'Utilisation ». Aucun sélecteur de rôle.
- Le couple téléphone + code établissement part sur POST /v2/verify_school_code (lib/data/repository.dart). La réponse porte status_code, mobile_access, school, role, person_id, pin_defined.
- Le rôle vient donc du backend, pas d'un choix local. Il est stocké (Prefs.roleKey) puis renvoyé au serveur à l'OTP (POST /v2/verify_otp) et à la modification de PIN (POST /v2/pin/modification/complete). Les valeurs possibles du rôle ne sont pas énumérées dans le client : champ libre, non trouvé.
- Si un PIN est défini : écran « Enter pin » (PUT /v2/pin/verify, token Firebase personnalisé). Sinon : OTP par SMS (/v2/sms/send) puis création de PIN.
- Après connexion, le routeur (lib/widgets/app_router.dart) ouvre le shell parents à quatre onglets (« Accueil », « Factures », « Notes », « Paramètres »), quel que soit le rôle. Dans la build 3.0.2+270, un professeur ou un administrateur qui se connecte voit l'interface parents. Aucun écran professeur ou administrateur n'existe dans lib/.
- Vestige administrateur : lib/helpers.dart contient backToImpersonate(), qui écrit un scope « ROLE_ADMIN » et un jeton d'impersonation dans le stockage. Globals.scope n'est lu nulle part ailleurs : cette fonctionnalité n'est reliée à aucune interface. Aucun écran d'impersonation : non trouvé.

Dans les maquettes, la connexion est hors périmètre (les decks démarrent après login). Le changement de rôle est en revanche spécifié et implémenté (spec design/.agents/design/profiles-switcher.md) :

- Bloc identité en tête du drawer, sur chaque écran de chaque espace : avatar initiales, nom, rôle actif et mention « changer de profil » (exemple professeur : « M. Diallo », « Professeur · changer de profil »).
- Tap sur le bloc : bottom sheet « Changer de profil » qui liste les profils du compte, l'actif marqué « Actif », les autres en liens vers l'accueil de l'espace cible. Pas de reconnexion.
- Le bloc n'existe que pour les comptes multi-profils ; un compte mono-profil ne l'affiche pas.
- Comptes de démonstration multi-profils : Papa Seydou BA (Parent + Manager), Mamadou Diallo (Professeur + Parent), Omar Ndiaye (Manager + Professeur).

## 2. Rôle par rôle

### 2.1 Professeur — « Espace Professeur » (maquettes, design/forks/actuel/profs/screens/)

#### a. Accueil

Fichier tableau-m2.html, titre d'onglet « Athena Profs — Vue classes ». Widget par widget :

- En-tête : logo « ATHENA », sous-titre « Espace Professeur », salutation « Bonjour, M. Diallo ».
- Module « Pointage » : par défaut, message « Le pointage existe dans Athena, mais il n'est pas actif dans votre établissement. » avec puce « Non activé ». Variante avec pointage activé (tableau-m2-pointage.html) : carte « Pointer votre arrivée » (« Scannez le QR à l'entrée pour signaler votre présence à l'école. », bouton « Pointer », preuve « Scannée 7h58 · Porte A ») et carte « Pointer — Salle 4 » (« Vous êtes bien en Salle 4 ? Pointez pour confirmer votre présence à la séance. », bouton « Pointer », lien « Scanner pour pointer », preuve « Scannée 8h02 · Salle 4 »).
- Chips de jours : « Lun 26 », « Mar 27 », « Mer 28 », « Jeu 29 », « Ven 30 ».
- Section « Mes cours » avec lien « Emploi du temps › » : pour le jour choisi, chaque cours montre la classe, la matière et le créneau (exemple : « CM1 B », « Mathématiques », « 08h00 – 09h00 »).

#### b. Navigation

Drawer (barre latérale), dans l'ordre :

1. Bloc identité « M. Diallo », « Professeur · changer de profil » (ouvre « Changer de profil »).
2. « Notifications » avec compteur de non lues et lien « Tout voir › ».
3. Groupe « Accueil » : lien « Ma journée » (vers tableau-m2.html).
4. Groupe « Emploi du temps » : lien « Emploi du temps ».
5. Groupe « Devoirs » : lien « Devoirs ».
6. Groupe « Réglages » : liens « Paramètres » et « Déconnexion ».

Sheet « Changer de profil » : « Espace Professeur », détail « Vos classes · l'appel · le cahier », marqueur « Actif » ; puis « Espace Parents », détail « Suivre la scolarité de vos enfants ».

#### c. Liste des écrans

| Fichier | Titre français | Objet | Informations clés | Actions (libellés exacts) |
|---|---|---|---|---|
| tableau-m2.html | « Athena Profs — Vue classes » | Accueil de l'espace | Pointage (état), jours, « Mes cours » | Ouvrir un cours, « Emploi du temps › », pointage si activé |
| tableau-m2-pointage.html | « Athena Profs — Vue classes » | Accueil, variante pointage actif | Cartes arrivée (porte) et séance (salle) | « Pointer », « Scanner pour pointer », « Viseur caméra — visez le QR de la salle » |
| fiche-classe.html | « Athena Profs — Classe » | Classe du jour | « CM1 B — Mathématiques », « Mercredi 28/01/2026 · 08h00 · Salle 4 », liste d'appel élève par élève avec matière et état « Présent » | Bascule « Présent », « Cahier de texte », « Retard », « Sanction », « Pointer — Salle 4 », « Publier », « Modifier » |
| emploi-du-temps.html | « Athena Profs — Emploi du temps » | Semaine type | Grille « Lun » à « Ven », créneaux 08h à 14h, ligne « Pause » | Lecture seule |
| devoirs.html | « Athena Profs — Devoirs » | Devoirs et notes | Onglets « À venir » et « Passés », état « À saisir », moyenne « 11,4 », « 25/29 ont réussi », mention « abs. » pour un élève absent à l'évaluation | Saisir les notes, ouvrir le détail d'un devoir noté (liste élève/note, « Moyenne de la classe ») |
| notifications.html | « Athena Profs — Notifications » | Centre de notifications | Onglets « Tout » et « Non lues » | « Tout marquer comme lu » |
| parametres.html | « Athena Profs — Paramètres » | Réglages | 4 rangées + version + lien CGU + sheet PIN | Voir 2.1 g |
| parametres-etablissement.html | « Athena Profs — Informations de l'établissement » | Établissement | Bloc logo « Athena School », carte « Contact » : « Numéro de téléphone » et « Adresse E-mail » | Lecture seule |
| parametres-mes-infos.html | « Athena Profs — Mes informations » | Profil du compte | Carte « Profil » : « Prénoms & Nom », « Numéro de téléphone », « Rôle » avec valeur « Professeur » | Lecture seule |
| parametres-cgu.html | « Athena Profs — Conditions générales d'utilisation » | CGU | Texte « ATHENA SCHOOL BY SEPRO » (GROUPE SEPRO SARL), extrait + emplacement réservé pour le texte officiel | Lecture seule |

#### d. Tâches de bout en bout (séquences conçues dans les maquettes)

- Faire l'appel : accueil, choisir le jour et le cours (exemple « CM1 B · Mathématiques · 08h00 »), la fiche-classe s'ouvre, basculer chaque élève entre « Présent » et absent. Mention affichée : « Modifications transmises automatiquement à la vie scolaire. »
- Pointer sa présence : « Pointer votre arrivée », viser le QR de l'entrée, preuve « Scannée 7h58 · Porte A » ; à l'heure de la séance, « Pointer — Salle 4 », confirmation « Vous êtes bien en Salle 4 ? », preuve « Scannée 8h02 · Salle 4 ».
- Remplir le cahier de texte : fiche-classe, bouton « Cahier de texte », sheet « Cahier — CM1 B » ; champ « En classe (on a fait) » avec libellé « Séance du jour » et dictée vocale (« Enregistrement… », « J'ai terminé », « Annuler l'enregistrement ») ; champ « À faire (prochaine séance) » avec libellé « Travail donné » ; bouton « Publier » avec mention « Visible par les parents dans le cahier de texte. » ; une fois publié : « Publié — visible par les parents » et bouton « Modifier ».
- Déclarer un retard ou une sanction : fiche-classe, bouton « Retard » ou « Sanction », sheet avec « Motif : » (vocabulaire exact : « Bavardage », « Retard », « Devoir non fait », « Tenue », « Insolence », « Autre »), champ « Note (optionnel) », bouton « Ajouter la sanction ».
- Saisir les notes d'un devoir : devoirs, ouvrir un devoir à l'état « À saisir », saisir une note par élève (absent : « abs. »), la moyenne se calcule et s'affiche « Moyenne de la classe ».
- Consulter son emploi du temps : accueil, lien « Emploi du temps › » ou drawer, groupe « Emploi du temps ».
- Changer de profil : drawer, bloc identité, sheet « Changer de profil », rangée « Espace Parents ».

Vérification des exemples demandés :

| Tâche | Verdict |
|---|---|
| Faire l'appel (présences) | Oui, maquettes (appel par classe, transmission automatique à la vie scolaire) |
| Saisir des notes | Oui, maquettes (saisie par devoir, moyenne de classe) |
| Remplir le cahier de texte | Oui, maquettes (dont dictée vocale) |
| Voir l'emploi du temps | Oui, maquettes (lecture) |
| Envoyer une annonce | Non trouvé (aucun écran de rédaction d'annonce ; l'espace reçoit « Message de la direction » en notification) |
| Écrire aux parents | Non trouvé (pas de messagerie ; le canal vers les parents est le cahier publié) |
| Gérer classes ou élèves | Non (le professeur consulte ses classes, aucune création ni modification) |
| Factures et paiements | Non (aucun accès professeur) |
| Bus | Non pour le professeur (l'accompagnateur a son propre espace) |
| Réinscription | Non |
| Approuver des demandes | Non trouvé |

#### e. Permissions et limites

- Périmètre : ses classes seulement. Le compte de démonstration a cinq classes (CM1 B et CM2 A en Mathématiques, 6e A et 6e B en Français, CM1 A en Mathématiques) ; le CM1 B compte 30 élèves.
- L'appel et le cahier alimentent automatiquement la vie scolaire et le cahier que les parents lisent.
- Aucun accès : finance, effectifs, autres classes, paramètres de l'établissement (lecture seule).

#### f. Notifications

Centre dédié (page et drawer). Notifications de démonstration, types internes entre parenthèses :

- « Cahier de texte à remplir » — « CM1 B · séance du jour non publiée » (cahier)
- « Devoirs à valider » — « CM1 B · 2 devoirs cette semaine » (devoir)
- « Message de la direction » — « Conseil de classe — mer. 4 fév. » (direction)
- « Appel enregistré » — « 6e A · appel du 26 janv. transmis » (appel)
- « Sanction enregistrée » — « Modou Gueye · bavardages répétés » (sanction)

#### g. Paramètres et profil

Liste « Paramètres », 4 rangées : « Informations de l'établissement » (détail « École · contacts »), « Mes informations » (détail « Compte et profil »), « Modifier mon code PIN » (détail « Code secret à 4 chiffres »), « Me déconnecter » (détail « Quitter l'application »). Sous le pied de page « Version: 3.0.3, Build:281 », lien « Conditions générales d'utilisation ». Sheet de confirmation PIN : « Modification de code PIN », « Êtes-vous sûr de vouloir modifier votre code PIN actuel ? », boutons « Annuler » et « Confirmer ». Pas d'écran de saisie du nouveau PIN dans la maquette : non trouvé.

### 2.2 Manager (l'administrateur) — « Espace Manager » (maquettes, design/forks/actuel/admins/screens/)

#### a. Accueil

Fichier accueil.html, titre d'onglet « Athena Manager — Tableau de bord ». Widget par widget :

- En-tête : logo « ATHENA », sous-titre « Espace Manager », salutation « Bonjour, M. Ndiaye », date « Mercredi 28 janvier ».
- Bande de 4 indicateurs : « Encaissé — ce jour » (600 000), « Absents — semaine » (29), « Encaissé — ce mois » (9 697 000), « Sanctions — semaine » (3).
- Section « Finance » : restants par cycle (total 8 350 000 ; « Élémentaire », « Moyen », « Secondaire »), pastille rouge « 2 annulations », lien « Tout voir › ».
- Section « Effectifs par cycle » : « 439 apprenants », « Élémentaire », « Moyen », « Secondaire », lien « Tout voir › ».
- Section « Vie scolaire — ce mois » : par cycle (absences, retards, sanctions), lien « Tout voir › ».
- Section « Suivi des profs » : « 5 profs non pointés aujourd'hui », « 4 profs en retard cette semaine », « 7 classes à vérifier » et « 12 cours sans pointage », lien « Tout voir › ».
- Note de fin : « +7 autres absences aujourd'hui — détail dans Vie scolaire. »

#### b. Navigation

Drawer, dans l'ordre : bloc identité « M. Ndiaye », « Manager · changer de profil » ; « Notifications » + « Tout voir › » ; groupes :

1. « Pilotage » : « Tableau de bord », « Finance », « Effectifs ».
2. « Professeurs » : « Suivi des profs ».
3. « Vie scolaire » : « Vie scolaire école », « Fiche classe ».
4. « Réglages » : « Paramètres », « Déconnexion ».

#### c. Liste des écrans

| Fichier | Titre français | Objet | Informations clés | Actions (libellés exacts) |
|---|---|---|---|---|
| accueil.html | « Athena Manager — Tableau de bord » | Tableau de bord école | Voir 2.2 a | Forages vers les écrans, pastille « 2 annulations » |
| finance.html | « Athena Manager — Finance » | Finance école | « Restant — toutes périodes » (8 350 000, « 15 classes concernées »), « Facturé vs Encaissé » (onglets « Mois » / « Année »), « Encaissements » (onglets « Jour » / « Mois » / « Année »), « Encaissements par mode — janvier » (« Wave », « Orange Money », « Espèces », « Total »), « Restants par cycle », « Dépenses — Janvier 2026 » (« Salaires & charges », « Cantine & fournitures », « Entretien & factures », « Total ») | « Voir le détail › », onglets, graphiques |
| restants.html | « Athena Manager — Restants » | Impayés par apprenant | Total « 8 350 000 », groupes « Élémentaire », « Moyen », « Secondaire » ; chaque ligne : élève, classe, numéro de facture, mois, montant ; « Aucune facture impayée pour ces filtres. » ; mention « Échantillon de factures impayées par apprenant — la liste complète sera alimentée par le back-office. » | Filtres (« Cycle », « Mois », « Réinitialiser », « Appliquer »), tap facture : sheet « Facture » (« Facturé », « Encaissé », « Restant », « Reçus », « Aucun reçu — rien n'a été encaissé sur cette facture. ») |
| annulations.html | « Athena Manager — Annulations » | Documents annulés | « Annulé — semaine » (86 000, « 2 documents »), sections « Factures annulées », « Reçus annulés », « Paiements annulés » ; règle : « Un document annulé n'est jamais supprimé de l'historique : il est marqué, gardé, et visible ici. » ; limite : « Consultation seule. Cette page ne permet ni de rétablir ni de modifier un document. » | Filtres « Période » (« Semaine », « Mois », « Trimestre », « Année ») ; détail : « Montant facturé », « Émise le », « Annulée le », « Annulée par », « Motif déclaré » |
| effectifs.html | « Athena Manager — Effectifs » | Effectifs par niveau | « Inscrits 2025-2026 » (439), « Classes » (18), « Nouveaux » (+39), « Professeurs » (20) ; « Par cycle » puis par niveau (CP à 6e) avec classes, professeur et effectif | « Ouvrir » par classe, onglets par cycle |
| vie-scolaire.html | « Athena Manager — Vie scolaire école » | Vie scolaire de l'école | Onglets « Ce mois » / « Trimestre » ; par cycle : absences, retards, sanctions (exemple trimestre : 214 absences, 87 retards, 18 sanctions, note « Sanctions — dont 16 avertissements · 2 exclusions d'1 jour ») ; « Données transmises par l'appel des classes. » | Filtre « Type d'événement » (« Tous », « Absence », « Retard », « Sanction », « Appliquer ») ; forage vers la fiche classe |
| classe.html | « Athena Manager — Classe CM1 B » | Fiche classe | Sous-titre « M. Diallo · Salle 4 · 30 apprenants » ; tuiles « Effectif » (30), « Absences — mois » (11), « Retards — mois » (7), « Sanctions — mois » (2) ; module « Cahier de texte » (« Entrées cette semaine », « Entrées ce mois », « Devoirs donnés — mois », « Jours de classe renseignés », « Dernière publication ») ; listes du mois ; limite « Dossier de classe en lecture seule. » | « Tout voir › » vers les sous-écrans |
| classe-eleves.html | « Athena Manager — Apprenants CM1 B » | Roster de la classe | « M. Diallo · Salle 4 · 30 apprenants · 16 F / 14 M », compteurs du mois ; « Roster transmis par la scolarité — lecture seule. » | Filtre, « Réinitialiser » |
| classe-vie-scolaire.html | « Athena Manager — Vie scolaire CM1 B » | Vie scolaire de la classe | Onglets « Absences » / « Retards » / « Sanctions » et fenêtres « Semaine » / « Mois » / « Année » ; un bloc par apprenant | Filtres (« Justification », « Motif », « Réinitialiser les filtres », « Appliquer ») |
| classe-cahier.html | « Athena Manager — Cahier de texte CM1 B » | Cahier publié de la classe | Filtres par matière et période ; « Journal publié par les professeurs — mêmes entrées que celles vues par les familles, en lecture seule. » | Filtres (« Toutes » matières, « Période » : « Tout » / « Ce mois » / « Cette semaine », « Pièces jointes », « Réinitialiser », « Appliquer ») |
| profs.html | « Athena Manager — Suivi des profs » | Assiduité des professeurs | Onglets « Semaine » / « Trimestre » ; indicateurs « Présents », « En retard », « Profs non pointés », « Cours à vérifier » ; « Répartition — semaine » (« À l'heure » 39, « En retard » 9, « Non pointés » 12, note « 20 profs × 3 jours · 60 pointages · référence 08h00 + 10 min ») ; « Retards par jour » ; « Classes à vérifier » ; « Profs à suivre » ; règle « Un prof non pointé un jour de cours = séance à vérifier (oubli de scan possible) — jamais compté absent. » | Filtres (« Cycle », « Statut » : « Retards », « Non pointés », « Appliquer », « Réinitialiser ») ; détail prof et détail classe |
| notifications.html | « Athena Manager — Notifications » | Centre de notifications | Onglets « Tout » / « Non lues » | « Tout marquer comme lu » |
| parametres.html | « Athena Manager — Paramètres » | Réglages | 4 rangées identiques au professeur + version + lien CGU + sheet PIN | Voir 2.2 g |
| parametres-etablissement.html | « Athena Manager — Informations de l'établissement » | Établissement | Identique au professeur | Lecture seule |
| parametres-mes-infos.html | « Athena Manager — Mes informations » | Profil | « Prénoms & Nom » : Omar NDIAYE ; « Numéro de téléphone » ; « Rôle » : « Directeur » | Lecture seule |
| parametres-cgu.html | « Athena Manager — Conditions générales d'utilisation » | CGU | Identique au professeur | Lecture seule |

Remarque : annulations.html n'est déclarée dans aucun groupe du manifest (groupes « Pilotage » : finance, restants, effectifs). Elle est atteinte par la pastille rouge « 2 annulations » du tableau de bord.

#### d. Tâches de bout en bout (séquences conçues dans les maquettes)

- Piloter la finance : accueil, section « Finance », « Tout voir › » vers Finance, changer d'onglet (« Mois » / « Année »), « Voir le détail › » vers Restants, filtrer par cycle et mois, ouvrir une facture, consulter ses reçus.
- Consulter les annulations : accueil, pastille « 2 annulations », page Annulations, filtrer par période, ouvrir un document pour voir le motif.
- Suivre les effectifs : accueil, « Effectifs par cycle », « Tout voir › », choisir un cycle puis un niveau, « Ouvrir » une classe vers la fiche.
- Suivre la vie scolaire école : accueil, « Vie scolaire — ce mois », « Tout voir › », filtrer par type d'événement, forer vers une classe.
- Consulter le dossier de classe : vie-scolaire ou effectifs, ouvrir la classe, onglets vers « Apprenants », « Vie scolaire », « Cahier de texte ».
- Suivre les professeurs : accueil, section « Suivi des profs », « Tout voir › », filtrer (« Retards », « Non pointés »), ouvrir un prof ou une classe à vérifier.

Vérification des exemples demandés :

| Tâche | Verdict |
|---|---|
| Gérer factures et paiements | Non : lecture et consultation seulement (restants, reçus, annulations) ; aucune création ni saisie |
| Approuver des demandes | Non trouvé (les annulations sont consultatives ; aucun flux de validation) |
| Gérer classes ou élèves | Consultation seule (« Roster transmis par la scolarité — lecture seule. ») |
| Envoyer une annonce | Non trouvé |
| Écrire aux parents | Non trouvé |
| Bus | Consultation d'une notification « Absences déclarées au transport » ; aucun écran de gestion du bus |
| Réinscription | Suivi par notification « à relancer auprès des familles » ; aucun écran de gestion : non trouvé |
| Faire l'appel / saisir des notes / cahier | Non : ce sont des tâches professeur ; le manager les consulte |

#### e. Permissions et limites

- Périmètre : toute l'école (439 apprenants, 18 classes, 20 professeurs, 6 niveaux, 3 cycles « Élémentaire », « Moyen », « Secondaire »).
- Tout est en lecture seule : la maquette le répète sur chaque écran de suivi (« lecture seule », « Consultation seule »). Aucune création, modification ou annulation n'est possible depuis l'espace.

#### f. Notifications

Notifications de démonstration, types internes entre parenthèses :

- « Absences déclarées au transport » — « 2 enfants ce matin · Ndeye Fall (CM2 A), Fatou Sarr (CP A) » (bus ; portée par la fonctionnalité bus)
- « 11 absents aujourd'hui » — « Awa Sow (CM1 B) · non justifiée » (absence)
- « Restants à recouvrer » — « 16 factures impayées · 326 000 F » (finance)
- « Professeurs non pointés » — « Mme Sow (CE2 B) · 3 jours sans scan » (pointage)
- « Sanction enregistrée » — « CM1 B · Modou Gueye — bavardages » (sanction)
- « Réinscriptions 2026-2027 » — « à relancer auprès des familles » (inscription)

#### g. Paramètres et profil

Identiques au professeur (mêmes 4 rangées, même sheet PIN, même lien CGU et même version). Différence : « Mes informations » affiche le rôle « Directeur ».

### 2.3 Surveillant de sortie (maquette, design/forks/actuel/surveillant-sortie/screens/)

Un seul écran : accueil.html, titre d'onglet « Athena — Poste de sortie ». C'est « le poste de la porte » (spec athena-recuperation-deleguee) : vérifier l'adulte qui récupère un enfant et libérer l'enfant.

- Action « Scanner une remise » : « Présentez le QR de l'adulte », bouton « Scanner le QR », règle « Sans QR, le poste appelle le parent : personne ne part sans confirmation. »
- Action « Vérifier une remise » (sans QR) : « Le parent confirme par téléphone », « Pas de QR : appeler, puis journaliser « sur appel ». », bouton « Appeler », règle « Sans réseau, on appelle le parent : personne ne part sans confirmation. »
- Journal du jour : « Aujourd'hui · Mercredi 28 janvier », entrées horodatées avec verdict, par exemple « 08:20 · M. Faye », « Fatou Sarr », « Remis » et « 16:20 · Mme Sarr », « Amadou Sarr », « Refusé ».
- Fiche de remise : « Les 2 enfants » avec classe et point de remise (par exemple « Amadou Sarr », « CM1 B · Rue 12 », état « Autorisé ») ; « Qui se présente » (« Mme Ndiaye », « Délégué par le parent », bouton « Appeler ») ; règle « Le QR peut être montré par n'importe qui : à la porte, c'est le nom qui se vérifie. »
- Décisions : « Remettre les 2 enfants », « Refuser la remise », « Appeler le parent ». Refus : « Motif du refus », « Pourquoi ce refus ? », « Confirmer le refus », « Revenir à la vérification », avec les règles « Refuser ne renvoie personne : l'enfant reste à l'école. » et « Le motif part au parent et reste au poste : le collègue qui prend la relève le lira avant d'ouvrir la porte. »
- Drawer propre à l'espace : groupes « Le poste » (lien « Aujourd'hui ») et « Système » (lien « Déconnexion »), sans centre de notifications (la notification de sortie part au parent).
- Incohérence de maquette à corriger avant capture : le bloc identité du drawer reprend le compte parent (« Papa Seydou BA », « Parent · changer de profil ») au lieu d'un compte surveillant.

Tâches possibles : vérifier et libérer une remise (avec ou sans QR), refuser une remise avec motif, consulter le journal du jour. « Approuver des demandes » au sens générique : non trouvé ; l'équivalent local est confirmer ou refuser une remise à la porte.

### 2.4 Accompagnateur — « Espace Bus scolaire » (maquettes, design/forks/actuel/accompagnateur/screens/)

Trois écrans. L'accompagnateur déclare les présences (« il pointe, il signale »), le parent lit.

- accueil.html, titre d'onglet « Athena — Bus scolaire » : bandeau « Bus A · Mme Diop », statut « En route », « il y a 1 min » ; carte carte « Plein écran » / « Quitter » avec repère « Départ 07:02 · vers 07:50 à l'école » ; tuiles « Ce matin » (« À monter » 31, « À bord » 8 / 39) et « Cet après-midi » (« À descendre » 38, « Absents déclarés » 1) ; section « Mes deux tournées » : « Aller » (« Départ 07:02 · 8 à bord ») et « Retour » (« Départ de l'école 16:30 · 38 à descendre »), boutons « Démarrer » et « Arrêter », états « À venir » / « Terminée » ; dialogs de confirmation « Démarrer la tournée du matin ? » (« Le suivi GPS démarre avec elle, et le parent voit le bus avancer. Rien n'est pointé avant votre premier geste. », boutons « Démarrer la tournée » et « Ouvrir la tournée sans la démarrer ») et « Arrêter la tournée du matin ? » (« La session se ferme : le suivi GPS s'arrête, et le parent ne voit plus le bus avancer. Les pointages déjà faits, eux, restent. »).
- tournee.html, titre d'onglet « Athena — Aller » : état de session (« Session fermée » / « Session ouverte », « Ouverte à 07:02 · aucune montée »), boutons « Démarrer la tournée » / « Arrêter la tournée » ; « Scanner une montée » ; compteur « 8 / 40 à bord » ; liste des enfants avec états « Monté à 07:12 » (ou « Monté »), « Pas encore monté » / « À pointer », « Absent déclaré » ; règles « 1 tap = monté. L'heure vient du geste, jamais d'une position GPS. » et « Chaque présence est déclarée d'un tap : jamais déduite d'une position. » ; fiche enfant : « Point de montée » (quartier), « Personnes autorisées » avec lien et bouton « Appeler » (ou « Aucun responsable renseigné », « À compléter par l'école », « À compléter ») ; « Signaler un retard ou un incident » : motifs « Circulation », « Panne », « Route barrée », « Autre », mention « Ce que vous écrivez, le parent le lit. », bouton « Envoyer le signalement » ; scan : « Présentez le QR de l'enfant à la caméra », « Un QR par enfant. Le scan est la preuve du geste, jamais la position. », confirmation « Montée enregistrée ».
- tournee-soir.html, titre d'onglet « Athena — Retour » : même mécanique pour les descentes (« 38 à descendre »).
- Notifications : l'accompagnateur voit les « Absents déclarés » (déclarations des parents) sur ses écrans ; ses signalements partent au parent. Pas de centre de notifications dédié : non trouvé.
- Incohérence de maquette à corriger avant capture : le drawer est celui du deck parents (identité « Papa Seydou BA », « Parent · changer de profil », liens « Enfants », « Scolarité », « Finance », « Transport », « Réglages »).
- Périmètre : son bus et ses deux tournées (bus A, aller et retour).

## 3. Tableau de disponibilité

Build = application Flutter lue (3.0.2+270). Maquettes = design/forks (actuel, et boutique pour la librairie). Statut : complet, partiel, maquette seule, ou caché par un drapeau.

| Fonctionnalité | Build 3.0.2+270 | Maquettes | Statut | Notes |
|---|---|---|---|---|
| Connexion téléphone + code établissement | Oui (/v2/verify_school_code) | Hors périmètre des decks | Complet | Écran unique pour tous les rôles |
| OTP SMS puis création de PIN | Oui (/v2/sms/send, /v2/verify_otp) | Non visible | Complet | Token Firebase personnalisé |
| Connexion par PIN | Oui (/v2/pin/verify) | Non visible | Complet | |
| Accueil, enfants, notes, absences, sanctions, emploi du temps enfant, factures, paiement mobile, notifications, activités, paramètres (Espace Parents) | Oui | Oui | Complet | Déjà couvert par le kit (docs/CAPTURES.md) |
| Bulletin (consultation par l'enfant) | Oui, dans le parcours Notes (student_note_screen.dart, widgets/bulletin.dart, /v2/scores/bulletin) | Oui (bulletins.html) | Complet | La maquette en fait un écran dédié, la build l'intègre à Notes |
| Cahier de texte côté parent | Non (aucun écran ni endpoint) | Oui (cahier-texte.html) | Maquette seule | |
| Suivi du bus côté parent | Non | Oui (bus.html, bus-etats.html) | Maquette seule | Le manifest marque la fonctionnalité « livré » côté maquettes ; absente de la build |
| Réinscription côté parent | Non | Oui (reinscription.html, reinscription-confirm.html) | Maquette seule | |
| Librairie (boutique) | Non | Oui (fork boutique, 7 écrans) | Caché par un drapeau | Drapeau FEATURES.boutique = « non livré » |
| Sélecteur de profil multi-rôles | Non | Oui (bloc identité drawer + sheet « Changer de profil ») | Maquette seule | Spec profiles-switcher |
| Espace Professeur complet (10 écrans) | Non | Oui | Maquette seule | |
| Pointage professeur (QR porte + salle) | Non | Oui | Maquette seule | Peut être « Non activé » par établissement |
| Appel (présences) par le professeur | Non | Oui | Maquette seule | Transmis automatiquement à la vie scolaire |
| Cahier de texte + dictée vocale (professeur) | Non | Oui | Maquette seule | |
| Saisie des notes / devoirs (professeur) | Non | Oui | Maquette seule | La build ne fait que lire les notes côté parent |
| Emploi du temps professeur | Non | Oui | Maquette seule | La build a l'emploi du temps enfant (schedule_screen.dart) |
| Espace Manager complet (16 écrans) | Non | Oui | Maquette seule | |
| Finance école (facturé vs encaissé, modes, dépenses) | Non | Oui | Maquette seule | Lecture seule |
| Restants (impayés par apprenant) | Non | Oui | Maquette seule | « la liste complète sera alimentée par le back-office » |
| Annulations | Non | Oui | Maquette seule | Écran absent des groupes du manifest, lié depuis le tableau de bord |
| Effectifs par cycle / niveau / classe | Non | Oui | Maquette seule | |
| Vie scolaire école + dossier de classe | Non | Oui | Maquette seule | |
| Suivi des profs (pointages, retards) | Non | Oui | Maquette seule | Référence 08h00 + 10 min |
| Poste de sortie (surveillant) | Non | Oui (1 écran) | Maquette seule | |
| Espace Bus scolaire (accompagnateur) | Non | Oui (3 écrans) | Maquette seule | |
| Notifications push (FCM) | Oui (fcm.dart : jeton, /v2/token/fcm_update, centre + /v2/notifications) | Oui (centres par espace) | Partiel | Aucun topic par rôle : non trouvé |
| Impersonation administrateur | Vestige (backToImpersonate, scope « ROLE_ADMIN ») | Non | Caché (code mort côté UI) | Globals.scope jamais lu |

## 4. Données de démonstration

### 4.1 Où vit la donnée

- Maquettes : source unique design/system/data.js, lu par les écrans générés (design/scripts/gen_athena_screens.js, gen_profs_screens.js, gen_admins_screens.js, gen_accompagnateur_screens.js, gen_surveillant_screens.js). Blocs window.ATHENA (parents et bus), window.PROFS (professeur), window.ADMIN (manager), registres REGISTRE_SEPT_DEC et REGISTRE_JANVIER (vie scolaire), window.DEMO_PHOTOS (avatars fictifs générés, 85 % des enfants).
- Build : aucun jeu de données local. Aucun fichier mock, fixture ou seed trouvé dans lib/ (recherche « mock, fixture, seed » sur les 149 fichiers Dart) : la build ne fonctionne que contre le backend. Pour capturer la build, il faut un compte de démonstration créé côté serveur, hors périmètre de ce dépôt.

### 4.2 Casting fictif (à réutiliser pour rester cohérent avec les maquettes)

- École : « Athena School » (application « ATHENA SCHOOL BY SEPRO »), 439 apprenants, 18 classes, 20 professeurs, 6 niveaux (CP à 6e), 3 cycles (« Élémentaire », « Moyen », « Secondaire »).
- Parent : « Papa Seydou BA » (profils Parent + Manager). Enfants : Amadou Sarr (CM1 B, matricule E220092), Khadi Sarr (CM2 A, matricule E220106), Fatou Sarr (CP A).
- Professeur : Mamadou Diallo, affiché « M. Diallo » (profils Professeur + Parent). Classes : CM1 B (Mathématiques, Salle 4, 30 élèves), 6e A et 6e B (Français), CM1 A (Mathématiques), CM2 A (Mathématiques). CM1 B est la classe vitrine de toutes les démos.
- Manager : Omar Ndiaye, affiché « M. Ndiaye », rôle « Directeur » (profils Manager + Professeur).
- Bus : « Bus A · Mme Diop », tournées « Aller » (départ 07:02) et « Retour » (départ 16:30).
- Élèves récurrents de CM1 B : Awa Sow, Modou Gueye, Cheikh Fall, Fatou Bah, Bineta Touré, Mame Diarra Dème, Assane Diarra.

### 4.3 Montants et repères chiffrés déjà en place

- Factures parents : mensualité 70 000 F (Amadou) et 75 000 F (Khadi), cantine 18 000 F, inscription 150 000 F ; numéros au format FA2526-000xxx ; statuts « Payée », « En cours », « À payer », « En retard ».
- Finance école : encaissé de janvier 9 697 000 F, facturé mensuel 11 400 000 F, restants 8 350 000 F (15 classes), dépenses de janvier 6 740 000 F dont salaires 5 420 000 F ; modes « Wave », « Orange Money », « Espèces ».
- Vie scolaire : janvier = 11 absents sur 439 ; trimestre = 214 absences, 87 retards, 18 sanctions.
- Motifs de sanction : « Bavardage », « Retard », « Devoir non fait », « Tenue », « Insolence », « Autre ».

### 4.4 Créer des comptes fictifs pour les captures

- Maquettes : rien à créer. Éditer design/system/data.js (bloc du rôle concerné), puis régénérer les écrans avec le script gen_* correspondant et servir le dossier design (serveur local du design system, commandes dans design/package.json). Les écrans peuvent aussi s'ouvrir en direct, mais les interactions (sheets, accordéons) exigent le serveur.
- Comptes de démonstration prêts dans data.js : les trois comptes multi-profils du 1.1. Pour un espace mono-rôle (surveillant, accompagnateur), il faudra ajouter un compte dédié : non trouvé dans data.js, les deux écrans réutilisent aujourd'hui le compte parent.
- Build : prévoir un compte de test chez l'hébergeur (téléphone + code établissement + PIN), avec des données réelles neutralisées. Les écrans « Mes informations » et les fiches bus affichent des numéros de téléphone : les valeurs des maquettes sont fictives (format +221), et toute capture de la build doit masquer ces champs.

## 5. Ce qui est partagé avec le flux parents

Réutilisable tel quel pour les vidéos des autres rôles :

- Design system unique : design/system/tokens.css, ui.css, components.js (listRow, chips ok/due/late/muted/class, sheets, drawer, appHeader, statusBar). Tous les espaces partagent la même charte (olive, marine, Poppins).
- Drawer et changement de profil : mêmes composants partout (bloc identité, sheet « Changer de profil ») ; seuls les groupes de liens changent par espace.
- Centres de notifications : même page dans les trois espaces (« Tout » / « Non lues », « Tout marquer comme lu », « Tout voir › » dans le drawer).
- Paramètres : même structure dans les trois espaces (mêmes 4 rangées, même sheet « Modification de code PIN », même lien CGU, même pied de page « Version: 3.0.3, Build:281 ») ; sous-écrans « Informations de l'établissement » et « Mes informations » identiques au contenu près ; CGU partagée (window.ATHENA.cgu).
- Wording commun : « ATHENA », « Espace ... », « Athena School », « by SEPRO ».
- Côté build : la connexion (auth, OTP, PIN) est commune à tous les rôles et déjà documentée dans le kit ; les widgets parents (appbar, header_section, student_card, school_card, quick_actions_section) sont la base de composants à réutiliser pour un futur portage.
- Écart à connaître : dans la build, l'écran « Paramètres » parents liste 5 rangées dont « Conditions générales d'utilisation » ; dans les maquettes des trois espaces, la CGU est un lien sous la version et la liste en compte 4.

## 6. Risques, inconnues et questions au fondateur

- Aucun endpoint connu pour les nouveaux rôles : lib/data/repository.dart n'expose que des API parents (/v2/students, /v2/scores, /v2/invoices, /v2/payment, /v2/absences, /v2/sanctions, /v2/schedules, /v2/informations, /v2/notifications, /v2/me, /v2/academic_years, /v2/schools/current, /v2/documents, /v2/verify_school_code, /v2/verify_otp, /v2/pin/*, /v2/token/fcm_update, /v2/sms/send, /v2/resources/logo). Le portage des espaces professeur et manager dépend d'API à définir : première question au fondateur.
- Vocabulaire des rôles côté backend inconnu : la valeur du champ role de /v2/verify_school_code n'est énumérée nulle part dans le client. L'app « Manager » des maquettes correspond-elle à un rôle « ROLE_ADMIN » du backend (cf. le vestige d'impersonation) ? À confirmer.
- Pointage QR (professeur) : dépend d'un scanner et d'une activation par établissement ; l'état par défaut des maquettes est « Non activé ». Le manager raisonne sur des pointages (référence 08h00 + 10 min) qui n'existent pas encore dans la build.
- Dictée vocale du cahier : la maquette montre « Enregistrement… » / « J'ai terminé » ; la technique (sur l'appareil ou côté serveur) n'est pas précisée.
- Bus : « Suivi arrêté · la position ne se rafraîchit qu'une fois la session ouverte » ; la session GPS dépend du réseau et de la batterie de l'accompagnateur. Les tuiles « À monter / À bord / À descendre » supposent des listes par tournée entretenues par l'école.
- Incohérences de maquettes à corriger avant toute capture : drawer parents (identité « Papa Seydou BA ») sur les écrans accompagnateur et surveillant ; pas de compte dédié pour ces deux rôles.
- annulations.html absente du manifest : statut à trancher (écran à part entière ou forage du tableau de bord).
- Les listes manager (restants, annulations, suivi des profs) sont des échantillons de démonstration : « la liste complète sera alimentée par le back-office ». Volumes réels inconnus.
- Version : maquettes « 3.0.3, Build:281 » contre build lue « 3.0.2+270 » ; certaines captures du kit peuvent montrer des numéros de version différents.
- Écrans fragiles pour de futures captures : les sheets Alpine (filtres, reçu, PIN) exigent le serveur du design system, pas l'ouverture directe des fichiers ; la page profs.html et tournee.html sont longues (grilles de 20 professeurs, listes d'enfants) et dépassent le cadre 412×917 au défilement.
- Questions au fondateur : quel back-office pour les rôles professeur et manager (même API que l'app parents ?) ; le manager doit-il rester en lecture seule (c'est le choix actuel des maquettes) ; un rôle comptable existe-t-il ailleurs que dans l'app ; l'impersonation « ROLE_ADMIN » est-elle encore prévue ; quels comptes de démonstration créer pour capturer surveillant et accompagnateur ; le pointage QR doit-il apparaître activé ou non dans les vidéos.
