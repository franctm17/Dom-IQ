## Dom-IQ v1.3.106

**Diagnostica integrata: basta andare a tentoni**

- 🔧 **Nuovo comando "diagnostica"**: apri l'assistente, scrivi `diagnostica` e premi invio. La card mostra un report completo di QUESTO dispositivo: **versione realmente in esecuzione** (svela subito se l'app sta usando una cache vecchia — il motivo più comune per cui "gli aggiornamenti non cambiano nulla"), stato dell'impronta vocale e dello spotter (attivo/punteggi/soglia), stato dell'audio, motori TTS visti da HA, e sorgenti licenza (per confrontare due dispositivi dello stesso server).
- 🏷️ **Versione visibile**: accanto al titolo "Dom-IQ Assistant" ora compare la versione in piccolo — a colpo d'occhio sai se il dispositivo è aggiornato.
- 🎤 **Test wake guidato**: la diagnostica spiega come verificare in 30 secondi se lo spotter *sente* ma *non riconosce* (→ ri-registrare l'impronta) o *non sente affatto* (→ microfono/audio della app).

📌 Se su un dispositivo i problemi "persistono nonostante gli aggiornamenti": quasi sempre la versione mostrata è vecchia → nell'app Home Assistant vai in *Impostazioni → App companion → Debug → Svuota cache frontend* (o cancella i dati dell'app) e riapri.

_Dom-IQ BETA_
