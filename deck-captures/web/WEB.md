# ATHENA MANAGER - deck captures

Demo captures for the sales deck. Tenant tdanges, one account throughout, light theme, French UI, sidebar with the ATHENA logo visible. Every PNG is exactly 2752 x 1720 px: viewport 1376 x 860 CSS px at device scale factor 2, iPad Pro 13" landscape cropped to 16:10, no iPad user agent and no touch emulation, so the app keeps its desktop layout. The app does not switch to a hamburger layout at this width, so no 1440x900 recaptures were needed. No page scrolled at this height, so no _full.png variants are shipped.

## This is demo data

The tenant is a development environment with almost no data (4 students, 400 000 XOF total billing). Every number on these screens was rewritten in the browser to match the fact sheet below. Nothing was submitted, saved, created or deleted on the server: only the rendered DOM, the chart canvases and the SVG bars were edited, client side.

## Fact sheet used on every screen

- Group name: Groupe Scolaire Teranga (replaces "Tdanges"). Academic year 2024-2025. Currency XOF.
- 5 campuses: Almadies, Parcelles Assainies, Thies, Mbour, Saint-Louis.
- Cycles: Prescolaire, Elementaire (CI to CM2), Moyen (6e to 3e), Secondaire (2nde, 1ere, Terminale, series S1, S2, L1, L2).
- Students enrolled 3 240 (Prescolaire 380, Elementaire 1 360, Moyen 920, Secondaire 580). Girls 51 %. New 412, re-enrolments 2 828, departures 164, previous year 3 096.
- 96 classes, 168 teachers, 42 administrative staff, 2 480 parents.
- Finance: billed 1 245 600 000 XOF, collected 1 142 300 000 XOF (recovery 91,7 %, objective 90 %), remaining 103 300 000 XOF, committed expenses 618 400 000 XOF, treasury 523 900 000 XOF.
- Recovery by cycle: Prescolaire 94 %, Elementaire 92 %, Moyen 91 %, Secondaire 89 %.
- Monthly collected, Oct to Jul (millions XOF): 214, 128, 121, 116, 109, 112, 98, 94, 86, 64.
- Pedagogy Trimester 1: overall average 13,4/20, pass rate 91,3 %. Bell curve centred on 13,4.
- School life: absence rate 3,8 %, lateness 2,1 %, 57 sanctions this month.
- Account label in the header: "Direction". Static label "Notifications" instead of "Notification de maintenance".

## What was edited per screen

- Header, all screens: "elhadji" replaced by "Direction"; "Notification de maintenance" replaced by "Notifications"; every "Tdanges" replaced by "Groupe Scolaire Teranga".
- KPI and stat cards: values and footnotes replaced from the fact sheet (text nodes only).
- Canvas charts: redrawn with the 2D context at device pixel ratio. Monthly collected versus previous year (10 paired bars), recovery by cycle (4 bars), effectif by cycle (4 bars), grade bell curve (15 bars), monthly absences (9 bars).
- SVG bar charts: the rects inside .stat-card-chart are repositioned and resized, not regenerated.
- Tables: existing rows cloned or rebuilt to fill the viewport, then every cell written from the fact sheet.
- Invoice table: 24 rows, references FA2425-000001 upward, 45 000 to 185 000 XOF, 16 Payee (green), 4 Commencee (orange), 4 Non payee (red). Column widths were set explicitly so the Etat column is fully visible.

## Files

| File | What it shows | Menu path |
| --- | --- | --- |
| admin_dashboard.png | Synthèse tab: effectifs 3 240, recovery 91,7 %, remaining 103,3 M XOF, average 13,4/20, pass rate 91,3 %, students to watch 126, monthly collected chart, A surveiller panel | Home cockpit, then Dashboard |
| admin_dashboard_effectifs.png | Effectifs tab: new 412, re-enrolments 2 828, departures 164, girls 51 %, previous year 3 096, effectif par cycle chart, filled level table | Dashboard, Effectifs tab |
| admin_dashboard_finances.png | Finances tab: billed 1 245 600 000, collected 1 142 300 000, remaining 103 300 000, recovery 91,7 %, expenses 618 400 000, treasury 523 900 000, both charts | Dashboard, Finances tab |
| admin_dashboard_vie-scolaire.png | Vie scolaire tab: absences 412, lateness 2,1 %, 57 sanctions, monthly absences chart | Dashboard, Vie scolaire tab |
| admin_dashboard_pedagogie.png | Pédagogie tab: average 13,4/20, pass rate 91,3 %, best 17,8, median 13,1, lowest 6,2, grade distribution bell curve | Dashboard, Pédagogie tab |
| admin_enrolment.png | New-student form (Apprenant), fully filled with consistent demo values, not submitted and discarded | Élèves, Tous, Ajouter |
| admin_invoicing.png | Invoice list, 24 rows, mixed paid, started and unpaid statuses, amounts and remaining balances visible | Facturation, Toutes les factures |
| admin_invoicing_overview.png | Invoicing dashboard: billed, collected, remaining, recovery rate, monthly table | Facturation, Tableau de bord |
| admin_students.png | Student list with pagination "1-50 de 3 240", filters in the sidebar, 17 filled rows | Élèves, Tous |
| admin_student-file.png | One student's full file: identity block, finance strip, Parents / Inscriptions / Parcours / Factures / Dossier médical tabs | Élèves, Tous, open a row |
| admin_teachers.png | Teacher list, 168 in the pagination, codes, names, gender | Professeurs, Professeurs |
| admin_grades.png | Grades for a cycle: best 17,8, median 13,1, lowest 6,2, bell curve, top 5 and bottom 5 tables with 30 élèves | Évaluations, Élémentaire, Trimestre 1 |
| admin_unpaid.png | Students not yet invoiced, 16 filled rows with class and level | Facturation, Élèves non facturés |
| admin_revenue.png | Receipts list: 17 rows, dates, class, payer, payment type (Liquide, Virement, Chèque, Wave, Orange Money), amounts | Facturation, Recettes & Dépenses, Recettes |
| admin_cash-bank.png | Bank and cash entries, 18 rows, 1 010 000 style balances, account column | Banque & Caisse, Écritures |
| admin_budget.png | Monthly budget report, planned / executed / gap / execution rate per line | Budget, Rapport mensuel |
| admin_services.png | Bus subscriptions: plate, driver, fuel type, seats, zone across the 5 campuses | Services, Abonnement sur un bus |
| admin_statistics.png | Registrations statistics: effectif, boys, girls, re-enrolment rate, new and re-enrolled, latest registrations | Statistiques, Inscriptions |
| admin_attendance.png | Absences overview per cycle (412 total) with the most-absent students table | Alertes, Absences |
| admin_options.png | Activity types catalogue used for purchases, accounting and the DAARA / franco-arabe modules | Administration, Types d'activités |

