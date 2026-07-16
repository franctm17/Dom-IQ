## Dom-IQ v1.3.103

**Licenza attiva su tutti i dispositivi in automatico + wake word più precisa su mobile**

- 🔑 **Attivazione automatica ovunque**: se attivi la licenza da un dispositivo, ora **tutti gli altri** (PC compreso, anche via DuckDNS) risultano attivi **da soli** — senza incollare nulla nel YAML. La card propaga la licenza a tutto il server tramite Home Assistant, anche quando la dashboard è in modalità YAML o l'utente non è amministratore (era il caso in cui "da mobile attiva, da PC no"). Ogni dispositivo attivo la mantiene viva per gli altri, anche dopo un riavvio.
- 🔇 **Meno falsi positivi (versi) su mobile**: con l'impronta vocale registrata, ho reso più severi i filtri anti-rumore (dinamica e soglia di somiglianza) → i versi/rumori monotoni non attivano più l'assistente.
- 📍 **Niente plancia "fantasma"**: l'assistente si apre sulla plancia che **stai davvero usando** (ora conta anche l'ultima plancia che hai toccato), mai su una dashboard rimasta in background.

💡 Se hai ancora qualche attivazione di troppo, imposta la **Sensibilità wake** su *Bassa* nelle impostazioni: massima precisione.

_Dom-IQ BETA_
