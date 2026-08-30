# Guida — pubblicare Kettlebell 2027 come PWA su GitHub Pages

Questa cartella è già pronta per GitHub Pages. Non servono Node.js, framework, build o App Store.

## 1. Crea il repository GitHub

1. Accedi a GitHub.
2. Seleziona **New repository**.
3. Usa un nome semplice, ad esempio `kettlebell-2027`.
4. Per GitHub Free, scegli **Public** se vuoi usare GitHub Pages senza un piano a pagamento.
5. Crea il repository.

> Il sito pubblicato con GitHub Pages è accessibile via Internet. Il programma di allenamento sarà quindi pubblicamente raggiungibile tramite URL. I dati che inserisci nell'app (RPE, workout completati, note) restano invece nel browser del dispositivo e non vengono caricati nel repository.

## 2. Carica i file — metodo senza terminale

Nel repository appena creato:

1. Apri la scheda **Code**.
2. Seleziona **Add file → Upload files**.
3. Carica il **contenuto** della cartella `kettlebell_2027_pwa`, mantenendo la cartella `icons`.
4. Verifica che `index.html`, `manifest.webmanifest` e `sw.js` siano nella root del repository.
5. Esegui **Commit changes** sul branch `main`.

Struttura finale attesa:

```text
kettlebell-2027/
├── index.html
├── manifest.webmanifest
├── sw.js
├── README.md
├── GUIDA_GITHUB_PAGES.md
├── .nojekyll
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── maskable-512.png
    └── apple-touch-icon.png
```

`.nojekyll` è utile ma non indispensabile per questa app. Se l'interfaccia di upload non mostra i file nascosti, puoi procedere anche senza quel file.

## 3. Attiva GitHub Pages

1. Nel repository apri **Settings**.
2. Nel menu laterale apri **Pages**.
3. In **Build and deployment**, alla voce **Source**, scegli **Deploy from a branch**.
4. In **Branch** scegli `main`.
5. Come directory scegli `/ (root)`.
6. Premi **Save**.

GitHub pubblicherà la PWA all'indirizzo simile a:

```text
https://TUO-USERNAME.github.io/kettlebell-2027/
```

Se invece il repository si chiama esattamente `TUO-USERNAME.github.io`, il sito sarà disponibile direttamente su:

```text
https://TUO-USERNAME.github.io/
```

## 4. Verifica la PWA

Apri l'URL HTTPS dal telefono almeno una volta con connessione Internet.

Controlla:

- la Home del programma si apre normalmente;
- il calendario e i workout sono navigabili;
- compare la card **Installa Kettlebell 2027**;
- dopo il primo caricamento, ricaricando senza rete, l'app continua ad aprirsi.

Il service worker funziona soltanto da HTTPS (o `localhost` per test), non aprendo direttamente `index.html` come file locale.

## 5. Installazione Android

Con Chrome/Edge Android:

1. Apri l'URL GitHub Pages.
2. Se compare **Installa** dentro l'app, premilo.
3. In alternativa usa il menu del browser e scegli **Installa app** o **Aggiungi a schermata Home**.
4. Conferma.

L'icona `KB 2027` comparirà nella Home/app launcher. L'app si aprirà in modalità standalone, senza la normale barra del browser.

## 6. Installazione iPhone / iPad

Con Safari:

1. Apri l'URL GitHub Pages.
2. Tocca **Condividi**.
3. Seleziona **Aggiungi alla schermata Home**.
4. Conferma con **Aggiungi**.

L'app userà `apple-touch-icon.png` come icona e si aprirà come web app standalone.

## 7. Aggiornare il programma in futuro

Quando modifichi `index.html` o altri file:

1. carica/committa la nuova versione su `main`;
2. GitHub Pages ripubblica automaticamente il sito;
3. quando modifichi in modo sostanziale risorse offline, cambia in `sw.js` la versione della cache, per esempio:

```javascript
const CACHE_NAME = "kb2027-pwa-v2";
```

Alla successiva apertura online, il nuovo service worker sostituirà la cache precedente.

## 8. Backup dei progressi

Attualmente completamenti, RPE e note sono conservati solo sul dispositivo tramite `localStorage`. Cancellando i dati del browser o rimuovendo il sito, possono andare persi.

Per una successiva evoluzione dell'app è consigliabile aggiungere **Esporta backup / Importa backup** in JSON, mantenendo comunque l'app senza backend.

## 9. Troubleshooting rapido

### Non compare "Installa"

- verifica di stare usando l'URL `https://...github.io/...`, non il file locale;
- apri il sito almeno una volta normalmente nel browser;
- controlla che `manifest.webmanifest`, `sw.js` e `icons/` siano pubblicati nello stesso percorso di `index.html`;
- su iPhone usa il percorso Safari → Condividi → Aggiungi alla schermata Home.

### L'app non funziona offline

Aprila una prima volta con rete. Il primo caricamento installa il service worker e salva l'app shell in cache.

### Dopo un aggiornamento vedo ancora la versione precedente

Aggiorna la versione `CACHE_NAME` in `sw.js`, fai commit e riapri la PWA mentre sei online.
