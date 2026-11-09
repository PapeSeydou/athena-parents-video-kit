# Workflow de rendu (Windows, machine du fondateur)

## Environnement vérifié

- Python 3.11 + pillow + numpy + playwright : `C:Userslog.dshlocal-workspaceproduct-video.venvScriptspython.exe`
- Chromium Playwright sous %LOCALAPPDATA%ms-playwright ; ffmpeg + ffprobe sur le PATH ; node 22.
- `bash.exe` INUTILISABLE (WSL sans /bin/bash). Utiliser les wrappers pwsh.

## Pipeline (compétence « product-tutorial-video », template = assets/template/)

```powershell
$sk = 'C:Userslog.dshskillsproduct-tutorial-video'
$py = 'C:Userslog.dshlocal-workspaceproduct-video.venvScriptspython.exe'
$w  = '<workdir>'   # HORS OneDrive (ex: C:Userslog.dshlocal-workspaceproduct-videoworkathena-parents)

# 1. copier assets/template/ vers $wmods (scene-*.js, scenes.json, base.css, shared.js)
#    puis : fonts + player.html
pwsh -File "$skscriptswinsetup_render.ps1" -Workdir $w -Mods "$wmods" -Assets "$wassets" -Python $py

# 2. stills pour valider le look
& $py "$skscriptswinender.py" stills "$wplayer.html" "$wstills" 1.6 6.5 16.5 43.5

# 3. frames PAR CHUNKS de 700 (les process meurent entre commandes)
& $py "$skscriptswinender.py" frames "$wplayer.html" "$wrames" 60 0 700
& $py "$skscriptswinender.py" frames "$wplayer.html" "$wrames" 60 700 1400

# 4. audio (timeline.json : voice[{file,start}], bed{bpm,first_bar,bars,finale}, events[])
& $py "$skscriptsmix_audio.py" "$w	imeline.json"

# 5. encode
pwsh -File "$skscriptswinencode.ps1" -Frames "$wrames" -Audio "$waudio_final.wav" -Out "$winal.mp4"
```

## Pièges (tous rencontrés)

1. **encode.ps1 suppose 60 fps** : si les frames sont à 30 fps, le film est accéléré x2.
   Pour le film final, rendre à 60 fps. (Ou ffmpeg direct avec `-framerate 30` et
   `-i f%05d.jpg` — pattern à 5 chiffres.)
2. **mix_audio.py écrit `out` relatif au CWD** : mettre `out` en chemin absolu, ou lancer
   depuis le workdir.
3. `shared.js` a `TOTAL` codé en dur (barre de progression) : le mettre à jour avec la durée.
4. Rendre par chunks de 700 frames (~60-75 s par chunk à 1080p JPEG q95, 9-14 f/s).
5. La carte écran du template (`.scr`, 880x681) est prévue pour des captures desktop 16:9.
   Pour des captures téléphone portrait, écrire une carte dédiée (ex : .pcard, rayon 36,
   bordure 1 px, ombre douce) et NE PAS réutiliser `UI.rect()` du template (mauvais mapping).
6. Équilibrage loudness des découpes : RMS par scène, gain clampé ±2 dB, la prise maîtresse
   reste intacte.
7. Music bed : généré par mix_audio.py (bed.bpm/first_bar/bars/finale + events[]).

## Maquette existante (référence de mécanique, look refusé)

Workdir : `C:Userslog.dshlocal-workspaceproduct-videoworkathena-parents`
(mods/ contient des scènes fonctionnelles : ouverture, connexion, scolarité avec vignette SVG
et éventail, fin). 45,7 s à 30 fps — refaire à 60 fps pour le film.
