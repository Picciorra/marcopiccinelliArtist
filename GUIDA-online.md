# Galleria 3D di Marco Piccinelli — online con CMS

Guida pratica per pubblicare il sito e gestire le opere da un pannello, senza toccare il codice.

## Come sono organizzati i file

```
/ (radice del sito)
├── galleria-3d.html      → la galleria 3D (pagina principale, o rinominala index.html)
├── opere.json            → la lista delle opere (la gestisce il CMS)
├── admin/
│   ├── index.html        → il pannello CMS
│   └── config.yml        → configurazione del pannello
└── images/opere/         → qui finiscono le foto caricate dal pannello
```

Il sito è statico: legge `opere.json` e disegna la galleria. Il CMS non fa altro che
modificare `opere.json` e caricare le foto in `images/opere/`. Quando salvi, il sito si
aggiorna da solo.

---

## Passo 1 — Metti i file su GitHub

Serve un account gratuito su github.com.

1. Crea un nuovo repository (es. `galleria-piccinelli`), privato o pubblico.
2. Carica tutti i file qui sopra mantenendo la struttura delle cartelle.
   (Puoi trascinarli nella pagina del repo con "Add file → Upload files".)
3. Se vuoi che la galleria sia la home, rinomina `galleria-3d.html` in `index.html`.

## Passo 2 — Pubblica su Netlify (gratis)

1. Vai su netlify.com, accedi con GitHub.
2. "Add new site" → "Import an existing project" → scegli il repo.
3. Lascia i campi di build vuoti (è un sito statico, nessuna build) e conferma.
4. In un minuto il sito è online su un indirizzo tipo `nome-a-caso.netlify.app`.
   Già così puoi vederlo e mostrarlo a Marco.

## Passo 3 — Attiva il pannello CMS

Il CMS usa il login di Netlify per farti entrare e salvare le modifiche.

1. Nel sito su Netlify: **Site configuration → Identity → Enable Identity**.
2. In **Identity → Registration** metti "Invite only" (così solo tu entri).
3. Sempre in Identity, abilita **Git Gateway** (Services → Git Gateway → Enable).
4. Torna su **Identity → Invite users** e invita la tua email. Arriva un invito,
   imposti la password.
5. Apri `https://TUO-SITO/admin/` → fai login → vedi la sezione "Opere".

Da qui aggiungi/modifichi le opere e carichi le foto. Ogni salvataggio aggiorna il sito.

> Nota: nel file `admin/config.yml` controlla che `branch:` sia il nome del tuo branch
> principale su GitHub (di solito `main`).

## Passo 4 — Il dominio

Il `.netlify.app` va bene per le prove. Per il dominio vero:

1. Compra il dominio (es. `marcopiccinelli.com`, `marcopiccinelli.art` o `.it`).
   Registrar consigliati: Cloudflare, Namecheap, o un registrar italiano per il `.it`.
   Costo indicativo: 10–20 €/anno.
2. Su Netlify: **Domain management → Add a domain** → inserisci il dominio.
3. Netlify ti dà i record DNS da impostare (o i nameserver da usare). Li incolli nel
   pannello del registrar. In poche ore il dominio punta al sito.
4. L'**HTTPS** si attiva da solo (certificato gratuito).

---

## Come aggiungere un'opera (uso quotidiano)

1. Vai su `https://TUO-SITO/admin/` e accedi.
2. "Opere" → "Add Opera".
3. Compila: Titolo, Anno, Dimensioni, Stato (Disponibile/Venduta).
4. **Parete**: in fondo / sinistra / destra. **Posizione**: 0 = centro, oppure -2.2 / 2.2
   per spostarla di lato (utile se metti più opere sulla stessa parete).
5. Carica la **Foto dell'opera**.
6. "Publish". Fatto: l'opera compare nella galleria.

Se non carichi una foto, viene mostrata una texture segnaposto (puoi cambiarne il
disegno con i campi "Seed" e "Palette").

## Consigli

- **Foto**: caricale già ottimizzate (lato lungo ~1600 px, JPG). Le opere d'arte in
  altissima risoluzione appesantiscono il caricamento.
- **Quante opere**: 5–8 per sala rendono bene. Se diventano molte, meglio più "sale"
  o una griglia 2D di supporto.
- **Backup**: essendo tutto su GitHub, ogni modifica è versionata e reversibile.

## Se un domani vuoi cambiare piattaforma

Tutto è codice tuo e dati in un JSON: puoi spostare il sito su qualsiasi hosting
statico (Cloudflare Pages, Hostinger, ecc.) senza riscrivere nulla. Nessun lock-in.
