# 🏠 Dom-IQ

> La dashboard premium per Home Assistant: la tua casa in **3D** + energia, clima, sicurezza, robot, meteo e **qualsiasi card di Home Assistant** — tutto in un solo elemento Lovelace.

[![HACS](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://hacs.xyz)
[![License](https://img.shields.io/badge/license-Proprietary-blue)](#-licenza)

---

## ✨ Cosa offre

Una sola card che sostituisce decine di card Lovelace separate:

- **🏠 Mappa 3D interattiva** — la planimetria della tua casa con gli stati live di luci, tapparelle e dispositivi. Tocca una stanza per aprire i suoi controlli.
- **📐 Creazione stanze con disegno libero** — crea ogni ambiente direttamente sulla planimetria: rettangolo, cerchio o **disegno libero** punto-per-punto per riprodurre qualsiasi forma. Trascina, ruota e ridimensiona a piacere.
- **⚡ Energia & Solare** — produzione FV, consumi, batteria e rete in tempo reale; storico giornaliero, mensile e annuale; stima dei costi; autosufficienza; previsione di produzione solare e confronto previsto/reale.
- **🌡️ Clima multi-zona** — termostati e condizionatori, preset, sensori di temperatura e umidità per stanza.
- **🔒 Sicurezza & Camere** — allarme, telecamere (anche a schermo intero), serrature e sensori porta/finestra, con avvisi visivi.
- **🤖 Robot aspirapolvere** — avvio, stop, ritorno alla base, potenza di aspirazione e stato in tempo reale. Compatibile con i robot supportati da Home Assistant.
- **🌤️ Meteo & Sensori** — condizioni live, previsioni, pioggia, vento, umidità e sensori ambientali.
- **🎛️ Card Custom di Home Assistant** — aggiungi **qualsiasi** card Lovelace nativa o della community tramite il picker integrato. Più elenco dispositivi e link/dashboard esterne.
- **🔔 Notifiche intelligenti** — avvisi basati su stato, soglie o fasce orarie, con toast eleganti direttamente sulla dashboard.
- **👥 Persone** — avatar con stato "a casa" in tempo reale.
- **📊 HUD** — pillole configurabili (energia / meteo) sopra la mappa.
- **🌅 Sfondo dinamico** — cambia con l'ora del giorno e con il meteo.
- **🖥️ Modalità Kiosk** — per tablet a muro: nasconde le barre di Home Assistant, schermo sempre acceso e screensaver.
- **🌍 Multilingua** — Italiano · English · Español · Français · Deutsch.
- **🔄 Sync cross-device** — la configurazione è condivisa automaticamente su PC, tablet e telefono.
- **🎨 Editor visuale completo** — niente YAML: tutto si configura dentro la card.

---

## 🚀 Installazione

### Via HACS (raccomandato)

1. **[➕ Aggiungi a Home Assistant](https://my.home-assistant.io/redirect/hacs_repository/?owner=franctm17&repository=Dom-IQ&category=plugin)** (apre HACS sul tuo HA con il repository già pronto)
   — in alternativa: **HACS → menu (⋮) → Custom repositories**, URL `https://github.com/franctm17/Dom-IQ`, categoria **Dashboard/Lovelace**
2. Cerca **"Dom-IQ"** → **Download**
3. **Impostazioni → Sistema → Riavvia Home Assistant**

### Manuale

1. Scarica `domiq.js` dall'ultima [release](https://github.com/franctm17/Dom-IQ/releases)
2. Copialo in `/config/www/domiq.js`
3. **Impostazioni → Dashboard → Risorse → + Aggiungi risorsa**
   - URL: `/local/domiq.js` · Tipo: **Modulo JavaScript**

---

## 🔑 Attivazione licenza

1. Crea un account su **[dom-iq.com](https://dom-iq.com)**
2. Aggiungi la card a una dashboard: mostrerà il tuo **Dom-IQ-ID**
3. Inserisci il Dom-IQ-ID nel tuo account → ottieni la **license key** nella dashboard
4. Incolla la key nella card → ✅ attivata

- **Una licenza = un server**: la key è vincolata al tuo server Home Assistant.
- **Multi-utente**: tutti gli utenti dello stesso server usano la stessa licenza, in automatico.
- **Cambio server**: contatta il [supporto](https://dom-iq.com/support).

---

## ⚙️ Configurazione

1. **Dashboard → ⋮ → Modifica dashboard**
2. **+ Aggiungi card → Manuale**, incolla:
   ```yaml
   type: custom:domiq-card
   ```
3. **Salva**. Poi configura tutto dall'**editor visuale** (rotella ⚙): stanze, pannelli, persone, HUD e mappa.

Le modifiche si salvano e si **sincronizzano automaticamente** tra i dispositivi. Nessun YAML da scrivere a mano.

---

## 📦 Compatibilità

| Cosa | Requisito |
|---|---|
| **Home Assistant** | 2024.1 o superiore |
| **Browser** | Chrome ≥ 100, Safari ≥ 16.4, Firefox ≥ 100, Edge ≥ 100 |
| **Mobile** | App Companion Home Assistant |
| **Tablet a muro** | Fully Kiosk Browser, BrowserMod |

Funziona via **HTTP** in rete locale, **HTTPS**, **Nabu Casa** e qualsiasi altro accesso.

---

## ❓ FAQ

**Serve scrivere YAML?**
No. Tutto si configura dall'editor visuale dentro la card.

**Posso configurare più impianti fotovoltaici?**
Sì. Puoi creare più pannelli "Energia" con sensori diversi, ognuno con il proprio storico.

**Lo storico si perde con un aggiornamento?**
No. È salvato lato Home Assistant e sincronizzato tra i dispositivi; gli aggiornamenti HACS e i riavvii non lo cancellano.

**Funziona con più utenti dello stesso Home Assistant?**
Sì. Tutti gli utenti dello stesso server vedono la card già attivata e ogni utente controlla le entità a cui ha accesso.

**Se cambio il nome/posizione in Home Assistant, la card smette di funzionare?**
No. La licenza è legata all'ID di installazione del server, non al nome.

**Supporta la light mode?**
La card è ottimizzata per la dark mode.

---

## 🛠 Supporto

- 💬 **Supporto e assistenza**: [dom-iq.com/support](https://dom-iq.com/support)
- 🐛 **Bug**: [GitHub Issues](https://github.com/franctm17/Dom-IQ/issues)

---

## ⚖️ Licenza

Software **proprietario**. Il codice è pubblico per consentire audit di sicurezza, ma:

- ❌ Vietata la redistribuzione del bundle
- ❌ Vietato l'uso senza una license key valida
- ❌ Vietato rimuovere o aggirare il sistema di licenza
- ✅ Permesso segnalare bug pubblicamente

---

🌟 **Se ti piace il progetto, lascia una stella!**
