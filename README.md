# Kettlebell 2027 PWA

Progressive Web App statica e offline-first per il programma annuale Kettlebell 2027.

## File

- `index.html` — applicazione completa.
- `manifest.webmanifest` — metadata PWA e icone.
- `sw.js` — service worker per uso offline.
- `icons/` — icone Android/iOS, inclusa maskable icon.
- `.nojekyll` — pubblicazione statica diretta su GitHub Pages.
- `GUIDA_GITHUB_PAGES.md` — guida operativa al deploy e all'installazione sul telefono.

## Dati personali dell'app

Completamenti, RPE e note sono salvati nel `localStorage` del browser sul singolo dispositivo. Non vengono caricati nel repository GitHub né inviati a un server.
