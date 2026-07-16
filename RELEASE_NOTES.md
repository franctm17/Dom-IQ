## Dom-IQ v1.3.101

**Dom-IQ Link — solo automazioni, il bot lo gestisce l'integrazione ufficiale**

- 🧹 Il pacchetto generato **non contiene più il blocco `telegram_bot:`**: la ricezione dei messaggi la gestisce l'integrazione **ufficiale "Telegram Bot"** di HA. Così niente conflitti e niente configurazioni doppie — il file `dom_iq_link.yaml` contiene solo le automazioni.
- 📡 Promemoria in chiaro nella card: l'integrazione Telegram Bot deve essere in modalità **Polling** (la modalità *Broadcast* invia soltanto e **non riceve** i messaggi) con il tuo chat id negli *allowed chat ids*.

_Dom-IQ BETA_
