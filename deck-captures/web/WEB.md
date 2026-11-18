# ATHENA MANAGER - web captures

Partial run, work in progress. Tenant tdanges, account elhadji, light theme, French UI, single browser session.

Capture spec: iPad Pro 13" landscape, viewport 1376x860 CSS px at device scale factor 2, so every PNG is exactly 2752x1720. No iPad user agent and no touch emulation, so the desktop layout is kept. The app does not switch to a hamburger layout at this width, so no 1440x900 recapture was needed.

None of these pages scroll at 1376x860, so no _full.png variants are shipped. Where a page does scroll later, the full-page twin will be added.

## Files

| File | Shows | Menu path |
| --- | --- | --- |
| admin_dashboard.png | Group dashboard, Synthese tab. Effectifs 4, taux de recouvrement 96,9 %, reste a recouvrer 12 500 XOF, moyenne generale 13,79/20, taux de reussite 100 %, plus the Encaisse et decaisse par mois bar chart and the A surveiller panel | Home cockpit (Accueil), then Dashboard |
| admin_dashboard_effectifs.png | Effectifs tab, same dashboard. Filles/Garcons split, reinscriptions, departs, effectif par cycle table with 8 levels | Dashboard, then Effectifs tab |
| admin_invoicing.png | Invoice list. 4 invoices, three paid plus one partially paid (122 500 total, 110 000 paid, 12 500 remaining, status Commencee), amounts and references visible | Facturation, then Toutes les factures |
| admin_invoicing_overview.png | Invoicing dashboard tab. Facture 400 000 XOF, encaisse 387 500 XOF, reliquat 12 500 XOF, recouvrement 96,9 %, depenses, plus the monthly Facture/Encaisse/Reliquat table for 10 months | Facturation, then Tableau de bord |
| admin_enrolment.png | Enrolment form for a new student, fields filled with demo values, not submitted. Discarded after capture | Eleves, then Tous, then Ajouter |

## Personal data

Names are replaced with dummy names in the page DOM before each screenshot, so the PNGs show fictional people: AWA DIOP, MOUSSA FALL, FATOU SARR and so on. Student codes of the form E230072 and invoice references such as FA2425-000001 are kept because they carry no personal meaning. The login page was never captured and the credentials appear in no file.

One caveat on admin_enrolment.png: the surname field shows the dummy name MARIAMA NDAO while the first name field shows Awa, because the redaction pass runs after the form was filled.

## Menu list from the exploration step

Top-level app menu (22 entries), with what each page showed and whether it had data.

| Menu | Sub-pages | Data |
| --- | --- | --- |
| Dashboard | Synthese, Effectifs, Finances, Vie scolaire, Pedagogie | Yes, KPIs and charts |
| Eleves | Tous 188, Diplomes 0, Exclusion 0, Transfere 5, Abandonne 1, Non reinscrits 21, Absences | Yes, 188 students |
| Inscriptions | Elementaire 2, Moyen 2, Prescolaire 0, Cours Coraniques Enfants 0 | Partial, cycle overview only, no enrolment certificate reached |
| Comptabilite & Facturation | Ventes, Achats, Referentiel, Comptabilite generale | No, thin |
| Classes | Elementaire 2, Moyen 2, Prescolaire 0, Cours Coraniques Enfants 0 | Partial, overview cards, timetable not reached |
| Produits | Categorie 0, Produits 0, Services 0 | No |
| Parents / Partenaires | Parents 98, Partenaires 0 | Yes, 34 parent rows |
| Professeurs | Professeurs, Emargement | Yes, 10 teacher rows, emargement empty |
| Depot | Depots, Quantites, Lots de stock, Numeros de serie, Reservations, Mouvements, Inventaires | No |
| Services | Abonnement sur un bus 2, Supervision des trajets, Indisponibilites | Yes, 2 buses |
| Projet | Taches, Observations, Projets en derive, Tous les projets | No |
| Activites | Activites | No |
| Evaluations | Evaluations, Elementaire 2, Moyen 2, Prescolaire 0, Cours Coraniques Enfants 0 | Yes on Trimestre 1, empty on trimesters 2 and 3 |
| Depenses | Depenses, Depenses a valider, Depense par categorie, Categories | Yes, 1 expense |
| Facturation | Ventes, Achats, Referentiel, Comptabilite generale | Yes |
| Banque & Caisse | Banques 0, Comptes 1, Comptes par type, par banque, par devise, Ecritures | Yes, 1 account, 1 010 000 XOF |
| Budget | Nomenclature 0, Categories 3, Preparation 0, Annuel 0, Treso 0, Projet 0, Rapport mensuel | Yes, 20 rows |
| Statistiques | Inscriptions, Moyennes, Notes | Partial, 4 registration rows |
| Alertes | Apprenants a risque, Risque de decrochage, Absences, Sanctions | No |
| Achat | Demandes, Commandes, Reactions, Fournisseurs 0, Prix d'achat 0 | No |
| Administration | Produit, Entites 1, Utilisateurs 5, Groupes 0, Roles 1, Contacts 310, Etiquettes 0, Types d'activites 12, Unites de mesure 6, Devises 1, Mails envoyes, Messages, Configurations, Templates | Yes |
| Administration systeme | Modules, Textes, Sessions, Journal d'activite, SAAS Clients, Securite API, Statistiques, Paiements mobiles | Partial |

The sidebar holds three entries only: Accueil, Agenda, Mes validations. The module menu opens from the app-switcher button in the header.

## Must-haves

- Done: admin_dashboard.png, admin_enrolment.png, admin_invoicing.png, admin_classes_list.png is MISSING (list not reached, only the cycle overview was available).
- Outstanding: admin_enrolment_certificate.png, admin_classes.png (timetable), admin_grades.png, admin_report-card.png.

## Missing from this partial run

Class timetable and class list, generated report card (bulletin), enrolment/schooling certificate, unpaid invoices and reminders view, revenue tracking page, one student's full file, the professor portal (not attempted yet). The just-in-case list (unpaid, revenue, cash-bank, student file, students, teachers, attendance, services, multisite, statistics, options, extras) is not captured yet.

## Session notes

One login, one browser, one context, one tab for the whole run. No session kick-out happened, so no re-login was needed. No form was submitted and no record was created, edited or deleted.
