# 🏠 Domiq

> Card premium per Home Assistant — dashboard 3D interattiva, energia, meteo, sicurezza, robot, allarme, climate, persone. Tutto in un singolo elemento Lovelace.

[![HACS](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://hacs.xyz)
[![License](https://img.shields.io/badge/license-Proprietary-blue)](#-licenza)

---

## 📋 Indice

- [Installazione](#-installazione)
- [Attivazione licenza](#-attivazione-licenza)
- [Configurazione card](#-configurazione-card)
- [Funzionalità](#-funzionalità)
  - [Mappa 3D interattiva](#-mappa-3d-interattiva)
  - [Pannello Energia](#-pannello-energia)
  - [Pannello Meteo](#-pannello-meteo)
  - [Pannello Sicurezza](#-pannello-sicurezza)
  - [Pannello Robot](#-pannello-robot)
  - [Pannello Allarme](#-pannello-allarme)
  - [Pannello Climate](#-pannello-climate)
  - [Card Persone](#-card-persone)
  - [HUD pillole](#-hud-pillole)
  - [Sfondo dinamico](#-sfondo-dinamico)
- [Personalizzazione](#-personalizzazione)
- [Compatibilità](#-compatibilità)
- [FAQ](#-faq)

---

## 🚀 Installazione

### Via HACS (raccomandato)

1. **HACS → menu (⋮) → Custom repositories**
2. URL: `https://github.com/franctm17/Domiq` · Categoria: **Lovelace**
3. Cerca "Domiq" nella lista frontend → **Download**
4. **Settings → System → Restart Home Assistant**

### Manuale

1. Scarica `domiq.js` dall'ultima [release](https://github.com/franctm17/Domiq/releases)
2. Copia in `/config/www/domiq.js`
3. **Settings → Dashboards → Resources → + Add Resource**
   - URL: `/local/domiq.js` · Tipo: **JavaScript Module**

---

## 🔑 Attivazione licenza

Dopo l'installazione la card mostra una schermata di pre-attivazione con il tuo **Domiq-ID**.

1. **Acquista** una licenza (contatta il supporto per i prezzi)
2. **Copia il Domiq-ID** della tua istanza HA dalla card
3. **Inviaci l'ID** insieme al pagamento
4. **Ricevi la license key** via email
5. **Incollala** nella card → ✅ unlock

### Caratteristiche del licensing

- **Una licenza, un server**: la key è vincolata al Domiq-ID del tuo server. Stessa key non funziona altrove.
- **Multi-utente same-server**: tutti gli utenti dello stesso HA possono usare la card. Se l'admin attiva, la key si propaga automaticamente al YAML del dashboard.
- **Funziona offline**: dopo la prima attivazione, non serve internet (verifica firma locale Ed25519).
- **Cambio server**: contatta il supporto per ottenere una nuova key.

---

## ⚙️ Configurazione card

### Aggiungere la card

1. **Dashboard → ⋮ → Edit Dashboard**
2. **+ Add Card → Manual**
3. Incolla:
   ```yaml
   type: custom:domiq-card
   ```
4. **Save**

Il `card_id` viene generato automaticamente al primo salvataggio. Non devi configurarlo manualmente.

### Configurare il contenuto

La card ha un **editor visuale completo** dentro l'interfaccia stessa:

- Click sulla rotella **⚙ Impostazioni** in alto a destra
- Configura **titolo**, **panels**, **persone**, **HUD pillole**, **mappa 3D**
- Tutte le modifiche si salvano automaticamente (sincronizzate fra dispositivi via HA storage)

Niente YAML da editare manualmente.

---

## 🌟 Funzionalità

### 🗺 Mappa 3D interattiva

- **Modello 3D della tua casa** caricato da immagine personalizzata
- **Zone cliccabili** sulle stanze: tap su una stanza apre il pannello con i suoi dispositivi
- **Stato luci/sensori** in tempo reale tramite glow colorati per stanza
- **Override personali**: ogni utente può personalizzare l'icona/nome di ogni dispositivo
- **Camere stanza**: ogni stanza ha la sua collezione di dispositivi (luci, prese, fan, climate, ecc.)
- **Drag & drop** in modalità arrange per riposizionare le zone

### ⚡ Pannello Energia

#### Caratteristiche

- **Real-time**: produzione FV, consumo casa, prelievo/immissione rete, batteria
- **Storico professionale**: dati giornalieri sealed alle 23:55 (immutabili dopo)
- **Aggregazioni**: settimana corrente/scorsa, mese corrente/scorso, anno corrente/scorso
- **Multi-impianto**: configura più pannelli energia con sensori diversi → storici separati
- **Costi e ricavi**: calcolo bolletta in base a tariffe F1/F2/F3 italiane, immissione in rete
- **Autosufficienza**: % auto-consumo + rapporto FV/load + risparmio vs no-FV

#### Previsioni solari professionali

Sistema di previsione **astronomicamente accurato**:

1. **Solar elevation** calcolato con formula NOAA (lat/lng dalla config HA + ora del giorno)
2. **Clear-sky factor** modellato con trasmittanza atmosferica
3. **Cloud modulation** dal weather forecast orario (`cloud_coverage` o `condition`)
4. **Historical correction**: media trimmed degli ultimi 14 giorni `actual/theoretical` → fattore impianto-specifico (orientamento, ombre, sporcizia, degradazione)
5. **Realtime calibration**: dopo le 6 di mattina, scala le ore future col rapporto effettivo finora osservato
6. **Confidence score**: 0-1, riflette quanti dati affidabili abbiamo

#### Confronto previsto vs reale

Tabella accuratezza con i giorni passati: `previsto X kWh · reale Y kWh · errore Z%`. Permette di valutare l'affidabilità del modello.

#### Notifiche intelligenti

- **Mattutina** (es. 7-8): previsione del giorno + suggerimenti
- **Serale** (es. 21-22): riepilogo + previsione domani
- Disabilitabili per pannello

#### Sensori richiesti (minimi)

```yaml
# Almeno UNO di questi
pv_today: sensor.fotovoltaico_oggi      # kWh prodotti oggi
pv_total: sensor.fotovoltaico_lifetime  # kWh totali (counter)

# Per il forecast
weather_entity: weather.casa
pv_peak_kw: 6                            # potenza nominale impianto in kWp
```

I valori `_today` mancanti vengono calcolati dal bilancio energetico (`pv + imp + batD - exp - batC`).

### 🌤 Pannello Meteo

- **Condizioni live**: temperatura, umidità, vento (con raffiche e direzione)
- **Pioggia**: rate corrente, totale giorno/settimana/mese/anno
- **UV index** + radiazione solare
- **Pressione atmosferica + dew point**
- **Temperatura interna** + umidità interna
- **Forecast 7 giorni** con condizione, max/min, probabilità pioggia
- **Forecast orario** (24h)

### 🔒 Pannello Sicurezza

- **Serrature**: stato + comando lock/unlock con conferma
- **Sensori porta/finestra**: stato aperto/chiuso
- **Telecamere**: thumbnail MJPEG live + fullscreen
- **Allarmi**: card dedicata con stati arm_home/arm_away/arm_night/disarmed
- **Badge alert**: pallino rosso sulla card-pulsante quando c'è una porta aperta o serratura sbloccata

### 🤖 Pannello Robot (vacuum + tagliaerba)

Supporto **multi-marca**:
- Vacuum: Roborock, Xiaomi, Dreame, Ecovacs, Roomba, ecc.
- Lawn mower: Worx, Husqvarna, Stihl, Gardena, Robonect, ecc.

#### Funzionalità

- **Stato**: in pulizia / docking / errore / pausa con icone state-aware
- **Batteria %** + tempo ciclo + area pulita
- **Mappa interattiva** (auto-detect camera mappa)
- **Stanze cliccabili**: pulizia mirata via `app_segment_clean` / `vacuum.send_command`
- **Selettore potenza aspirazione** (Quiet/Normal/Max/Max+)
- **Livello acqua** (per aspira+lava)
- **Manutenzione**: spazzole, filtro, lame con % usura e alert <25%
- **Storico cicli**: ultimi 10 cicli + totali (area, tempo, n°)
- **Tagliaerba dedicato**: pioggia, zone prato, modalità edge, ore lame
- **Tema colore** per tipo: blu vacuum, verde mower, ciano piscina

### 🚨 Pannello Allarme

- **Stati standard HA**: armed_home, armed_away, armed_night, armed_vacation, disarmed, triggered
- **Pre-arm dialog** con sensori aperti rilevati: opzione "ignora" o "force-arm" (Alarmo)
- **Codice numerico** con UI keypad responsive
- **Wrong-password warning** con shake animation
- **Countdown** exit-delay
- **Multi-stato**: card sicurezza + card stand-alone

### 🌡 Pannello Climate

- **Termostati**: target temp, current temp, fan modes, swing
- **Preset** (eco, comfort, away, sleep)
- **Range mode** per heat_cool con due cursori
- **Override** modalità via tap sul tipo (heat/cool/auto/off)

### 👥 Card Persone

- **Avatar foto/iniziali**: se non configuri iniziali, prende la foto dalla person entity HA
- **Outline verde animato** quando la persona è "home"
- **Click → more-info** dell'entità person

### 📊 HUD pillole

Due pillole configurabili (sinistra e destra) sopra la mappa 3D. Tipi disponibili:

- **Energia**: produzione + consumo realtime in W con colori semaforo
- **Meteo**: temp + umidità + icona condizione

### 🌅 Sfondo dinamico

Sfondo gradient che cambia in tempo reale:

- **Time-aware**: usa `sun.sun` di HA per **alba/tramonto reali** (varia con stagione)
  - Estate: sfondo "giorno pieno" più ampio
  - Inverno: tramonti precoci, notte più lunga
- **Phase-based**: notte profonda → pre-dawn → dawn → mattina → mezzogiorno → golden hour → sunset → dusk
- **Sole/luna astronomici**: posizione su arco da sunrise (sx) → noon (top) → sunset (dx)
- **Meteo-aware**: pioggia/neve/nuvole/temporale/nebbia modulano colori e aggiungono effetti animati (gocce di pioggia, fiocchi di neve, lampi, ecc.)

---

## 🎨 Personalizzazione

### Per ogni dispositivo nelle stanze

- **Nome custom**: sostituisce il `friendly_name` HA
- **Icona custom**: emoji + override per stato (es. icona diversa per acceso/spento)
- **Colore accent**: customizzabile per dispositivo

### Per ogni stanza

- **Etichetta + icona** custom
- **Colore accent** della stanza (glow + accent bar)
- **Posizione zona** sulla mappa 3D
- **Layout della camera**: griglia di dispositivi con drag & drop per riordinare

### Tema

- **Cromia** della card è coerente: ogni pannello ha il suo colore tema (energia gialla, meteo azzurra, sicurezza rossa, ecc.)
- **Container queries** responsive: la card si adatta da 320px a 1920px+

### Posizione nav bar

- **Bottom** (default), **top**, **left**, **right**
- Personalizzabile in modalità "arrange" da menu

### Dimensione card

- Minimum height 520px
- Container queries built-in: tutti i font, padding, gap si scalano automaticamente

---

## 📦 Compatibilità

| Cosa | Versione minima |
|---|---|
| **Home Assistant** | 2024.1 |
| **Browser** | Chrome ≥ 100, Safari ≥ 16.4, Firefox ≥ 100, Edge ≥ 100 |
| **Mobile** | App Companion HA |
| **Wallpanel** | Fully Kiosk Browser, BrowserMod |
| **Tablet** | iOS 16+, Android 10+ |

### Funziona su HTTP non-localhost?

Sì. La card include un polyfill crittografico (`tweetnacl`) che permette di lavorare anche dove `crypto.subtle` non è disponibile (IP della LAN su HTTP). Performance leggermente inferiore ma funzionale.

### Multi-utente HA

Funziona anche con utenti non-admin: la card mostra il more-info delle entità a cui l'utente ha accesso. Le impostazioni della card sono per-istanza HA (server-wide), non per-utente.

---

## ❓ FAQ

### Quanto tempo prima che le previsioni siano accurate?

- **Giorni 1-2**: previsioni basate solo su astronomia + meteo (accuratezza ~75-80%)
- **Giorni 3-7**: historical correction comincia ad essere significativo
- **Giorni 7-14**: previsioni molto accurate, calibrate sull'impianto specifico (~90-95%)

### Posso avere più impianti FV?

Sì. Crea più pannelli "Energia" via ⚙ Impostazioni con sensori diversi. Ognuno ha il suo storico, le sue previsioni e il suo historical correction factor (orientamento, ombre — calcolato per impianto).

### Lo storico si perde con un update?

No. Lo storico è salvato in:
- **HA storage** (server-wide, sincronizzato fra browser/utenti)
- **localStorage** (cache locale per performance)

Update HACS / restart HA non lo cancellano.

### Cosa succede se cambio il `pv_peak_kw`?

La previsione si ricalcola immediatamente. L'historical correction si autocalibra nei giorni successivi.

### Cambio location_name in HA — la card si rompe?

No. Il binding licenza è basato su `hass.config.uuid` (install ID stabile), non su location_name. Solo una reinstallazione completa di HA (senza backup) cambia l'uuid.

### La card è sicura?

- Codice **offuscato** con javascript-obfuscator (string array RC4, control flow flattening, self-defending)
- License key firmate **Ed25519** (algoritmo crittografico standard)
- Public key embedded nel bundle, private key MAI distribuita
- Lista revoca scaricata da GitHub raw ad ogni reload (revoche immediate)
- Bundle validato via SHA-256 prima dell'esecuzione

### Posso usare la card su tablet wallpanel offline?

Sì. La card cachea il bundle e funziona anche con il dispositivo offline. La verifica licenza richiede internet ogni 7 giorni; oltre, la card va in modalità di fallback.

### Supporta light mode?

La card è ottimizzata per dark mode. Light mode è in roadmap.

---

## 🛠 Supporto

- 🐛 **Bug**: [GitHub Issues](https://github.com/franctm17/Domiq/issues)
- 💬 **Forum**: [community.home-assistant.io](https://community.home-assistant.io/)
- ✉️ **Email**: support@domiq.app (se configurato)

---

## ⚖️ Licenza

Software **proprietario**. Il codice è disponibile pubblicamente per audit di sicurezza, ma:

- ❌ **Vietata** la redistribuzione del bundle
- ❌ **Vietato** uso senza license key valida
- ❌ **Vietato** rimuovere/bypassare il sistema di licensing
- ✅ **Permesso** modificare il codice per uso personale
- ✅ **Permesso** segnalare bug pubblicamente

---

🌟 **Se ti piace il progetto, lascia una stella!**