WEB.md is one of the files; it is not a screenshot.

## Menu list from the exploration step

Top-level app menu, 22 entries. The sidebar itself holds three entries only (Accueil, Agenda, Mes validations); the module menu opens from the app-switcher button in the header.

| Menu | Sub-pages | Data in the dev tenant |
| --- | --- | --- |
| Dashboard | Synthèse, Effectifs, Finances, Vie scolaire, Pédagogie | Yes |
| Élèves | Tous, Diplômés, Exclusion, Transféré, Abandonné, Non réinscrits, Absences | Yes, 188 students |
| Inscriptions | Élémentaire, Moyen, Préscolaire, Cours Coraniques Enfants | Cycle overview only |
| Comptabilité & Facturation | Ventes, Achats, Référentiel, Comptabilité générale | Thin |
| Classes | Élémentaire, Moyen, Préscolaire, Cours Coraniques Enfants | Cycle overview only, no class list, no timetable |
| Produits | Catégorie, Produits, Services | Empty |
| Parents / Partenaires | Parents, Partenaires | Yes, 34 parents |
| Professeurs | Professeurs, Émargement | Yes, 10 teachers, émargement empty |
| Dépôt | Dépôts, Quantités, Lots, Numéros de série, Réservations, Mouvements, Inventaires | Empty |
| Services | Abonnement sur un bus, Supervision des trajets, Indisponibilités | Yes, 2 buses |
| Projet | Tâches, Observations, Projets en dérive, Tous les projets | Empty |
| Activités | Activités | Empty |
| Évaluations | Évaluations, Élémentaire, Moyen, Préscolaire, Cours Coraniques | Yes on Trimestre 1 only |
| Dépenses | Dépenses, Dépenses à valider, Dépense par catégorie, Catégories | One expense |
| Facturation | Ventes, Achats, Référentiel, Comptabilité générale | Yes |
| Banque & Caisse | Banques, Comptes, Comptes par type, par banque, par devise, Écritures | Yes, 1 account |
| Budget | Nomenclature, Catégories, Préparation, Annuel, Treso, Projet, Rapport mensuel | Yes |
| Statistiques | Inscriptions, Moyennes, Notes | Registrations only |
| Alertes | Apprenants à risque, Risque de décrochage, Absences, Sanctions | Absences cards only |
| Achat | Demandes, Commandes, Réceptions, Fournisseurs, Prix d'achat | Empty |
| Administration | Produit, Entités, Utilisateurs, Groupes, Rôles, Contacts, Étiquettes, Types d'activités, Unités, Devises, Mails, Messages, Configurations, Templates | Yes |
| Administration système | Modules, Textes, Sessions, Journal, SAAS Clients, Sécurité API, Statistiques, Paiements mobiles | Partial |

## Missing

Wanted by the brief but not captured, mostly because the tenant does not expose the screen at all:

- admin_classes.png (a class with its timetable, Monday to Saturday). The Classes module only renders per-cycle overview cards. No page I reached has an emploi du temps.
- admin_classes_list.png (the list of classes). Same reason: there is no class table, only cycle cards.
- admin_report-card.png (a generated bulletin). No bulletin or print-preview path was reachable from a student file.
- admin_enrolment_certificate.png (generated certificate or student ID). Same.
- admin_multisite.png (site switcher or consolidated group view). The tenant has a single entity, no switcher.
- prof_dashboard.png, prof_textbook.png, prof_grade-entry.png. The professor portal was not reached; the account is an admin account.
- admin_extra_01.png to admin_extra_10.png.

## Session notes

One browser, one context, one tab for the whole job, navigation sequential. Two session kick-outs happened (the app expires the session and shows a "Dépassement du temps de la session" dialog). Each time I stopped, waited 60 seconds, logged in once in the same tab and resumed. The login page was never captured, and no credential appears in any file, commit or screenshot.

The app itself throws an internal error dialog ("Problème inattendu, Code T6") when a second dashboard tab is clicked in the same page load, so each dashboard tab was captured after a fresh page load.

## Names

Screens show fictional Senegalese names only: Awa Diop, Moussa Fall, Fatou Sarr, Ibrahima Ba, Khadija Gueye, Cheikh Ndiaye, Mariama Sow, Abdou Kane, Aminata Diallo, Modou Faye, Seynabou Mbaye, Pape Thiam and similar. Real student names present in the tenant were replaced in the DOM before capture. Student codes follow the E24xxxx pattern and invoice references follow FA2425-0000xx; both are shown because they carry no personal meaning.
