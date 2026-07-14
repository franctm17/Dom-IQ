## Dom-IQ v1.3.98

**Dom-IQ Link — configurazione del bot inclusa nel pacchetto (niente più passaggi a mano)**

Il motivo più comune per cui l'assistente su Telegram "non risponde" è la configurazione manuale dell'integrazione Telegram Bot (modalità sbagliata o il proprio chat id non tra gli *allowed chat ids*). Ora **non serve più**: il pacchetto generato **contiene già la configurazione del bot** (token + il tuo id), pronta.

- 📦 **Un solo file, una sola volta**: incolli `dom-iq-link.yaml`, riavvii, e sia la ricezione dei messaggi sia le automazioni sono a posto.
- ⚠️ **Importante**: se avevi aggiunto "Telegram Bot" dall'interfaccia di HA, **rimuovilo** — ora è definito nel pacchetto, altrimenti vanno in conflitto e il bot non riceve.
- ✅ Controlli integrati: se manca il token o il chat id non è un numero, la card te lo dice prima di generare.

_Dom-IQ BETA_
