## Dom-IQ v1.3.97

**Dom-IQ Link — avviso se il chat id è sbagliato**

- ⚠️ L'errore più comune nel collegare Telegram è mettere nel campo *"Il TUO chat id"* un **@nome** (il nome del bot o del canale) invece del **tuo numero**. In quel caso Home Assistant scarta i messaggi e l'assistente non risponde. Ora, se premi **Genera configurazione** con un valore che non è numerico, la card te lo segnala subito e ti spiega come ottenere il numero (scrivendo a **@userinfobot**).

Promemoria: il chat id è **il tuo numero personale** (es. `123456789`), e va messo sia nel campo della card sia negli *allowed chat ids* dell'integrazione Telegram Bot in HA.

_Dom-IQ BETA_
