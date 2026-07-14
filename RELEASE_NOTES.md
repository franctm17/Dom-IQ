## Dom-IQ v1.3.96

**Fix Dom-IQ Link — pacchetto sempre valido**

- 🛠️ Il pacchetto generato poteva dare un errore YAML in Home Assistant (*"found character '@' that cannot start any token"*) quando il chat id era un `@nomecanale`, oppure quando un dispositivo non veniva rilevato (segnaposto). Ora il generatore **quota correttamente** il destinatario (numerico lasciato "nudo", `@canale`/segnaposto tra virgolette) e usa segnaposto sempre validi → il pacchetto si incolla e riavvia senza errori.

Se avevi già incollato la versione precedente: apri di nuovo **Impostazioni → Dom-IQ Link → Genera configurazione**, ricopia e sostituisci il file.

_Dom-IQ BETA_
