# Sito Latanza

Sito web professionale per lo studio del Dott. Latanza, pensato per presentare i servizi offerti, il profilo professionale e i contatti dello studio.

## Stack Tecnologico

* **Framework:** SvelteKit 5
* **Styling:** Tailwind CSS 4 (con i plugin `@tailwindcss/forms` e `@tailwindcss/typography`)
* **Icone:** Lucide Svelte
* **Build tool:** Vite
* **Linting & Formattazione:** ESLint + Prettier (con supporto per Svelte e Tailwind)

## Struttura del Progetto

Il sito è organizzato in componenti riutilizzabili all'interno di `src/lib/components/`:

* **Navbar** — Barra di navigazione principale
* **Hero** — Sezione di apertura della homepage
* **ChiSono** — Presentazione del professionista
* **Servizi** — Elenco dei servizi offerti
* **Contatti** — Informazioni e modalità di contatto
* **Footer** — Piè di pagina

Le pagine e il layout dell'applicazione si trovano in `src/routes/`.

## Configurazione e Avvio in Locale

### Installazione delle Dipendenze

```bash
npm install
```

### Avvio del Server di Sviluppo

```bash
npm run dev
```

Il sito sarà disponibile all'indirizzo `http://localhost:5173` (porta di default di Vite).

Per avviare il server e aprire automaticamente il browser:

```bash
npm run dev -- --open
```

### Build di Produzione

Per generare la versione ottimizzata per la produzione:

```bash
npm run build
```

È possibile visualizzare in anteprima la build di produzione con:

```bash
npm run preview
```

### Controllo Qualità del Codice

Per verificare la formattazione e la qualità del codice:

```bash
npm run lint
```

Per formattare automaticamente tutti i file:

```bash
npm run format
```

## Deploy

Il progetto utilizza `@sveltejs/adapter-auto`, che seleziona automaticamente l'adapter più adatto in base alla piattaforma di hosting scelta (Vercel, Netlify, ecc.). Per maggiori informazioni, consultare la [documentazione ufficiale degli adapter SvelteKit](https://svelte.dev/docs/kit/adapters).