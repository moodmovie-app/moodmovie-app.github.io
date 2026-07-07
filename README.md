# MoodMovie

App PWA di scoperta film/serie TV per mood, basata su TMDB. Non riproduce
contenuti: mostra dove guardare legalmente un titolo (piattaforme in
abbonamento, noleggio/acquisto) e genera entrate tramite link di
affiliazione e pubblicità.

Live su: **https://moodmovie-app.github.io/**

## Struttura

```text
├── index.html        # app principale (telefono/desktop, PWA)
├── tv.html / tv-app.js  # variante per Smart TV (senza consenso cookie/monetizzazione, vedi sotto)
├── sw.js              # service worker (funzionamento offline/installabile)
├── manifest.json      # manifest PWA
├── privacy.html        # Privacy Policy, cookie, disclosure affiliazione
```

## Attivare la monetizzazione reale

Tutti i placeholder sono raccolti in un solo punto, in cima allo script di
`index.html`, nell'oggetto `MONETIZATION`:

```js
const MONETIZATION = {
    vpnUrl: 'https://nordvpn.com/',       // sostituisci col tuo link di affiliazione VPN
    amazonAssociateTag: 'moodmovie-21'    // tag Amazon Associates reale, già attivo
};
```

Per la pubblicità, cerca `function loadAds()` nello stesso file: contiene le
istruzioni commentate per collegare il tuo publisher ID Google AdSense.

## Deploy

Il repository si chiama esattamente `moodmovie-app.github.io` (come
l'organizzazione): questo lo rende automaticamente il "sito principale"
dell'organizzazione su GitHub Pages, pubblicato alla radice del dominio
(nessuna sottocartella). Ogni `git push` sul branch `main` aggiorna il sito
online entro un minuto, senza costi né limiti di build.

## Stato monetizzazione

- **VPN (Surfshark)**: richiesta inviata, in attesa di approvazione.
- **Amazon Associates**: approvato, tag `moodmovie-21` attivo.
- **Google AdSense**: iscrizione in corso.

## Nota sulla versione TV

`tv.html`/`tv-app.js` hanno la stessa rimozione del player pirata e lo stesso
pannello "Dove guardarlo", ma **non** hanno banner cookie né link di
affiliazione (la navigazione a telecomando rende scomodo un banner
cliccabile). Da aggiungere in un secondo momento se l'app TV viene
pubblicata seriamente.
