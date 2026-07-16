## Dom-IQ v1.3.99

**Fix Dom-IQ Link — nome del file del pacchetto valido per Home Assistant**

- 🛠️ Home Assistant **non accetta i trattini** nel nome di un package: il file suggerito si chiamava `dom-iq-link.yaml` e HA lo scartava in blocco (*"invalid slug dom-iq-link, try dom_iq_link"*) → non si caricavano né il bot né le automazioni. Ora la card indica il nome corretto **`dom_iq_link.yaml`** (con underscore).

Se avevi già creato il file: **rinominalo** in `dom_iq_link.yaml` e riavvia HA. Ricorda: **un solo** ricevitore Telegram deve essere attivo — o quello incluso nel pacchetto, o l'integrazione ufficiale "Telegram Bot", non entrambi (altrimenti vanno in conflitto).

_Dom-IQ BETA_
