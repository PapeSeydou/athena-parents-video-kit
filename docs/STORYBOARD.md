# Storyboard visuel (dispositifs validés en intention, look à créer)

Deux dispositifs demandés par le client :

1. **Vignettes SVG « l'ancien monde jeté »** : quand la voix dit « FINI les carnets perdus, les
   appels et les allers-retours », montrer des illustrations SVG (cahier, téléphone « 1 appel
   manqué », ticket de file d'attente) éparpillés qui tournoient et s'envolent, puis l'interface
   propre se dresse. Idem esprit pour « sans file d'attente ni déplacement » (factures).
2. **Éventail de scènes avec spot** : pour les passages rapides (scolarité : notes, bulletins,
   vie scolaire, cahier), montrer les 4 écrans EN MÊME TEMPS en éventail ; celui que la voix nomme
   passe à 100 % d'opacité et grandit légèrement, les autres descendent à ~30-35 % et rétrécissent ;
   « tout est là, LIMPIDE » => l'éventail se range en rangée nette.

## Plan scène par scène

| # | Scène (début film) | Traitement |
|---|---|---|
| 1 | Ouverture (0 s) | Dark navy, anneaux qui pulsent, logo blanc, « L'école de vos enfants, dans votre POCHE. » qui frappe |
| 2 | Connexion (4,39 s) | Capture réelle auth-01 en carte portrait, point de tap sur Envoyer, checklist qui se coche (numéro, code établissement, compte reconnu) |
| 3 | Code + PIN (13,49 s) | Push vers auth-04 (les 6 cases se remplissent case par case), puis auth-05 / auth-02 (PIN 4 chiffres, puis saisie) ; la checklist continue (SMS reçu, PIN créé) |
| 4 | Accueil (25,07 s) | screen-accueil en carte, pastille de tap sur les flèches de changement d'enfant, mini-confettis |
| 5 | Scolarité (34,77 s) | Les 3 temps : vignette SVG -> éventail des 4 écrans avec spot -> rangée nette. 26,5 s, la scène signature |
| 6 | Factures (61,75 s) | screen-factures -> feuille de paiement (Max It / Wave) -> tampon « Payée » reconstruit en animation (PAS de capture réelle de confirmation, choix du client) sur le <sigh> |
| 7 | Notifications (73,85 s) | screen-notifications, badge qui pop |
| 8 | Bus + réinscription (80,85 s) | screen-bus (point qui avance sur la ligne, <gasp>), bandeau réinscription |
| 9 | Fin (93,59 s) | Dark navy, confettis, logo, « L'école, plus près de vous. » + by SEPRO. RIEN d'autre (choix du client : pas d'URL ni badge store) |

## Règles de look (héritées du pipeline, à respecter)

- Écrans ENTIERS, dérive lente (1-2 %) au lieu de zooms ; spotlight = contour + atténuation des autres.
- Alternance clair/sombre ; ouverture et clôture navy.
- Stickers emoji d'état (👀 ✍️ ☑️ 🚀 ✅ 🎉) qui flottent et poppent avec overshoot.
- Checklist qui se coche elle-même : une rangée par donnée, fill vert + check dessiné + counter n/N.
- Barre de progression 8 px en bas. Texte dans les 920 px centraux. Titres 84-112 px Poppins 800.
- Une seule chose bouge à la fois, sur la voix. Ease out en entrée, ease in en sortie, overshoot sur
  les stickers et le premier mot.
