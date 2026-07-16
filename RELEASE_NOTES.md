## Dom-IQ v1.3.104

**Licenza: risolto "già attiva su un altro server" tra dispositivi dello stesso server + wake word di nuovo funzionante su mobile**

- 🔑 **"Licenza già attiva su un altro server" (stesso server, PC diverso) — risolto**: il PC non riusciva a riprodurre l'impronta del server (a cui è legata la licenza) e la scambiava per un altro server. Ora la card **propaga e adotta automaticamente l'identità del server** tra tutti i dispositivi tramite Home Assistant → l'impronta combacia ovunque e la licenza risulta attiva su ogni dispositivo, senza incollare nulla.
  - Per applicarlo: aggiorna la card a v1.3.104 su **tutti** i dispositivi, **apri una volta** la dashboard sul dispositivo dove è già attiva (telefono), poi **ricarica sul PC** → risulterà attiva.
- 🎙️ **Wake word su mobile di nuovo funzionante**: nell'ultima versione avevo reso i filtri troppo severi e la parola vera veniva rifiutata. Ripristinati i valori funzionanti. Per meno falsi positivi: imposta la **Sensibilità wake su "Bassa"** e, se serve, ri-registra l'impronta con 3 campioni puliti.

_Dom-IQ BETA_
