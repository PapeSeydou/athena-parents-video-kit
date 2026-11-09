# Captures d'écran — inventaire et méthode

## assets/screens/ — maquettes HTML capturées (22 fichiers)

Source de vérité : `design/forks/actuel/athena/screens/*.html` du dépôt athena_mobile
(fork « actuel » = la version LIVRÉE ; le fork « boutique » = à venir, NE PAS UTILISER).
Capture @2x, 824x1834, Edge headless :

```powershell
& "C:Program Files (x86)MicrosoftEdgeApplicationmsedge.exe" --headless=new --disable-gpu `
  --hide-scrollbars --force-device-scale-factor=2 --window-size=412,917 --virtual-time-budget=12000 `
  --default-background-color=FFFFFFFF --no-first-run --no-default-browser-check `
  --user-data-dir=<profil jetable> --screenshot=<out.png> "file:///<chemin>/accueil.html"
```

La barre d'état des maquettes est une fausse barre peinte (9:30) : cohérente entre écrans, à garder.
Liste : accueil, activites, bulletins, bus, bus-etats, cahier-texte, drawer, etats, factures,
factures-vide, mes-enfants, notes, notes-enfant-unique, notifications, parametres,
parametres-cgu, parametres-etablissement, parametres-mes-infos, parametres-personnes-autorisees,
reinscription, reinscription-confirm, vie-scolaire.

## assets/auth/ — captures RÉELLES (6 fichiers, téléphone réel 1264x2780)

- `01_connexion.jpg` : numéro + code établissement + CGU + Envoyer (champs vides)
- `02_code_pin_a.jpg` / `03_code_pin_b.jpg` : saisie du PIN (avec/sans clavier)
- `04_otp_a.jpg` / `04_otp_b.jpg` : écran OTP — **le numéro réel est PIXELISÉ** (bande x>=682,
  y 964-1060, vérifiée par OCR). Ne pas utiliser les originaux du téléphone du fondateur.
- `05_pin_definition.jpg` : « Définir un code PIN (4 chiffres) »
- Manque (optionnel) : l'écran de CONFIRMATION du PIN — écran identique au 05, texte différent,
  à produire en retouchant le texte.

## Avertissement données

Les maquettes contiennent des données de démo fictives (3 enfants, avatars dicebear). Les garder
telles quelles ; ne rien remplacer par des données réelles.
