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

Completamenti, RPE, note e preferenze sono salvati nel `localStorage` del browser sul singolo dispositivo. Non vengono caricati nel repository GitHub né inviati a un server.

## Backup / Restore JSON

Dalla Home dell’app:

- **Backup JSON** scarica un file `kettlebell-2027-backup-YYYY-MM-DD.json` con tutti i dati locali dell’app.
- **Ripristina** permette di selezionare quel file su questo o su un altro dispositivo.
- Il restore sostituisce i dati locali `kb2027-*` presenti sul dispositivo; l’app chiede conferma prima di procedere.

Conserva il file JSON in un luogo sicuro (ad esempio Drive/iCloud/Files).
## Stato workout nel calendario
- Pallino rosso: workout pianificato / da completare.
- Pallino verde: workout completato.
- Lo stato si aggiorna automaticamente quando si torna alla vista mensile.

