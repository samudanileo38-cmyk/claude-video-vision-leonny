---
description: "Analizza un reel o video competitor per Leonardo Benedetti — hook type, TOFU/MOFU/BOFU, lead gen score, adattamento brand Leo"
argument-hint: "path/to/video.mp4 [domanda opzionale]"
---

# Analyze Reel — Leo Mode

Analisi completa di un reel/short-form video applicando il framework Leo (Hormozi/Brunson/Schwartz + brand S&C tennis/padel).

## Workflow

1. `video_info` → verifica file valido, ottieni durata e presenza audio.

2. Se durata > 30s: `video_analyze` con filtri:
   ```
   scene_changes: true
   silence: true
   transcription: true
   motion: true
   ```

3. `video_watch`:
   - Reel < 60s → `fps: "auto"`, niente `view_sample` (full coverage)
   - Short-form 60s–3min → `segments` basati su scene_changes, `view_sample: 10`
   - Max resolution 512 standard, 768 se ci sono testi piccoli in overlay

4. Analizza i primi 3 secondi con attenzione particolare → classifica hook type.

5. Leggi trascrizione completa → identifica struttura, CTA, funnel stage.

6. Applica **Leo Mode** dal skill `video-perception` e restituisci output nel formato standard.

7. Se l'utente ha fornito una domanda specifica, rispondi anche a quella dopo il formato standard.

## Note

- Se `video_watch` fallisce con setup error → `video_setup` prima, poi riprova.
- Per video senza audio (muted reel) → imposta `skip_audio: true` e nota nell'output.
- Per video in inglese → analizza comunque, poi nella sezione "Per Leo" adatta in italiano.
